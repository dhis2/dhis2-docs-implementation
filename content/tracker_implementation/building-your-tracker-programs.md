# Planning your Tracker Implementation

The purpose of this section is to give a high level overview of the considerations that will lead to success in your Tracker implementation, grouped by topic and with links to specific tools.

This section will cover:

1. Defining purpose, aim and scope
2. Scale
3. Design and Configuration process
4. Real-time vs. Secondary Data Entry
5. Mobile vs. Web
6. Establishing a Core Team
7. Hosting
8. Training
9. Roll-out

## DEFINE PURPOSE, AIM AND SCOPE

A clear purpose and well-defined aims are the key to establishing a common understanding of the project's scope and limitations, and to being able to communicate the process of developing and running a Tracker program internally and externally.

- Define the primary and secondary purposes of the Tracker program.
- Identify the tracked entities, the scope of data collection, and the health cadres involved in data collection.
- Determine how to uniquely identify members of the target population, (e.g., use of unique identification numbers or a combination of attributes).
- Clarify initial expectations among the core team, as well as other stakeholders and system users.
- Brainstorm and discuss key issues and areas of concern to be addressed during the development phase.
- Prepare to conduct a development phase: Develop a timeline and incorporate contingency plans for unexpected events that incur delays. Articulate anticipated problems and discuss how to mitigate.

## Determining Scale

Because individual-level data systems (i.e. Tracker) are aimed at the lowest levels of a system, Tracker programs can dramatically increase the number of users, hardware/devices, technical resources and organisational support required to implement and maintain the system. Countries often have limited personnel that are qualified to manage deployments and there are significant costs associated with the work. 

Scale can refer to several dimensions: programmatic scale, functional scale or geographic scale, to mention a few. 

Scaling geographically can thus take time and resources. There are different strategies to achieving geographical scale i.e. cover one region completely or start “small” in several regions at the same time and scale at a slightly slower pace in parallel.

As implementations scale, a snowball effect tends to take place. When you start scaling things will happen faster; the number of users can increase exponentially, which requires more people and stronger support mechanisms. Hence, planners can ensure that support teams are equipped to handle an increased volume and speed by taking into consideration the following:

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

We recommend to start the design process by asking the following questions to initiate discussions:

1. What is the purpose of the data you collect? How do you intend to use the data?
2. Who will benefit from the Tracker implementation?
3. How will the users entering data benefit from the Tracker implementation?
4. Do you currently collect this data today? How? What is the current data flow?
5. Are there data elements you currently collect that you do not need?


**FORMATIVE PHASE**

Gain a clear understanding of the health system (or other system that the Tracker program will cover, for non-health implementations) to understand the "pain points” of the current system, identify opportunities for improvement, and ultimately develop a useful and suitable system that addresses these issues and opportunities. This includes understanding health workers, the data they collect, their clinical workflows, and their supervisory and reporting systems.

- Prepare and undertake field visits to map clinical workflows and supervisory and reporting demands with the participation of all cadres of health staff who would use the Tracker.
- Prepare and undertake stakeholder meetings to inform, explore and get feedback.
- Verify existing national (clinical) guidelines relevant to the scope of the Tracker.
- Map the existing documentation workflow: Document what workers currently do and ensure your design supports their work practices rather than making them more cumbersome.
- Map indicators and associated data points for reporting.
- Consider whether there is a need for revision of guidelines or reporting points. If so, make parallel plans for revision of guidelines and reporting.

**DEVELOPMENT PHASE**

- Get an overview of current clinical guidelines, interventions, indicators and algorithms.
- Based on current guidelines -- as well as indicators and data points for reporting -- formulate algorithms and data points for electronic tracking.
- Define the target groups and level of complexity of decision support. According to the level of workflow support, create rules for the support and communicate this to software developers in an agreed-upon requirements format.
- Enable an iterative review process to ensure that the developers’ translation is consistent with the health care providers’ needs.

**CUSTOMIZATION AND TEST PHASE**

This phase is an iterative process of working with stakeholders, software developers, implementers and users and incorporating their feedback.

- Establish a structured and easily accessible digital system for comprehensive and immediate feedback channels among the core working group.
- Ensure that content development is in line with the expectations of stakeholders, system users and funders.
- Maintain ongoing, open-minded discussions about translation, use of information buttons, etc., to avoid misinterpretation.
- Make sure that there are continuous, parallel processes that involve and promote information flow among all user groups in these phases.
- Define milestones for developers, implementers and users.
- Establish a structured and easily accessible online digital system for comprehensive and detailed feedback from end users.

**WHO DHIS2 Health Data Toolkit**

DHIS2 works in partnership with the World Health Organization (WHO) on a variety of health-related initiatives, including the creation of standardized metadata packages to strengthen data use on a national and international level. The WHO-approved DHIS2 Health Data Toolkit provides a digital set of tools to support adoption of WHO routine health data standards into the national routine health information system. Aligned with the WHO Toolkit for Routine Health Information Systems Data, integrated analysis and program-specific DHIS2 modules are designed according to global data analysis guidance and standards for measurement. The DHIS2 toolkit provides a fully digitized reference implementation consisting of installable metadata packages, technical documentation, demo databases and implementation guidance. WHO-approved DHIS2 metadata packages can be installed in standalone DHIS2 systems or integrated into existing DHIS2 instances and adapted according to national context. The metadata packages bring together global standards and DHIS2’s evidence-based design practices for integrated health information systems in an installable toolkit that can be used for design reference or as a direct import for local use.

For more information on the WHO DHIS2 Health Data Toolkit documentation and tools, [see here](https://dhis2.org/who/).

## Determining your M&E Framework

A monitoring and evaluation (M&E) framework is an essential component of a DHIS2 Tracker implementation. It enables the assessment of the implementation's progress and success, and the identification of areas for improvement. A mature tracker implementation should have a robust M&E framework in place to ensure that data collection, use practices, DHIS2 version updates, user administration, security, hosting, user support, and training are all being effectively managed.

**What does a mature tracker implementation look like?**

A mature tracker implementation should have a comprehensive M&E framework that covers all aspects of the implementation. This includes regular evaluations of data collection, data use practices, DHIS2 version updates, user administration, security, hosting, user support, and training. The M&E framework should also include a process for identifying and addressing any issues that arise.

**Maintain and evaluate data collection**

It is important to regularly evaluate the data collection process to ensure that it is accurate, complete, and timely. This includes assessing the quality of data entered, the completeness of the data, and the timeliness of data submission. Identifying and addressing any issues with data collection will improve the overall quality of the data.

**Maintain and evaluate data use practices**

Regularly evaluating data use practices will ensure that the data is being used effectively to inform decision-making and that it is being used in a way that aligns with the organization's goals and objectives. This includes assessing the quality of data analysis, the use of data in decision-making, and the effectiveness of data dissemination.

**Maintain and evaluate keep up with new DHIS 2 versions**

Keeping up with new DHIS2 versions is important to ensure that the implementation is using the most up-to-date version of the software. This includes regularly assessing the version of DHIS2 being used, evaluating the benefits of upgrading to a new version, and implementing any necessary upgrades.

**Maintain and evaluate user admin**

Regularly evaluating user administration will ensure that users have the appropriate access to the system, that user roles and permissions are properly configured, and that user accounts are being managed effectively. This includes assessing the number of active users, the number of new users, and the number of inactive users.

**Maintain and evaluate security**

Regularly evaluating the implementation's security measures will ensure that the data is being protected and that the system is in compliance with security regulations. This includes assessing the effectiveness of the system's authentication and authorization processes, the security of the hosting environment, and the effectiveness of the system's disaster recovery plan.

**Maintain and evaluate hosting**

Regularly evaluating the hosting environment will ensure that the system is properly configured, that the system is performing well, and that the system is available to users. This includes assessing the stability and performance of the hosting environment, the security of the hosting environment, and the availability of the system.

**Maintain and evaluate user suppor**

Regularly evaluating user support will ensure that users are able to effectively use the system and that any issues are being resolved in a timely manner. This includes assessing the responsiveness of the user support team, the effectiveness of the user support team, and the quality of the user support documentation.

**Maintain and evaluate training**

Regularly evaluating the training program will ensure that users are properly trained and that the training program is meeting the needs of the organization. This includes assessing the effectiveness of the training program, the quality of the training materials, and the number of users who have completed the training program.

It is important to note that the monitoring and evaluation framework should be regularly reviewed and updated to ensure that it is meeting the needs of the organization and that it is aligned with the organization's goals and objectives. It should also be compliant with any national and international regulations and standards related to data security and protection.


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

The DHIS2 Tracker program and collected data must be hosted on a server. This can be done locally (such as at the ministry of health or IT), through a local professional service provider, or in the cloud. Each option has its own advantages and disadvantages. For example, hosting a tracker implementation in the cloud means the administrator does not need to worry about server capacity and downtime, but there may be legal issues with hosting the data outside the country's borders unless a local provider is used. Regardless of the hosting strategy, security is a key consideration. This includes identity management, authentication and authorization (restricting access to data or services), and protecting servers.

Additionally, it is important to decide whether to configure the tracker in a separate or the same instance as your aggregate system. A major advantage of having one instance is the ability to directly generate reports from tracker data. However, having the two in the same instance requires stricter standard operating procedures (SOPs) for maintaining user accounts to ensure proper access to patient data is restricted.

**10 hosting and security principles that should be included in your hosting plan, regardless of whether the instance is local or in the cloud:**

- The operating system is a Long-Term Service (LTS) edition
- There is an automatic process for applying OS security patches
- A host-based firewall is configured to allow minimal access
- Access is via Secure Shell (SSH) according to agreed policy (keys, no root access, etc.)
- The DHIS2 version is not more than 3 versions behind the latest release, and a process exists to apply patch releases regularly.
- An automated backup system is in place and regularly tested, including offsite.
- PostgreSQL database access controls allow minimal access
- A Web-proxy server is properly (SSL Labs test A+) configured with Secure Sockets Layer (SSL)
- All Database data is stored on a separate data partition (allowing encryption at rest, performance settings)
- A monitoring and alerting system is in place
      - There is a wide range of options available, depending on the environment. For example, boombox might be fine with email + logwatch + munin.
- Enough/stable electricity to charge devices
- If using Android, there must be a network with a certain amount of uptime to sync.
- If web-based, a stable network is present


**Management and sustainability of the IT systems:**

Documentation exists on security plans and protocols, both at a high-level as well as technical procedures. Thi is especially critical for locally-hosted systems without a “security first” culture.

One individual needs to be responsible for developing, maintaining, and implementing the security plan. Another security manager committed to identifying and mitigating risks. Both roles require experience, capacity, and incentives.

Ensure that there is a documented set of technical controls mandated, and that there is an audit process against those controls

Published and available SOPs for operational, network, and physical security (locking PCs, strong passwords, data encryption, etc.), as well as for monitoring and response if the system is down or system breach


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

When designing the tracker, it is important to consider the basic reporting requirements of the Health Management Information System (HMIS) to avoid double reporting. The data entered into the tracker forms the basis for generating aggregate numbers. For example, if there are 4 patient entries, 2 with condition X and 2 with condition Y. The tracker should support the aggregate system, rather than being an additional burden on data collectors. The system design should take into consideration how to meet aggregate data requirements using the data entered through the tracker.

There are different options to consider, such as automation or manual methods with the help of tools. It is crucial to have a clear workflow, tools, and governance model for data quality and completeness assurance and the data authorization process. This includes determining who can approve and process data from individual to aggregate data and how this process occurs.

When designing the integration with the HMIS, make sure to thoroughly review the indicators, create the reports, establish a governance model for data quality and publishing, and ensure that the data revision processes are working. It is important to involve care providers in the process to ensure they understand the indicators and are able to input into how they are calculated. Additionally, involve Ministry/policy-makers in the process so that they understand the fundamental differences between how reporting happened before vs. now in a tracker or eRegistry.

**Feeding into the HMIS**

The data entered into the tracker forms the basis for generating aggregate numbers. The tracker should support the aggregate system, rather than being an additional burden on data collectors. The system design should take into consideration how to meet aggregate data requirements using the data entered through the tracker. In other words, the workflow should avoid additional work for health workers and they should not have to aggregate data manually and enter it manually into the HMIS.

The difference between aggregate data collection systems, where the final numbers are input into online reporting forms, and a tracker/eRegistry that does automated reporting is the significantly more effort required in software design to cover all reporting and indicator needs. It is important to define indicators and understand what is to be measured, including the numerator and denominator.

Removing traditional paper reporting can be time-consuming and behavior-change takes time. It is important to make sure that care providers understand the indicators and are able to input into how they are calculated. Involve Ministry/policy-makers in the process so that they understand the fundamental differences between how reporting happened before vs. now in an eRegistry.

> *References*:  
>
> Venkateswaran M: Attributes and consequences of health information systems data for antenatal care – health status, health system performance and policy, PhD dissertation, University of Bergen 
>
> Venkateswaran M, Mørkrid K, Khader KA, Awwad T, Friberg IK, Ghanem B, Hijaz T, Frøen JF: Comparing individual-level clinical data from antenatal records with routine health information systems indicators for antenatal care in the West Bank: A cross-sectional study. PloS one 2018, 13(11): e0207813 



