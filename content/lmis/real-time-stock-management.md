# Real-Time Stock Management Tool


![](media/image95.png)

## 1 OVERVIEW OF THE DHIS2 REAL-TIME STOCK MANAGEMENT TOOL

This entire document describes the expected system behaviour, functionality and management and neither the current processes or systems nor the change from the "as is" to the "to be" state.

### 1.1 Use case overview

The DHIS2-RTS provides a web and mobile app-based tool (with off-line capability), real-time digital solution for stock management which can be integrated with national eLMIS systems for managing stock replenishment as well as end-to-end supply chain analytics.

The system provides global, real-time stock and data visibility from healthcare facilities to pharmacy staff as well as health and logistics staff at all levels of the supply chain regardless of their physical location.

Staff at healthcare facilities replace data collection on paper or with spreadsheet applications by recording data directly on mobile devices on-line (with off-line capability) using a dedicated mobile device application. Staff at healthcare facilities or at the district level no longer have to re-enter data provided by pharmacies into Excel files (or any other application) for calculating monthly replenishment orders.

The current, paper- (or spreadsheet) based, workflow for replenishing pharmacies at assisted healthcare facilities is replaced by a fully digital, integrated and systematic workflow which is standardized across all healthcare facilities.

Recording individual stock transactions rather than recording and reporting stock data once a month is a significant change of procedures which has many benefits:

- Stocks are (re)calculated in real-time during every stock transaction and users at any level have real-time visibility of stock levels as well as customer demand ("consumption")

- All transactions are recorded digitally on a central DHIS2 server and eliminate the cumbersome, boring, time-consuming and painstaking need for recording every transaction in a stock card

- The system, in principle, eliminates the need for counting all stocks at the end of the month which takes between (at least) 2-5 days every month during which the pharmacy is closed

- The system eliminates to manually tally up distributions for each item at the end of the month from stock cards which is an equally cumbersome, boring, time-consuming and painstaking activity

- The system eliminates redundancies for data collection with national LMIS systems (even if on paper or in Excel) as a single data value, namely the transaction quantity of every item, is recorded.

**Structures and preconditions**

The application is based on adherence to specific structures and processes which inform the system design and functionality.

- All medical stocks are stored and managed in a single central pharmacy in every healthcare facility.

- While the system and the application are primarily designed for managing healthcare goods, any other types of goods such as food, cleaning materials, stationery etc. could also be managed.

- A single (central) pharmacy supplies all departments and services in a healthcare facility.

- The system will replace and facilitate certain current processes, but healthcare facilities are of course free to continue any additional manual or electronic data recording and processing systems (such as using batch cards, stock cards, delivery records, tally sheets etc.).

- All pharmacies have at least daily access to at least a 2G mobile phone network for transmitting data. However, it is strongly recommended that a permanent Internet connection is used as otherwise there is a high risk of losing all data which has not been synchronized yet in case of any fault of the mobile device.

- In case the system fails, pharmacies are able to "switch" back to a manual (backup) system, such as resuming the use of stock cards, at any time without in any way impairing the supply of the pharmacy.

- State authorities, health authorities (national, provincial, district level), management of healthcare facilities as well as pharmacy staff agree on using mobile devices for recording, storing, managing and transmitting pharmacy stock data.

- Mobile devices are available and reliably maintained.
- Staff at the healthcare facility are conversant with the use of mobile devices or can be trained (within reasonable time).

### 1.2 System components

The system consists of the following distinct components:

- Central DHIS2 server and database
- DHIS2 web portal (user interface)
- DHIS2 Tracker Program
- DHIS2 Data Entry Form for monthly "snapshots" as well as a fallback open in case of DHIS2-RTS failure

- DHIS2 mobile app for recording transactions by scanning barcodes
- DHIS2 mobile app analytics in the DHIS2-RTS, particularly electronic stock cards and monthly stock report

- In addition (!!!) mobile app analytics in a default data entry form for monthly reporting and analysis

- Optionally (but highly recommended): national eLMIS which is integrated with DHIS2

The guiding principle of the DHIS2-RTS concept is using mainly national eLMIS functionality for managing all logistics processes and collecting only the data which is generated at the healthcare facility with the DHIS2-RTS app. This strictly follows the DRY ("Don\'t Repeat Yourself") software development principle: "Every piece of knowledge must have a single, unambiguous, authoritative representation within a system".

### 1.3 Overview of business processes and workflows

The DHIS2-RTS mobile application is used by storekeepers of pharmacies and medical stores at healthcare facilities, called "end-users".

"Department and service" stands for any facility or service within any healthcare facility which holds and manages stocks of any kind which are regularly replenished such as patient wards, dispensaries (OPD), operating theatres, sterilization services, laboratory and blood transfusion services, diagnostic imaging, laundry, maintenance services or other services.

**Processes**

- Receiving and put-away of stocks received from upstream medical distribution centres

- Managing medical stocks
- Receiving, recording and managing periodic orders from wards and services (not part of the DHIS2-RTS mobile application but indispensable part of the workflow)

- Picking, packing and delivering ordered goods to departments and services

- Viewing current stock on hand
- Various analytics such as analysis of (aggregate) monthly demand

The mobile device application is primarily intended for collecting, temporarily storing and transmitting only essential data which could not be collected otherwise to the server.

Among other reasons, this approach minimizes the frequency, amount of data and size of data packages which need to be transmitted from the mobile device which reduces the time of data transmission, reduces costs and increases resilience of the data transmission to poor mobile Internet connections.

Around 50 stock items (Primary Health Care centre) to 500 stock items (hospitals) will and can be managed by this mobile device application. Although in principle there is no limitation by the system, usability decreases with an increasing number of stock items. For comparison: a hospital pharmacy in an industrialized country will manage around 3,000 drug products and around 20,000 other health care products.

The DHIS2 web portal may be used by managers at the healthcare facilities but is more likely to be used by health or logistics managers almost exclusively for consulting analytics reports.

### 1.4 Stock calculations

The "Stock on hand" is (re)calculated in real-time after every transaction which are mainly recorded on the mobile device but are also be affected by transactions through the Tracker Program in the web portal or through integrations with a national upstream eLMIS.

The "Stock on hand" calculation is always iterative with the Program Rules processing every transaction one at a time. This means that the calculation is based on the current "Stock on hand" (which results from the most recent transaction) as well as the most recent transaction for again calculating the current "Stock on hand". Consequently, the system does not keep any historic memory of the "Stock on hand" at any time except for the current value. In principle the current "Stock on hand" could be calculated by adding all transactions for any specific item and Organisation Unit from the time the database was established. However, this would require increasingly complex calculations which are redundant and unnecessary.

It is important to note that, except for the "Correction" all transaction "Quantity" represent the quantities of the transaction while for the "Correction" the user is required to enter the result of the actual physical stock count while the system will calculate the difference between the two values as the (virtual) transaction quantity which is required for analysis.

The second important logistics data item which the system captures is the transaction quantity. This is critical for calculating the monthly demand which in turn is indispensable for demand analysis, forecasting, demand planning and stock replenishment calculations.

In principle, only transactions which increase the "Stock on hand" (receipts, "positive" corrections, return) should have positive signs while any transactions which reduce the "Stock on hand" (distribution, "negative" corrections, discard and transfer) should in principle should use negative signs. However, requiring storekeepers to use a "-" sign would not only pose an unnecessary hassle and delay, it would also be a significant source of errors. Therefore the "+" or "-" signs have to be "hard coded" into the metadata, particularly the Program Rules.

All transactions as well as the actual "Stock on hand" always have positive integer values and can never be zero (as this is by definition not a transaction).

Transactions have different boundaries and affect the calculated logistics data in different ways:

Transaction type Effect on "Stock on hand" Effect on total monthly demand

---

Distribution Decrease Increase Discard Decrease Not effected Correction: SoH \> calculated value Increase Not effected Correction: SoH \< calculated value Decrease Not effected Return Increase Decrease Transfer Decrease Not effected Receipt Increase Not effected

### 1.5 Mobile device management

The entity or organization, such as the Ministry of Health, must provide and ensure maintenance of mobile devices and govern their use. For the sake of data protection, sustainability and managing data subscriptions, the use of private devices should be discouraged.

In order to avoid reliance on a single device and interruption in case that device fails, is lost or stolen, the DHIS2-RTS application should only be used if at least one back-up device is available at every health care facility.

The DHIS2-RTS mobile app is built on the concept and assumption that transactions are exclusively recorded on mobile devices. In principle, the web-based application could be used on desktop or laptop computer with an external barcode reader. However, these would not allow scanning barcodes directly at the storage location (shelf or pallet) inside storerooms. This would require first picking the items and then processing them at a table in the dispatch room. However, it would not be in any way practical to keep the barcodes in this place for processing the transactions using a barcode scanner.

If mobile devices are purchased specifically for the implementation of DHIS2-RTS, the native DHIS2 recommendations should be followed and in addition the following points need to be considered:

- In any case, they should feature SIM-cards for connecting to a mobile network as a primary or back-up means of data transmission and synchronization and allow connecting to WLAN

- Mobile devices must feature a rear camera for scanning bar codes
- Mobile devices should feature an integrated microphone (for the optional speech-to-text recording)

- For carrying out transactions, a small and light device should be favoured

- For studying the analytics, ideally a larger tablet computer should be used

- The device should withstand the rugged climatic conditions in the country in terms of temperature, humidity and dust and be resilient to drops and other physical damage

The DHIS2 documentation lists the following mobile device specification requirements (last updated 11.08.2022): [DHIS2 Mobile Device Specifications](https://docs.dhis2.org/en/implement/android-implementation/mobile-device-specifications.html)

**Specification** **DHIS2**

---

Construction Lifespan of at least 2 years Android operating system version minimum 5.0, minimum recommended 7.X and recommended 8.X or higher Processor 4 cores, 1.2 GHz RAM (tablet) minimum 1.5 Gb, recommended more than 3 Gb Storage minimum 8 Gb, recommended 32 Gb Screen size minimum 7 inches Camera minimum 5 megapixel, recommended at least 8 mega pixel Connectivity 4G (LTE) / 3G and WLAN

One possible (future) option for resolving the conflict between a small and light device for order picking and the preference of a larger screen for analytics is attaching a larger mobile device to a cart during transactions while scanning the barcodes with an external barcode scanner connected to the mobile device through an USB-cable or a Bluetooth connection.

### 1.6 Contingency plan in case of device failure

In case the mobile device fails or malfunctions for any reason (out of charge, damaged, not found, stolen, authentication forgotten) or the Internet access is not available for more than one day, healthcare facilities should consider using alternative mobile device or Internet access.

**In case the Internet is unavailable for less than one day**

- Wait for restoring of the Internet connection provided no urgent orders have to be treated

- Keep the requests from departments and services and carefully record the actually distributed quantities

- Retrospectively enter the transaction by scrolling down the stock item list and recording quantities

**In case of Internet is unavailable for more than one day**

- Resume manual recording of transactions on stock cards
- Use a DHIS2 Default Data Entry Form at the end of the month (which is much less work than retrospectively entering hundreds of transactions

**In case all systems fail**

At any time, users can resort to the manual, paper- or spreadsheet-based method which were in use before the introduction of the DHIS2-RTS application:

- Carry out the physical stock count
- Record the stock on hand and monthly consumption on a worksheet printout or other paper record

- Calculate the monthly replenishment order using a paper record or a spreadsheet application

## 2 DHIS2 METADATA CONFIGURATION

Although configuration of DHIS2 in general and the DHIS2 Tracker Program in particular are not part of the development, many settings are closely linked to the custom development and critical for its functioning. Moreover, this chapter is added in order to provide full documentation of the entire system which is required for running and using DHIS2-RTS.

All the configurations and settings use only native DHIS2 functionality and do not require extending or developing any DHIS2 features.

### 2.1 DHIS2 server instance system configuration

The DHIS2 server (instance) is the physical device where the DHIS2 software as well as the database holding the data is installed, permanently running and allows a large number of users to connect to the DHIS2 web portal as well as the DHIS2 mobile device application and its data base at any time.

Maintenance of the server, backups, upgrades and resolving errors will have to be ensured by the entity in charge of managing the public health supply system, usually the Ministry of Health (MoH). This work is carried out according to standard DHIS2 guidelines and recommendations.

### 2.2 User app

The Users app allows configuring User roles, creating user profiles for individual users and assigning them to defined User groups.

#### 2.2.1 User

User access will be managed by the entity managing the central DHIS2 server and according to national policies concerning data security.

By default, the language is set to the national language used in the country, or in case there is more than one, according to national policies but can be adapted to individual users or user groups if needed.

The DHIS2-RTS should allow using any language configured on the central DHIS2 server.

According to their responsibilities, needs for accessing (viewing) data and authority to change (edit) data, every user is assigned one or several of the "User roles" and assigned to one specific (or exceptionally more than one) Organisation unit for which s/he has access for viewing and editing data.

#### 2.2.2 User role

Three distinct User roles are configured which each give access to specific DHIS2 apps and determine whether users can access certain metadata such as Data elements, Data sets or Organisation units.

If a Default Data Entry Form is configured as a "backup" in case of DHIS2-RTS failure, user rights have to be configured both for the Data Entry Form as well as the Tracker Program.

While configuring user settings is a native DHIS2 functionality, the details of providing users access to the DHIS2-RTS mobile app (and module) need to be developed.

**DHIS2-RTS - Data entry**

This User role allows users to access the DHIS2 Capture Android app (native app) on mobile devices as well as to DHIS2-RTS within the "module" for viewing, entering and recording transactions.

**DHIS2-RTS - Reader**

This User role allows users to view stock data in the DHIS2-RTS (or only viewing the in-app off-line analytics reports).

**DHIS2-RTS - Superuser**

This user role is reserved to system administrators and allows configuring settings and managing the DHIS2 instance and system.

#### 2.2.3 User group

The main purpose of user groups is facilitating configuration of "Sharing" settings (which determine viewing and editing rights) by groups rather than having to manage them at the level of hundreds of individual users.

User groups should be configured according to the User Role into the same three groups:

- Data entry
- Reader
- Superuser

### 2.3 Maintenance app

The DHIS2 Maintenance app allows the system administrator to configure and modify DHIS2 metadata which are necessary for running the DHIS2 application as well as the DHIS" RTS mobile application.

All geographical conventions must follow national conventions, ideally replicating conventions of a national Master Facility List.

Metadata requires configuration only when setting up the DHIS2 instance and whenever changing the master data such as adding or "inactivating" Organisation units, adding or removing items from the item catalogue. These configurations and settings are not changed frequently but need to be carefully and meticulously managed to ensure that the DHIS2 is always kept up to date.

In DHIS2 all metadata is automatically assigned unique IDs ("keys") which are not visible to field users but indispensable for the functioning of databases.

#### 2.3.1 Organisation Unit

This application allows creating new and editing existing geographical entities. As the hierarchy of regions, countries and First Administrative Level is defined by national policies and does not change, the main objective of this application is adding new healthcare facilities.

The "Latitude" and "Longitude" are useful for mapping the location of healthcare facilities in the Data Visualizer.

#### 2.3.2 Organisation Unit group

The "Organisation unit groups" allow grouping healthcare facilities according to their level of care, for example "clinic", "hospital" etc. and are configured according to national policies.

#### 2.3.3 Organisation Unit level

The Organisation unit levels allow representing the geographical structure and hierarchy of healthcare facilities and are configured according to national policies and the Master Facility List.

#### 2.3.4 Hierarchy operations

The Hierarchy operations application represents the complete geographical and hierarchical structure of the Organisation units and allows changing the position of Organisation units in the Organisation unit hierarchy if they were not created at the correct hierarchical levels. Once created, the place in the hierarchy should, in principle, never change.

#### 2.3.5 Category option

Category options are not needed for recording transactions in the Tracker Program but required for the monthly Tracker Program "snapshot" data as well as a fallback system in case the DHIS2-RTS (temporarily) fails. In addition to the transactions, a separate Category option is needed for each of the "Deliver to" options in order to record all details of "Distribution" transactions:

- "DIS - (Other)"
- "DIS - Diagn. imaging"
- "DIS - Emergency Room"
- "DIS - High Depend. Unit"
- "DIS - Housekeeping"
- "DIS - Inp. Med. Depart."
- "DIS - Inp. Surg. Depart."
- "DIS - Laboratory Depart."
- "DIS - Mortuary"
- "DIS - OPD"
- "DIS - Obst. & Gynae."
- "DIS - Oper. Theatre"
- "DIS - Paed. Dep."
- "DIS - Physioth. Dep."
- "DIS - Recovery Room"
- "DIS - Steril. Dep."
- "DIS - Transf. services"
- Previous stock balance
- Stock correction
- Stock discard
- Stock distribution
- Stock on hand
- Stock receipt
- Stock on hand Yes/No

Note that the "Stock distribution" corresponds to the total quantity of all the "DIS - [Deliver to] Category options and can be removed/added or be hidden/unhidden as and if needed.

#### 2.3.6 Category

The Category "RTS - Daily stock report" combines the following "Category options":

- Name (\*): "RTS - Daily stock report"
- Short name (\*): "RTS - Daily stock report"
- Data dimension type (\*): "Disaggregation"
- "Data dimension": check (appears as white tick in a blue square)
- Category options (please note the correct order):
- Previous stock balance
- Stock receipt
- "DIS - Diagn. imaging"
- "DIS - Emergency Room"
- "DIS - High Depend. Unit"
- "DIS - Housekeeping"
- "DIS - Inp. Med. Depart."
- "DIS - Inp. Surg. Depart."
- "DIS - Laboratory Depart."
- "DIS - Mortuary"
- "DIS - Obst. & Gynae."
- "DIS - OPD"
- "DIS - Oper. Theatre"
- "DIS - (Other)"
- "DIS - Paed. Dep."
- "DIS - Physioth. Dep."
- "DIS - Recovery Room"
- "DIS - Steril. Dep."
- "DIS - Transf. services"
- Stock distribution
- Stock discard
- Stock correction
- Stock on hand
- Stock on hand Yes/No

The Category "RTS - Monthly stock report" combines the following "Category options":

- Name (\*): "RTS - Monthly stock report"
- Short name (\*): "RTS - Monthly stock report"
- Data dimension type (\*): "Disaggregation"
- "Data dimension": check (appears as white tick in a blue square)
- Category options (please note the correct order):
- Previous stock balance
- Stock receipt
- "DIS - Diagn. imaging"
- "DIS - Emergency Room"
- "DIS - High Depend. Unit"
- "DIS - Housekeeping"
- "DIS - Inp. Med. Depart."
- "DIS - Inp. Surg. Depart."
- "DIS - Laboratory Depart."
- "DIS - Mortuary"
- "DIS - Obst. & Gynae."
- "DIS - OPD"
- "DIS - Oper. Theatre"
- "DIS - (Other)"
- "DIS - Paed. Dep."
- "DIS - Physioth. Dep."
- "DIS - Recovery Room"
- "DIS - Steril. Dep."
- "DIS - Transf. services"
- Stock distribution
- Stock discard
- Stock correction
- Stock on hand

#### 2.3.7 Category combination

The only "Category combination" mirrors the only "Category": which is required for technical reasons:

- Name (\*): "RTS - Monthly stock report"
- Data dimension type (\*): "Disaggregation"
- Categories: "RTS - Monthly stock report"

#### 2.3.8 Data element - item catalogue

Data elements represent the items (healthcare products) for which logistics data is recorded and managed.

All health care products which are registered in the DHIS2-RTS as "Tracked Entity Instance" (TEIs) need to be "mirrored" as identical Data Elements for configuring the Data Sets which are needed for every Organization Unit as a backup system.

Note that Data Elements and TEIs cannot be automatically "linked" but new TEIs can be exported, for example once a month, and "re-loaded" as Data Elements.

A separate Data Element is created for each health care product in use and the naming follows national conventions, ideally according to a national item master catalogue. In case DHIS2 is integrated with a national eLMIS item codes as well as item descriptions in DHIS2 must exactly match the item codes and item descriptions in the national eLMIS.

In case item codes are in use, they can be concatenated in the "Name" field together with the item description. However, not that if the item code is followed by the item description, all Data Elements will automatically and invariably be sorted by the item code which may useless for storing health care goods according to their groups.

The "Domain type" must be set to "Aggregate", the "Value type" to "Positive or Zero Integer" and the "Aggregation type" to "None". The field "Store zero data values" must be checked in order to allow storing the value of zero and the "Category combination" must be set to "Health facility - monthly stock report".

Data elements which have been created and used cannot be deleted from the database any more as the historic data needs to be maintained. But Data Elements which are no longer needed can simply be removed from the respective Data Sets.

- Name (\*): DORAALBE4T - ALBENDAZOLE, 400 mg, tab. MTH
- Short name (\*): DORAALBE4T - MTH
- Code: DORAALBE4T - MTH
- Domain type (\*): "Aggregate"
- Value type (\*): "Positive or Zero Integer"
- Store zero data values: check (appears as white tick in a blue square)

- Category combination (\*): "RTS - Monthly stock report"
- Aggregation levels: "Facility" [Question: confirm this need]

In addition, for each item an equivalent item with the suffix "DAY" is needed for configuring the "RTS Daily report" Data set.

#### 2.3.9 Data element group

The creation of Data element groups is a precondition for using the "Group Predictor" functionality which allows using a placeholder and the Data element group ID for creating a single Predictor which is automatically applied to all Data elements in the respective Data element group. For example for calculating the stock coverage time.

**[Stock item list - CL]**

- Name (\*): "Stock item list"
- Short name (\*): Stock item list
- Data elements: include all Data elements of Data collection and calculation report

**[Stock item list] - DAY**

- Name (\*): "[Stock item list] - DAY"
- Short name (\*): "[Stock item list] - DAY"
- Data elements: include all Data elements from daily RTS report

#### 2.3.10 Data set

Data sets for each Organisation unit are required both for recording monthly "snapshots" of Tracker Program data as well as a fallback system in case the DHIS2-RTS fails.

- Name (\*): "RTS Monthly report "
- Short name (\*): "RTS Monthly report"
- Expiry days: 5
- Open future periods for data entry: 1
- Days after period to qualify for timely submission: 5
- Period type (\*): "Monthly"
- Category combination (\*): "None"
- Data elements: add all Data elements with the suffix "MTH" required for the respective health facility.

The stock item list (list of Data elements) will have to be manually harmonized and aligned with the TEIs registered for the respective Organisation unit.

Every Data set is assigned to the Organisation Unit for which it has been configured. Alternatively, all Organisation Units could use the same Data set.

"Expiry days" denotes the number of days after the end of the monthly reporting period until which data for that reporting period can still be entered. In order to allow completion of physical stock counts in the days following the end of the month in case the end of the month falls on a day off, the default setting is 5 (days).

"Open future periods for data entry" is set to 1 by default which allows to record data any time during the month of the current reporting period. For example, stock data for January can be entered and edited throughout the month from the first to the last day of January.

"Days after period to qualify for timely submission" is also set to 5 days for the sake of consistency meaning that reports completed within the first five days of the following month are considered having been submitted on-time.

The "Period type" is set to "Monthly" by default as all healthcare facilities are requested to submit reports every month.

The "Category combination" is a mandatory field and must be set to "None".

All other settings are left blank.

In addition, a separate Data set for the daily aggregate reports is required:

- Name (\*): "RTS Daily report "
- Short name (\*): "RTS Daily report"
- Expiry days: 5
- Open future periods for data entry": 1
- Days after period to qualify for timely submission": 5
- Period type (\*): "Daily"
- Category combination (\*): "None"
- Data elements: add all Data elements with the suffix "DAY" required for the respective health facility.

#### 2.3.11 Default Data Entry form for monthly stock data "snapshots"

The Data set with its components such as the Category options appears as a Default Data Entry form in the "Data Entry" app. As Custom Data Entry Forms do not render on mobile devices, they must not be used. All users must have the option of entering monthly stock report data on a mobile device as a fallback option in case the DHIS2-RTS mobile application (temporarily) fails.

Ideally, two reports one with the total distributions and one with the "Deliver to" details would be available but it is not possible to assign more than one "Category combination" to any Data element and for displaying two different Data Entry forms, every Data element would have to be duplicated. As a work around, one single Data Entry form contains all the the "Deliver to" options as separate columns as well as the "Distribution" which is the summary of total distributions. This allows to configure two separate reports (and others of course) as "Pivot table" in the "Data Visualizer".

#### 2.3.12 Indicator

The Indicator functionality is used to configure the "Stock coverage time". In principle it would be preferable to configure the "Stock coverage time" as Predictor (as it would allow using the "Group predictor" function) but because the "Stock coverage time" requires displaying decimals and the Data Entry form only allows a single number format for all Category Options, an indicator is used instead. This approach allows freely setting the number of decimals in the Indicator settings.

Note that using the Indicator for calculating stock coverage times allows using only the distribution from the current month (which is highly inaccurate and leads to high fluctuations) and does not allow calculating an average, for example over the past three to six months.

A separate Indicator is required for every Data element.

Name (\*): Stock coverage time - [Data element name]

Short name (\*): Stock coverage time - [Data element code]

Decimals in data output: "1"

Indicator type (\*): "Number factor 1"

Legends: "Stock coverage time"

Edit enumerator:

- Description: "Stock coverage time - [Data element name]"
- Calculation: #{XsOfl0jZU8S.dOkDb0N10Aw}/#{XsOfl0jZU8S.X57v4Hidl3C}

[Data element.Stock on hand] / [Data element.Stock distribution] /

For example:

DORAALBE4T - ALBENDAZOLE, 400 mg, tab. Stock on hand/DORAALBE4T - ALBENDAZOLE, 400 mg, tab. Stock distribution

Denominator: 1

**Stockout days**

This indicator returns the value "1" for any day where the stock on hand is zero otherwise a "0" and allows automatically calculating the number of stockout days in a month. An indicator is needed for every Data element separately.

Name (\*): DORACEFI4T - CEFIXIME, 400 mg, tab. T2A MTH - Stockout days

Short name (\*): DORACEFI4T MTH - Stockout days

Indicator type (\*): "Number factor 1"

Edit enumerator:

- Description: "DORACEFI4T MTH - Stockout days"
- Calculation: #{GdVh0GGFZh1.t4Exdgy3kDb}

DORACEFI4T - CEFIXIME, 400 mg, tab. T2A DAY Stock on hand Yes/No

Denominator: 1

#### 2.3.13 Indicator type

The "Indicator type" is a precondition for configuring any "Indicator".

- Name (\*): "Number factor 1"
- Factor (\*): "1"

### 2.4 Tracker Program

The DHIS2 Tracker Program which serves as the foundation on which the DHIS2-RTS mobile application is built, is very simple and uses only native DHIS2 functionality without any modifications. The two program rules are absolutely critical to the entire configuration as they provide and ensure the real-time calculation of the stock on hand as soon as any transaction is validated.

#### 2.4.1 Organisation Unit

The Organisation Unit, Organisation Unit group and Organisation Unit level described above apply to the entire database and therefore also apply to all Tracker Programs.

Organisation Units are created and added according to national protocols and policies and/or existing DHIS2 configuration.

#### 2.4.2 Data element

In addition to the Data elements created for each of the items, the Tracker Program requires a separate Data element for each of the "Program stages":

Name (\*):

- "Deliver to": "Text", "Option set" = "Deliver to"
- "Previous Stock Balance": "Positive or Zero Integer"
- "Stock correction": "Integer"
- "Stock count": "Positive or Zero Integer"
- "Stock discard": "Positive or Zero Integer"
- "Stock distribution": "Positive or Zero Integer"
- "Stock on hand": "Positive or Zero Integer"
- "Stock receipt": "Positive integer"

Short name (\*): (same as "Name (\*)"

Domain type (\*): "Tracker"

Value type (\*): differs depending on the Data Element, see above

Aggregation type (\*): "Sum"

Store zero data values: not check (appears as a blank square)

Aggregation levels: "None"

Note that the Data element names must not have any prefixes or suffixes as these are redundant and will appear in the Line Listing.

While for "Stock distribution" and "Stock discard" only positive integers are meaningful, zero is allowed for technical reasons as the entry of "0" on the mobile device cannot be prevented but systematically prompts an unresolvable synchronization error.

#### 2.4.3 Option set

Option sets are used for listing, managing and editing the "Deliver to" places as well as for the Transaction types [to be discussed]. The use of options provides a great deal of flexibility to the customization by individual countries, which are indispensable, without having to modify the DHIS2-RTS app code itself.

The following options are configured by default which can be customized by removing, changing or adding to national needs as required:

[PRIMARY DETAILS]{.underline}

"Name (\*)": "Destinations / supplied to"

"Value type (\*)": "Text"

[OPTIONS ("Name (\*)" / "Code (\*)")]{.underline}

"Diagnostic imaging (X-Ray)" / "x-ray"

"Emergency Room" / "emerg_room"

"High Dependency Unit" / "hi_dep_unit"

"Inpatient Medical Department" / "inp_med_dep"

"Inpatient Surgical Department" / "inp_surg_dep"

"Laboratory Department" / "lab_dep"

"Mortuary" / "mortuary"

"Obstetrics & Gynaecology services" / "obs_gyn"

"Operating Theatre" / "op_theatre"

"Out-Patient Department" / "outp_dep"

"Paediatric Department" / "paed_dep"

"Physiotherapy Department" / "pt_dep"

"Recovery Room" / "rec_room"

"Sanitation / Housekeeping" / "san_housek"

"Sterilization Department" / "steriliz_dep"

"Transfusion services" / "transf_serv"

"(Other)" / other

It is important to always include the "(Other)" option to avoid that other departments or services are "polluted" with transaction data which actually does not apply to them.

#### 2.4.4 Tracked entity attribute

This are the "fixed" attributes of the items (compared with the "variable" data which is collected).

Name (\*):

- "Item code" / "Unique"
- Item description / not "Unique"

"Short name (\*)": same as "Name"

"Short name (\*)": "Barcode" (etc.)

"Value type (\*)": "Text"

"Aggregation type (\*)": "None"

"Unique": see above

Note that the "Item code" is unique only for any specific Organisation Unit but the same "Item code" can be used in any number of different Organisation Units.

#### 2.4.5 Tracked entity type

"Name (\*)": "Item"

"Enable tracked entity instance audit log": not checked

"Minimum number of attributes required to search": "1"

"Maximum number of tracked entity instances to return in search": "0"

"Feature type": "None"

"Tracked entity type attributes": move all three "Tracked entity attributes" (see above) to the right column, arrange the fields in the correct order

- "Display in list": unchecked for all three Tracked Entity Attributes

- "Mandatory": unchecked for all three Tracked Entity Attributes
- "Searchable": "Item PSM - Barcode" = "Searchable" the other two are not "Searchable"

#### 2.4.6 Program

Name: "Real-Time Stock Management"

Program type: "Tracker Program"

## 1 Program details

Name (\*): "Real-Time Stock Management"

Short name (\*): "Real-Time Stock Management"

Color: #304FFE![](media/image12.png)

Icon: "homework"

Version: (automatically numbered)

"Tracked entity type (\*)": "Item"

"Category combination": "None"

"Display front page list": check (appears as white tick in a blue square)

"Access level": "Open"

"Minimum number of attributes required to search": "1".

## 2 Enrollment details

"Show incident date": check (appears as white tick in a blue square)

## 3 Attributes - 1 Assign attributes

- Program tracked entity attributes:
- - "Item code"
- - "Item description"

Note that the item code is separate as it is needed as a distinct field for scanning the barcode.

![](media/image11.png)

## 3 Attributes - 2 Create registration form

(Leave blank)

## 4 Programme stages

"Stock on Hand"

### 4.1 Program stages - "1 Stage Details"

Name: "Stock on Hand"

Scheduled days from start (\*): "0"

"Repeatable": check (appears as white tick in a blue square)

### 4.2 Program stages - "Assign data elements"

Search available/selected items:

- "Stock distribution"
- "Stock discard"
- "Stock receipt"
- "Stock on hand"
- "Deliver to"
- "Previous stock balance"
- "Stock count"
- "Stock correction"

![](media/image36.png)

### 4.2 Program stages - "Create data entry form"

"BASIC"

- "Stock distribution"
- "Stock discard"
- "Stock receipt"
- "Stock on hand"
- "Deliver to"
- "Previous stock balance"
- "Stock count"
- "Stock correction"

## 5 Access

"X Organisation units selected": select each Organisation Unit separately (at the lowest level) but not the Organisation Unit levels.

"Roles and Access": "Pharmacy Stock Management"

"APPLY TO SELECTED STAGES": "Stock on Hand": check (appears as white tick in a blue square)

## 6 Notifications

(blank)

#### 2.4.7 Program rule

In total, four Program rules are configured for completing all required calculations:

- "Assign previous stock balance"
- "Assign Stock on Hand"

The other two Program rule manage the "Stock correction" transaction:

- "Assign Stock correction"
- "Assign Stock on Hand correction".

Two Program rules together provide the real time stock on hand update.

In principle, the transaction quantities from the current event are added to the current Stock on Hand. But since

If "Stock on hand" had a previous event, the "Stock on hand" value from the previous event is written to the Data Element "Previous Stock Balance". This Program rule "saves" the current "Stock on hand" value which is used as a basis for the (re)calculation of the current "Stock on hand". Using a single field would lead to an infinite recursion and an error as, for example, "Stock on hand" cannot be equal to "Stock on hand" + "Receipt" at the same time. Instead two different fields are needed which interact with each other:

- "Stock on hand": the most recent value before a transaction is effected

- "Previous stock balance": the most recent Stock on hand value is written to this field as soon as a new transaction is started

- The calculation of the current transaction is effected by adding all transaction quantities to the "Previous stock balance"

- After completing the transaction, the result of the calculation "overwrites" the "Stock on hand" field

- The process starts again from scratch

The screenshot below shows an example of a transaction. Before the transaction was started, the "Stock on hand" was 1. This value is written to the "Previous stock balance". When the "Stock receipt" of 1 is entered, the "Stock on hand" is increased to 2. Not that the "Previous stock balance" is still 1 which keeps the "memory" of the "Stock on hand" before the transaction started.

The two Data elements "Previous Stock Balance" and "Stock on hand" are greyed out as the are automatically updated by Program rules.

![](media/image94.png)

Note that the (re)calculation of the stock on hand is iterative, only based on the most recent transaction and not in anyway affected by retrospective editing of any other than the current transactions. Therefore any editing of past data must be categorically avoided. Any mistakes must only be corrected with the "Correction" transaction.

Two program rules manage the calculation of the "Stock correction". Entering a quantity corresponding to the difference between the "Stock on hand" currently stored in the system and the "Stock on hand" resulting from the physical stock count would require considering whether the correction is a positive or negative value and a calculation by the user which is prone to error. Instead storekeepers enter the result of the physical stock count and the two program rules update the "Stock on hand" and calculate the difference (which can be positive or negative) for the user:

- "Assign Stock on Hand": if the "Stock count" field has a value entered, this value "overwrites" (replaces) the "Stock on hand" which is currently stored in the system

- "Assign Stock correction": if the "Stock count" field has a value entered, the difference between the "Previous stock balance" and the "Stock count" is "written" to the field "Stock correction".

**Calculations**

Stock on Hand = "Previous stock balance" + "Stock received" - "Stock distribution" - "Stock discarded"

Stock correction = "Count" - "Previous stock balance", replaces "Stock on hand"

"Stock received" (positive integer): increases "Stock on hand"

"Stock distribution" (positive integer): decreases "Stock on hand"

"Stock discard" (positive integer): decreases "Stock on hand"

"Stock correction":

- negative integer if the physical stock count is less than the calculated value

- positive integer if the physical stock count is greater than the calculated value

**Assign Stock correction**

[1 Enter program rule details]{.underline}

Program (\*): "Real-Time Stock Management"

"Trigger rule only for program stage"

Name (\*): "Assign Stock correction"

[2 Enter program rule expression]{.underline}

Condition: "d2:hasValue(#{Stock count})"

[3 Define program rule actions]{.underline}

Action: "Assign value"

Data element to assign to: "Stock correction"

Expression to evaluate and assign:

"#{Stock count }-#{ Previous stock balance}"

**Assign Stock on Hand**

[1 Enter program rule details]{.underline}

Program (\*): "Real-Time Stock Management"

"Trigger rule only for program stage"

Name (\*): "Assign Stock on Hand"

[2 Enter program rule expression]{.underline}

Condition: "true"

[3 Define program rule actions]{.underline}

Action: "Assign value"

Data element to assign to: "Stock on hand"

Expression to evaluate and assign:

"#{Previous stock balance} + #{Stock received} - #{Stock distributed} - #{Stock discarded} "

**Assign previous stock balance**

[1 Enter program rule details]{.underline}

Program (\*): "Real-Time Stock Management"

"Trigger rule only for program stage"

Name (\*): "Assign previous stock balance"

[2 Enter program rule expression]{.underline}

Condition: "d2:hasValue(#{Initial stock on hand - Previous event})"

[3 Define program rule actions]{.underline}

Action: "Assign value"

Data element to assign to: "Previous stock balance"

Expression to evaluate and assign:

"#{Initial stock on hand - Previous event}"

**Assign Stock on Hand correction**

[1 Enter program rule details]{.underline}

Program (\*): "Real-Time Stock Management"

"Trigger rule only for program stage"

Name (\*): "Assign Stock on Hand correction"

[2 Enter program rule expression]{.underline}

Condition: "d2:hasValue(#{Stock count})"

[3 Define program rule actions]{.underline}

Action: "Assign value"

Data element to assign to: "Stock on hand"

Expression to evaluate and assign:

"#{Stock count}"

#### 2.4.8 Program rule variable

Initial stock on hand - Previous event

- Source type (\*): "Data element from previous event"
- Data element: "Stock on hand"

Previous stock balance

- Source type (\*): "Data element in current event"
- Data element: "Previous stock balance"

Stock correction

- Source type (\*): ""Data element in current event"
- Data element: "Stock on hand"

Stock count

- Source type (\*): ""Data element in current event"
- Data element: "Stock count"

Stock discarded

- Source type (\*): "Data element in current event"
- Data element: "Stock discard"

Stock distribution

- Source type (\*): "Data element in current event"
- Data element: "Stock distribution"

Stock received

- Source type (\*): "Data element in current event"
- Data element: "Stock receipt"

#### 2.4.9 Program indicator

Program indicators are the work-around for avoiding the use of third party apps or scripts. Data elements can be displayed in the Data Visualizer but only count the number of events and do not aggregate the transaction values.

A separate Program indicator has to be created for every "pair" of item description and transaction type. For example:

DASDCHLC5S1 - Distribution

DASDCHLC5S1 - Discard

DASDCHLC5S1 - Correction

DASDCHLC5S1 - Receipt

DASDCHLC5S1 - Stock on hand

The item is determined by setting a corresponding "filter" and the transaction type by selecting the respective Data element from the "Stock on Hand" program stage.

Below one example for the configuration of the aggregated, daily "Distribution" quantities is detailed for one item.

It is critically important that the "Aggregation type (\*)" of the Data element (for example for "Stock distribution") is set to "Sum" in the Data element settings since otherwise the transaction quantities will not aggregte.

Note that the same "Program Indicator" can "feed" the Predictor for the "MTH" (monthly period) as well as the "DAY" (daily period).

**Program indicator**

- Program (\*): Real-Time Stock Management
- Name (\*): DASDCHLC5S1 - Distribution
- Aggregation type: "Sum"
- Analytics type (\*): "Event"
- Analytics period boundaries:
- - Boundary target: "Event date"
- - Analytics period boundary type: "After start of reporting period"
- - Offset period by amount: 0
- - Period type: (leave blank)
- - Boundary target: "Event date"
- - Analytics period boundary type: "Before end of reporting period"
- - Offset period by amount: 0
- - Period type: (leave blank)
- Display in form: select (appears as a white tick in a blue square)

**Edit expression**

- #{CSszngrLaoW.smwdEfUz8vo}

"Stock on Hand\\.Stock distribution"

**Edit filter**

- A{XYvrLoYSMRU} == \'DASDCHLC5S1\'

"Item code == \'DASDCHLC5S1\'"

#### 2.4.10 Predictor

These Predictors "transfer" the Program indicators to the respective Category option of the Data Entry form for providing users with daily or monthly "snapshots" of all transactions. Note that in principle the same Program indicator can be used for daily and monthly aggregations ("snapshots") but separate Predictors, one with the "Period type (\*)" daily is needed for daily "snapshots" and a second Predictor with "Period type (\*)" monthly is needed for monthly "snapshots".

One Predictor is needed for each item (Data element = Tracked Entity Instance), for each transaction type as well as for each for each "Deliver to" (Category option) and one each for the daily report and the monthly report as the "Group Predictor" function is not available for Program Indicators. List of Predictors required for every Data element:

[Data element name] - Discard

[Data element name] - Distribution - Diagnostic imaging (X-Ray)

[Data element name] - Distribution - Distribution - total (for all wards/services)

[Data element name] - Distribution - Emergency Room

[Data element name] - Distribution - High Dependency Unit

[Data element name] - Distribution - Inpatient Medical Department

[Data element name] - Distribution - Inpatient Surgical Department

[Data element name] - Distribution - Laboratory Department

[Data element name] - Distribution - Mortuary

[Data element name] - Distribution - Obstetric & Gynaecology services

[Data element name] - Distribution - Opening balance (stock on hand)

[Data element name] - Distribution - Operating Theatre

[Data element name] - Distribution - Out-Patient Department

[Data element name] - Distribution - Paediatric Department

[Data element name] - Distribution - Physiotherapy Department

[Data element name] - Distribution - Receipt

[Data element name] - Distribution - Recovery Room

[Data element name] - Distribution - Sanitation Housekeeping

[Data element name] - Distribution - Sterilization Department

[Data element name] - Distribution - Stock on hand (closing balance)

[Data element name] - Distribution - Transfusion services

[Data element name] - Distribution (Other)

[Data element name] - Stock correction

Note that one Predictor is needed to "feed" the monthly report while a second Predictor "feeds" the daily report.

Below the configuration for a single Predictor is given as an example while all other Predictors are created analogously:

**Predictor**

- Name: "T2A - DORAALBE4T - ALBENDAZOLE, 400 mg, tab. - DIST - PR - MTH/DAY

- Short name (\*): "T2A - DORAALBE4T - DIST - PR - MTH/DAY
- Output data element: DORAALBE4T - ALBENDAZOLE, 400 mg, tab. MTH/DAY
- Output category option combo: "Stock distribution"
- Period type (\*): "Monthly" / "Daily" for the "DAY" Predictor
- Organisation unit levels: "Facility"

**_THIS IS ABSOLUTELY CRITICAL and must the lowest level in the hierarchy must be selected (and not "Country") otherwise Predictors are generated but the values are blank._**

- Organisation units providing data (\*): "At selected level(s) only"

"**Generator**"

- Description: "T2A - DORAALBE4T - ALBENDAZOLE, 400 mg, tab. - PR - MTH/DAY"

- Generator:
- - Programs: "Real-Time Stock Management"
- - Indicators: select [Item] - [Transaction type] from the available options

- - Generator field: I{[Item] - [Transaction type]}

For example: "I{SPzpOCVuS4e}"

"DORAALBE4T - Distribution"

- Sequential sample count: "0" (which means the calculation is based only on the value of one previous month)

- Annual sample count: "0"
- Sequential skip count: (blank)

Note: the Predictor "copies" the Program indicator without any aggregation (such as sum) as the aggregation is already achieved by the Program indicator. The "Sequential sample count" of 0 ensures that the transaction quantities of the current day or month or aggregated.

The following differences need to be considered for the different Predictors as the "Opening SoH" and "Stock on hand" are (re)calculated from other Predictor calculation results rather than from Program Indicators as these values are not sums but only the last value in the month is needed.

**Opening SoH**

- Output category option combo: "Opening SoH"
- Generator:
- - Data elements: select [Data element] - Stock on hand
- - avg(#{XsOfl0jZU8S.dOkDb0N10Aw})

avg(DORAALBE4T - ALBENDAZOLE, 400 mg, tab. Stock on hand)

- Sequential sample count (\*): "1" (this calculation is based on values from the previous month)

**SoH closing**

The "Stock on hand" is (re)calculating by adding all transactions to the "Opening balance" as the "Stock on hand" cannot be aggregated from the Tracker Program values.

Opening SoH +

Stock receipt -

Stock distribution -

Stock discard +

Stock correction

- Output category option combo: "Stock on hand"
- Generator:

{XsOfl0jZU8S.r8mxZGLEIpr}+

{XsOfl0jZU8S.EGYpLpsRoYC}-

{XsOfl0jZU8S.X57v4Hidl3C}-

{XsOfl0jZU8S.KwF12LCuQqt}+

{XsOfl0jZU8S.qrAl2aJnDop}

DORAALBE4T - ALBENDAZOLE, 400 mg, tab. Opening SoH+ DORAALBE4T - ALBENDAZOLE, 400 mg, tab. Stock receipt- DORAALBE4T - ALBENDAZOLE, 400 mg, tab. Stock distribution- DORAALBE4T - ALBENDAZOLE, 400 mg, tab. Stock discard+ DORAALBE4T - ALBENDAZOLE, 400 mg, tab. Stock correction

Please note that the "Stock correction" has to be added (and not be subtracted).

- Sequential sample count (\*): "0" (this calculation is based on the values from the current month)

**STOCK ITEM LIST - Stock coverage - PR**

- Output data element (\*): "DORAALBE4T - ALBENDAZOLE, 400 mg, tab."
- Output category option combo: "Stock coverage"
- Generator:

forEach ?de in :DEG:lbfCwX4ahtd \--\> #{?de.dOkDb0N10Aw}/#{?de.X57v4Hidl3C}

[Data element].Stock on hand / [Data element].Stock distribution

forEach ?de in Stock item list \--\> #{?de.dOkDb0N10Aw}/#{?de.X57v4Hidl3C}

- Sequential sample count (\*): "0" (this calculation is based on values from the current month)

**[Stock list] - Stockout days count**

- Output data element (\*): "DORACEFI4T - CEFIXIME, 400 mg, tab. T2A DAY"

- Output category option combo: "Stock on hand Yes/No"
- Generator:

```
forEach ?de in :DEG:yhNPz0Qve28 → if(#{?de.KoT8qU1DYiB}==0,1,0)

forEach ?de in [Stock item list] - DAY \--\>
if(#{?de.KoT8qU1DYiB}==0,1,0)
```

- Sequential sample count (\*): "0" (this calculation is based on values from the current day)

#### 2.4.11 Predictor group

The "Predictor group" is required in order to allow running all Predictors periodically and together by the "Scheduler" rather than having to prompt them one by one.

- Name (\*): "T2A Predictors"
- Predictors: include all configured Predictors.

#### 2.4.12 Scheduler app

The "Scheduler" app allows configuring the automatic and periodic execution of all Predictors (separately or conveniently grouped in a "Predictor group":

Configuration

- Name \*: "T2A Predictors"
- Job type \*: "Predictor"
- CRON Expression \*: "00 05 00 \* \* \*" ("At 12:05:00 AM)

This CRON job is automatically executed every day at 00:05. If required, the Scheduler can also be set to run more frequently, for example twice a day, every four hours or every hour.

Parameters

- Relative start: "-32"
- Relative end: "32"

Note that the "Relative start" and "Relative end" are always configured in days. In order for the Predictors to aggregate the enter last month, the "Relative start" must always be set to a day in the previous month and the "Relative end" date must also fall into the next month. In order to cater for all possible constellations during the month, 32 days should be used.

This configuration will update Predictors once every day in order to provide monthly updates on transaction quantities rather than showing zero for the entire month and then providing values for the previous month only on the first day of the following month.

#### 2.4.13 Legend

A conventional legend for stockouts is applied to the "DHIS2-RTS Current Stock on hand" Line Listing report to indicate stockout occurrences with a red background:

- Stock on Hand = 0: red background
- Stock on Hand \>=1: light yellow background
- Name (\*): "Stockout"

Stockout

- Name: Stockout
- Start value: 0
- End value: 1
- Colour: #F74432

Stock

- Name: Stock
- Start value: 1
- End value: 999999
- Colour: #F9E6BB

![](media/image8.png)

#### 2.4.14 Capture app (web portal)

The web portal Capture app is used for "enrolling" new Tracked Entity Instances which each correspond to an item (health care product).

TEIs are registered once in a specific DHIS2 database and the same TEI (with the same ID) is used for different OUs as well as possibly in other Tracker programs or Event programs.

Note that the "Report date" can be added from the cog wheel menu once the "STAGE FILTER" has been added.

Note that the order of the columns can be changed by "drag and drop" in the cogwheel menu.

**DHIS2-RTS Stock report working list**

- Open "Capture" app and "Save as": "DHIS2-RTS Stock report" (note that a new name cannot be created later on)

**More filters**

- "Program stage": "Stock on hand"
- Add all available filters for the columns displayed below.

**Select columns** - "Columns to show in table" (cogwheel icon)

- "Report Date"
- "Deliver to"
- "Item code"
- "Item description"
- "Previous Stock Balance"
- "Stock receipt"
- "Stock distribution"
- "Stock discard"
- "Stock correction"
- "Stock on hand"
- "Stock count"

[Question: apparently the "Program stage" filter is not saved and disappears when exiting the screen without any possibility to "update" or "save" the view].![](media/image37.png)

#### 2.4.15 Capture app

In principle, this application will not be used as transactions will be exclusively managed in the customized app and a dashboard will be available for analysis of all transactions. However, the Capture app may be used for registering and enrolling (additional) items in an Organisation unit (health facility) and possibly for managing "manual" stock receipts for a small number of items.

**Working list**

Saved as "DHIS2-RTS Stock item list" after customization:

![](media/image65.png)

**Enrollment Dashboard**

This dashboard shows the "Item profile" as well as a record of all transactions in chronological order:

![](media/image40.png)

Note that the transactions with the same date are not placed in chronological order. Therefore any data entry through the web portal must only be made on the very last transactions as otherwise the Program rules lead to incorrect values for the current stock on hand.

### 2.5 Android settings app configuration

The "Android settings app" allows to customize some functionality across all mobile devices using the Capture Android app. The settings in this chapter should be merely considered as a recommendation to simplify user interfaces but do not have any immediate impact on the DHIS2-RTS app itself.

#### 2.5.1 Synchronization settings

**Global**

While it is strongly recommended that users synchronize mobile devices data immediately after every completed transaction, a daily synchronization is recommended as a backup.

Since it will be difficult to inform all users of any change to the metadata, its synchronization should also be completed once a day to ensure that all mobile devices are always updated.

> How often should metadata sync?: "1 Day"
>
> How often should data sync?: "1 Day"

Note that this daily, periodic synchronization will only be affected automatically if a network connection is available at the time the synchronization is prompted on the mobile device.

**Data sets**

Limiting the number of periods for which data is downloaded to the mobile device will limit storage requirements and improve usability. Moreover, it is unlikely a storekeeper would want to analyse monthly report daily, say, five years back and one year of data should be sufficient.

Maximum number of periods to download data sets for: "12".

#### 2.5.2 Appearance settings

Although this settings does not affect the DHIS2-RTS app itself (for which the home screen is "fixed", for convenience it is recommended to reduce the filter options on the home screen.

Date: do not tag

Organisation Unit: tag

Sync status: do not tag

Assigned to me: do not tag

#### 2.5.3 Analytics settings

This chapter describes the configuration for visualizing some analytics on the mobile device.

### 2.6 Use Case Configuration app

This new DHIS2 app "links" the "Real-Time Stock Management" Tracker Program to the customized mobile app. While the Tracker Program will have the appearance of any other Tracker Program on the Capture Android app home screen, selecting a Tracker Program which is "linked" to the "Real-Time Stock Management" app will invoke the customized app instead of opening the conventional TEI dashboard.

Select "Add Program" to add a new Tracker Program configured for real-time stock management.

**Configure Program**

**General**

- Program Types: "Logistics"
- Description: "Real-time stock management application"
- Program \*: "Real-Time Stock Management"

**Details**

- Item Code \*: "Item code"
- Item Description \*: "Item description"
- Stock on Hand \*: "Stock on hand"

**Transactions**

Distributed

- Distributed to \*: "Deliver to"
- Distributed Stock \*: "Stock distribution"

Corrected

- Corrected Stock \*: "Stock correction"
- Stock Count \*: "Stock count"

Discarded

- Discarded Stock \*: "Stock discard"

### 2.7 Analytics configuration

The DHIS2-RTS analytics are a critical and indispensable component of the DHIS2-RTS concept. The DHIS2-RTS app allows managing all transactions without the need for keeping paper records. However, recording transactions as such is nearly useless unless a record of all transactions is instantly and available to the storekeeper. Despite the availability of detailed transactional reports, compliance with monthly reporting requirements must be maintained.

The DHIS2 analytics provides reports both on individual transactions as well as "snapshots" with stock values on the last day of every month.

Reports are accessible to all users with the respective authorities on mobile device (with limitations) as well as in the web portal.

#### 2.7.1 Line Listing

The Line Listing reports provide details of individual transactions but are not able to provide any type of aggregation.

Important notice: the "Last updated on" date and time stamp indicates the actual data that respective transaction was made on the mobile device (and not the date and time of synchronization). The time indicated in the Line Listing corresponds to the time set on the mobile device.

For stock receipts entered through the web portal, the "Last updated on" reflects the server time of the DHIS2 instance. Therefore, the server time and the time on mobile devices must both be set to the same date and time and should correspond to the time zone used in the respective country. If the times set on mobile devices and the DHIS2 server instance differ, the Line Listing will no longer display all transactions made on mobile devices and the web portal in chronological order.

##### 2.7.1.1 DHIS2-RTS Digital stock card

This report replaces the manual (hand written) stock card and displays the accurate chronology of all transactions with the "Previous stock balance" and the "Stock on hand" (after the transaction).

**Input**

- Event

**Program dimensions**

- Program: "Real-Time Stock Management"
- Stage: "Stock on Hand"

**Columns**

- Last updated on: "Today", "Last 90 days"
- Deliver to: (no condition)
- Item code (no condition)
- Item description (no condition)
- Previous Stock Balance (no condition)
- Stock receipt (no condition)
- Stock distribution (no condition)
- Stock discard (no condition)
- Stock correction (no condition)
- Stock on hand (no condition)

**Filter**

- Organisation unit / "User organisation unit"

**Options**

- Style / Digit group separator: "Comma"![](media/image76.png)

##### 2.7.1.2 DHIS2-RTS Stock distribution report

This report (selectively) lists all "Distribution" transactions.

**Input**

- Event

**Program dimensions**

- Program: Real-Time Stock Management
- Stage: Stock on Hand

**Columns**

- Last updated on: "Today", "Last 90 days"
- Deliver to (no condition)
- Item code (no condition)
- Item description (no condition)
- Stock distribution: "greater than (\>)" 0

**Filter**

- Organisation unit / "User organisation unit"

**Options**

- Style / Digit group separator: "Comma"

![](media/image16.png)

##### 2.7.1.3 Current Stock on hand report

This report is identical to viewing the stock item list with available stocks in the DHIS2-RTS and may be considered as redundant. The advantage of having a separate report is the possibility to give users (such as health staff in wards and services) read only access and not having to train them on the DHIS2-RTS. Moreover there is no need to select a "Transaction type" and "Deliver to" just to view the current stock position.

Exceptionally and intentionally, "Event" (and not "Enrollment") has to be selected as "Input".

**Input**

- Enrollment (!)

**Program dimensions**

- Program: Real-Time Stock Management

**Columns**

- Item code (no condition)
- Item description (no condition)
- Stock on hand:
- "Conditions": none
- "Repeated events": "Most recent events" = "1", "Oldest events" = "0"

- Enrollment date: "Relative periods" and "Months": "This month" and "Last 12 months"

**Filter**

- Organisation unit / "User organisation unit"

**Options**

- Style / Digit group separator: "Comma"
- Legend: "Choose a single legend for the entire visualization": "Stockout"

[Question: legend not appearing under Styles]

![](media/image43.png)

##### 2.7.1.4 DHIS2-RTS Discard report

This report (selectively) lists all "Discard" transactions.

**Input**

- Event

**Program dimensions**

- Program: Real-Time Stock Management
- Stage: Stock on Hand

**Columns**

- Last updated on: "Today", "Last 90 days"
- Deliver to (no condition)
- Item code (no condition)
- Item description (no condition)
- Stock discard: "greater than (\>)" 0

**Filter**

- Organisation unit / "User organisation unit"

**Options**

- **Style / Digit group separator: "Comma"**

![](media/image21.png)

##### 2.7.1.5 DHIS2-RTS Stock correction report

This report (selectively) lists all "Stock correction" transactions.

**Input**

- Event

**Program dimensions**

- Program: Real-Time Stock Management
- Stage: Stock on Hand

**Columns**

- Last updated on: "Today", "Last 90 days"
- Deliver to (no condition)
- Item code (no condition)
- Item description (no condition)
- Stock correction: "greater than (\>)" 0

**Filter**

- Organisation unit / "User organisation unit"

**Options**

- **Style / Digit group separator: "Comma"**

![](media/image18.png)

#### 2.7.2 Data Visualizer / Data Entry form

These group of reports is generated from Data elements and the category options from the Data Entry form for visualizing daily and monthly totals of transactions.

##### 2.7.2.1 DHIS2-RTS Monthly report - Summary

This reports provides the monthly totals of all transactions but only with the total "Distribution" quantity without details on the "Deliver to" for "Distribution" transactions.

**Name**

"RTS Monthly report - Detailed"

**Columns**

"RTS - Monthly stock report" (from "Your Dimensions"):

- Previous stock balance
- Stock receipt
- Stock distribution
- Stock discard
- Stock correction
- Stock on hand

**Rows**

- Data: "Data Type" = "Data elements", then select all Data elements

- Period: "Fixed periods" and "Monthly", then select the last three months (or more as required)

**Filter**

- Organisation unit: "0001 CH Mahosot"

**Options**

- Empty data: "Hide empty columns" and "Hide empty rows": check both

![](media/image53.png)

##### 2.7.2.2 DHIS2-RTS Monthly report - Details

This reports provides the monthly totals of all transactions including details on the "Deliver to" for "Distribution" transactions.

**Name**

"RTS Monthly report - Detailed"

**Columns**

"RTS - Monthly stock report" (from "Your Dimensions"):

- Previous stock balance
- Stock receipt
- "DIS - Diagn. imaging"
- "DIS - Emergency Room"
- "DIS - High Depend. Unit"
- "DIS - Housekeeping"
- "DIS - Inp. Med. Depart."
- "DIS - Inp. Surg. Depart."
- "DIS - Laboratory Depart."
- "DIS - Mortuary"
- "DIS - Obst. & Gynae."
- "DIS - OPD"
- "DIS - Oper. Theatre"
- "DIS - (Other)"
- "DIS - Paed. Dep."
- "DIS - Physioth. Dep."
- "DIS - Recovery Room"
- "DIS - Steril. Dep."
- "DIS - Transf. services"
- Stock distribution
- Stock discard
- Stock correction
- Stock on hand

**Rows**

- Data: "Data Type" = "Data elements", then select all Data elements

- Period: "Fixed periods" and "Monthly", then select January to December 2023

**Filter**

- Organisation unit: "0001 CH Mahosot"

**Options**

- Empty data: "Hide empty columns" and "Hide empty rows": check both

![](media/image64.png)

##### 2.7.2.3 DHIS2-RTS Monthly stockout days count report

This report automatically provides the monthly number of stockout days for each item which is managed with the DHIS2-RTS mobile application.

**Name**

"DHIS2-RTS Stockout days count - Monthly"

**Columns**

- Period: "Fixed periods" and "Monthly", then select all months for 2023

**Rows**

- Data: "Data Type" = "Indicators", then select all "Stockout days" indicators

**Filter**

- Organisation unit: "0001 CH Mahosot"

**Options**

- Data: "Columns totals" and "Row totals"
- Empty data: "Hide empty columns" and "Hide empty rows": check both

![](media/image75.png)

##### 2.7.2.4 DHIS2-RTS Daily report - Summary

This reports provides the daily totals of all transactions but without details on the "Deliver to" for "Distribution" transactions.

**Name**

"RTS Monthly report - Detailed"

**Columns**

"RTS - Monthly stock report" (from "Your Dimensions"):

- Previous stock balance
- Stock receipt
- Stock distribution
- Stock discard
- Stock correction
- Stock on hand
- Period: "Fixed periods" and "Monthly", then select the last three months (or more as required)

**Rows**

Note that the order of these two fields can be switched either displaying items with their chronological order of transactions or displaying days in chronological order with the transactions of every day in alphabetical order of the items.

- Data: "Data Type" = "Data elements", then select all Data elements

**Filter**

- Organisation unit: "0001 CH Mahosot"

**Options**

- Empty data: "Hide empty columns" and "Hide empty rows": check both

![](media/image38.png)

##### 2.7.2.5 DHISDaily report - Details

This reports provides the daily totals of all transactions including details on the "Deliver to" for "Distribution" transactions.

**Name**

"RTS Daily report - Detailed"

**Columns**

"RTS - Monthly stock report" (from "Your Dimensions"):

- Previous stock balance
- Stock receipt
- "DIS - Diagn. imaging"
- "DIS - Emergency Room"
- "DIS - High Depend. Unit"
- "DIS - Housekeeping"
- "DIS - Inp. Med. Depart."
- "DIS - Inp. Surg. Depart."
- "DIS - Laboratory Depart."
- "DIS - Mortuary"
- "DIS - Obst. & Gynae."
- "DIS - OPD"
- "DIS - Oper. Theatre"
- "DIS - (Other)"
- "DIS - Paed. Dep."
- "DIS - Physioth. Dep."
- "DIS - Recovery Room"
- "DIS - Steril. Dep."
- "DIS - Transf. services"
- Stock distribution
- Stock discard
- Stock correction
- Stock on hand

**Rows**

- Data: "Data Type" = "Data elements", then select all Data elements

- Period: "Fixed periods" and "Daily", then select all days for 2023

**Filter**

- Organisation unit: "0001 CH Mahosot"

**Options**

- Empty data: "Hide empty columns" and "Hide empty rows": check both

![](media/image10.png)

##### 2.7.2.6 DHIS2-RTS Daily stockout days count report

This report automatically provides the number of items which are out of stock every day for each item which is managed with the DHIS2-RTS mobile application.

**Name**

"DHIS2-RTS Stockout days count - Daily"

**Columns**

- Period: "Fixed periods" and "Daily", then select all days for 2023

**Rows**

- Data: "Data Type" = "Indicators", then select all "Stockout days" indicators

**Filter**

- Organisation unit: "0001 CH Mahosot"

**Options**

- Data: "Columns totals" and "Row totals"
- Empty data: "Hide empty columns" and "Hide empty rows": check both

![](media/image48.png)

#### 2.7.3 DHIS2-RTS Dashboards

Each of the DHIS2-RTS dashboards presents a single Line Listing or Data Visualizer report or visualization in order to maximize their size when viewed on a (small) mobile device.

All dashboards need to be configured as "Make available offline" so that they can be viewed on a mobile device when it is offline.

### 2.8 Summary of metadata configuration

This chapter provides a summary of the metadata configuration.

#### 2.8.1 Summary of data model

The following logic is used for configuring the metadata used for the Tracker Program:

Data element Represent the various transactions which affect the Stock on hand calculations (receipt, distributions, corrections etc.)

---

Option set The "Deliver to" Data element uses the "Deliver to" Option Set which lists the names of the different departments Tracked entity attribute The item attributes are Item code, description and the barcode (field for scanning) Tracked entity type The item (health care product) is tracked

> The "Previous stock balance" Data element is needed for the Program rules to temporarily store Stock on hand values.
>
> The Tracker Program uses a single repeatable Program stage named "Stock on hand":

![](media/image88.png)

**2.8.2 Summary of metadata configuration for "aggregate" Data entry form**

The table below summarizes the main metadata configurations and settings for the "aggregate" Default Data Entry Form which is used in parallel to the Tracker Program for capturing monthly "snapshots" of the last stock on hand record during any reporting period and the total monthly distribution for each reporting period. This monthly data will also be used for analytics.

The user of the "Imprest Level" inventory control system is highly recommended but could be replaced by other systems or removed if the stock replenishment is managed in the upstream, national eLMIS.

| **ORGANISATION UNIT** |  |
| --- | --- |
| > Organisation unit | Name of the healthcare facility<br>(for each healthcare facility) |
| > Organisation unit group | [Created/Added according to<br>national policies and/or existing<br>DHIS2 configuration] |
| > Organisation unit group set | [Created/Added according to<br>national policies and/or existing<br>DHIS2 configuration] |
| > Organisation unit level | [Created/Added according to<br>national policies and/or existing<br>DHIS2 configuration] |
| > Hierarchy operations | [derives from the settings above] |
| > **CATEGORY** | **System default settings** |
| > Category option | Imprest Level (only for monthly<br>"snapshots")<br>Stock distributed<br>Stock on hand |
| > Category | [Healthcare facility name] -<br>monthly stock report |
| > Category combination | [Healthcare facility name] -<br>monthly stock report |
| > Category option combination | (auto-generated by the system) |
| > Category option group | (not used) |
| > Category option group set | (not used) |
| > **DATA ELEMENT** |  |
| > Data element | One Data element is created for<br>every item (healthcare product)<br>with [Item code] - [Item<br>description] with the "Category<br>combination" [Healthcare facility<br>name] - monthly stock report |
| > Data element group | (not used) |
| > Data element group set | (not used) |
| > **DATA ELEMENT** |  |
| > Data set | One Data set (stock item list) for<br>every healthcare facility with<br>[Healthcare facility name] -<br>stock item list |
| > Data set notifications | (not used) |
| > **PREDICTOR** |  |
| > Predictor | One predictor for every Data<br>element with [Item name] -<br>"Imprest Level Predictor" |
| > Predictor group | "Imprest Level - carried forward<br>from previous month" grouping all<br>Predictors |
| > **SCHEDULER** |  |
| > Scheduler app | "Imprest level - predictor -<br>rolling forward to the next month"<br>running at 00:05:00 every first day<br>of the month |

#### 2.8.3 Summary of metadata configuration for Tracker Program

The table below summarizes the main metadata configurations and settings for the Tracker Program on which the customized DHIS2-RTS is based and using "in the background". While not visible to users it is indispensable and critical for customizing the configuration to individual countries as well as for managing data such as adding or removing items (health care products).

| **CATEGORY** | **System default settings** |
| --- | --- |
| > Organisation unit | According to national protocols<br>and policies and/or existing<br>DHIS2 configuration |
| > Data element | Name (\*):<br>\- "Deliver to": "Text" /<br>"Option set" = "Deliver to"<br>\- "Previous stock balance":<br>"Positive integer"<br>\- "Stock correction":<br>"Number"<br>\- "Stock count": "Positive<br>integer"<br>\- "Stock discard": "Positive<br>integer"<br>\- "Stock distribution":<br>"Positive integer"<br>\- "Stock on hand": "Positive<br>integer"<br>\- "Stock received":<br>"Positive integer"<br>Domain type (\*): "Tracker"<br>Value type (\*): see above<br>Store zero data values: tag |
| > Option set | Primary Details / Name:<br>"Deliver to"<br>Primary Details / Value type:<br>"Text"<br>Options / Name:<br>\- "Diagnostic imaging<br>(X-ray)" / "diagn_imag"<br>\- "Emergency Room" /<br>"emerg_room"<br>\- "High Dependency Unit" /<br>"hi_dep_unit"<br>\- "Inpatient Medical<br>Department" / "inp_med_dep"<br>\- "Inpatient Surgical<br>Department" /<br>"inp_surg_dep"<br>\- "Laboratory Department" /<br>"lab_dep"<br>\- "Mortuary" / "mort"<br>\- "Obstetrics an Gynaecology<br>services" / "obs_gyn"<br>\- "Operating Theatre" /<br>"op_theatre"<br>\- "Out-Patient Department" /<br>"outpat_dep"<br>\- "Paediatric Department" /<br>"paed_dep"<br>\- "Physiotherapy Department"<br>/ "phys_dep"<br>\- "Recovery Room" /<br>"rec_room"<br>\- "Sanitation and<br>Housekeeping" / "san_housek"<br>\- "Sterilization Department"<br>/ "sterii_dep"<br>\- "Transfusion services" /<br>"transf_serv" |
| > Tracked entity attribute | Name:<br>\- "Item barcode"<br>\- "Item code"<br>\- "Item description"<br>"Value type (\*)": "Text"<br>"Aggregation type (\*)":<br>"None"<br>"Unique": "Unique" /<br>"Organisation unit" |
| > Tracked entity type | Name: "Item"<br>"Minimum number of attributes<br>required to search": "1"<br>"Feature type": "None"<br>"Tracked entity type<br>attributes":<br>\- Item code / not "Searchable"<br>\- Item description / not<br>"Searchable"<br>\- "Display in list":<br>unchecked<br>\- "Mandatory": unchecked<br>\- "Searchable": see above<br>Note: "Item barcode" is<br>intentionally not included here. |
| > Program | "Real-Time Stock management" |
| > 1 Program details | "Name (\*)": "Real-Time Stock<br>Management"<br>"Short name (\*)": "Real-Time<br>Stock Management"<br>"Tracked entity type (\*)":<br>"Item"<br>"Display front page list":<br>check (appears as white tick in<br>a blue square)<br>"Access level": "Open"<br>"Minimum number of attributes<br>required to search": "1". |
| > 2 Enrollment details | "Show incident date": check |
| > 3 Attributes |  |
| > Assign attributes | "Program tracked entity<br>attributes":<br>\- Item barcode<br>\- Item code<br>\- Item description |
| > Create registration form | Leave blank |
| > 4 Program stages |  |
| > Stage Details | Name: "Stock on Hand"<br>"Scheduled days from start<br>(\*)": "0"<br>Repeatable: check (appears as<br>white tick in a blue square) |
| > Assign data elements | Selected items:<br>\- "Stock count"<br>\- "Stock distribution"<br>\- "Stock correction"<br>\- "Stock discarded"<br>\- "Stock received"<br>\- "Stock on Hand"<br>\- "Deliver to"<br>\- "Previous stock balance" |
| > Create data entry form | BASIC: "Stock management":<br>\- "Stock distribution"<br>\- "Stock count"<br>\- "Stock discarded"<br>\- "Stock received"<br>\- "Stock on hand"<br>\- "Deliver to"<br>\- "Previous stock balance" |
| > 5 Access | X Organisation units:<br>\- "0001 CH Mahosot"<br>\- "0002 CH Mittahap»<br>"Roles and Access":<br>"Real-Time Stock Management"<br>"APPLY TO SELECTED STAGES":<br>"Stock on Hand" |
| > 6 Notification | (blank) |
| > Program rule |  |
| > Assign Stock correction | Program (\*): "Real-Time Stock<br>Management"<br>Name (\*): "Assign Stock<br>correction"<br>Condition: "d2:hasValue(<br>#{Stock count} )"<br>Action: "Assign value"<br>Data element to assign to:<br>"Stock on hand"<br>Expression to evaluate and<br>assign: "#{Stock<br>count}-#{Previous stock<br>balance}" |
| > Assign Stock on Hand | Program (\*): "Real-Time Stock<br>Management"<br>Name (\*): "Assign Stock on<br>Hand"<br>Condition: "true"<br>Action: "Assign value"<br>Data element to assign to:<br>"Stock on hand"<br>Expression to evaluate and<br>assign: "#{Previous stock<br>balance}+#{Stock<br>received}-#{Stock<br>distribution}-#{Stock<br>discarded}" |
| > Assign Stock on hand | Program (\*): "Real-Time Stock |
| > correction | Management"<br>Name (\*): "Assign Stock <br>correction"<br>Condition: "d2:hasValue( <br>#{Stock count} )"<br>Action: "Assign value"<br>Data element to assign to: <br>"Stock on hand"<br>Expression to evaluate and <br>assign: "#{Stock count}" |
| > Assign previous stock balance | Name (\*): "Assign previous<br>stock balance"<br>Condition: "d2:hasValue(<br>#{Initial stock on hand -<br>Previous event} )"<br>Action: "Assign value"<br>Data element to assign to:<br>"Previous Stock Balance"<br>Expression to evaluate and<br>assign: "#{Initial stock on<br>hand - Previous event}" |
| > Program rule variable | Program (\*): "Real-Time Stock<br>Management"<br>Name / Data element<br>\- "Initial stock on hand -<br>Previous event": "Data element<br>from previous event" / "Stock<br>on hand"<br>\- "Previous stock balance":<br>"Data element in current<br>event" / "Previous stock<br>balance"<br>\- "Stock correction": "Data<br>element in current event" /<br>"Stock on hand"<br>\- "Stock count": "Data<br>element in current event"/<br>"Stock on hand"<br>\- "Stock discarded": "Data<br>element in current event" /<br>"Stock discarded"<br>\- "Stock distribution":<br>"Data element in current<br>event" / "Stock distribution"<br>\- "Stock received": "Data<br>element in current event" /<br>"Stock received"<br>Source type (\*): see above<br>Data element: see above |
| > Use case configuration app | Use case configuration app<br>Configure Program<br>General<br>\- Program Types: "Logistics"<br>\- Description: "Real-time<br>stock management application"<br>\- Program \*: "Real-Time Stock<br>Management"<br>Details<br>\- Item Code \*: "Item code"<br>\- Item Description \*: "Item<br>description"<br>\- Stock on Hand \*: "Stock on<br>hand"<br>Transactions<br>Distributed<br>\- Distributed to \*: "Deliver<br>to"<br>\- Distributed Stock \*: "Stock<br>distribution"<br>Corrected<br>\- Corrected Stock \*: "Stock<br>correction"<br>\- Stock Count \*: "Stock<br>count"<br>Discarded<br>\- Discarded Stock \*: "Stock<br>discard" |

## 3 DHIS2 REAL-TIME STOCK MANAGEMENT MOBILE APPLICATION

The mobile device application (front-end, user interface) consists of a login screen, a single screen for entering and editing data by pharmacy staff, a third (and last) screen for viewing and correcting the summary and a final screen for the analytics.

Any other functionality is placed in the native DHIS2 settings menu.

### 3.1 General use case

Medical stocks comprise drug products (tablets, injections, diagnostic test etc.) as well as single use medical devices such as syringes, bandages, catheters, drains, x-ray films etc.

Medical stores are usually replenished once a month from district, provincial or national stores. Upon delivery, they receive a detailed packing for each consignment which provides details of the item codes and names, quantities, batch numbers and expiry dates. After counting the quantity of each item goods are put away and placed in order of the item group, within alphabetically and within by expiry date in the medical store.

Depending on the organization of the healthcare facility, every ward or service presents a request form with a list of required items and quantities once a day, several times a week according to an agreed schedule, every week or once a month to the central pharmacy. The storekeeper then picks the required quantities of the required items and prepares them for delivery to the requester.

Traditionally, medical stores are managed by recording each transaction in a batch card which is placed on the shelves next to each item. At the end of the month, the stock of each item is counted, the actual balance is compared with the running balance indicated in the batch card and, if necessary, the balance is corrected. All transactions of each batch card are summarized in a stock card which is also kept for each item and calculating the stock balance from all stock receipts and stock issues. The data on monthly stock issues as well as the stock on hand at the end of the month are then used for calculating monthly replenishment orders which closes the replenishment cycle.

This process is laborious, boring, prone to error and very time consuming. The monthly stock count alone takes between two to five working days every month.

The fundamental improvement of the DHIS2-RTS is to record only the stock transactions by scanning a bar code, adding the received stock from electronic packing lists and calculating the remaining balance in real-time. The stock card is then automatically provided by the DHIS2-RTS app as an output which eliminates the need for any paper records. The process of the monthly stock count is eliminated and replaced residual balance counting and (optionally) by spot checks.

The DHIS2-RTS will be used by

- pharmacists
- storekeepers
- health workers
- immunization workers
- supervisors and pharmacy managers
- community health workers

for managing medical stocks at hospitals, Primary Healthcare facilities (clinics), Immunization services and those managed by community health workers.

One of the main tasks of storekeepers is keeping records of all transactions of all items they manage and providing detailed reports at the end of the month. These records include the following information for each transaction:

- place of the transaction (Organisation Unit)
- transaction date and time
- person who carried out the transaction (user)
- requesting ward or service
- item code and name (name of the drug product or single use device)
- quantity of the transaction

Storekeepers need to differentiate between and record the following transaction:

- stock receipts (from upstream stores)
- stock distributions
- stock discards
- stock corrections

Stock receipts are managed "manually" by the storekeeper through the DHIS2-RTS app, by "uploading" in the Tracker Program in the DHIS2 web portal with a template or through integration with the national eLMIS.

Almost all transactions are "distributions" of healthcare goods to wards and services. Occasionally expired or damaged goods have to be discarded and have to be removed from the stock but without being considered in the "distributed" quantity as otherwise the stock replenishment quantities would be falsely calculated too high. Finally, any discrepancies caused by mistakes, mislaying or theft need to be corrected in order to ensure accurate stock replenishment calculations.

[Question: include returns to upstream stores and redistributions to other healthcare facilities. The alternative is to manage these as "negative deliveries" from the upstream store].

The DHIS2-RTS data and analytics provides the storekeeper with information on:

- current stock on hand of every item
- total monthly transactions (receipts, distributions, discard and correction) for each item

- distributions by supplied ward or service

### 3.2 General design principles and business requirements

The principle of "digital frugality" of keeping the mobile device application as simple, "light" and "lean" as possible is an explicit objective of the project. The mobile device application features only a login window for authentication, a window for order picking and a third window for reviewing and confirmation. Any information displayed on any user interface must be essential and indispensable to business processes and workflows.

The ability to work off-line is absolutely critical for the context of LMICs with intermittent or unreliable network connectivity.

This mobile application will mainly be used by health workers which have not received any training in logistics and supply chain management and most likely have acquired the principles of stock management through "learning by doing". Therefore, the processes, workflows, user interfaces and interactions with the mobile device should be:

- as far as possible, native DHIS2 functionality is used
- custom development is only applied to functionality which is not natively available but required for the DHIS2-RTS application

- Custom development must be minimized also in order to minimize work for future maintenance such as ensuring compatibility with future DHIS2 versions

- in particular, the functionality of the "Settings" (side bar) menu is maintained for the DHIS2-RTS application

- be as simple as possible
- be as intuitive as possible
- be as far as possible be self-evident and require minimal training
- offer users as few options as necessary
- guide users to the next step with little possibility of making any errors

- prevent (serious) errors by requiring additional confirmation
- should offer good usability on mobile phones (6 inch display) as well as tablets

- should be designed for a highly repetitive task
- only include text and visual elements which are absolutely indispensable

- Prepare for customization: it is inevitable that user will want to modify the Tracker Program. For example, to modify the list of "Deliver to" options. Another very frequent request is that users want to differentiate "Stock discarded" into expiry, damaged and stolen stock. As far as possible drop-down menus (such as for transaction type and the "Deliver to" options) should be configured in a way that they can be easily modified in the Tracker Program without having to change the app. For example, by using Option sets for the "Deliver to" options or Data elements for the transaction types. This system allows to keep the DHIS2-RTS as simple as possible (rather than building in all possible user requirements) while still allowing easy customization.

- Language: English by default with the DHIS2 native language options

**User interface business requirements**

- All quantities of all healthcare goods are exclusively indicated in units of measure (UoM) of "EA" (Each) and never in any packaging quantities. "EACH" refers to the smallest usable unit of a healthcare product such as one tablet, one syringe, one disposable glove or one pair (!) of sterile gloves (as these must always be used in pairs). In exceptional cases where the packaging quantity (such as "kit of 100 tests" is indicated in the item description, "EACH" refers to one kit (and not one test) as such products do not contain separate diagnostic tests but are an actual kit with bottles of liquids and other components sufficient for the indicated number of tests.
- In tables, all text fields are left aligned
- In tables, all value fields are right aligned
- All dates are displayed in the dd/mm/yyyy (day/month/year) format
- All times are displayed in the hh:mm (hour/minute) format using 24 hour format.
- Except for analytics, no decimals are used for values (unnecessary, prone to errors, prone to confusion with thousand separators and decreases legibility)
- All numbers greater than 999 are displayed with a comma (",") as thousand group separator (for example 1,200).
- Numeric fields allow values with a maximum of 7 digits (the largest value allowed is 9,999,999)
- All text fields (including the item code field) are alphanumeric (English alphabet A to Z and numbers 0-9, no other characters are needed).
- All items are sorted alphabetically by their "Name"
- Single field for concatenation of the item code and item description (not ideal but a constraint in DHIS2)
- Any data values entered on the mobile device using the DHIS2 Capture Android is stored instantly upon entry and does not require "saving"
- The mobile device application does not allow users to export or download data from the mobile device in any way nor is this required. Previously recorded data can be viewed in dashboards on the mobile device or in the DHIS2 web portal

### 3.3 DHIS2 mobile device application installation

Before using the application for the very first time, as well as in case of any error in the mobile device, the mobile device application must be installed on every mobile device individually.

As the DHIS2-RTS is a native module in the DHIS2 Capture Android app, installation of the DHIS2 Capture Android app automatically covers installation of the DHIS2-RTS application.

The user downloads the native DHIS2 Capture Android app from Google Play Store by searching for "DHIS2" and installing the mobile app like any other application.

### 3.4 DHIS2 mobile device application user access (login and logout)

This process allows users to login and access the mobile device application.

As the DHIS2-RTS is a native module in the DHIS2 Capture Android app, the login (and logout) is also native functionality which applies to the DHIS2-RTS Stock app.

Users can login according to their user profile and account settings as configured in the DHIS2 web portal. Access to the DHIS2-RTS functionality is controlled through the user settings, the Tracker Program setting as well as the Android Settings app [this to be confirmed].

### 3.5 "Distribution" transaction

More than 99% of all transactions will be "Distribution" transactions where storekeepers pick and pack healthcare goods requested by a department, service, community health care and immunization workers which are then either picked up by the requester or delivered by the pharmacy.

The DHIS2-RTS is designed for instant digital recording and explicitly not intended for recording transactions on paper records and re-entering them on a mobile device later as this would unnecessarily duplicate the work effort. Moreover, the main purpose of providing real-time stock updates to storekeepers and other stakeholders is not achieved by "retrospective" entry.

- Users enter transactions item by item immediately as the transactions take place and not retrospectively.

- A setting allows differentiating between actual distributions (issue to patients, wards, services and community health workers) as well as losses caused by expiry, damage, theft or any other use of stock which is not an actual stock issue.

- As the stock on hand is automatically calculated, users have the possibility of manually correcting any discrepancies by recording correcting the actual, current stock on hand.

#### 3.5.1 "Distribution" transaction workflow

For each "Distribution" transaction the following workflow is required. User

- receives a written request from departments, services or community health workers indicating a list of healthcare products and their quantities which are requested and need to be prepared by the pharmacy

- starts the mobile device
- open the DHIS2-RTS mobile app
- selects the transaction type "Distribution"
- selects the "Organisation Unit" (name of the healthcare facility) if s/he has access to more than one

- selects the ward/service etc. which is requesting the goods and for which the order picking is carried out

- selects the first item by scrolling, searching or using the barcode scanner

- enters the quantity manually by typing on the on-screen keyboard
- repeats process for each requested item
- carries out a final review of all picked items and, if needed corrects, confirms (or discards) the transaction

- informs the requester to pick up the goods are delivers them to the requesting department/service

#### 3.5.2 "Distribution" transaction use case

1.  User authenticates and accesses the DHIS2 Capture Android app.
2.  The DHIS2 Capture Android app home screen appears and displays all the DHIS2 Data Sets and Programs to which the user is assigned and has access to. ![](media/image25.png)
3.  User accesses the respective DHIS2-RTS Tracker program from the home screen by tapping on it.
4.  The DHIS2-RTS home screen opens, and in the top bar by default "Distribution" appears as transaction type with a blue background. If the user is assigned to a single Organisation Unit, it appears by default under "From". By default the "Deliver to" field is blank to force the user to deliberately select one of the options. Note that the "Search" field is not active until the "From" and "Deliver to" fields are filled. ![](media/image9.png)
5.  Optionally (should be a very rare exception): the user opens the "From" drop-down menu.
6.  A list of available Organisation Units is displayed in the drop-down menu. If the user is assigned to a single Organisation Unit, the field is "static" and no drop-down menu opens. ![](media/image56.png)
7.  User selects the required Organisation unit by checking the box and selecting "DONE".
8.  The DHIS2-RTS home screen reverts which now indicates the selected Organisation unit. ![](media/image68.png)
9.  User opens the "Deliver to\..." drop-down window for selecting the required department or service which requested the goods and to which the goods are being provided. Note that this drop-down window only applies to "Distribution" (but neither to "Discard" nor to "Correction"). By default the drop-down window is intentionally blank to force the user to enter a selection and the use cannot proceed before completing this selection.
10. The available "Deliver to" options are displayed in a drop-down window. Note that the details may differ by Tracker Program as these options can be freely configured in the respective "Option set". ![](media/image70.png)
11. User selects the required "Deliver to" department or service from the drop-down menu.
12. The drop-down menu collapses and displays only the selected "Deliver to" choice. Note that as soon as all three entries (transaction type, Organisation Unit and "Deliver to") have been selected, the stock item list with the current stock is immediately and automatically displayed. ![](media/image87.png)
13. This completes the selection of the transaction type, Organisation unit and the "Deliver to" option from the DHIS2-RTS home screen. User selects the "Settings" icon or the "\^" icon for "collapsing" the header.
14. The header information for the transaction type, Organisation unit and "Deliver to" selection is compacted into the header of the screen and displayed during the entire transaction. ![](media/image49.png)
15. In case the user tries to make a change to the transaction type after entering any quantity (or quantities), the "From" and "Deliver to" field a warning will appear that any data entered so far will be lost, cannot be retrieved and will have to be entered again.
16. A dialogue window with the warning is displayed at the bottom of the screen: ![](media/image83.png)
17. The user can either select "Discard changes" and forgo the entered data or select "Keep editing" and proceed with the transaction with the previously selected Organisation Unit and "Deliver to" selection.
18. Depending on the choice, the home screen reverts or the user continues where s/he left off editing data.
19. The user is now ready to start preparing the requisition. The user has three possibilities for searching for items in the list:


    -   Manually scrolling down the list until the requested
    item is found
    -   Entering a search term in the "Search" window
    -   Scanning the barcode attached to the item on the shelf
    The first option is to simply scroll down the list and tap
    in the "Quantity" field.

20. The "Quantity" field becomes editable and the name of the item as well as the entered value appear between the list and the on-screen keyboard in a separate field. ![](media/image61.png)
21. The second option is to enter text in the "Search" field.
22. The list displays only the items which contain the text entered in the "Search" field. Note that this screen is only "filtering" the entire list according to the most recent search but with the entire list "in the background" and none of the items are actually removed from the list. Also note that this filter is "contextual" and as characters are added, the list of results is automatically adapted and shortened according to the entered text string. The text in the search window can be edited or cleared by tapping on the "X" icon. As above the user taps in the "Quantity" field and enters a value. As soon as the user taps onto the blue ✓ icon or taps into another "Quantity" field, the "Stock" is recalculated in real-time. ![](media/image24.png)
23. The third and last option is tapping on the barcode symbol which is found on the far right of the "Search" window.
24. The barcode viewfinder window opens which displays a white field with a horizontal red line displaying the view of the mobile device camera: ![](media/image97.png)
25. User places the viewfinder window in front of the barcode which is attached to the label on the shelf and positions the red line across the centre of the barcode: ![](media/image50.png)
26. The DHIS2 Capture Android app will audibly signal ("beep") as soon as the mobile device has captured the barcode, close the viewfinder window and display only the selected item in the window. The "Search" field will display the selected item as a search result. The window will display the current "Stock" (stock on hand, which should correspond to the actual remaining stock on the shelf) next to the item and reprints the item name with a quantity field at the bottom of the screen for editing. Note that this screen is only "filtering" the entire list according to the most recent search but with the entire list "in the background". ![](media/image89.png)
27. User taps in the "Quantity" field for opening the on-screen keyboard and enters the picked quantity. Users are blocked from entering negative values, zero or positive non-integer values.
28. The entered "Quantity" is displayed in the respective line as well as in the separate dialogue window window above the on-screen keyboard. The user can edit the quantity or delete it by removing all digits with the "back" button. ![](media/image42.png)
29. User confirms the (final) quantity by tapping on the blue ✓ icon.
30. The on-screen keyboard and the editing line are closed and the entered quantity is instantly and automatically deducted from the "Stock" and immediately displays the final stock balance (after the respective quantity has been removed from the shelf). ![](media/image52.png)
31. The user effects another entry by tapping on the barcode icon or selecting the next item. Note that the list will only display items corresponding to the entry in the "Search" window and for viewing all (so far) selected items, the "Search" field has to be voided by tapping on the "X" icon.
32. This completes the recording of the first item which is picked and the user continues to pick the remaining items for the same department or service. The user can either continue using the barcode scanner which does not require "expanding" the entire list. If the user is not using the barcode scanner s/he needs to select the "x" in the search window for reverting to the entire list. Note that if the stock item list is "expanded" all entered values for the selected items are maintained. ![](media/image57.png)
33. After the last required item has been picked, the user selects the "Review" button at the bottom right of the screen.
34. The user is referred to the "Review" screen which displays only the previously selected items (and not the entire stock item list) with the entered "Quantity" in the alphabetical order of the stock item list. Note that "Under review" is displayed below the item list, the "Review" button is no longer displayed and instead the "Confirm" button is displayed. This screen allows comparing the selected items with the original request from the department or service and, if necessary, making corrections. ![](media/image78.png)
35. Optionally: the user can revert from the "Review" to the previous data entry interface (for example because requested items were forgotten) without any previous entries being lost.
36. Optionally: after completing the corrections, the user advances to the "Review" screen again.
37. By tapping inside the "Quantity" field, the user can reopen the on-screen keyboard and edit as well as delete any quantity.
38. The on-screen keyboard is opened and the "Quantity" field is again editable. Note that in this final steps items cannot be added to the list any more and the "Search item" as well as the "Scan" icon can only be used for searching items within the list (in case the list is long and the user is not sure that a certain item was correctly picked). In case items are actually missing the user can either discard all entries and start from scratch or simply complete the transaction and then start a second transaction for the same ward or service for the items which were missed. In case the user entered an incorrect transaction type or "Deliver to" option, the user can discard the transaction by selecting the back button (arrow) but all entered "Quantity" fields will be lost. ![](media/image19.png)
39. Once the review and editing has been completed, the user selects the "Confirm" button. **_Note that this step is irreversible_** and cannot be reversed or be undone in any way.
40. The home screen reverts with all options in the header reset to their defaults. A dialogue window displaying "The transaction was successfully completed" appears at the bottom of the screen. ![](media/image93.png)
41. User selects the synchronization icon at the top right of the screen. The synchronization of the local database with the central server can be effected at any time but any particular transaction can only be synchronized once it has been completed.
42. A dialogue window opens at the bottom of the screen with information on the synchronization. ![](media/image77.png)
43. User selects the "Send" button.
44. The successfully completed synchronization is confirmed by the "Synced" caption and by changing the colour of the synchronization icon from grey to green. Note that the user is offered the "Refresh" option even if the synchronization has been completed successfully in order to align with native DHIS2 behaviour. ![](media/image23.png)
45. User selects "Not now" to close the confirmation message.
46. The confirmation message closes, the home screen reverts and the user is ready for entering the next transaction. ![](media/image34.png)

### 3.6 "Discard" transaction

Stock is discarded whenever healthcare goods are expired, damaged or no longer usable for other reasons. Those products must be removed from the "active" stock and segregated in a locked cupboard or room to prevent inadvertent use until the products are disposed of.

There are several reasons for differentiating between "Distribution" and "Discard" transactions:

- In terms of stock replenishment, discarded stock is issued from the stock but must not be included in the (monthly) demand. In most cases the discarded stock has to be replaced but only one-off (!) while included the quantity as "Distribution" transaction would falsely imply that those quantities have been distributed and use and that demand has increased

- The amount and value of discarded stock is an important indicator for the quality of stock management

The workflow and use case are almost identical with those of the "Distribution" transaction with the only difference that the "Deliver to" option is not required and therefore not displayed.

#### 3.6.1 "Discard" transaction workflow

For each "Discard" transaction the following workflow is required: user

- identifies batches of health care products which are no longer usable

- starts the mobile device
- opens the DHIS2-RTS mobile app
- selects "Discard" from the transactions drop-down menu
- selects the healthcare facility ("Organisation Unit") if s/he has access to more than one

- scans the barcode of the first healthcare product
- records the quantity which is being discarded
- repeats process for each batch of all items
- carries out a final review of all picked items and confirms (or discards) the transaction

- places the selected products in quarantine to prevent inadvertent use

#### 3.6.2 "Discard" transaction use case

This use case only shows the steps which differ from the "Distribution" use case.

.

1.  User accesses the DHIS2-RTS mobile device application.
2.  The DHIS2-RTS home screen opens. ![](media/image7.png)
3.  User taps on the "Distribution" button of the DHIS2-RTS home screen.
4.  A drop-down menu with all available transactions opens. ![](media/image60.png)
5.  User selects "Discard" from the drop-down menu.
6.  "Discard" is displayed instead of "Distribution" in the header, the background colour changes to red and the text colour changes to red to signal that this is not a "Distribution" transaction and ensure users are aware that this is as "Discard" transaction. Note that the "Deliver to" field is no longer available. ![](media/image74.png)
7.  User selects the Organisation unit from the "From" drop-down menu (see "Distribution" transaction).
8.  The header displays "Discard" as transaction type and the Organisation unit as "From" and the user is ready to select the items and quantities which need to be discarded in the same way as for the "Distribution" workflow. ![](media/image91.png)

### 3.7 "Correction" transaction

Stock corrections must only be made if the mistake in previous transactions cannot be correct by recording additional transactions and may be needed for various reasons:

- Quantity received physically is more or less than received in the system

- Stock is lost
- Stock is mislaid (placed in another place and not found during counting)

- Theft
- The quantity recorded during any previous transaction is larger or smaller than the actual transaction quantity and the mistake was not noted during the transaction

In most case the mistake will never be found and it is important to differentiate these transactions from other transactions as they must not be taken into account for calculating demand and stock replenishment orders.

The workflow for "Correction" transactions is almost identical with the "Distribution" workflow with the important difference that, unlike all other transactions, the user does not enter the transaction quantity but instead enters the quantity resulting from a physical stock count and DHIS2-RTS then calculates the discrepancy. Moreover, the "Correction" transaction is the only transaction where entries or "0" (zero) make sense.

#### 3.7.1 "Correction" transaction workflow

For each "Correction" transaction the following workflow is required, user:

- identifies an item with a discrepancy between the current stock on hand in DHIS2-RTS and the result of the physical stock count

- starts the mobile device
- opens the DHIS2-RTS mobile app
- selects "Correction" transaction from the drop-down menu
- selects the healthcare facility ("Organisation Unit") if s/he has access to more than one

- scans the barcode of the first healthcare product
- enters the quantity resulting from the physical stock
- repeats process for each item
- carries out a final review of all items for which a stock correction was entered

#### 3.7.2 "Correction" transaction use case

This use case only shows the steps which differ from the "Distribution" use case.

1.  User accesses the DHIS2-RTS mobile device application.
2.  The DHIS2-RTS home screen opens. ![](media/image7.png)
3.  User taps on the "Distribution" button of the DHIS2-RTS home screen.
4.  A drop-down menu with the available transactions opens. ![](media/image99.png)
5.  User selects "Correction" from the drop-down menu.
6.  "Correction" is displayed as transaction type instead of "Distribution" in the header, the background colour changes to orange and the text colour also changes to orange to signal that this is not a "Distribution" transaction and ensure users are aware that this is as "Correction" transaction. Note that the "Delivery to" option is no longer available and **_instead of the "Quantity" column, the "Count" column is displayed_**. ![](media/image81.png)
7.  User selects the Organisation unit from the "From" drop-down menu (see "Distribution" transaction).
8.  The user selects the first item (see the instructions for the "Distribution" transaction) by scrolling, searching or using the barcode scanner.
9.  Only the selected item appears on the screen.
10. User counts the actual quantity in stock, compares it with the calculated quantity displayed by the DHIS2-RTS app and, if any discrepancy is confirmed, **_enters the actual quantity in stock_**. Note that DHIS2 will "reset" the Stock on hand to the entered quantity and automatically calculate the difference with the previous value as "stock correction".
11. The user interface displays the correct stock on hand in the "Stock" column.
12. The user repeats the process above for every item to be picked, proceed to the "Review" and completes the transaction as described in the previous sub-chapter.

### 3.8 Mobile device analytics

DHIS2 natively provides users with on-line and off-line analytics.

The DHIS2-RTS analytics replaces "reading" of stock records which may be needed at any time by the storekeeper for:

- Consulting or verifying the current stock on hand
- Viewing any (recent) transaction by "Deliver to", item and/or date
- Analysing demand of a certain item

It is important to note that apart from the pharmacy staff as the main user, any other health professional in the same health care facility also would greatly benefit from access to analytics for:

- Checking the availability of certain health care products, for example before a physician prescribes a drug product and either confirming availability or prescribing an alternative drug product

- Checking the availability of stocks by department/ward supervisors before preparing their daily/weekly orders and, if necessary, ordering (more of) alternative health care products

#### 3.8.1 Analytics through progressive web app (PWA)

The native DHIS2 progressive web app functionality allows viewing any DHIS2 dashboards which are configured as "Make available offline" on a mobile device through any installed web browser.

All the visualizations from the Line Listing app as well as the Data Visualizer app indicated in chapter 2.7.3 "DHIS2-RTS Dashboards" can be accessed through any web browser on a mobile device by any user has been granted the respective user access.

The DHIS2 analytics (as of the time the mobile device was connected to the Internet the last time ) can be viewed any time while the mobile device is offline. Any changes made to the data and analytics while the mobile device will not be visible but the last update of the data will be visible indefinitely while the mobile device is offline.

In order to view the the visualizations without the dashboard headers select "View fullscreen" from the three dot menu in the upper right corner of each visualization.

#### 3.8.2 Summary analytics through Data entry forms

While the Pivot tables from the Data Visualizer app are too complex for viewing the offline analytics, the same information is available from the daily and monthly detailed reports from the respective Data entry forms which are natively available offline.

#### 3.8.3 Offline in-app analytics

_Under development_.

### 3.9 Mobile device synchronization

The DHIS2-RTS mobile app uses the native synchronization functionality which is included in the detailed DHIS2 documentation. The simplest way for synchronizing the mobile after every transaction is using the synchronization icon (double reverse arrow) in the header bar without having to leave the DHIS2-RTS user interface. However, there are some important operational considerations which are specific to the real-time stock management use case.

Note that it is a logical impossibility, and not a technical shortcoming, to keep a correct real-time record of the stock on hand on both devices if one or both are working offline. It would be in principle possible to recalculate and correct the stock balance after both devices are synchronized, but the DHIS2-RTS does not have this capability.

As the program rules can run on the web portal as well as any number of different mobile devices, it is critical that for any specific item (healthcare product), transactions are made on a single device at a time. At any time, there must only be a single device which recalculates the stock on hand and after completion of that calculation which must be synchronized with the next device which effects any transaction for the same item.

After completion of the transactions, all data should be synchronized with the central DHIS2 server as soon as possible. But in any case, a successful synchronization must be completed before any other device (using the web portal or the mobile app) effects any transaction for the same item.

If two devices, for example two mobile devices or one mobile device and one desktop computer, each effect a transaction for the same item "in parallel", the program rules on either device will calculate different Stock on hand levels for the same item. Even if all devices are then synchronized, the Stock on hand from the last device which synchronizes with the server will "override" any Stock on hand calculation which was made "in parallel", the overall stock record will be incorrect and not correct until a manual stock "Correction" transaction is effected.

In general, DHIS2 web access will be used exclusively for effecting stock receipts and is explicitly strongly recommended not to use the web portal for effecting any "Distribution", "Discard" or "Correction" transactions as the Events in the Tracker Program have only a date stamp but no time stamp and therefore cannot keep correct track of the chronological order of transaction. In contrast, the DHIS2-RTS mobile app uses a date and time stamp with hour, minutes, seconds, split seconds and therefore keeps a precise record of the exact time the transaction was effected on the mobile device. Therefore, all "Distribution", "Discard" or "Correction" transactions must only be effected on mobile devices.

For the operational use of the real-time stock management system in practice this means:

- at any given time, transactions for any specific item must be effected on a single device (mobile device or on the web portal) which must be synchronized before any other transaction is made for the same item

- if more than one mobile device is used at the same Organisation Unit then only one of them must be used for effecting transactions for any particular item at any time and must be synchronized with the central DHIS2 server before the other mobile device effects any transaction for the same item

- stock receipt transactions must only be effected on the web portal after all mobile devices have synchronized all their data with the web portal

- mobile device must only resume effecting transactions after completion of a stock receipt on the web portal and only after a successful completion of the synchronization

In most health facilities only a single mobile device will be needed and the coordination with the stock receipts which take place only once or twice a month will not pose any difficulties.

In case a health facility uses more than one mobile device at the same time, these constraints just require a simple rule work process rule for preventing any data discrepancy or stock on hand mismatch: if storekeepers receive several requests from different wards/services for supplying the same item, those requests are "split" among the storekeepers according to the group of items. For example, one storekeeper will pick all the oral drug products for the surgical ward, paediatric ward and out patient department while another storekeeper (using the second mobile device) will pick all the dressing material. In this way, each of the devices maintains an accurate real-time record for the items which are being picked and after both mobile devices synchronize their data, all transactions as well as stock on hand will be reflected correctly on the central DHIS2 server.

In principle, transactions can be recorded on a mobile device indefinitely before synchronizing. However, it is still strongly recommended to synchronize all mobile devices after every transactions or at least once a day for the following reasons:

- visibility of the real-time stock data will be available to any other users, for example at the district level, only after synchronization

- in case the device fails or a synchronization failure can only be resolved by deleting all local data from the device, all data which has not been synchronized yet will be lost without any way to recover the data

If the network connectivity does not allow synchronizing mobile devices with the central server (at least) once a day, the DHIS2-RTS mobile application is not a suitable solution for managing stock at the health care facility.

Note that, by design, the DHIS2 Capture Android app does not automatically synchronize data with the central DHIS2 server during login and if any data was not yet synchronized before logging out, the synchronization will have to be prompted "manually".

## 4 DHIS2 REAL-TIME STOCK WEB PORTAL MANAGEMENT

While the DHIS2-RTS use at the health facility level is conceived for exclusive use on mobile devices, the initial set-up and configuration, routine administration as well as the regular stock receipts can only be made through the DHIS2 web portal.

### 4.1 Creating stock item list

Before the DHIS2-RTS mobile application can be used, all health care products (items) used in any specific health facility (Organisation unit) must be "registered" and "enrolled" with their own and unique ID (identification) in each of the health care facility where those products are used. For example, paracetamol tablet, 500 mg has to be enrolled and registered in each Organisation unit (OU) separately as the product must uniquely assigned to its Organisation unit for correctly recording transactions and providing correct analytics. Note that an item, such as paracetamol tablets, with identical specifications in many facilities across a country, has to have its own and unique ID for each of these health facilities.

Items can be "registered" and "enrolled" manually through the native Capture app functionality by recording the "Item code" as well well as the "Item description" for each health care product.

Alternatively a list of items can be uploaded by using the "TEI import" function of the native DHIS2 Import/Export app or the third-party "Bulk Load" app.

### 4.2 Adding items to and removing from the DHIS2-RTS app

In the same way that items are created and added to the stock item list initially, items can be added to any health facility at any time.

[Question: how to remove (or "hide") items no longer in use. If they are deleted, will the analytics still be available].

### 4.3 Stock receipts

When consignments are received at the health care facility, the user confirms receipt to the district level where the stocks are uploaded from an electronic record.

The DHIS2-RTS design intentionally does not foresee any possibility for users to receive stocks through the DHIS2-RTS app itself as recording a large number of items one by one would be very cumbersome, time consuming and prone to error.

Stock receipts can be effected using the native Import/Export app or the third-party Bulk Load app. But ideally, all stock receipts should be effected directly and automatically through a real-time integration with the upstream, national LMIS. In this system, the items and quantities on the respective packing list are "loaded" into DHIS2 directly through its API-endpoints from the upstream, national LMIS as soon as the storekeeper has confirmed receipt.

### 4.4 Adding items to and removing from the Default Data Entry Form

Whenever items (health care products) are added to the DHIS2 Tracker Program, the corresponding Data elements must be configured and must be added to all DHIS2-RTS Data entry forms.

At any item, the list of TEIs (Tracked Entity Instances) of any Organisation unit must correspond completely and exactly with the list of Data elements in all DHIS2-RTS Data sets in order to ensure availability of the Data entry form for monthly reporting as a backup as well as for ensuring accurate analytics reporting.

### 4.5 Web portal analytics

All the analytics indicated in chapter 2.7 "Analytics configuration" are available in the DHIS2 web portal.

## 5 PHARMACY STOCK MANAGEMENT WITH THE DHIS2-RTS APP

In any implementation, national regulations and guidelines must be respected. This chapter focuses on technical and practical aspects and should only be considered as recommendations which may or may not be useful.

### 5.1 Preparations for implementing the mobile application

Using the DHIS2-RTS mobile application requires availability and sustainable management of an existing central DHIS2 server instance with technical support.

Most pharmacies rely on paper records such as stock cards, batch cards and various register books for managing stocks and stock data. Any health facility and anybody wanting to implement the use of the DHIS2-RTS system is well advised to consult with and obtain advice from HISP groups and colleagues who have implemented and are successfully using the system already.

Any implementation must be approved and planned by the national Health authorities as well as the respective health facilities.

Mobile device need to be provided and sustained, a really network connection needs to be available and financed and competent users need to be identified and trained on the application.

#### 5.1.1 Providing and setting up mobile devices

Every health facility should have at least one tablet PCsavailable which is dedicated for use by storekeepers and, ideally, a second backup device which may be shared with other users at the health facility.

Private devices should not be used as this poses data security risks and leads to arguments about payment for the Internet connection. Details on the specifications for recommended devices are given in chapter 1.6.

#### 5.1.2 Obtaining user access

At every health facility, at least the (main) pharmacist or storekeeper and another person replacing her/him in case of absence should have full access to the mobile device and the application. Other staff supervising pharmacists or storekeepers should also have access in order to be able to provide advice and training as well as understand any problems which may occur.

Every user must be configured in the central DHIS2 database with a username, password, user profile and corresponding user access and user rights.

#### 5.1.3 Adding health facilities to DHIS2

Only health care facilities which use the DHIS2-RTS should be configured in the DHIS2-RTS Tracker Program and therefore any additional health facility which intend to implement the system must be configured by DHIS2 system administrator.

Any Organisation units which are already configured in the DHIS2 database and in use for other DHIS2 applications must be used to avoid duplication of facilities and facility names.

#### 5.1.4 Setting up stock item list in DHIS2

A single, central stock item list for each health care facility is indispensable for using the DHIS2-RTS as well as for order management and stock management. In most cases, such a stock item list which details of all items which are permanently maintained in the pharmacy and are regularly replenished will already be available.

The stock item list can differ for each health facility or be standardized for each type of health care facility.

All stock item lists must use the same item codes and item descriptions which should be based on the national Essential Drug List managed by the Ministry of Health (MoH) in the country.

The consistent use of a single item code and item description across facilities is particularly important if the DHIS2-RTS system is integrated with a national, upstream LMIS system for managing medical stocks at the district, regional and central level.

It is very strongly recommended to only use "Each" as unit of measure (and never packages) which means that all health care products are managed as number of tablets, ampoules, cannulas, compresses etc. The use of packages is not practical as secondary packaging quantities are likely to differ between manufacturers and manufacturers may change secondary packaging quantities over time which makes the comparison of quantities over time as well as correct stock replenishment calculations impossible.

The use of item codes is optional but recommended. It is important to note that the DHIS2-RTS mobile application will always (and can only) display all items in their alphabetical order and it is not possible to group items into drug products, dressing materials, drains, cannulas etc. Therefore all items would appear "scrambled" according to their alphabetical names. For this reason using item codification systems which group health care products into their category are useful.

If no coding system is used or the coding system (such as numbers) do not allow grouping items, grouping can be achieved by preceding item descriptions with abbreviations for product groups such as DORA (oral drugs), DVAS (vaccines), MDRE (dressing material) etc.

#### 5.1.5 Uploading initial stock

Before the DHIS2-RTS mobile application is used, a complete phyiscal stock count should be carried out to confirm the available stock on hand. The result of this stock count is then simply uploaded as the initial stock receipt explained in chapter 4.3.

### 5.2 Pharmacy setup

Again, this chapter should be considered as a recommendation and possible solution which has been tried and tested in the field but which is superseded by national regulations and policies.

Using the DHIS2 Reat-Time Stock management system requires a high level of discipline and accuracy since the application automatically recalculates the remaining stock balance after every transaction and any mistakes are perpetuated.

#### 5.2.1 Storage equipment and health care good storage

All stocks should be arranged in alphabetical order of their item groups and within by item codes and item descriptions. The first batch of each item should be placed in a bin ("active bin") according to FEFO/FIFO. Any other batches which are not received in the tertiary supplier packaging should also be placed in separate bins while any health care goods delivered in tertiary supplier packaging should not be opened but placed on the shelf in the order of expiry dates. When the "active bin" is emptied, stock from the next batch can be placed in that bin for the next distribution.

In order to quickly identify the next batch for every item available for order picking, all "active" bins (first bin of each item only) should be fitted with barcodes which are clipped to the bin with a strong paper clip. The labels must not be pasted on the bins as otherwise a large number of bins without stock will accumulate which require a lot of storage space and it is much easier to just swap the barcode labels. The labels must also not be pasted on the shelves as the storage volumes fluctuate and it is much easier to change the location of bins with their labels.

Below an example of a best practice set-up from an actual implementation in hospital pharmacy is shown:

![](media/image17.png)![](media/image79.png)

Note the scanning barcode requires good lighting conditions and that barcodes must not be placed to close together as at any time a single barcode must be visible in the barcode scanner viewer finder for that barcode to be promptly and correctly recognized by the software application.

#### 5.2.2 Generating barcode labels for stock

Linear barcodes as well as QR codes are both equally recognized with the DHIS2-RTS mobile app. Linear barcodes have the advantage that they can be easily generated from a simple Excel spreadsheet but the disadvantage that they are quite long even for codes with only a few characters and the mobile device has to be held exactly horizontally during scanning (the red line in the barcode scanner window has to cover the entire barcode from left to right) in order for the barcode to be recognized.

Although QR codes can be generated from many websites for free, they can only be generated one by one and cannot be generated with a spreadsheet application. But the have the big advantage of being far smaller, being able to store longer codes and that they can be read from any angle, even if the mobile device is tilted (rotated) to the left or right and from greater distances.

Barcode labels can be very simply printed from Excel on any computer provided that the "LibreBarcode39" font is installed:

- close all Microsoft Excel files
- copy the LibreBarcode39-Regular.ttf file to your computer
- in the Windows Explorer right-click on the file: a pop-up window opens

- select "install": a pop-up window opens
- select: "Yes": the font installs on the computer
- open the Excel file for printing barcode labels: any copied Excel file with the font set to barcodes will now display barcodes

- highlight any (additional) fields which should display barcodes
- click in the drop-down window with the fonts
- scroll down to the list of available fonts to the letter L which will appear as a barcode and display "Libre Barcode 39" when mousing over

![](media/image47.png)

- Select "Libre Barcode 39": the drop-down window closes and the text appears as barcodes

The "PSM barcode label template" Excel file contains three worksheets

"A Item catalogue": this worksheet contains a list of all the stock items used in the respective pharmacy. The user tags the items for which a label is required by typing "X" next to the item in column B.

"B Label selection": this worksheet uses a lookup function to display only the items selected from the worksheet.

"C Label print": this worksheet correctly formats the item code, barcode and item description on four labels per page if printed in landscape which can be printed on any printer.

#### 5.2.3 Stock receipts

The receipt of consignments should must be acknowledged to the medical distribution centre shipping them, ideally using a simple DHIS2 application. After receiving the respective (district) medical store has received this notification, the logistics team will upload the items and quantities indicated in the packing list to the respective Organisation unit (health facility) where those quantities will be automatically added to the "Stock on hand". Ideally, this process will be fully automatized by integrating the upstream national LMIS with the DHIS2 serve.

It is important that the mobile device at the health facility receiving consignments, synchronize their data after the stock receipt has been effected in order to update and display the correct Stock on hand on the mobile devices before picking any further orders.

In case of any discrepancies between the packing list and the physically received consignments, the logistic team should be contacted for either arranging delivery of the short-shipped items and quantities or correcting the records in national LMIS system. If excess stock was delivered, the logistics services can simply issue a packing list for the missing quantities which are again acknowledged with the IRIS "Goods Confirmation" application and will correct the record. Either way, the corrected stock receipt quantities will eventually be updated in the DHIS2 database.

#### 5.2.4 Recording distributions

Storekeepers will usually receive a list of items and quantities required for each ward or service once a day, weekly or according to another established schedule.

The storekeeper will locate the first item on the list in the pharmacy, scan the barcode for selecting the correct item from the stock item list, and the picked quantity and then move on to pick the next item. This method is the fastest option and since a single row is displayed after scanning a barcode, the storekeeper cannot accidentally enter the value into the wrong row (for the wrong item). Alternatively, the storekeeper can scroll down the list until s/he finds the item or enter the required item in the search window.

Once all items in the required quantity have been picked, the storekeeper will confirm the transaction and deliver the goods to the requester before starting treatment of the next requisition.

Negative balances are deliberately blocked by the DHIS2-RTS mobile application to force storekeepers to effect corrections immediately since if delaying them would be allowed, stock discrepancies occurring by "postponed" corrections would inevitably accumulate. Therefore, if the remaining quantity on the shelf is greater than indicated as Stock on hand on the mobile device, the storekeeper can only pick the available quantity indicated in the mobile app. After completing the transaction, a stock correction needs to be made and then in a second transaction the now available quantities can be picked. Creating two separate transactions for the same ward or service will not make any difference for overall stock management and calculations. Alternatively, the storekeeper can interrupt the transaction but will lose all recorded data, then effect the stock transaction and start the initially intended transaction from scratch.

In case during the order picking mistakes were made, they cannot be corrected after confirming the transaction. If the recorded quantity is less than the actually picked quantity, the mistake can be simply corrected by effecting another transaction. If the recorded quantity is larger than picked (and needed) then either the "excess" quantity is delivered to the ward or service, kept aside to be included in the next distribution (without recording) or by creating a "Correction" transaction. However, if only a "Correction" transaction is effected, the full quantity recorded as shipped to the ward/service remains recorded in the system and these incorrect values cannot be corrected.

The "excess" quantity can also be given to another ward or service without recording. While the total stock on hand is thereby corrected, the statistics on distributions to each ward or service would again no longer be correct (and cannot be corrected).

#### 5.2.5 Recording discarded stocks

Stock which is expired, damaged or unusable for other reasons must be removed from the stock and be stored in a locked cupboard or room which is dedicated only to stock waiting for disposable. In order to account for reduction of the stock on hand without allocating stocks as distribution to any specific ward or service, the storekeeper carries out a "Discard" transaction in the same way as for the "Distribution" transaction.

#### 5.2.6 Recording stock corrections

Discrepancies between the physically available stock on hand on the shelf and the stock on hand balance calculated in the DHIS2-RTS mobile application may occur for various reasons.

• the quantities physically delivered to the health care facility are greater or less than in the electronic record (and not noted at the time of receipts)

• during order picking either greater or smaller quantities than indicated in the transaction are picked and delivered to wards and services (and not noted)

• stock is mislaid, misplaced in a wrong location, lost or stolen

In all of these cases, storekeepers must effect a "Correction" transaction in the DHIS2-RTS mobile application which will correct the calculated stock on hand. The number of "Correction" transactions and the quantities are a very good indicator for the overall quality of stock management.

In case "loans" are given to or received from other organizations or health care facilities options are not to create any transaction (as eventually the loan will be "repaid") or by effecting two stock corrections which cancel each other out.

#### 5.2.7 Residual balance counting for stock on hand

As the stock on hand as well as the transaction quantities are instantly updated in the DHIS2-RTS mobile application, a complete and updated record of the current stock on hand is available in the system at any time and in principle no (monthly) physical stock counts are necessary. However, if stocks are never counted, discrepancies will only become apparent if and once negative stocks would occur during a transaction.

There are simple and fast ways for counting and checking the remaining stock on hand in certain situations which will allow detecting any discrepancies. This "residual batch counting" has the big advantage that the items with the largest number of stock transactions are counted more often and that discrepancies can, in principle, be detected immediately rather than only at the end of the month when it is often difficult to retrace the error.

Residual balance counting methods include:

- counting the remaining stock whenever a batch is depleted, and the next batch of an item is placed in the "active bin" (tertiary packaging is often provided in "round" quantities such as multiple of thousands with the quantities indicated on the tertiary packaging)

- just before opening any tertiary packaging, checking whether the remaining stock on hand is a "round" quantity (even without actually counting the entire remaining stock.

- physically counting the remaining stock on hand for small quantities of items which can be effected quickly

### 5.3 Backup plan in case of system failure

Any digital systems can fail at any level: the mobile device at the health facility, the Internet connection can fail for prolonged periods and central servers and databases can fail.

In order to ensure continuity of services while at the same maintaining an accurate record of any transactions which could not be reported in DHIS2, a backup system needs to be in place from the beginning.

The simplest way is to continue or resume the use of stock cards for any transactions which cannot be reported in DHIS2.

For the "Advanced mode", the quantities distributed to each ward or service can be tallied up and entered with a single transaction for each ward or service once the system is restored. This will falsify the transaction dates but still maintain an accurate record of the total quantities distributed to each ward or service. In case of prolonged system failure, the "aggregate" Data entry form with a monthly reporting period can be used for documenting the stock on hand at the end of the month as well as the total quantities during the month. The details of these transactions will be permanently missing in the system but, after effecting a stock "Correction", use of the DHIS2-RTS mobile application can be resumed once all systems are restored.

## 6 DHIS2 REAL-TIME STOCK INTEGRATION WITH NATIONAL eLMIS

As the integration of DHIS2 with an upstream, national eLMIS requires a detailed mapping of data and a dedicated project, this chapter can only provide an general outline of an integration.

The DHIS2-RTS concept is based on the assumption, that the DHIS2-RTS mobile application is used only for recording stock transactions and all forecasting, demand planning and calculation of stock replenishment orders are effected only by the national eLMIS.

Furthermore, that as soon as storekeepers at a health facility confirm receipt of consignments through a dedicated DHIS2 Event program, the respective items and quantities are synchronized with the DHIS2 server and recorded as stock receipt in the DHIS2 Tracker Program.

The integration of DHIS2 used (only) at the health facility level with a national eLMIS which is used for all logistics processes and workflows at all upstream (district, province and central) level together provide real-time and end-to-end visibility of all logistics data as well as a seamless, integrated end-to-end stock replenishment system.

The synchronization of facility level DHIS2 data with the central DHIS2 server is managed fully by native DHIS2 functionality. The integration of DHIS2 with the national eLMIS requires synchronization of data from the central DHIS2 server with the national eLMIS server as well as synchronization of (some) data from the national eLMIS server with the central DHIS2 server. As every DHIS2 entity features a unique ID, integration is best accomplished by using (only) these IDs rather than the actual field names appearing for users which are natively available from any DHIS2 instance through the Web API.

### 6.1 Data synchronization from DHIS2 to national eLMIS from

The following data fields from the DHIS2 Tracker Program need to by synchronized with the national eLMIS server, ideally in real-time.

**Health facility data**

- Organisation unit name
- Item code (the item description is redundant and not needed)
- User names (for notifications)

**Transaction data**

- Current Stock on hand
- Stock "Distribution": quantities and date/time stamp, optional: "Deliver to"

- Optional: Stock "Discard": quantities and date/time stamp
- Optional: Stock "Correction": quantities and date/time stamp

**Stock receipts**

- Consignment: ID and date/time stamp, optional: user name

### 6.2 Data synchronization from DHIS2 to national eLMIS from

The following data fields need to be synchronized from the national eLMIS to the central DHIS2 server, which in turn manages synchronization of the data with the respective mobile devices at health facilities.

**Consignment data**

- Organisation unit name
- Item code (the item description is redundant and not needed)
- Stock "Receipt": quantities and date/time stamp

bbh10012024

GMc editing test on 11-01-2024 at 19:11
