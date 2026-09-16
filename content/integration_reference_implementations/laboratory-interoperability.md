# Laboratory interoperability reference implementation { #lab_interop }

> This guide accompanies the [laboratory interoperability reference implementation](https://github.com/dhis2/reference-dhis2-tracker-lab-result-integration)

## Introduction { #lab_interop_introduction }

This guide is for implementers who are considering, evaluating, or actively working with the DHIS2 laboratory interoperability reference implementation. A DHIS2 reference implementation is a well-documented, working starting point that demonstrates one way to solve an integration problem. It is meant to be adapted to your own context rather than deployed as-is — it shows one set of answers to a set of design questions you will still need to answer for yourself.

Laboratory results are one of the more common — and more painful — interoperability problems in DHIS2 implementations. Laboratory systems are almost always external to DHIS2, run by a different team, and often not designed with DHIS2 in mind. Results need to reach the right person's record reliably, without manual re-entry and without the risk of a result landing against the wrong case. This reference implementation demonstrates one concrete way to solve the "getting the result in" half of that problem.

Laboratory data is a key part of any surveillance system, but what counts as relevant varies — both by disease and by country, since not every test is performed at every level of the health system. Beyond getting a result onto the right case, it's often also useful to be able to track how the laboratory side of the process is performing, e.g. turnaround times.

It's worth keeping in mind, though, that system interoperability isn't a prerequisite for capturing laboratory data in a surveillance system. Giving laboratory staff direct access to enter just the relevant results into the surveillance system can meaningfully speed up data capture at relatively low cost, without any integration work at all. Whether interoperability is worth the investment over a simpler approach like that is a cost/benefit and sustainability question implementers should work through for their own context before committing to it — this guide picks up once that decision has already been made in favour of interoperability.

## What this guide covers — and what's in the repository { #lab_interop_scope }

Laboratory results are typically entered by hand into whatever case-based surveillance or EMR-style program holds the patient's record. Manual entry is slow, prone to transcription errors, and delays the information reaching the health workers and managers who need it. Sending the result electronically instead — straight from the laboratory system into DHIS2 — speeds up that decision-making, removes the retyping step (and the errors that come with it), and makes the result available to everyone with access to the record as soon as it lands.

The system on the other side of this integration is usually a **Laboratory Information System (LIS)**: a system built specifically to support laboratory workflow — tracking a specimen from intake through testing to reported result, and making that result available, in a timely and complete way, to the laboratory staff, clinicians, and other stakeholders who rely on it.

This reference implementation covers **the flow of test results into DHIS2 — it does not cover placing test orders.** The scenario it addresses is: a specimen has already been collected and identified, the laboratory has processed it, and the result now needs to reach the correct record in DHIS2. Ordering workflows are explicitly out of scope; this reference implementation's responsibility begins once a specimen ID already exists in DHIS2. Generating that ID and placing the underlying laboratory order are assumed to have happened earlier in the broader surveillance workflow — for example, at the point of initial clinical diagnosis.

### This guide vs. the repository { #lab_interop_guide_vs_repository }

The two are meant to be read together, and they do different jobs:

| This guide | The [repository](https://github.com/dhis2/reference-dhis2-tracker-lab-result-integration) |
| --- | --- |
| What laboratory interoperability involves, conceptually | The working code |
| The design decisions you face, the options available, and their tradeoffs | Quick start, Docker setup, and how to run it |
| Which answers this reference implementation chose, and why | Architecture diagrams and implementation detail |
| General recommendations applicable to any context | Configuration, mapping files, and test scripts |

Where this guide describes something the reference implementation actually does, it points to the relevant part of the repository rather than repeating the detail.

## Prerequisites and assumptions { #lab_interop_prerequisites }

This reference implementation assumes the country implementation has already worked out a mechanism for assigning a **specimen ID**. How that ID is generated or assigned is outside the scope of this guide — the reference implementation takes it as a given and builds the results workflow on top of it.

This reliance on the specimen ID brings two preconditions with it:

* The specimen ID must already exist in DHIS2 before the result arrives — registered at the facility, and searchable or entered into the surveillance program, prior to synchronisation.
* The laboratory system must reuse that same, pregenerated specimen ID when it later returns the result.

Two further points worth being explicit about:

* Uniqueness needs to hold across the whole set of laboratory requests, not just within a single case — two different cases must never be able to collide on the same specimen ID.
* This implementation takes the specimen ID as unique and correct. It does not detect or resolve duplicate or malformed IDs.

If your context doesn't yet have a specimen ID mechanism in place, that work needs to happen before this reference implementation becomes useful to you.

The specimen ID is not the only possible way to link a laboratory result back to a case, and the choice of linking identifier is a design decision in its own right — see [How a case is uniquely identified](#lab_interop_decision_identifier) below.

## How laboratory interoperability works { #lab_interop_how_it_works }

At a high level, any laboratory result interoperability solution needs four things in place, regardless of the specific technology behind them:

* **DHIS2** — holds the record where the specimen was registered against a specimen ID, and where the result ultimately needs to land.
* **A source system producing the result** — something that produces the result once the laboratory has finished processing the specimen, in a form other systems can consume. In production this is the LIS. In this reference implementation, a HAPI FHIR server plays this role, standing in for a real LIS.
* **A shared way of structuring the result** — an agreed structure, ideally backed by an existing standard, that both sides understand, so that any system producing results in that shape can be picked up on the destination side without a bespoke integration per laboratory. In this reference implementation, that role is played by HL7 FHIR's [Universal Laboratory Report IG](https://build.fhir.org/ig/HL7/uv-lab-rep-ig/).
* **Something that moves the result between them** — the component that fetches the result, transforms it, and writes it into DHIS2. This is the part implementers have to build, buy, or configure, and it is where most of the decisions in this guide land. In this reference implementation it is the Interoperability Layer (IOL), an Apache Camel application in the repository's `iol` directory.

None of these four roles is tied to a particular product — swapping in a real LIS, a different results standard, or a different destination system changes how each piece is implemented, not the overall shape of the integration. This reference implementation picks HAPI FHIR and the Universal Laboratory Report IG specifically to demonstrate the DHIS2-facing half of the integration — how a correctly structured result gets matched and imported — without needing a real laboratory vendor's system connected. Implementers are expected to swap in their own LIS's actual output, and, where it makes sense, a different results standard, on the source side.

### The shape of the flow { #lab_interop_flow }

The flow follows the same shape as the specimen ID assumption described earlier: a specimen is registered in DHIS2 and assigned an ID before the laboratory is ever involved. The laboratory processes the specimen and produces a result, structured according to the agreed shared format and referencing that same specimen ID. That result is then matched back to the correct record using the specimen ID and written into the relevant program.

At its core, the work of moving the result is a three-step pipeline:

1. **Fetch** the result from the laboratory system once it's ready.
2. **Transform** it into the shape DHIS2 expects.
3. **Write** it into the correct record via the DHIS2 API.

This guide covers the decisions you face at each of those three steps. The repository shows one concrete implementation of them — see its README and architecture diagram for how the IOL carries them out.

### The DHIS2 side: three logical stages { #lab_interop_dhis2_stages }

On the DHIS2 side, this typically plays out across three logical stages of the same case record:

* an **enrollment stage**, where the case is registered against a suspected diagnosis;
* a **laboratory request stage**, where the specimen ID (and any other linking identifiers) are captured, establishing the link the sync process will later use; **TODO**
* a **laboratory result stage**, which starts out empty and is the one this reference implementation is responsible for populating once a matching result becomes available.

Completing the laboratory request stage doesn't itself trigger a laboratory order — ordering is assumed to already be underway elsewhere in the workflow.

### Simulating the laboratory side { #lab_interop_simulating_the_lab }

Since there's no real-world LIS in this reference implementation, a set of scripts stands in for one. Their job is to create the FHIR resources that a real LIS would otherwise produce and make available on the FHIR server, so that the DHIS2-facing half of the integration has something realistic to work against. In the repository these are run with the Bruno script runner, and they stand in for the laboratory analyser that would report results to a real LIS.

These scripts walk through the same lifecycle a real laboratory would, end to end:

* Create an anonymous patient on the FHIR server — a placeholder patient record to attach the specimen and result to, since this is a demo and not tied to any real identity.
* Fetch laboratory requests from DHIS2 and create a matching specimen on the FHIR server — mirroring the moment a real laboratory receives a specimen for an order that already exists in DHIS2.
* Create a laboratory "observation" from that request — the raw result value the laboratory would have measured.
* Create a laboratory request in the FHIR server that, in turn, is used to fetch the "LIS Diagnostic Report" — the packaged FHIR resource, shaped per the Laboratory Report IG, that DHIS2 ultimately consumes.

In a production setting, these steps would be performed by the real LIS itself. Here, the scripts exist purely to generate realistic test data so implementers can see the full round trip without needing a real laboratory system connected. They are a test kit, not part of the integration — an adaptation drops them.

### Mapping laboratory results to DHIS2 { #lab_interop_mapping }

The other piece implementers will want to understand is how data coming from the source system — the FHIR server, in this reference implementation — actually lands in the right place in DHIS2. That mapping is not hardcoded into the integration logic. It is **driven from DHIS2**, and it comes in two parts.

**Structural mapping — FHIR resources to DHIS2 events.** The DHIS2 datastore holds a [DataSonnet](https://datasonnet.github.io/datasonnet-mapper/datasonnet/latest/index.html) script that translates the incoming FHIR resources into a DHIS2 Tracker event. DataSonnet is a JSON-oriented template language well suited to JSON-to-JSON transformation. The IOL fetches this script from the datastore at runtime and applies it to each diagnostic report, so changing the transformation is a datastore edit rather than a code change and redeployment.

**Terminology mapping — laboratory codes to DHIS2 metadata.** DHIS2 binds its own data elements and option set values to laboratory terminology using metadata **attributes**. Each data element or option that corresponds to a laboratory concept carries the relevant code in a dedicated attribute; the IOL reads those attribute values and builds a lookup from laboratory code to DHIS2 code. For example, an option set value config can map either the LOINC code `LA11882-0` or `LA6576-8` to the option set value `POSITIVE`. Because the event is imported using the `CODE` identifier scheme for data elements, the mapping targets stable codes rather than instance-specific UIDs.

The benefit of this arrangement is a clean separation of responsibility: an implementer can revise the code mappings inside DHIS2 without involving the technical team that maintains the IOL, and an implementer comfortable with DataSonnet and the DHIS2 Web API can adjust the structural transformation too — again without touching the IOL. This is one of the main places you'll customise this reference implementation for your own context.

The mapping itself can be built on any coding system supported by the implementation guide you've chosen to follow (LOINC, SNOMED CT, and others) — in this reference implementation's case, the [Universal Laboratory Report IG](https://build.fhir.org/ig/HL7/uv-lab-rep-ig/) allows for [LOINC](http://loinc.org) and [NPU](http://terminology.hl7.org/6.2.0/CodeSystem-NPU.html) codes. The underlying principle is the same regardless of which coding system ends up in use: each incoming code needs to resolve to the right DHIS2 data element or option.

Not every result will have a corresponding code available, whether because the terminology doesn't cover it or because no mapping has been defined yet for it in DHIS2. What to do in that case is a decision worth making deliberately — see [Terminology and code mapping](#lab_interop_decision_terminology) below.

## Design decisions { #lab_interop_design_decisions }

The sections below set out the decisions an implementer needs to make when building a laboratory results integration. This reference implementation answers each one a particular way, but a different country context may reasonably answer them differently.

Each decision is presented the same way: what you're deciding, the options available, the tradeoffs between them, and what this reference implementation chose. **Whatever your own adaptation decides, it's worth documenting these answers explicitly, and why you reached them** — that record is as valuable to whoever maintains the integration next as the code itself.

### 1. How a case is uniquely identified { #lab_interop_decision_identifier }

**What you're deciding.** An incoming result has to be matched to exactly one record in DHIS2. Whatever identifier carries that match needs to be available on both sides of the integration, unique enough to prevent a result landing against the wrong case, and practical for laboratory staff to capture.

Unique identification is a challenge for any individual-level reporting system, and laboratory data adds an extra wrinkle: samples sent to a small number of central laboratories often need to be uniquely identifiable in their own right. On the other hand, case-based surveillance doesn't usually need to track a person across multiple, separate episodes over time — a single identifier that holds from notification through to outcome is normally enough.

**Options.** Implementers will need to identify and define how a patient or case can be uniquely identified in their local context; this may vary from country to country. Candidates include a specimen ID, a generic national ID, a surveillance-program-specific case ID, an insurance number, a phone number, the patient's name, or some other unique attribute. DHIS2 supports several identifier types and can combine more than one for the same case, so the choice doesn't have to be all-or-nothing.

One candidate is the National ID tracked entity attribute (TEA), described as:

> "Unique identifier for a person that is managed and maintained at the national level; this type of identifier is not programme-specific. This may include, for example, a national health identification number, a national insurance number, or other similar unique identifier. This is intended to be adapted to the local context."

**Tradeoffs.** Each option carries its own: a name can be ambiguous or restricted for privacy reasons; a case ID may not be visible to the laboratory at all. A specimen ID keeps patient identifiers out of the exchange entirely, which is a privacy advantage, but it only links a *sample* to a case — it says nothing about the person, so it cannot help you recognise that two cases are the same individual. A person-level identifier can do that, at the cost of carrying identifying data across the boundary and of the ambiguity described below. It's worth weighing how widely available each option is against how well it works for finding and matching cases before settling on one. See the DHIS2 documentation on [tracked entity attributes as personal identifiers](https://docs.dhis2.org/en/implement/database-design/tracker-system-design/defining-the-tracked-entity.html#tracked-entity-attributes-as-personal-identifiers) for more detail.

**What this reference implementation does.** It uses the specimen ID as the primary key for matching an incoming result to the right record in DHIS2, on the basis that the specimen ID tends to be the identifier already understood on both sides of the integration. The specimen ID is captured in a mandatory field on the lab request stage and carried on the FHIR `Specimen` resource, where the IOL searches on it. A few things worth keeping in mind when relying on it:

* Ideally, the ID should be captured through a non-manual entry method (e.g. barcode scanning) rather than typed in, to reduce the risk of transcription errors.
* Matching may also need to rely on more than the specimen ID alone — for example, the date specimen collected and the date specimen sent to the laboratory — as a triangulation to help avoid accidental mismatches between samples and cases. Where non-manual entry isn't possible, this triangulation matters more.
* In some cases, a single specimen may end up with more than one result over its lifetime — a laboratory can issue a correction, amendment, or appended addition to a report it already sent. See [Where the result lands in the DHIS2 data model](#lab_interop_decision_data_model) for how that affects program design.

**An alternative: matching on the National ID.** Drawing on prior work in this area, three elements are critical to this alternative path:

* A common identifier between the laboratory and the case surveillance program — using the National ID, since it's an identifier that applies on both sides of the integration.
* Date parameters to filter laboratory results before and after a specified date — i.e. the enrollment date.
* Sync status tracking — expected to be managed at the middleware level rather than in DHIS2 or the laboratory system itself.

Even with a common identifier like the National ID in place, matching isn't fully automatic. A laboratory result associated with a given National ID may correspond to more than one enrollment — the same tracked entity instance (TEI) may have been enrolled in different programs, and the match may be ambiguous. A manual confirmation step is therefore still required — for example, via a Capture app plugin that lets the user select which TEI a given laboratory result should be mapped to before it's synced or imported. This manual selection step is a necessary part of the alternative workflow, not an edge case to design around.

### 2. Communication pattern between DHIS2 and the laboratory { #lab_interop_decision_communication }

**What you're deciding.** As with any two systems that need to coordinate on a shared piece of work, there's more than one way to manage how the laboratory request and its eventual result move between DHIS2 and the laboratory system. In some cases no explicit workflow-management layer is needed at all — the two systems simply exchange resources in an ad-hoc fashion, as the moment requires.

**Options and tradeoffs.** The questions below are worth working through for your own context. The right-hand column records how this reference implementation answers each one.

| Question to work through | This reference implementation |
| --- | --- |
| Does the state of the workflow need to be shared between DHIS2 and the laboratory system, or is it enough for each side to hold its own view? | Each side holds its own view. There is no shared workflow state and no separate sync-status store — the IOL derives what it still needs from the DHIS2 data itself (see [Push or poll](#lab_interop_decision_push_or_poll)) |
| Which paradigm do you want to use — REST, messaging, services, or a mix? | REST on both sides: the DHIS2 Web API and the LIS FHIR API |
| Who owns and manages the specimen and result — DHIS2 (as the requester), the laboratory system (as the performer), or another participant, such as a referral laboratory sitting between the two? | DHIS2 as requester, the laboratory system as performer |
| Is there infrastructure in place to support polling, push notifications via subscriptions, or both? | Polling only |
| Is there a need for the laboratory to confirm it has accepted the request, or can that be presumed? | Presumed — no acceptance step |
| Is there a need to negotiate whether, or how, the requested test will be performed? | No negotiation step |
| Can DHIS2 and the laboratory system communicate directly — can they post to each other's servers, if using REST? | Neither system contacts the other. The IOL sits between them and calls both |
| Is there an ability, or a need, to use a queue server to facilitate the workflow? | No queue server is used |
| How many potential actors are involved — a single laboratory, or several candidate laboratories? | A single laboratory |
| Will the workflow always be directed at a specific laboratory, or is there a pool of laboratories that could choose to perform the requested test? | Always directed at a specific laboratory |

A different country context — for example one with multiple candidate laboratories, or a laboratory capable of pushing results as soon as they're ready — may reasonably answer these differently.

### 3. Push or poll { #lab_interop_decision_push_or_poll }

**What you're deciding.** How DHIS2 comes to learn that a result is ready. This is one of the few decisions that is usually settled by infrastructure rather than preference, so it's worth establishing early: it determines who has to be able to reach whom, and who operates what.

**Option A: poll.** Something asks, repeatedly, whether there is anything new. Polling needs two things: a schedule, and a way of knowing what has already been taken so the same result isn't imported twice. Its great advantage in practice is that it only requires *outbound* connectivity from wherever the polling component runs. That matters, because in many country deployments the LIS sits on a laboratory's local network behind a firewall while DHIS2 sits in a national data centre or in the cloud, and neither can readily accept inbound connections from the other. Polling also degrades gracefully: if the poller is down for an hour, it catches up on the next run without anything being lost.

**Option B: push.** The source notifies the destination as soon as a result is finalised — in FHIR terms, typically via Subscriptions. Latency is lower and there are no wasted calls. The costs are that the source must be able to reach an endpoint on the DHIS2 side, somebody must operate and secure that endpoint, and the source needs a retry policy for when the endpoint is unavailable — otherwise a notification missed is a result lost. Push also tends to require more from the LIS vendor, which may or may not be within your influence.

**Option C: both.** Push as the trigger for low latency, with a periodic poll as the safety net that catches anything the notifications missed. This is the most robust arrangement and the most work to build.

**Tradeoffs and how to choose.** Start from connectivity direction and operational ownership rather than from latency. Then sanity-check the latency requirement against clinical reality: laboratory turnaround is usually measured in hours or days, so a poll every few minutes is invisible to the surveillance officer, and chasing seconds rarely buys anything clinically. Finally, consider what the polling cost scales with — if you poll DHIS2 for open cases, the cost grows with the number of active cases, not with the number of results, which is worth modelling before national rollout.

**What this reference implementation does.** It polls, and it polls both sides — neither DHIS2 nor the LIS ever initiates contact. A scheduled job in the IOL wakes on a configurable cron expression (`run.interval`), fetches active enrollments in the case surveillance program from the DHIS2 Web API, finds the completed lab request events within them, extracts each specimen ID, and searches the LIS for a matching diagnostic report. The sandbox ships with a very short interval so the demo feels immediate; a real deployment would widen it considerably.

Two details are worth noticing, because they are good practice independent of this implementation:

* **There is no separate sync-status store.** For each lab request, the IOL looks at the most recent lab result event already in DHIS2 for that specimen ID and uses its creation timestamp as a watermark, passing it to the LIS search so that only reports updated since then are returned. Where no result exists yet, the watermark defaults to a date far in the past. The consequence is that the integration's state lives in the data it has already written, so there is nothing to reconcile if the IOL restarts or is redeployed.
* **The search is narrowed to reports that are actually reportable** — those with a status of final, amended, appended or corrected — so preliminary or cancelled reports are not imported.

### 4. Which standard and implementation guide { #lab_interop_decision_standard }

**What you're deciding.** The shared structure that lets the destination side consume results without a bespoke integration per laboratory. Most implementers do not start from a free choice here: the LIS emits what it emits, and the country may already have a standard. The realistic question is usually *how much translation work you take on, and where you put it.*

**Option A: HL7 FHIR with the Universal Laboratory Report IG.** The choice made here. It gives you a maintained, internationally reviewed set of profiles for exactly this exchange, a REST API, and a body of tooling. The cost is that both sides must speak FHIR, and that the IG is a moving target while still in ballot.

**Option B: a national FHIR IG.** Where the country has one, it usually takes precedence over a global IG, and it may be mandated as part of a national health information exchange architecture. Check for this before adopting an international IG — retrofitting later is expensive.

**Option C: plain FHIR with no IG.** Faster to start with and reasonable for a single known laboratory, but you give up the guarantees an IG provides about which elements are present and how they are coded. In practice you end up writing and maintaining those constraints yourself, informally.

**Option D: HL7 v2.x, typically an `ORU^R01` result message.** Worth stating plainly rather than omitting: a large share of laboratory systems in production today emit HL7 v2, not FHIR. It is a message-based, delimited format rather than a REST API, so the integration changes shape — you need something that receives or collects messages and maps them, either an interface engine or a v2-to-FHIR translation step, before the rest of the pipeline looks as it does here. The important point is that a v2-only LIS is not a reason to abandon the integration; it moves the transformation burden upstream and leaves the DHIS2-facing half largely unchanged.

**Option E: a proprietary API or flat-file export (CSV, vendor-specific JSON, a database view).** Often the pragmatic reality with a single laboratory, and sometimes the only thing on offer. It can work, but you own the contract: you must define it, version it, and renegotiate it whenever the vendor changes anything. It also buys you nothing when the second laboratory arrives.

**Tradeoffs and how to choose.** Work through, in this order: what the LIS can actually produce today; whether a national IG or HIE standard applies; how many laboratories you expect to onboard (a standard starts paying for itself from the second one); and where you want the transformation burden to sit — in the LIS, in an interface engine, or in your interoperability layer. Whatever you choose, **pin the version**. Continuous-build URLs such as `build.fhir.org` move under you; production work should reference a published, versioned package.

**What this reference implementation uses.** The underlying standard is HL7 FHIR's [Universal Laboratory Report Implementation Guide (IG)](https://build.fhir.org/ig/HL7/uv-lab-rep-ig/), on FHIR R4, with the IG package installed locally on the FHIR server rather than fetched from a registry. This IG was built on the earlier European Laboratory Report IG, adapted into a global, HL7-maintained standard. It was selected for its broad scope, reflecting the participation of experts from several countries, projects and initiatives. To keep the demo focused on the DHIS2-facing side of the integration rather than the particulars of any one laboratory system, this reference implementation is built against a HAPI FHIR server standing in for an LIS, rather than a real-world LIS.

The IG profiles many resources; four are used here:

| Resource | Role in this integration |
| --- | --- |
| `Specimen` | Carries the specimen ID and the date the specimen was received at the laboratory — the link back to the DHIS2 lab request |
| `Observation` | Carries the LOINC code identifying the test performed, and its result |
| `Patient` | The test subject, which can be anonymous so that no patient data crosses the boundary |
| `DiagnosticReport` | Bundles specimen, observation and patient together, and carries the report status |

### 5. Point-to-point or an interoperability layer { #lab_interop_decision_layer }

**What you're deciding.** Where the fetch, transform and write logic lives — and with it, where the mapping, the sync state, the logging and the retries live. This decision determines who has to make a change when the mapping changes, which in the long run matters more than the initial build.

**Option A: direct, point-to-point.** The LIS writes results straight to the DHIS2 Web API, or DHIS2 pulls them itself. Fewest moving parts, nothing extra to host, and perfectly defensible for a single laboratory with a capable and cooperative vendor. The drawbacks show up later: the LIS becomes coupled to your DHIS2 data model, so every metadata change becomes a vendor request; and the work is repeated from scratch for the second laboratory.

**Option B: a dedicated interoperability layer.** A component of your own sits between the two systems. It gives you one place for transformation and terminology mapping, sync state, logging and error handling, and it shields each side from the other's changes. The cost is real: another service to deploy, monitor, secure and keep patched, and a skill set to maintain it.

**Option C: an established HIE or mediator platform** — for example OpenHIM and its mediators. This adds routing, audit, and client authentication across many systems rather than just this one. It is heavier to operate, and it makes most sense where the country already has a health information exchange strategy and this laboratory flow is one integration among several rather than a standalone project.

**Tradeoffs and how to choose.** The case for a layer strengthens with the number of laboratories and the number of integrations, and with how likely your DHIS2 metadata is to change. Weigh it against who will actually run it: an interoperability layer nobody is funded to operate is a liability, and a point-to-point integration that works is better than an elegant architecture that goes unmaintained. Wherever the layer sits, keep the mapping out of compiled code — see [Mapping laboratory results to DHIS2](#lab_interop_mapping).

**What this reference implementation does.** It uses a dedicated interoperability layer: the IOL, a low-code, customisable [Apache Camel](https://camel.apache.org/) application running on the JVM as a background process. Its integration routes are declared in YAML rather than written in Java, so the flow can be read and adjusted without deep Java work, and it is configured through YAML files or environment variables — DHIS2 API base URL and credentials, LIS API URL, and the DHIS2 metadata identifiers it needs to work against.

The design decision worth borrowing is that the IOL is **DHIS2-driven**: both the structural transformation (the DataSonnet script) and the terminology mapping (attributes on data elements and options) are held in DHIS2, not in the IOL. A DHIS2 implementer can therefore change how results map into their metadata without involving the team that maintains the IOL, and without a redeployment. That separation is most of the reason to prefer a layer over a point-to-point integration in the first place.

### 6. Where the result lands in the DHIS2 data model { #lab_interop_decision_data_model }

**What you're deciding.** How the incoming result is represented in the case record — which determines whether the history of a result is preserved, what a reviewer sees, and how the data behaves in analytics. This is a program design decision, so it is made once and is awkward to change after data has accumulated.

The specific complication with laboratory data is that a result is not necessarily final. A laboratory can issue a **correction**, an **amendment**, or an **appended addition** to a report it has already sent. Any design that only keeps the latest value silently discards the fact that something changed.

**Option A: a repeatable result stage, single event updated in place.** The simplest shape: one result per case, one form to read. A later correction overwrites the earlier value, so the case record shows the current answer and no history. Acceptable where corrections are genuinely rare and where the source system retains the audit trail — risky otherwise, because a clinician cannot tell that the result they acted on last week has since changed.

**Option B: a repeatable result stage, one event per incoming result.** Each result — including each correction or amendment — is recorded as its own event. Anyone reviewing the case can see what changed and when. The cost is that "the result" becomes a derived question rather than a stored value: reports and program indicators must pick the right event, usually the latest for a given specimen, and that logic has to be written deliberately rather than assumed.

**Tradeoffs and how to choose.** Ask how often the source laboratory issues corrections, whether a reviewer needs to see that a value changed, and what you intend to report on. If turnaround time is a goal, both the request and the result need reliable dates on them, which the repeatable-event shape supports naturally. Also decide up front which result "counts" for analytics — the first final result, or the latest amendment — because indicators and any turnaround-time measure depend on that choice.

**TODO**

**What this reference implementation does.** It uses a **repeatable lab result program stage, single event updated in place**, with one event per incoming diagnostic report. Multiple lab results can therefore exist for a single lab request, and successive events represent corrections or amendments in the source laboratory report; the status change is visible in the event notes. The lab request stage is repeatable too, so a single case can carry several specimens, each with its own thread of results. Each result event carries the specimen ID data element, which is what ties the result back to its lab request — and, as described under [Push or poll](#lab_interop_decision_push_or_poll), what the IOL uses to work out whether it already has the latest version.

The import happens without human intervention: when a laboratory report whose specimen ID links it to a DHIS2 lab request becomes available in the LIS, the corresponding lab result form is populated for the surveillance officer to review.

### 7. Terminology and code mapping { #lab_interop_decision_terminology }

**What you're deciding.** Each incoming code needs to resolve to the right DHIS2 data element or option. In practice, not every result will have a corresponding code available — whether because the terminology doesn't cover it or because no mapping has been defined yet for it in DHIS2. When that happens, implementers need to make a deliberate decision about how to still capture the result rather than silently dropping it.

**Option A: fall back to free text.** One common fallback is to make the corresponding data element free text, so the value is at least captured. That comes with a real tradeoff: free text isn't structured or codeable in the same way, which makes it considerably harder to analyse later on. It's worth treating free text as a fallback for the codes you can't yet resolve, rather than a default, and closing that gap with a proper mapping over time wherever it's feasible.

**Option B: extend the implementation guide.** Rather than falling back to free text, implementers can extend or expand the implementation guide itself to add the missing codes — proposing new codes, or maintaining a local extension of the value set, so the result is still captured in a structured, codeable form. This avoids the analytical downside of free text, but comes with its own cost: it means engaging with the IG's governance process (or maintaining and versioning a local extension) rather than making a change confined to your own DHIS2 datastore mapping, and it takes longer than simply switching a data element to free text.

**How to choose.** Which approach makes more sense will depend on how often the missing code is likely to recur and how much analytical value would be lost by leaving it as free text in the meantime.

Whichever route you take, treat the mapping as something that needs an owner. Codes are added to terminologies, laboratories change the panels they run, and DHIS2 metadata evolves — an unmaintained mapping quietly degrades into an increasing share of unmapped results.

### 8. Individual-level or aggregate { #lab_interop_decision_granularity }

**What you're deciding.** Whether the surveillance need actually requires individual results in a Tracker program, or whether counts would satisfy it. Getting this wrong in the ambitious direction is expensive: individual-level interoperability is the hardest version of this problem, because it is the version that requires matching.

**Option A: individual-level, into Tracker.** Necessary when a named case needs its result — for case management, contact tracing, clinical follow-up, or line-listed reporting. This is where the identifier and matching decisions above apply, and where most of the cost sits.

**Option B: aggregate, into a data set.** Sufficient when the requirement is counts — tests performed, tests positive, by facility and period. The matching problem disappears entirely: no specimen ID, no case linkage, and typically no patient identifiers crossing the boundary at all, which is a meaningful privacy advantage. The pipeline is still fetch, transform, write, but the write targets aggregate data values rather than Tracker events, and the mapping becomes test and result category to data element and category option combination, plus period and organisation unit. The hard parts move too: aligning periods, mapping the laboratory's own organisational units onto the DHIS2 hierarchy, and making re-runs safe so that figures are not double counted.

**Option C: individual-level in, aggregate out.** Import individual results into Tracker for case management, and derive aggregate reporting from those events within DHIS2. This is often the right end state, but it only makes sense once the individual-level path is justified on its own terms.

**Tradeoffs and how to choose.** This is the same cost/benefit question raised in the introduction, one level down. If the reporting requirement is genuinely aggregate, a periodic aggregate extract from the LIS — or even a routine report entered by laboratory staff — may satisfy it at a fraction of the cost and with none of the matching risk. Reserve individual-level interoperability for the cases where a named case record actually needs the result.

**What this reference implementation assumes.** Individual-level, case-based Tracker data: one event per result, matched to a specific enrollment. It does not address aggregate laboratory reporting.

### 9. Handling unmatched and failed results { #lab_interop_decision_failures }

**What you're deciding.** What happens to the results that don't sail through. This is the part of an integration that determines whether people trust it — an integration that loses results occasionally and silently is worse than manual entry, because staff stop checking and stop believing what they see.

**Failure modes to plan for.** No matching lab request in DHIS2 for an incoming result; more than one candidate match; more than one report for the same specimen ID; a result carrying a code with no DHIS2 mapping; a missing or malformed specimen ID; the same result arriving twice; an import rejected by DHIS2 for validation, sharing or program-rule reasons; and either system being unreachable.

**This is a policy question as much as a technical one.** Someone has to be responsible for looking at failures, through some interface, on some cadence. Decide who that is — a national data manager, the laboratory focal point, the team running the interoperability layer — before go-live, and give them somewhere to look. The one option to rule out is silent dropping.

**Options for genuinely unmatched results.** Hold them in a queue or review app for manual matching, which is unavoidable on the National ID path described in decision 1 and needs a user interface; reject them with a notification back to the laboratory, on the argument that the source is usually best placed to fix a bad identifier; or park them in DHIS2 for later reconciliation. Whichever you pick, make re-processing safe: either derive a stable identity for each result from the source report so a repeat import updates rather than duplicates, or advance your sync watermark only on success.

**What this reference implementation does — and doesn't.** Worth understanding precisely, because the direction of travel shapes the failure modes:

* Because the IOL is driven from DHIS2's lab requests and only asks the LIS for specimen IDs it already knows, an **unmatched result cannot really arise** in this design: a report sitting in the LIS with no corresponding DHIS2 lab request is simply never fetched. The flip side is that it is also never flagged. If your laboratory can produce results for specimens DHIS2 does not know about, that gap needs handling that this reference implementation does not provide.
* It assumes at most **one report per specimen ID**. Behaviour when the LIS returns several for the same specimen ID is explicitly undefined.
* A lab request with an **empty specimen ID** is skipped.
* If the LIS has **no report yet** for a specimen — the common case, since the laboratory has not finished — the request is skipped on that cycle and reconsidered on the next.
* The event is imported **synchronously**, and the import report is checked: success is logged, and anything else is logged as an error with the DHIS2 response. There is no retry policy, dead-letter queue or alerting. A failed import is, however, retried implicitly on the next poll, because the watermark only advances once a lab result event actually exists in DHIS2 — a useful property that falls out of keeping state in the data.
* Operational visibility is logs plus the IOL's health and management endpoints and its embedded console.

For production, the gaps to close are an explicit retry and backoff policy, alerting on repeated failures, and a named owner for the error log.

## Adapting this reference implementation { #lab_interop_adapting }

As with other DHIS2 reference implementations, this one is meant to be a starting point rather than a drop-in solution. Expect to adapt it to your own program design, your own specimen ID strategy, and — if you go down the National ID matching path described above — your own approach to patient matching and manual confirmation.

Concretely, an adaptation needs to work through the following. The parameter names are the IOL's configuration keys; see the repository README for the full list.

**Point it at your own metadata.** The IOL is configured with the identifiers of the program, the lab request stage, the lab result stage, the specimen ID data element, and the attribute that carries laboratory codes. All of these are demo values in the shipped configuration and must be replaced with your own.

**Bind your metadata to laboratory terminology.** Add the relevant laboratory codes to your own data elements and option set values using the code attribute, so the IOL can build its lookup. The reference implementation ships example mappings, such as two LOINC codes both resolving to a `POSITIVE` option.

**Replace the transformation script.** The DataSonnet script in the DHIS2 datastore is written against this reference implementation's lab result stage and the FHIR resources the mock LIS produces. Yours will need to match your stage's data elements and whatever your LIS actually emits. Note that the import uses the `CODE` identifier scheme for data elements, so the script targets codes rather than UIDs.

**Set connection details and credentials.** The DHIS2 API base URL plus either a personal access token (preferred) or a username and password, and the LIS API base URL. The shipped compose file uses well-known demo credentials and leaves the embedded console unauthenticated; both must change before this runs anywhere real.

**Choose a polling interval.** The sandbox default is deliberately aggressive so the demo responds quickly. Set it from your laboratory's actual turnaround times.

**Swap in the real source system.** Point the LIS URL at the real system, and if it does not speak FHIR with the chosen IG, add the translation step discussed in decision 4. The Bruno test kit that fakes laboratory analyser output is a demo aid, not part of the integration — drop it.

**Revisit your program design.** Your own enrollment, request and result stages, and in particular whether the result stage is repeatable (decision 6).

**Treat the environment as a sandbox, not a topology.** The Docker Compose setup exists to bring the pieces up on one machine with a seeded database. It is not a deployment architecture: production needs your own hosting, TLS, backups, secret management and monitoring.

## Resources { #lab_interop_resources }

As with other DHIS2 reference implementations, this one is meant to be a starting point rather than a drop-in solution.

* [Laboratory interoperability reference implementation](https://github.com/dhis2/reference-dhis2-tracker-lab-result-integration) — code, quick start, architecture diagram and configuration reference.
* [Universal Laboratory Report Implementation Guide](https://build.fhir.org/ig/HL7/uv-lab-rep-ig/).
* [DHIS2 Web API documentation](https://docs.dhis2.org/en/develop/using-the-api/dhis-core-version-master/introduction.html).
* [DHIS2 documentation: tracked entity attributes as personal identifiers](https://docs.dhis2.org/en/implement/database-design/tracker-system-design/defining-the-tracked-entity.html#tracked-entity-attributes-as-personal-identifiers).

**Questions and contributions.** Questions or feedback can be posted on the [DHIS2 Community of Practice](https://community.dhis2.org/).
