# Introduction

Tracker is the app within the DHIS2 platform that enables the capture and use of individual, longitudinal data. The functionality of Tracker covers a wide spectrum of needs, from monitoring the quality and availability of water wells, to collecting student attendance in a classroom, to capturing patient data in a shared health record. For the purposes of this guide, many of the examples will come from health systems, although Tracker is also widely used for education systems, environmental systems, logistics, and more.

Many countries and programs are making use of increased network availability and the widespread presence of mobile devices and other hardware to push information systems closer to the level where primary data are generated. Individual-level data adds granularity and nuance to datasets captured in routine information systems, providing opportunities for ad hoc analysis, shifting indicators over time, and improving data quality. Beyond its usefulness for reporting and analysis, individual-level data can also be used to eliminate reporting redundancies, empower lower level staff with better decision-making tools, and place the client at the center of the information system. In short, individual-level data is the smallest data unit, and as such can be repurposed in many ways to satisfy the various competing needs in national information systems.

## What can Tracker be used for?

As with the rest of the DHIS2 platform, Tracker has a generic data model that allows it to be configured by the user for many different purposes. At its most basic, Tracker allows the user to define a particular kind of thing (person, commodity, lab sample, catchment area, etc.) that they want to follow over time (a tracked entity), define the data that they want to collect about this entity (attributes, data elements), place the data elements in a specific order with accompanying conditions or logic (program stages, program rules), and determine the analytics that should be produced (program indicators, event reports, data visualizations, etc.)

An example of a simple Tracker program could be a program for collecting malaria case information at the point of care. The tracked entity would be a person, defined by attributes such as first name, last name, date of birth, or village. In general, attributes are data about the tracked entity (i.e. person) that are reasonably expected to stay the same over the period of follow-up and are often used to uniquely identify the entity (person). The program would contain data elements such as symptoms, test used and result, treatment provided, etc. These data elements might have pre-configured options for possible responses, such as possible tests available, or logic helping to ensure data quality, such as possible minimum and maximum values for a given data element. The data collected would be visible to the clinical user as a part of the malaria patient’s shared health record, but could also be used to generate monthly reports required by the national malaria control program, provide decision support to the clinician, generate SMS reminders to the patient to promote adherence to treatment, or populate a clinic-facing dashboard containing key performance indicators. For all these purposes, the data were collected only once -- during the patient visit -- but were reused many times for different needs.

DHIS2 also supports the collection of individual data without longitudinal tracking using the Capture and Event apps. Non-longitudinal tracking (Event programs) will be referred to throughout this documentation as well. Event programs generally follow the same data model as Tracker, with the exception of defining a tracked entity which is not required for non-longitudinal tracking. An example of such an Event program could be the reporting of line-listing malaria case data. The line-listing data captured by an Event program would contain the same individual data as in the previous (tracked entity) program, but without linking these data to a tracked entity (patient) for longitudinal tracking over time. As such, the data would not become a part of a shared health record (or perhaps not used to generate SMS message reminders to the patient, or other features that rely on tracking an entity over time); however, the Event program would capture more granular data about malaria cases than an aggregate data model, in turn enhancing analytical capability. 

As seen from the examples above, Tracker and the collection of individual data are quite different from traditional aggregate reporting for health management information systems (HMIS). Only one of the potential uses described above are satisfied by aggregate data collection -- that of monthly reporting -- whereas the patient-, clinician-, and facility-facing uses only become possible through the collection of individual data.

Even with regards to routine reporting, the collection of individual data introduces opportunities for improved data interpretation and analysis, and -- crucially -- for action to be taken. For example, an aggregate report might show that overall immunization coverage is 80%, but lacks detail as to whether the remaining 20% reflects errors in reporting, unintentional exclusion of certain individuals/groups (i.e. due to geographic or demographic factors), or other factors. The aggregate numbers also do not allow for the specific identification of non-vaccinated children that could be followed up with through a targeted outreach program. The aggregate numbers in this example address a basic need of Ministries of Health to report national progress on a global indicator, but not the needs of immunization program managers or providers to take specific actions to improve coverage.

One inherent benefit to using Tracker as an individual level system is the capacity for alignment with the existing aggregate DHIS2 system, which is already used in most lower- and middle-income countries as a national HMIS. Unlike a standalone Electronic Medical Record (EMR) or other application, Tracker encourages the collection of structured data that can natively aggregate upwards and be fed into the national HMIS, thus replacing secondary data entry and aggregation with primary source data.

As a core component of the DHIS2 platform, Tracker is updated twice annually along with the rest of the DHIS2 software. The driving inputs for improvements to Tracker come from real-country implementations, and are aligned with global recommendations, notably the [WHO Guidelines on Digital Interventions for Health Systems Strengthening](https://www.who.int/reproductivehealth/publications/digital-interventions-health-system-strengthening/en/). Of the ten recommended interventions, Tracker has specific functionality to support the following:

- Birth notification
- Death notification
- Stock notification and commodity management
- Targeted client communication
- Health worker decision support
- Digital tracking of client’s health status and services combined with decision support
- Digital tracking combined with decision support and targeted client communication
- Digital provision of training and educational content for health workers

Taking full advantage of such features requires that the data collected are systematic and adhere to normative standards. In health care, primary and public health services that are strongly driven by fixed guidelines and workflows are particularly suited for Tracker programs. For example in Antenatal Care (ANC), most countries have guidelines with algorithms for screening and patient management in response to test findings that can be incorporated in Tracker to follow a routine clinical workflow, supporting both the care provider and the reporting needs. In more complex areas of health care, with less documented and well-defined decision algorithms (such as in a referral hospital, for example) Tracker may be best used for simple data collection, allowing the clinician to determine the best use of the data for patient triage, and allowing the standardized data elements to be used for additional reporting or other purposes.

## Key aspects of DHIS2 Tracker include:

*Individual-Centric Data Management:*

DHIS2 Tracker is specifically tailored for programs that need to capture and analyze data at the individual level. It allows for the systematic collection and management of information related to individuals, such as patients, clients, program beneficiaries or students. It can also be used to track information related to any defined entity about which you need to enter data over time, such as a shipment of health commodities moving from one level of the supply chain to the next, a lab sample as it is first requested and then completed, or the water quality levels of a given well over time.

*Program-Oriented Approach:*

The Tracker functionality revolves around the concept of programs, representing a structured framework for capturing data relevant to specific health or programmatic interventions. This allows organizations to customize data collection forms, rules, and workflows based on the unique requirements of each program.

*Enrollment and Event Tracking:*

DHIS2 Tracker relies on the concepts of enrollment and event tracking. Enrollments represent the registration of individuals into specific programs, while events capture the occurrences or interactions within those programs. This dynamic framework enables the monitoring of individual journeys through various stages of a program.

*Flexible Data Elements and Attributes:*

The system supports the definition of custom data elements and attributes, providing flexibility in capturing a wide range of information. This adaptability ensures that organizations can tailor their data collection forms to capture the precise details needed for informed decision-making.

*Real-Time / Near real-time Data Capture:*

DHIS2 Tracker facilitates data entry through user-friendly interfaces on the web and on mobile devices. This allows frontline users to efficiently record data directly into the system, ensuring the availability of up-to-date information for analysis and reporting. It can be configured to support real-time data entry with decision support, or for secondary entry of data from another source, such as a paper register.

*Program Rules and Validation:*

The system incorporates program rules and validations, empowering organizations to define logical relationships and data quality checks. This supports the accuracy and integrity of the data collected, minimizing errors and enhancing data quality.

*Comprehensive Reporting and Analytics:*

DHIS2 Tracker seamlessly integrates with the reporting and analytics components of DHIS2. This integration enables organizations to generate detailed reports, conduct trend analyses, and derive actionable insights from the individual-level data captured through Tracker.

*Interoperability and Integration:*

The system is designed with interoperability in mind, supporting data exchange through various formats. It integrates seamlessly with other DHIS2 modules and can be extended to interface with external systems through APIs, facilitating a cohesive health information ecosystem.

 

## Example Tracker Use Cases

Throughout this guide, we will refer to use cases to give real-world examples of planning principles, decision points, software and data utilization, common hurdles and issues, and lessons learned at different stages of the Tracker planning and implementation process. A short introductory summary of these individual use cases is provided here. Greater detail for some of the use cases can be found on www.dhis2.org.

### Pre-configured Tracker Packages

Under the [DHIS2 Health Data Toolkit](https://dhis2.org/health-data-toolkit/), pre-configured Tracker programs have been created to cover a series of health topics. These packages are intended as the starting point for country programs, allowing for further configuration to match local context, while retaining global standards for indicators and practice. They can be added to existing DHIS2 systems, either together or individually. These packages can be accessed at the link above, as well as at who.dhis2.org. The current pre-configured packages cover the following topics:

- Adverse Events for Immunization
- Birth, Stillbirth and Death Notification for CRVS
- Cause of Death (including ICD-10 codes from the start-up mortality list)
- Malaria Breeding Site Investigation
- Malaria Diagnosis, Treatment, Case and Household Investigation
- Malaria Foci Investigation
- Mass Immunization Campaigns
- Routine Immunization Registry
- TB Case Surveillance

Additional packages are under development.

### Botswana: Nutrition and Immunization Program

Botswana has created a combined nutrition and immunization program providing key services to young children receiving nutrition assistance, while ensuring that the children are hitting their growth indicators and receiving the full set of vaccines. Working with the Botswana team, the Tracker platform was enhanced to produce standardized z-scores providing quick assessment of weight-for-height, weight-for-age, and height-for-age. 

### Ghana: HIV/ART and other eTracker modules

Since 2012, Ghana Health Services has led a pioneering program in reporting patient-level data through DHIS2 Tracker programs ("eTrackers"). As of 2019, they were using 8 different eTracker modules. A prime example is their HIV/ART eTracker, which tracks individual patients through testing and treatment and makes it easier for health personnel to identify and follow up with defaulters, while also supporting the reporting flow for aggregate HIV data, which has been ongoing in Ghana since 2006.
    
### Palestine: Maternal and Child Health eRegistry

Every woman in Palestine is assigned a primary health care clinic, and if that clinic does not provide the services she needs, she is asked to visit a higher-level clinic. This referral system requires an eRegistry that controls access to clinical patient files, supports the continuity of care across different healthcare sites, allows for data entry from several different points, and provides analytics to help drive decisions under Palestine's antenatal care guidelines. Our collaboration with Palestine started in 2014. The development and implementation of the maternal and child health (MCH) eRegistry included an iterative approach and dynamic dialogue between the developers, policymakers, public health officials and health care providers. This implementation features extensive use of automated SMS messages to communicate with patients, as well as quality improvement dashboards to measure performance of clinics and support the delivery of quality care.

### Zimbabwe: National Malaria Control Program

The DHIS2 Android Tracker implementation in Zimbabwe started in 2014 as a collaborative project between the National Malaria Control Program (NMCP) and the University of Oslo, and has since been scaled to cover nearly half of the country's 60+ districts. This implementation features offline data collection, detailed location data, and near real-time data collection and analysis, and is an example of working with multiple stakeholders at a global level to develop a program with potential for expansion across geographic regions and disease areas.

