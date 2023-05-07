
# Defining the Tracked Entity
![](resources/images/image43.png "Step2")


At this point you have mapped the reporting system in detail, and begun mapping of these reporting system concepts to DHIS2 terminologies. It may help to revisit key DHIS2 concepts to recall the difference between Tracked Entity Instances (TEI), Enrollments, Tracked Entity Attributes (TEA), and Data Elements.


In the following sections will build on this knowledge to describe:


* The core unit of analysis in routine reports (“*what kind of record is being tracked?*”)
* Data points which identify each record as distinct from others (“*how do users search for and identify a unique record?*”)

## Persons and Cases

The first question you should consider is whether the individual being tracked will have multiple encounters or follow-ups. If there is only one “touch point” with this client, for example a single-dose vaccination campaign, you might consider using the [Event Capture data model](#about_event_capture_app) instead. There is limited benefit to using Tracker unless the client will be seen multiple times. Indeed, individual level tracking presents an extra burden on care providers to enter and look-up patient identifiers, plus unnecessary data security risk of storing such sensitive information when it is not strictly needed.

The second question is whether the enrollment is **repeatable**, i.e. whether a person can be considered a “case” more than once in his or her lifetime. For some programs tracking chronic illnesses, such as Childhood immunisation and HIV, the case is considered duplicated if the same person enrols more than once. For others, such as antenatal care or malaria investigation, it may be common for the person to cycle through the program multiple times. This decision has consequences for the search process, deduplication of records, and the calculation of indicators.

Note, the majority of Tracker use cases have a tracked entity instance type of “Person”, with a key exception for disease surveillance “cases”. Persons might be enrolled in multiple programs where they receive different types of health services; to see an overview of a person’s clinical history, it is therefore useful to link all of the patient’s enrollments across programs to a common “Person” TEI. In disease surveillance scenarios, it may be more appropriate to use a “Case” Tracked Entity Instance type, where each case is assigned its own unique identifier number and considered a distinct record. In such a scenario rapid reporting is most urgent: there is no need to link together previous cases experienced by the patient, and searching for the Person’s TEI to link all the patient’s previous enrollments simply slows down the data entry process without adding value.

In addition, some niche use cases need to track non-persons as tracked entities, such as a logistics program to track medical supplies or drugs.

> **Note**
>
> To describe the most common Tracker scenarios, this guide will assume use cases where the Tracked Entity Type
> is a “Person”, “Patient”, or “Client”, unless stated otherwise.


## Identifiers and Data Elements

The next important distinction is separating **Tracked Entity Attributes** from other important data points.

As a general rule, Tracked Entity Attributes (TEA) help to identify the TEI record as belonging to a specific client. Some of them may be _searchable_, meaning users can query the DHIS2 database with a TEA value to find their patient’s enrollment. The user should only need to review the record’s TEA to determine that the record belongs to their client.

They are generally only captured once--the very first time a client is enrolled in the Tracker program--and therefore should be considered reliable and semi-fixed values which rarely change between encounters.

**Data Elements** are all other data entered for the tracker program. They are normally used to represent a client’s health condition, diagnosis, treatment, outcome, or other services received. Compared to TEA they are much more likely to change between encounters with the health care provider. Note that these data Elements should use domain type “Tracker” to separate these from data elements used in the aggregate domain.


> *Tracked Entity Attributes* relate to a client's *identity*, and help the user verify that the TEI they see in DHIS2  represents the specific person in question.
>
> *Data Elements* are all other *form fields*, and usually relate to a client's health record or other services they have received within the program.


Standard examples of Tracked Entity Attributes include Client Name, Date of Birth, Phone Number, and other national identifiers. Data elements vary often by health area, but often include Disease Diagnosis, Patient Weight, Lab Result, Medication Provided, and Treatment Outcome. 

Both Data Elements and Tracked Entity Attributes have a number of types, including Dates, Yes/No, Yes Only, Free Text, and “Select-One” Multiple Choice (Option Sets). Full lists of Tracked Entity Instance attribute value types and data element value types can be found in the  [Tracker User Guide.](#configure_tracked_entity)

Further, [program rules](#about_program_rules) can be applied to validate the values of these fields, or apply a skip logic to only show them under certain conditions. Program rules provide a way to produce dynamic behaviours in response to user input in tracker and event capture. More information on Program Rules can be found in the [Interaction Design](#interaction-design) section and in the User Guide.


## Tracked Entity Attributes as Personal Identifiers

Tracked Entity Attributes can be described as the data points that link a specific client’s identity to their individual health record. They assist care providers to initially _register_ a unique person, then later _search_ for and _retrieve_ that same record. In certain cases such as vaccination registries, an identifier can also _verify_ a person’s eligibility for services. In many contexts, not all patients have access to national identifiers; according to the World Bank,[ more than 1 billion people globally](https://id4d.worldbank.org/global-dataset/visualization) lack official identification. In these cases, a care provider may need to rely on combinations of different Tracked Entity Attributes to uniquely identify the patient in Tracker.


> An ideal Tracked Entity Attribute is both **_universal_** (high Availability) and **_unique_** (high Specificity). Tracker programs will generally need several TEA to help users perform search, registration, and verification actions.


The table below lists common examples of TEA by Availability and Specificity, based on the experience of DHIS2 implementers.

|Name of TEA|Availability|Specificity|Comments
|:--|:--|:--|:----|
|Family Name|High|Low|In any cultural context, there is often a high proportion of clients with the same last name (Smith, Gonzales, Banda, Ali, Devi, etc). Entering a family name as free text is also prone to misspelling or transliteration issues.|
|Date of Birth|Medium-High|High|Many clients may not know their precise date of birth. Note that the “Age” type TEIA will calculate an estimated date of birth from the reported age in years at enrollment, and so is very imprecise and inconsistent when used across programs. A better solution is to complement Date of Birth TEIA with a yes-only TEIA for “Date of Birth is Estimated”.|
|Phone number|Medium-High|High|Phone numbers can act well as distinct identifiers, although they may change over time as clients switch mobile service providers. Note some clients may not own a phone, or might share phone access with someone else. Program rules can validate the length or starting digits of the phone number during data entry.|
|Address|Medium-Low|Medium-High|Many clients in urban and rural settings live in communal housing or un-addressed residences. Prone to free-text misspellings and less useful as a client search criteria.|
|Village of Residence (or Other Regional Geographies)|High|Low|May be helpful to confirm a search result, especially if the residence is unaddressed. But similar problems of misspelling and low search accuracy persist.|
|National ID|Medium-Low|Very High|Although Civil Registration and Vital Statistics (CRVS) has improved globally, many contexts do not have a universal and unique identifier such as a national ID. While uniqueness is high in countries with a national ID scheme,  [surveys show](https://www.unaids.org/sites/default/files/media_asset/JC2640_nationalhealthidentifiers_en.pdf&sa=D&source=docs&ust=1683242277689786&usg=AOvVaw2ahTy7lR7SrC3qNRM7qAF5) the coverage can be unevenly distributed. Women, children, and lower income levels are less likely to have a national ID in low-income contexts. Some DHIS2 implementations link their system with a central CRVS register to enter a national ID into the client’s record automatically.|
|Country of Origin|Medium|Very Low|May be useful in disease surveillance to identify origin of disease, complement client address, or identify inequities of care. Not recommended for client search.|
|National Health (Insurance) ID|Medium|High|Where such IDs exist, some contexts may have multiple insurance schemes, or multiple national identifiers. Thus, users may need to select one from a handful of national identifiers during registration and search (e.g. passport number, insurance scheme number, birth ID).|
|Case ID (Written)|Medium|High|Some health units have a unique case ID for each patient pre-printed onto paper registers. This could be manually entered onto DHIS2 upon registration.*|
|Unique Identifier (Autogenerated)|High (web)  Medium-High (Android) | High|DHIS2 can auto-populate unique identifier fields on sequential or random patterns. These identifiers are reserved locally on Android devices, which require regular syncing to the server to refresh the local list of available IDs, so identifiers that include sequential IDs or dates may have [performance implications](#implementation_guide_dhis2_config_reserved_id) or [unexpected behaviour](https://community.dhis2.org/t/question-regarding-expiry-of-reserved-ids-of-an-auto-generated-unique-values-configured-with-a-text-pattern-containing-current-date-mm-yyyy/40761/2). More information on TextPattern found in the [User Guide](#working-with-textpattern).|



\*  In many scenarios, a “Person” could be considered a program “Case” multiple times during his or her lifetime. Thus, a Case ID should only be used as a Tracked Entity Attribute if the Tracked Entity Type is _Case_. If the Tracked Entity Type is _Person_, then the Case ID could be used as a data element in a program stage as a verification check, but it should *not* be used as a Tracked Entity Attribute, since a Person may have more than one Case ID. Conversely, in a disease surveillance context where the Tracked Entity Type is a “Case” instead of a “Person”, then an implementer cannot use any Unique Personal Identifiers such as National ID, since this could be replicated for multiple cases belonging to the same person.


### Sharing TEA across Programs

A client’s TEA can also be shared across any of her enrollments within the same DHIS2 database, which makes data entry quicker and supports deduplication efforts for contexts where health areas share clients (for example TB and HIV Case surveillance).

If a TEIA will only be used within a single program it should be [assigned to the program itself](#create-or-edit-a-tracker-program). If the TEIA should be shared across multiple programs, you assign it to the tracked entity _type_. If you decide to use the [Relationships](#relationship-model.html) feature to link two Tracked Entity Instances in two separate programs (for example a mother in ANC and child in Immunization Tracker), the TEIA assigned to the Tracked Entity Type will be shown in the dialog box when you searching for the “target” TEI to add the relationship to the current “from” TEI.


### Making TEIA Searchable

TEIA are essential to search client records, but to improve system performance, you may want to restrict searching to a smaller subset of all the TEIA associated with the program. There are certain types of searches which may return too many results or cause long server delays, so there is an inherent balance between search flexibility and search performance.

However, as a general rule, you should consider breaking all searchable TEIA into the smallest possible segments. For example, instead of a searchable TEIA for “full name”, consider one for “family name” and one for “given name”. Segmenting search criteria like this will generally provide quicker search results than scanning the entire full name for each TEIA.

TEIA may also be marked “confidential” during program configuration. If encryption is enabled in the DHIS2 instance, all “confidential” TEIA will be encrypted at rest in the database. It should be noted that this means confidential TEIA cannot be used as search criteria by end users.


### The Core TEIA Case Profile

A core set of TEIA captured in case surveillance programs, such as date of birth and given name, have been pre-generated for many DHIS2 metadata packages. An important recommendation for new tracker programs is to install the  [Common Metadata Library package](#gen-lib-design), including the WHO’s Core case profile, as a starting point for program configuration. 


### Linking Tracker with Population Registers

In the spirit of “enter data once, use it many times”, some countries have taken the step to link their national civil registration database (or “population register”) to DHIS2 Tracker programs used for priority use cases. Instead of searching for existing TEIs across an assortment of demographic details in a program–and then laboriously adding TEI Attribute values for every “new” patient–end users simply search by national identifier number, and key TEI Attributes such as name, birth date, and gender are filled in automatically. This makes the search process more efficient, and the demographic data are more likely to be accurate and high quality.

> **:mag: Country Use Cases**
>
>There are different approaches to linking with Tracker population registers, depending on the population characteristics, health programming use case, and legal context. During Covid-19 vaccination campaigns, Cape Verde and [Sri Lanka ](https://community.dhis2.org/t/implementing-large-scale-immunization-tracker-sri-lankan-experience/43008), and other countries found it practical to export data from the national population register, transform those data into DHIS2 tracked entity instances, and then perform a one-time import of those TEI into their national covid vaccine tracker. In both countries it was feasible to import into a single DHIS2 instance due to the manageable population sizes (500k and 21 million) and limited scope of the vaccination campaign (adults). For ongoing public health surveillance, sensitive subpopulations, or providing services to unregistered persons such as infants, a direct link with the  “live” CRVS system may be more appropriate. For example in Rwanda, custom javascript in the DHIS2 Tracker search page allows for a direct API query to the National CRVS system based on the national ID entered; when the search result is confirmed, demographic details are auto-populated into the registration page. This DHIS2-CRVS integration goes two ways. In [Rwanda’s childhood immunisation Tracker](https://dhis2.org/rwanda-crvs-eir-integration/), new non-registered births entered into the tracker notify civil registrars to provide a birth certificate.


## One Program or Multiple?

At this point, you should consider whether you need a single program or multiple programs for your Tracker system. A program defines the sequence of events that an entity can go through–the “frame” for events–and what attributes are required when an entity joins the program. If there are _multiple pathways to enter into or exit from a program_, then you may want to consider having a separate program for each pathway.

> **Example**
>
>A laboratory might test multiple specimens for a person suspected of tuberculosis, but each TB positive patient receives a defined set of services from the clinic. Because the lab and the clinic have different workflows, different users, and different entities being tracked (test samples vs individuals), then one might consider separate programs for laboratory data entry and TB case surveillance. Any TB patient already receiving treatment could be immediately enrolled into a TB case surveillance program, but a suspected case would only be enrolled into the TB Case Surveillance program after a confirmed test has been reported by the lab in the Laboratory program. If it were an integrated TB Case Surveillance and TB Screening program, the majority of enrollments would be suspected cases, and only some would receive treatment.



DHIS2 Tracker supports such behaviour by allowing TEI to be enrolled in multiple programs. The TEI Attributes may be shared or distinct between each program. Different sets of users could have access to each program according to their reporting duties. Further, line lists could be generated that display the TEI’s enrollment in each separate program. However, as of DHIS2 v2.40, there are no methods to analyse tracked entity instances by data element values in multiple programs.

