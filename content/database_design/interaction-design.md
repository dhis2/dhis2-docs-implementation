# Interaction Design 



![](resources/images/image30.png "Step5")


After defining the structure of the program–arranging it into stages, attributes, and data elements–you have a “workable” prototype that allows users to enter individual level data and produce routine data reports.

In practice, real people will be entering individual level data. They will often have pressures on their time to enter many data points for many patients in the same day. They will sometimes make errors and enter invalid or inconsistent data.

Smart **interaction design** improves the user experience, which can help with **improving data quality **and **facilitating intuitive data entry workflows**. These are not just aesthetic considerations, but key tools for supporting data entry personnel by making their jobs easier and more efficient. And as described above, program rules can also be used to support the design of program stage structures required for data entry workflow and analytics outputs.


## Tracker Features To Streamline User Experience

In DHIS2, strong interaction design can be configured through the following features, which support an end user to efficiently and effectively search for the correct TEI, navigate to the correct stage and event, then enter valid data element values.


> **Work In Progress**
>
> While full exploration of interaction design and Tracker capabilities is out of scope for this guide, configuration instructions are presented elsewhere in the documentation. See links below.


* **TEI Searches**
    * Patient Rosters (Working Lists)in [Capture](#capture_views) and [Tracker Capture](#webapi_tracker_api)
    * [Patient Listings  (Line Lists)](#using-the-line-listing-app)
    * Which TEI are [searchable](#configure_search), how long they need to be open
    * Trade-off between [search flexibility and performance](https://www.duo.uio.no/bitstream/handle/10852/91269/Ameen_MasterThesis_Final_14_11_2021.pdf?sequence=1&isAllowed=y)
    * “Search org units” and [accessibility](#configure-search-organisation-units-for-a-user)
    * [Tracker search optimization](#scheduling_tracker_search_optimization) (trigram indexing)
* **Program and Program Stage Settings**
    * [Expiry days and completed event expiry days](https://community.dhis2.org/t/could-block-last-three-month-for-event-capture-and-event-tracker/37465/2)
* **Program Rules**
    * [Skip logic (show/hides)](https://community.dhis2.org/t/programa-rules-hide-or-disable-a-data-element/48751/2)
    * [Assign](https://community.dhis2.org/t/problem-with-program-rule-action/49958)
    * [Warning boxes](https://community.dhis2.org/t/how-to-automate-patient-tracking/42304/3)
    * [Error boxes](https://community.dhis2.org/t/any-possibility-to-limit-a-repeatable-program-stage/42213/4)
    * [Priorities of rules to create a cascading logic](https://community.dhis2.org/t/program-rule-for-age-value-type/5002/2)
    * “Select multiple” data elements  –  Yes Only data elements within the same section with program rules overlaid so only one can be entered
    * [Differences of Android and Web program rule evaluation](#capture_app_pr)
* **TEI Dashboard layout**
    * [Widget layout](#widget-descriptions)
    * Feedback and Top Bar dynamic updates [through program rules](https://docs.dhis2.org/en/use/user-guides/dhis-core-version-238/configuring-the-system/programs.html?h=feedback+widget+use#program_rule_examples)
    * “Live” [program indicators](https://community.dhis2.org/t/how-to-create-and-view-indicators-for-a-tracked-entity-instance/51141)
    * [Android Settings app](#capture_app_android_settings_webapp)
* **Visual Configuration**
    * Icons and colours on data elements ([Android](#capture_app_visual))
* **Tracker Data Entry Modes**
    * [Timeline and tabular data entry](#widgets-for-data-entry)
***Other Tracker features to support intuitive workflows**
* [Program Notifications](#create-a-program-stage-notification) (SMS alerts, emails, or DHIS2 messages)
* [User Assignment](#capture_user_assignment)
* [Relationships](#relationship_model)

During the testing phase of the project, you should consult with beta testers on their experience of using the tracker program prototype, to understand  how these features can be best utilised to support their workflows. 
