# Building your Tracker Program(s)

The purpose of this section is to give a high level overview of the considerations that will lead to success in your Tracker implementation, grouped by topic and with links to specific tools.

This section will cover:

1. Scale
2. Design and Configuration
3. Real-time vs. Secondary Data Entry
4. Mobile vs. Web
5. Establishing a Core Team
6. Hosting
7. Training
8. Roll-out

## Determining Scale

Because Tracker is aimed at the lowest levels of a system, Tracker systems can mean dramatically increasing the number of  users, devices technical and organisational support requirements. Countries often have limited personnel that are qualified to do deployments and there are costs associated with the work. 

Scale can refer to several dimensions; programmatic scale, functional scale or geographic scale to mention a few. 

Scaling geographically can thus take time and resources. There are different strategies to geographical scale i.e. cover one region completely or start “small” in several regions at the same time and scale at a slightly slower pace in parallel.

When you start scaling things will happen faster; more people will work on it and need support. Hence, make sure that the team is rigged to handle an increased volume and speed by taking into consideration the following:

**Finalize and pilot the tracker before scaling it**  
Gather evidence and demonstrate impact before attempting to scale. Consider reduced investment in features that do not demonstrate impact, or resource-intensive features that have limited impact.  You should have a final design/configuration which is user tested and piloted and produces the targeted results in terms of information management and the wanted reports BEFORE you scale. When you start scaling, it is not the time for experimenting. In other words, test your design and set up with 100 rather than 5000 users.
 
**Governance**  
Ensure there are solid governance processes and a clear distribution of responsibilities before you attempt to scale. Make sure you audit this process to ensure the governance process is followed. Proper governance is also key to ensure the flexibility and adaptability of your tracker project, for example routines for adding new option sets or new clinics. Who makes these decisions and how do you document them and how do you communicate them to the users? 

**Cost/financial considerations**  
Consider your funding model, including revenue-generation options, social business models, the cost per user and financial paths to sustaining the initiative. Scaling leads to increased operational costs in terms of support, devices and connectivity. 

**Scaling up infrastructure**  
With increased scale you have to handle more connections that in turn requires increased resources in memory, processing power, storage and connectivity. 

Part of the scaling process makes sure you have a sound plan for speedy recovery because more people depend on the system. 

**Revise the process from the pilot**  
Scaling up can often not be done with the exact same tool and approach as is done in a pilot, particularly when it comes to the level of human resources and expertise needed in training and support to attain the level of use achieved in a pilot. Consequently, review your tool and implementation approach and consider what aspects can be redesigned and simplified to achieve your core goal   


*References*:    

- Principles of Digital Development

*Tools*:

- Readiness Assessment


## Design and configuration process

**Involve users closely in design and configuration of your Tracker program** to ensure that it improves and supports their work. In order to develop a Tracker program one needs to define what data to enter, define a workflow and define program rules. All of these definition decisions should be made in close collaboration with users, since they directly relate to -- and can affect -- how they do their work.

We recommend that you start the design process by asking the following questions to start discussions:

1. What is the purpose of the data you collect? How do you intend to use the data?
2. Who will benefit from the Tracker implementation?
3. How will the users entering data benefit from the Tracker implementation?
4. Do you currently collect this data today? How?
5.  Are there data elements you currently collect that you do not need?

DEFINE PURPOSE, AIM AND SCOPE

A clear purpose and well-defined aims are the key to establishing a common understanding of the project's scope and limitations, and to being able to communicate the process of developing and running a Tracker program internally and externally.

- Define the primary and secondary purposes of the Tracker program.
- Identify the tracked entities, the scope of data collection, and the health cadres involved in data collection.
- Determine how to uniquely identify members of the target population, (e.g., use of unique identification numbers or a combination of attributes).
- Clarify initial expectations among the core team, as well as other stakeholders and system users.
- Brainstorm and discuss key issues and areas of concern to be addressed during the development phase.
- Prepare to conduct a development phase: Develop a timeline and incorporate contingency plans for unexpected events that incur delays. Articulate anticipated problems and discuss how to mitigate.

FORMATIVE PHASE

Gain a clear understanding of the health system (or other system that the Tracker program will cover, for non-health implementations) to understand the "pain points” of the current system, identify opportunities for improvement, and ultimately develop a useful and suitable system that addresses these issues and opportunities. This includes understanding health workers, the data they collect, their clinical workflows, and their supervisory and reporting systems.

- Prepare and undertake field visits to map clinical workflows and supervisory and reporting demands with the participation of all cadres of health staff who would use the Tracker.
- Prepare and undertake stakeholder meetings to inform, explore and get feedback.
- Verify existing national (clinical) guidelines relevant to the scope of the Tracker.
- Map the existing documentation workflow: Document what workers currently do and ensure your design supports their work practices rather than making them more cumbersome.
- Map indicators and associated data points for reporting.
- Consider whether there is a need for revision of guidelines or reporting points. If so, make parallel plans for revision of guidelines and reporting.

DEVELOPMENT PHASE

- Get an overview of current clinical guidelines, interventions, indicators and algorithms.
- Based on current guidelines -- as well as indicators and data points for reporting -- formulate algorithms and data points for electronic tracking.
- Define the target groups and level of complexity of decision support. According to the level of workflow support, create rules for the support and communicate this to software developers in an agreed-upon requirements format.
- Enable an iterative review process to ensure that the developers’ translation is consistent with the health care providers’ needs.

CUSTOMIZATION AND TEST PHASE

This phase is an iterative process of working with stakeholders, software developers, implementers and users and incorporating their feedback.

- Establish a structured and easily accessible digital system for comprehensive and immediate feedback channels among the core working group.
- Ensure that content development is in line with the expectations of stakeholders, system users and funders.
- Maintain ongoing, open-minded discussions about translation, use of information buttons, etc., to avoid misinterpretation.
- Make sure that there are continuous, parallel processes that involve and promote information flow among all user groups in these phases.
- Define milestones for developers, implementers and users.
- Establish a structured and easily accessible online digital system for comprehensive and detailed feedback from end users.

Link to WHO package design documentation

## Determining your M&E Framework

Intro  
What does a mature tracker implementation look like?  
Maintain and evaluate data collection  
Maintain and evaluate data use practices  
Maintain and evaluate keep up with new DHIS 2 versions  
Maintain and evaluate user admin  
Maintain and evaluate security  
Maintain and evaluate hosting  
Maintain and evaluate user support  
Maintain and evaluate training


## Real-time vs secondary data entry

**Carefully evaluate whether the data should be entered real time** as this has several implications for how you structure your project. Trackers are used to track individuals through defined programs with associated data elements and rules. The data can be captured by health personnel during the consultation (real time point of care), or at the end of the day (or when they have time to enter it). The two different approaches naturally have consequences for what the Tracker is used for: If the data is entered at point of care - during the consultation - it is possible to provide decision support and validate data and avoid double data entry. However, it also introduces challenges with regards to connectivity, usability, increased number of devices, etc.

Entering data in real time also requires that the the setup of the Tracker matches the clinical (other domain) workflow. Hence it is critical to have clear SOPs for backup paper files, easy navigation to find clients and mechanisms to prevent errors (such as rules that make it impossible to enter a date in the future).

Link to WHO package design documentation

## Mobile vs Web

**Consider how and when the people doing data entry can access the Internet** There are contexts or locations where accessing the online central DHIS2 server through a computer is challenging or even impossible. The DHIS2 Android Capture App has been designed and developed to respond to those situations. However, introducing mobile devices into a DHIS2 implementation will impact your project on many levels, so it is a decision that needs to be made in an informed and conscious manner.  
  
**Web or Mobile?**  
There are two main aspects that should be taken into account when considering a mobile component for your Tracker implementation: internet availability and the mobility of your health posts. A given Tracker implementation may need to address only one of these two aspects, or both at the same time. We will attempt to define them and help you analyse your situation in this section.  
  
- **Mobility**: There are teams that provide their services in different locations through a mobile unit. In the locations visited by the mobile unit, there could be a facility with a proper work station for data collection, but sometimes data entry is done in a more dynamic environment or in the vehicle itself. In these cases it is not always easy to carry a laptop and it may be more suitable to use a mobile device instead.  
  
- **Internet availability**: There are many locations where access to the Internet is challenging. The different possible scenarios can be summarized in two main cases: *Internet connection is unstable or limited*, and *Internet connection is not available*.  
  
    - When the *Internet connection is unstable or limited* scenario is confined to certain moments in the day, it is possible to consider the use of either mobile or web for data entry. DHIS2 web data entry allows for the continuation of data entry when the Internet is interrupted. The data entered will be stored locally in the web browser cache, and the next time the user gets online the data, it will be automatically uploaded. Is important to note that this offline support depends on web browser storage and will only work while the browser window remains open. If a user is collecting data offline and closes the window where s/he is working while still offline, the data will unfortunately be lost. Offline support *absorbs* the impact of intermittent Internet connectivity interruptions to provide a smooth and stable work experience, but is not a full offline solution.
  
    - When *Internet connection is not available*, you should consider using the DHIS2 Android Capture App, which provides full offline support for data collection. This app can be used with both mobile devices and tablets, and it is also possible to run it on other devices such as Chromebooks. The Android Capture App can thus be suitable for those cases where you have Internet availability challenges but not challenges to mobility of the individuals doing the data collection.    
  
**Implications of the use the Android App**  
The DHIS2 Android Capture App facilitates offline use of Tracker data collection, but also brings with it implications that must be considered from the early phases of the project. Having a mobile component in your implementation could impact your planning, budget, training, configuration and deployment strategy, among other aspects.  
  
- **DHIS2 configuration:** When configuring Tracker for use with mobile devices you need to pay special attention to the configuration of mobile users, their access to data entry and organisation units. Mobile users are typically envisioned to be physically collecting data in the most remote and inaccessible areas, hence a mobile user is not expected to collect data from a high number of facilities, such as the organisation unit hierarchy of the entire country. While there is no maximum number of organisation units allowed in the App, large numbers can have impact in performance depending on the resources on the device (memory, processor). In general, below 250 organisation units should be safe, but that is still a very large number for a typical mobile use case.  
It is also very important to pay attention to the configuration of program rules and program indicators. The Android App aims to support all Tracker web functionalities, however some of them might behave slightly differently in Android, or be in the app development roadmap awaiting implementation. A detailed list of the behavior of program rules and program indicators in Android can be found in the _Program Rules_ and _Program indicators_ sections of the [Android App documentation]([https://www.dhis2.org/android-documentation](https://www.dhis2.org/android-documentation)).  
  
- **Visual representation of data collection:** The user experience of the Android App has been designed to be very visual and intuitive. Icons and colors can be used to configure the data entry forms and how they are displayed. Visual representation is configurable by the system administrator. There is an icon library of over four hundred images and a color palette, and both icons and colors are assignable to most metadata objects: Options, Data Elements, Attributes, Programs / Data Sets. More information for the visual configuration of DHIS2 can be found in the _Visual Configurations_ section of the [Android App documentation]([https://www.dhis2.org/android-documentation](https://www.dhis2.org/android-documentation)).  
  
- **Testing :** Testing is a very important phase in any DHIS2 implementation. You should test the Android App in parallel with your server configuration, to make sure that all configuration made in the server is properly reflected and working in the app. This is especially important during the configuration of the program rules. More information on the different types of testing and how to plan testing phases for your project can be found in the _Testing_ section of the [DHIS2 Mobile Implementation Guidelines](https://s3-eu-west-1.amazonaws.com/content.dhis2.org/Publications/DHIS+2+Mobile+Implementation+Guidelines.pdf).  
  
- **Security :** Depending on your Tracker configuration, you may be storing personal data on mobile devices, and there may be tension between the health system’s need for identifiable data, and the patient’s right to privacy. Ensuring that personal data is only accessible by authorized health staff is of utmost importance. Proper management of personal data is a critical component of user education, and it is vital to establish SOPs that describe the security measures to be applied, and to ensure these SOPs are shared with and followed by all users. System administrators also play an important role when configuring a user’s access level, by ensuring that data access is appropriate for each user and never unnecessarily excessive. Recommendations for an adequate security / privacy approach for any DHIS2 mobile implementation can be found in the _Data Security and Privacy_ section of the [DHIS 2 Mobile Implementation Guidelines](https://s3-eu-west-1.amazonaws.com/content.dhis2.org/Publications/DHIS+2+Mobile+Implementation+Guidelines.pdf).  
TODO; add link to security section in this document!
  
- **Purchasing mobile devices:** Mobile devices acquisition is a key aspect to a mobile deployment and needs to be considered for planning, budgeting and logistics. A good strategy is to get the best and newest devices that you can afford, such that they will last longer over the life of your project. In this sense, it is good practice to delay the bulk of the acquisition (in other words, any devices not required for initial testing and pilot phase) as much as possible, instead of purchasing all devices early in the planning process. Technology -- and particularly mobile devices -- evolves very rapidly. A given model is normally refreshed on an annual cycle, giving consumers access to significant technical improvements year-on-year at a similar price point. Specifications for mobile devices that can be used with the DHIS2 Capture Android App can be found [here](https://docs.google.com/document/d/1jZjw-hb1W8sszkPU9yPWrPoow91gEkTb0nyZJh3IJQQ/edit).  
When you have performed all testing and completed your pilot, you are ready to scale up your deployment with the acquisition of hardware and necessary services. You can find guidance for your mobile acquisition in the _Scale Up_ section of the [DHIS2 Mobile Implementation Guidelines](https://s3-eu-west-1.amazonaws.com/content.dhis2.org/Publications/DHIS+2+Mobile+Implementation+Guidelines.pdf). We summarize below the key aspects to consider in this phase:  

  1) Purchasing of devices vs BYOD (bring your own device): The advantage of BYOD is that it avoids the large initial cost for acquisition and reduces administrative costs and logistics considerations. On the other hand, using the BYOD model leads to the challenge of managing a very heterogeneous hardware environment, meaning different devices and Android OS versions, which can result in different end users having different capabilities for capturing and reviewing data, and can ultimately lead to challenges with upgrading the core Tracker instance, as newer versions may have limited backward compatibility with older app versions. The primary advantage of purchasing devices for end users is uniformity of devices and app versions, but this approach increases hardware costs and involves logistics challenges related to distributing the mobile devices, as well as maintaining and replacing them over time.

  2) Distribution of the app: you can manually install the Android Capture App by using the APK available in [Github](https://github.com/dhis2/dhis2-android-capture-app/releases) or use the [Google Play](https://play.google.com/store/apps/details?id=com.dhis2) store. With Google Play it is easier to update the app on all your devices, however you are forced to automatically install all updates of the app. Installing the APK allows you to control when to update and to which version, but it requires a more complex process for updating all your devices and is not recommended for projects not using Mobile Device Management software (see next item).  

  3) Telecommunication contracts: The process of selecting and signing a contract with a mobile provider varies by country, and will also depends on the procurement procedures of your organization.  
  
- **Management and Maintenance of devices:** Mobile Device Management (MDM) refers to software used for the administration of mobile devices. MDM software is necessary to support hundreds of devices, control the APK file distribution across all of these devices, provide tech support and enforce institutional policies. More information on the desirable features of an MDM, available options and guidance on the selection of the right MDM for your project can be found in the _Mobile Device Management_ section of the [DHIS2 Mobile Implementation Guidelines](https://s3-eu-west-1.amazonaws.com/content.dhis2.org/Publications/DHIS+2+Mobile+Implementation+Guidelines.pdf).

##  Human Resources and IT Support

No Tracker implementation will be successful over time without the right people on board. Before starting a tracker project it is important to make sure the right personnel with the right competence are available.  

Here are a few considerations when building your team:

1. Aim for long-term engagement. The people that will maintain the Tracker implementation over time should be part of the project from the start

2. In-country resources at all levels of the (health) system need to be involved from the very beginning. Handovers of project history, decisions and established routines from external consultants to permanent staff are often challenging.

3. If you already have an aggregate DHIS2 instance, remember that the people who are managing aggregate are not automatically “qualified” for the Tracker project, as Tracker is different from aggregate reporting.


|Role | Responsibilities/tasks |
|:------|----------------------|
|Project manager | Manage the Tracker project|
|Config/development lead	| Lead development work|
|Security manager | Responsible for security, policy ++|
|Training manager	| Organize training|
|Test lead | Lead test work|
|Trainers | Conduct training with end users|
|Support lead | Lead support efforts|
|Distributed support staff| Receive requests for support and help users|

### IT support unit

Support should be available close to the user, which often requires creating a new IT support structure at the district or sub-district level. If Tracker is used in real time, technical support should always be available during business hours to resolve and report issues. If Tracker will support clinical decisions, the IT staff should understand clinical workflow, and its represented in the technical system. Therefore, the Tracker IT support team may have different skill sets and backgrounds than other health information officers, and may be an entirely new and different cadre of worker within your health system.

**Team structure and administration**

Each member of the IT support unit should be trained before the first end user, and must demonstrate a high level of knowledge of the system and how it works. Often, the IT support unit consists of the same people leading the end-user training. At the very least, support staff should be introduced to the end users during training to develop rapport and trust from the start. A large component of support staff work is “supportive supervision” on the job. Effective support staff must also be knowledgeable, respected, and respectful, but are generally not in a position of direct authority over the end user, as this might reduce a user’s willingness to ask technical questions and report problems with the system.

Once the team is in place, an internal working hierarchy can be established, from increasing technical ability up the hierarchy (e.g. system administrator at top of the hierarchy), and increasing access to the end users down the hierarchy (e.g. direct supervisor of end user, field support staff). During this staffing organization phase, standard operating procedures for reporting and responding to issues from end users needs to be developed.

**Essential tools for any IT support unit**

- Frequently Asked Questions (FAQ) document: A simple paper depicting in graphics and/or local language the standard operating procedures for data entry and what to do in case of bugs. A FAQ should be distributed during all trainings, and it should be regularly updated by the IT support unit and shared with end users as the Tracker system evolves.

- Mobile device management: To protect patient-level data, a separate case management system must be implemented for tracking which users have access to which device to identify lost/stolen devices and follow up the case. This system can be as simple as a spreadsheet, but in larger and more complex instances an enterprise-level MDM system can be used to track device location, and can wipe an individual device remotely if needed.

- User management: The IT support unit should be able to document and manage basic system administration tasks such as creating new user accounts, de-activating inactive user accounts, or resetting passwords.

- Monitoring platform to track key system indicators: These key indicators include new enrollments by organisation unit, inactive users, server downtime, etc. At a minimum, the IT support unit should have access to aggregated indicators in a dedicated DHIS2 dashboard, where they can view implementation progress by time and region.

- Case management platform for registering bugs and tickets: These platforms (e.g. JIRA) allows members of the IT support staff to enter, edit, assign, track, and resolve bugs and other tickets, and allow supervisors to have oversight over important service-related factors, such as number of open tickets and unresolved bugs, average response time, etc.

- Knowledge management platform: This is a repository where employees can learn from previous tickets (thus building a knowledge base). The IT support unit understands the user’s real-world experience with Tracker better than any other implementer or system administrator, and their perspective can be invaluable to adapting Tracker to better meet the user’s needs. A knowledge platform–either electronic, or regular meetings among staff–can share common experiences, frustrations, or ideas for potential improvements

- Hotline to report bugs: This hotline can come in many forms. For example, it could be a phone number for support staff employees that is shared with each user, or an email address where users can send notes and screenshots. Regardless of format, there must be an SOP in place for entering bugs reported through the hotline into the case management platform mentioned above.

- Public chat groups: Many support teams find creating chat groups between staff and end users can support peer-to-peer learning (e.g. Whatsapp or Wechat to share screenshots, voice messages, or creative solutions for common problems).

*References*:  

- [Principles of Digital Development](https://digitalprinciples.org/) 



## Hosting

The tracker program itself and the collected data needs to be hosted on a server. This can be done locally (for example at the ministry), through a local professional service provider or in the cloud. The different options have pros and cons, e.g. hosting a tracker implementation in the cloud means administrator does not need to worry about server capacity, down time and so forth, but at the same time there might be legislative issues with hosting the data outside the country borders, unless you have a local provider. Regardless of hosting strategy - security is a key consideration. This entails identity management, authentication and authorization (restricting access to data or services) as well as protection of servers.

Additionally you have to decide if you want to configure the tracker in a separate or same instance as your aggregate system. A big advantage to having one instance is the possibility to directly generate your reports from tracker data. However, having the two in the same instance requires stricter SOPs for maintaining user accounts to ensure access to patient data is restricted properly.

10 principles for hosting and security 

1. Operating system is a LTS (long term service edition)
2. There is an automatic process for applying OS security patches    
3. Host based firewall configured allowing minimal access
4. Access is via ssh according to agreed policy - keys, no root access etc 
5. DHIS2 version is not more than 3 versions behind latest release. Process exists to apply patch releases regularly.
6. Automated backup system is in place and regularly tested, including offsite.
7. Postgresql database access controls allow minimal access      
8. Web-proxy server is properly (ssllabs test A+) configured with SSL
9. Database data is on separate data partition (allowing encryption at rest, performance settings)        
10. Monitoring and alerting system is in place (wide range of options depending on environment. eg. boombox might be fine with email + logwatch + munin ) 

Enough/stable electricity to charge devices  
In case of Android - network with a certain amount of uptime in order to sync.  
In case of web based - stable network

2) Servers/network/hosting

3) Hardware

Experience shows you need X number of devices per user

You need X % of devices for backup

Devices needs to rotate

- Database diagram (including virtual machines and physical networks)
- Minimum specifications for hardware… 
    - Servers
    - PCs
    - Android / M### Hosting & Securityobile
    - Other connected devices (e.g. fingerprint readers)
- Other infrastructure
    - Network access
    - Electricity access
    - SMS and data costs
    - Shared resources with other projects or ministries (e.g. government contract with SMS gateway provider)


 - Cloud-based vs Locally hosted: Depends on the regulatory environment of PII 
 - Management and sustainability of the IT systems.
 - Documentation exists on security plans and protocols. Both at high-level (non-jargon, but stating the principles) as well as technical procedures. Especially critical for locally-hosted systems without a “security first” culture.
 - One individual needs to be responsible of developing, maintaining and implementing the security plan. Another security manager committed to identifying and mitigating risks. Both roles require experience, capacity, and incentive.
 - Ensure that there is a documented set of technical controls mandated
 - Ensure that there is audit process against those controls
 - SOP for operational, network, and physical security (locking PCs, strong passwords, data encryption, etc)
 - SOP for monitoring and response if system is down or system breach
 - Disaster recovery plan and routine drills
 - Troubleshooting – process for “an external solution” in case of urgent crisis when situation cannot be resolved locally. 
 - What is process for granting database or ssh access to servers?
 - Access control and rules
 - Where should management of the IT system fall within the framework?


  
    
*References*:

  -   Security Guidelines for Country Implementers


## Training and Rollout

**Plan for high-quality, continual training.** Capacity building is crucial for a Tracker program to succeed, and it must be both high quality and continue periodically throughout the lifetime of the program. It is not sufficient to provide user training only once -- your training plan should provide for initial and refresher training over time. Frontline Tracker users are typically ground level health workers who may be less comfortable with technology than district staff who work more often with aggregated data. A strong emphasis on training will include time for familiarizing trainees with the tools as well as how to integrate Tracker into their workflow.

A key principle is to **develop training material in collaboration with users.** Working closely with users when you design the training material will allow you to understand what concepts are difficult for users to understand, so you can refine your material and timing for the training agenda. Do an initial entire training run with a group of real users to fine-tune your course.

Identify the appropriate training approach: There are multiple options for delivering your training (e.g. video, online test, on-site, meetings), which can be used individually or in conjunction with each other.

**Involve health staff** and not just IT staff in the trainings in order to explain and emphasise the health reasons behind the data entry processes. This is particularly relevant for configurations that involve decision support. Doing this helps end users to get a better understanding of why the Tracker program is significant, which can lead to more complete and accurate data entry, and thus a greater likelihood that the program will succeed in its goals.
Revise the material based on feedback from those attending the course, or if there are revisions of the Tracker program that cause the old training materials to become inaccurate.

**Logistics**  
Plan training of Tracker users as a series of training steps, such that they receive refresher training after some time. The refresher training schedule should ideally align with revision cycles of the Tracker software, to facilitate the introduction of end users to changes and new features in the program. 

Note that training a large group of users (especially spread out over a large geographical area) will often require that you first train other trainers (at a Training of Trainers, or ToT) early on, to help scale your training capacity.
Keep track of which Tracker users have been trained in spreadsheet, list, or other centralized database, and establish an SOP to update this list when new staff members join, or when existing staff members quit or are relocated. New/untrained staff members should be provided with training at the earliest possible opportunity.
Choose a training venue with care. Training can take place either on site (at or close to the users’ work environment) or in centralized trainings that bring larger groups of users from various workplaces to one centralized location. Both approaches have positive and negative aspects. Regardless of where the training takes place, the person responsible for planning the training will need to organize logistical details such as the venue, transport, food and drink, computers, Internet access, etc.

If possible, train users on the devices they will use in their work. Don’t underestimate the time it takes for people to log in and familiarize themselves with the device -- it can take a significant amount of time at the beginning of the training program to get all participants ready from a technical standpoint. It is recommended to have several members of the training team available to help troubleshoot these issues as they arise.
Schedule follow up regular/onsite training /refresher training

**Training in low bandwidth settings**  
If Internet connectivity is too slow, unreliable, or non-existent at your training location, you will need to install a local Tracker instance and configure it for training on a machine/local server, and set it up for the training such that participants can connect through a common local network environment, an IP address, or localhost client. Even in settings where Internet access is generally good, having a large number of users access the web-based Tracker instance through one WiFi network or Internet access point can lead to network issues. It is therefore generally advisable to have a training instance available as a backup in these cases.



## Relating Tracker to your Aggregate Data System

**Make sure to cover the basic reporting requirements from the HMIS when designing the tracker** to avoid double reporting. The data entered into tracker forms a basis for generating aggregate numbers. E.g. 4 patient entries = 2 with condition X and 2 with condition Y. Tracker should support the aggregate system, rather than be an extra burden on data collectors. System design should take into consideration how to meet aggregate data requirements using the data entered through tracker. 

There are different options to consider, either through automation or manually with the help of tools. You need a clear work flow, tools and governance model for data quality and completeness assurance and the data authorization process. In other words who can approve and process data from individual to aggregate data and how does this happen.

When you design the integration with the HMIS, make sure that the aggregation process is well thought through. 

- review the indicators
- create the reports
- create a governance model for data quality and publishing
- ensure the data revision processes are working (who owns the process and the data and what happens if you discover faulty data after deadlines)

It is important to make sure that care providers understand the indicators and are able to input into how they are calculated. Involve Ministry/policy-makers in the process so that they understand the fundamental differences between how reporting happened before vs. now in a tracker or eRegistry.


Feeding into the HMIS  
The data that is entered into tracker forms a basis for generating aggregate numbers. E.g. 4 patient entries = 2 with condition X and 2 with condition Y. Tracker should support the aggregate system, rather than be an extra burden on data collectors. System design should take into consideration how to meet aggregate data requirements using the data entered through tracker. In other words the workflow should avoid additional work for your health workers. They should not have to aggregate data manually and enter manually into the HMIS. 
 
Difference between aggregate data collection system, where the final numbers are input into online reporting forms vs. a tracker/an eRegistry that does automated reporting  

Significantly more effort in software design to cover all reporting and indicator needs 

Important to define indicators and understand what is to be measured: what is the numerator, what is the denominator 

Default denominator in an eRegistry: patients/clients 

Removing traditional paper reporting can be time-consuming, behavior-change takes time  

Important to make sure that care providers understand the indicators and are able to input into how they are calculated 

Involve Ministry/policy-makers in the process so that they understand the fundamental differences between how reporting happened before vs. now in an eRegistry 

> *References*:  
>
> Venkateswaran M: Attributes and consequences of health information systems data for antenatal care – health status, health system performance and policy, PhD dissertation, University of Bergen 
>
> Venkateswaran M, Mørkrid K, Khader KA, Awwad T, Friberg IK, Ghanem B, Hijaz T, Frøen JF: Comparing individual-level clinical data from antenatal records with routine health information systems indicators for antenatal care in the West Bank: A cross-sectional study. PloS one 2018, 13(11): e0207813 



