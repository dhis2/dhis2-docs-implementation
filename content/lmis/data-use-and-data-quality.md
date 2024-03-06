# DATA USE AND DATA QUALITY


##	LMIS data quality

xxx - To review
https://docs.dhis2.org/en/use/user-guides/dhis-core-version-240/collecting-data/data-quality.html
https://www.who.int/data/data-collection-tools
Manual for the DHIS2 quality tool
Improving Data Quality in Mobile Community-Based Health Information Systems
xxx
Text box:
The entities of all metrics is the quantity of an item (health care product) which are always measured in units of "Each" (single tablet, ampoule, compress) and never in unit packs.
xxx

### Introduction
While logistics and supply chain management is usually associated with the production, storage and distribution of (commercial) products, the associated data is far more important but usually as invisible as the roots of a tree. The physical flow (storage and distribution) of goods and consignments is by far the easiest task in logistics and supply chain management while the real, albeit less obvious, challenges are managing the complex flows of associated data: obtaining accurate as well as up-to-date logistics data in a timely way and sharing them throughout the supply network in real-time in order to allow decision-making which ensures that the required quantities of required healthcare products are in the places where they are required for providing healthcare services at the time the are required.
Trust between all actors and stakeholders are critical and indispensable for any effective and efficient supply network and the data is only as good as the trust the stakeholders have in it. Healthcare facility staff who do not trust supply managers will "inflate" order quantities hoping that this behaviour will increase supplies to them ("ration gaming"). On the other hand, if supply managers do not trust the facility level data they will resort to their own "estimates" for calculating replenishment orders which are always inferior to the systematic use of accurate and timely end-user data. Apart from continuously improving services, trust in data can be enhanced by freely and openly sharing data across supply networks, ideally in real-time.

The large number of different data quality dimensions are structured by UNICEF into the following four categories:
Access to data
- Data accessibility
Output quality dimensions
- Relevance
- Correctness
- Completeness
- Accuracy
- Reliability (reproducibility)
- Consistency
- Timeliness and punctuality
- Frequency
- Interpretability
- Comparability
Process quality dimensions
- Burden for data collectors
- Appropriateness of data sources
- Data collection process
- Transparency and documentation of data sources
Institutional quality
- Transparency and credibility
While conventional, paper-based LMIS data management systems require balancing various tradeoffs, such as the amount of data fields or data accuracy and timeliness, the use of digital data collection and management systems improve accuracy, timeliness, accessibility, consistency etc. at the same time.

###	Data accessibility
Generally, data is only of any use if the systems and people which require them have timely, easy and complete access for decision-making. While (even paper-based) data is usually readily available at the healthcare facility level, the time sharing and exchange of data across the entire supply network is indispensable and critical.
Storekeepers at healthcare facilities require visibility of their stock as well as visibility of order status and supply managers at upstream levels need timely access to updated and accurate stock data for effective and timely stock replenishment. Other stakeholders such as health managers at all levels of the health systems and other actors such as (commercial) suppliers or (international) donors also require access to logistics data for reporting and auditing.
Within the constraint of network connectivity, the use of digital LMIS systems allows instant and complete access of all LMIS data from all levels of the supply network without any national or international stakeholder. This data is accessible in tables displaying time series of essential LMIS data as well as customised reports. The same effectiveness and efficiency would be impossible to achieve by distributing paper-based records manually.
As DHIS2 stores and manages all data in a central database, all data is easily accessible by design.
Through its native and well documented API-endpoints, DHIS2 allows any professional information system to easily integrate for synchronising ("reading" as well as "writing) data.
Regular (daily) backups of the databases ensure that all data remains accessible even if parts of the information system network temporarily fails.

### Data output quality
The data output quality refers to the collected and shared data as such.

#### Relevance
Relevance of LMIS data refers to the ability to serve the purpose and make the decisions for which it was collected and shared. The main purpose of LMIS is ensuring effective and efficient stock replenishment while avoiding (preventable) expiry of stocks.
Different stakeholders in the supply network and in the health system may require different data for different purposes at different times. Generally speaking, too much data is being collected without having a clear purpose in mind.
In principle, managing supply networks effectively and efficiently requires only a small number of data points. For example, at the healthcare facility level, only stock transaction quantities (distributed/issued, discarded and lost stock) are relevant while all other (secondary) data can be derived. At upstream levels, in addition data on orders, consignments as well as details of stocks (batch numbers and expiry dates) need to be managed.
The use of DHIS2 at the healthcare facilities encourages limiting collected data points as it only complements data which is not (and cannot be) available in mSupply and the use of best practices is encourage during the design phase projects and advising project members.

#### Correctness
Data correctness refers to collecting the data items which correspond to the data fields which are being collected. For example, entering distributed quantities into the correct data field (column) of a paper-based or digital form.
The use of DHIS2 contributes to correctness by minimising the number of data fields which need to be collected. For example, when using DHIS2-RTS (Real-Time System) only transaction quantities are recorded and therefore the mistaken entry into a wrong data field (column) is impossible. The use of barcode scanners eliminates the risk of mistakenly recording any data for the wrong healthcare product in the wrong row.

#### Completeness
Data completeness refers to the number of data points (or data fields, reporting forms, number of healthcare facilities) for which data is recorded during every reporting period. If all collected data is relevant and essential then, by definition, one hundred percent of all data points are required for one hundred percent of the reporting periods for taking decisions.
For example, for effective and efficient stock replenishment it is absolutely critical that stock on hand and distribution quantities are collected every month for each and every item (healthcare product).
DHIS2 contributes to data completeness by intuitively visualising data gaps in Pivot tables as well as with various verification tools (see below).
When using the DHIS2-RTS (Real-time system) the issue of data completeness does not really arise as there is no retroactive recording or reporting of LMIS data during every reporting period. Instead all transactions are recording at the time the physical transaction (distribution or discard of stock) takes place and therefore necessary all data will be complete (unless recording of the stock transaction is omitted altogether).

#### Accuracy
Accuracy refers to the agreement of value of the collected data points with the physical entity which is being measured and reported. For example, whether the reported stock on hand actually corresponds to the quantity which is physically available in the store. Data accuracy requires both, to correctly count the stock and then to enter the correct quantity.
Neither manual nor digital data management systems can ever ensure the accuracy of all data and, in principle, information systems will not be able to detect incorrect counts or transactions which were mistakenly not corrected. However, DHIS2 provides various tools to identify data inconsistencies (see below). Often checks and balances will point to certain data values which are definitely incorrect and indicating the correct range of a certain data value but without allowing to determine the exact correct data value.

#### Reliability (reproducibility)
Reliability, or reproducibility, refers to the stability of data values if the data collection is repeated. For example, typically the end-of-year physical stock count will be carried out by two (or more) teams which both count the same stock (while any transactions are frozen) and should produce identical stock reports.
However, since recounting data is very time consuming it is rarely undertaken and DHIS2 will not immediately contribute to reliability of collected data.

#### Consistency
Consistency, or coherence, of data refers to the ability of being reconciled and whether the "numbers add up". For example, the stock on hand before and after a transaction must be identical to the transaction quantity or the stock on hand at the end of the reporting quantity must be identical with the sum of the stock on hand at the beginning of the reporting period and all transaction quantities during the reporting period.
DHIS2 contributes to data consistency with various checks and balances (see below). The DHIS2-RTS (Real-Time stock management system) updates the stock on hand instantly after recording any transaction quantity and allows storekeepers to quickly identify (obvious) discrepancies which in turn allow verifying, for example, the transaction quantity.

#### Timeliness and punctuality
Timeliness ("freshness", "up-to-dateness") refers to the delay between the change of the observed value and its reporting. Since periodic (usually monthly) reporting systems do not require immediate reporting of any changes to LMIS data, except for real-time systems, in practice only punctuality can be determined and measured. For real-time systems, timeliness only applies to data sharing and is measured by determining the difference between recording the transaction on a mobile device and the time it is synchronised with the (central) DHIS2 server.
Punctuality of data (collection) refers to completion of data collection before the defined due date. For example, for monthly stock reports, ideally stock data should be recorded and transmitted on the last day of the month at the latest. However, timeliness is related to the reporting frequency. For example, even if stock data is reliably reported on the last day of the month, no updates whatsoever are available between two reporting periods. Generally speaking, the "older" (more outdated) LMIS data is, the greater the difference between the last reported data value and current data value is likely to be and therefore the less useful it is.
Therefore, for any LMIS the optimal (best possible) system is a real-time data collection and sharing.
No information system can ensure that human beings record data on time but DHIS2 allows measuring any delays, providing feedback in reports and therefore encouraging staff to report on time.
For LMIS data the importance of timeliness depends on stock levels. As long as the current stock level does not prompt any stock replenishment, sharing that stock data will not prompt any action (replenishment) and is therefore not of immediate importance. On the other hand, it is critical to report low stock levels and stockouts as quickly as possible. DHIS2 allows both, regular monthly reporting as well as recording and sharing data on stockouts for the concerned healthcare products immediately as and when they occur.
Since the DHIS2-RTS (Real-Time stock management system) does not require any (retro-active) recording and reporting of data, timeliness is a given by default as every transaction is recorded and reported in real-time (or as soon as a network is available). In practice, network connectivity is likely to be intermittent but daily data updates are also sufficient for quickly responding to shortages and stockouts. Since, even at the healthcare facility level, real-time data recording and sharing is feasible, there is no reason to compromise and settle for anything less than real-time.

#### Frequency
The frequency refers to the length of the reporting period which is usually one month for LMIS data. For LMIS data, the higher the frequency the better with a real-time system being optimal.
The frequency of LMIS data collection and reporting at the healthcare facility level must be coordinated with business processes at the supplying medical stores to ensure that the data from (recent) stock reports is used as quickly as possible for calculating stock replenishment orders.
The "aggregate" periodic reporting provides for all commonly used reporting frequencies and periods such as daily, weekly, monthly, quarterly or annually with the real-time, transactional reporting being the preference.

#### Interpretability
Interpretability refers to the ease of understanding interpreting data and its usability and is an answer to the question "does the data make sense".
Essential LMIS data are clearly defined and do not allow for much choice. Apart from the unusual terminology in logistics and supply chain management, all LMIS data points, such as stock on hand or transaction quantities, are intuitive and easily understood.

#### Comparability
LMIS data needs to be comparable over time as well as across healthcare facilities and levels of the supply network. For example, all storekeepers throughout the supply network need to always count all healthcare products in units of use (tablet, syringe etc.) and not in (different) packaging quantities in order to be comparable. Another example is that stock transaction quantities need to be consistently recorded for the same time periods, usually in months, at all levels of the supply network. All actors in the supply network need to use the same (derived) data, for example performance management metrics.
DHIS2 contributes to comparability by providing all healthcare facilities with standardised and preset reporting forms for the whole country with predefined reporting periods which cannot be changed by users (unless they have administrator rights).
Likewise, in DHIS2 performance metrics for measuring the quality of logistics services are standardised across healthcare facility which ensures comparability.

### Data process quality
Data output quality is affected by data process quality which refers to the appropriateness of data sources, the means of obtaining, collecting and processing data as well as data verification and documentation.

#### Burden for data collectors
Generally, the effort, time and other resources required for accurate and timely data collection and sharing must be balanced with the benefits of using this data and ultimate with the direct or indirect impact the (additional) data has on improving stock availability and minimising stockouts at the healthcare facility level.
Minimising the burden of healthcare facility staff for obtaining, recording, aggregating and sharing data is a particular importance for managing LMIS data at the healthcare facility where health systems are plagued with collection of redundant LMIS data as well as primary and secondary data which is not used for a clearly defined purpose.
For example, healthcare facility staff are required to record "opening balances" and "closing balances" which are entirely redundant. Another typical example is the request to calculate metrics such as "stockout days" which are cumbersome to calculate by manual analysis of paper records although better and more easily obtainable metrics for calculating and monitoring stock availability are available.
The use of DHIS2 in itself cannot prevent or reduce the number of unnecessary und redundant data points implementing organizations wish to collect, as DHIS2 itself is flexible and allows to easily change the configuration of reporting forms. However, the importance of reducing the workload for healthcare facility staff is a key principle in designing LMIS tools and prominent in the documentation and technical advice provided.
The integration of DHIS2 at the healthcare facility level with mSupply allows eliminating the collection of redundant data. For example, the "Stock receipt" which is commonly collected is fully and professionally managed in mSupply and therefore does not need to be collected, a second time, in DHIS2. Nevertheless, mSupply can provide complete, detailed and accurate visibility of stock receipt if and as required.

#### Appropriateness of data sources
All periodic reporting systems rely on manual records such as batch cards, stock cards and other records as their primary data source even if the (monthly) reports (secondary data source) are recorded directly on digital devices. Therefore, for the period (monthly) reporting the use of DHIS2 relies entirely on the accuracy and reliability of the manual stock records and does not document or provide information on these data sources. For LMIS data the appropriateness of data sources is not critical in the sense that there are no alternative data sources.
However, for the data recorded and stored in and shared by DHIS2, the log files provide complete details and visibility of the place of data collection (provided the geolocation function is configured), the identity of the person who has logged into the mobile device as well as an exact date and time stamp of each and every data point which is being recorded as well as any changes to those data.
The DHIS2-RTS (Real-Time stock management system) allows managing medical stocks entirely without any paper-records. The only physical ("external") data source it relies on is the barcode which is attached to each healthcare product in the medical store. As for any other data recorded and managed in DHIS2, the DHIS2-RTS records the geolocation, user identity as well as a data and time stamp (hours, minutes, seconds and split seconds) of every recorded transaction.

#### Data collection process
The conventional process of counting (quantities), recording data and manually collating numbers at the end of the month is prone to error by recording data values for the wrong item, mistakes while copying data from one record to another as well as for collating data mentally or with a calculator. This manual process is not limited to healthcare facilities but is repeated at several other levels, such as the district, provincial and central level.
The collection, storage and sharing of data from the healthcare facility level using mobile devices eliminates any mistakes at upstream levels, both by eliminating any need to manually copy data as well as by automatically aggregating data or performing any other calculations automatically.
In the best case of using DHIS2-RTS, no duplication of any data is required (or even possible) and therefore any mistakes which would occur by duplicating data are safely avoided. As long as the collection of primary data (stock transaction quantities) is correct, all further errors are avoided. Furthermore, the entire data collection, storage and sharing process is digitally documented in log files with the data, user credentials, geolocation as well as data and time stamps which can be analysed and audited any time simply by downloaded data from the central DHIS2 server.

#### Transparency and documentation of data sources
The general meaning of providing clear, openly accessible information about operations, research design and data collection methodology which are documented for collecting health systems data does not equally apply to LMIS data as the data collection is a straightforward process which does not allow different options.
However, the information provided above on the documentation of the data collection, storage, processing and sharing mentioned above contributes to fulfilling this requirement.

### Institutional quality
LMIS data is only as good as the trust stakeholders in the health system have in it. Unfortunately, doubts about data quality and accuracy are quite common and, in the worst case, leads to ignoring LMIS data reported by healthcare facilities and second guessing essential LMIS data such as monthly (aggregate) stock issues.
DHIS2 greatly improves quality in data as records are transparent, easily accessible to and instantly shared with all stakeholders and can easily be analysed and audited.

### Summary of the DHIS2 contribution to data quality
The table below summarises how DHIS2 contributes to high data quality standards by design and various automatic algorithms.

| **Data quality dimension**  | **DHIS2 contribution** |
| :--- |  :--- |
| Access | Global accessibility from a single DHIS2 instance |
| Relevance | Data collection (forms) according to best practices |
| Correctness | Minimising the number of data fields, Barcode scanners for identifying healthcare products |
| Completeness | Intuitive visualisation of data gaps, Data completeness reports, Completeness by design when using DHIS2-RTS |
| Accuracy | Data consistency checks |
| Reliability (reproducibility) | - |
| Consistency | Data consistency checks, Instant stock on hand updates when using DHIS2-RTS |
| Timeliness and punctuality | Report punctuality analysis, Timeliness by design when using DHIS-RTS |
| Frequency | Flexible use of any reporting frequency, Real-time reporting (best practice) with DHIS2-RTS |
| Interpretability | Use of only essential LMIS data by design |
| Comparability | Standardised and present data reporting forms |
| Burden for data collectors | Minimal LMIS data collection by design, Avoids data redundancy |
| Appropriateness of data sources | Complete visibility of data collection through log files |
| Data collection process | Digitised data collection, Automated data sharing (synchronisation),Eliminates mistakes by data duplication and copying |
| Transparency and documentation | Transparency of data collection through log files |
| Transparency and credibility | Transparency and auditability of all data and log files |

## DHIS2 LMIS data quality analysis
DHIS2 natively features a range of tools and applications for preventing the entry of erroneous data, real-time validation of already entered data and (retro-active) analysis of entered data for identifying (potentially) false data values as well as data which was not recorded on time.

### DHIS2 data validation of individual data values
The native DHIS2 data validation features allow validating data values during data entry entry and thereby minimizing data handling errors. Data validation means ensuring that entered data values are within predefined ranges.
The DHIS2 "Value type" setting, which is natively available for all "Data elements", allows restricting the entry of data values to certain number sets such as natural numbers ("Positive Integer") or positive integers (which includes zero). This setting also prevents "accidental" data entry such as mistakenly entering text into a numeric data field.
During data entry, DHIS2 will indicate any data values which are outside the defined data range by highlighting the data field with a red background and displaying an additional error message on the screen. For example, DHIS2 will prevent users from entering non-integer or any negative values in a stock on hand field and prevent the user from saving any report until the error is corrected.
Users can open a on-screen pop-up window which will display the entire history of entered data values in a bar chart and line chart which allows to quickly identify inconsistent values and outliers.
The DHIS2-RTS (Real-Time System) goes even further by not only displaying an alert in real-time if negative data values are entered but even preventing the user from saving the data entry and continuing entry of any further data. In addition, a specific minimum and maximum data value can be configured for each data field which will display a real-time alert if the user enters a value which is outside of the configured range.
The DHIS2-RTS system prevents negative stock on hand values, prevents entry of any non-integer values in any data field and prevents entry of negative or zero values for any transaction quantities.
A dedicated DHIS2 "Validation rule" application allows configuring complex validation rules based on data values from different data fields such as entering any data values which would lead to negative stock on hand values. When users execute the validation, DHIS2 will display a list of alerts in a dedicated sidebar.
The DHIS2 "Data Quality" app allows defining a z-score, identifying any data values which lie outside of the set range and are therefore likely to be outliers.

###	Completeness and timeliness of reports
DHIS2 natively allows to set a "Days after period end to qualify for timely data submission" which allows to then determine whether reports were submitted on time. At the end of the monthly data recording users confirm completion by selecting the "Complete" button on the data entry screen. 
This data and time stamp then allows to generate a range of default reports for the completeness of reports in terms of data recordings for each data field as well as the timeliness (on-time) of reported data values.

## 3 LMIS data use
Although logistics and supply chain management is often associated with and perceived as handling (storing and transporting) physical goods and stocks, in reality logistics and main, and difficult, issues in logistics supply chain management is obtaining and processing timely and accurate data. The most difficult tasks in supply chain management of ensuring the availability of stocks in the place they are required and at the time they are required is entirely determined by data. Provided that stocks are available, the material handling (storage and transportation) is by far the easiest task.
Therefore data in general, and data from the last mile (first data mile) in particular, is absolutely essential, critical and indispensable. Only supply networks driven by first mile demand data can be effective as well as efficient and ensure that all goods required for providing high quality health care services are available at the service delivery point when they are needed.
Far too often, any logistics data is lumped together as "indicators" or even "Key Performance Indicators" (KPI) while actually logistics data serves different and distinct purposes.

###	Data use for inventory control
Inventory control (science, policies and systems for replenishing medical stocks at healthcare facilities and other medical stocks) lies at the heart of all supply chains and depends on the accurate and timely data from the healthcare facility as well as upstream levels. Therefore it is accurate and timely data together with rational and professional inventory control policies with make or break supply chains. Although the use of logistics data usually focuses on "reporting", the use for inventory control is by far the most important purpose.
Without stock data from healthcare facilities, supply managers have to resort to surrogate data such as shipments to healthcare facilities which inevitably causes demand distortion and reduces stock availability at all levels of the supply network.
Fortunately stock replenishment calculations require very little data but that data must be timely and absolutely correct:
- Stock on hand (the result of a physical stock count at the end of every month): indispensable for calculating stock replenishment quantities
- Aggregate, monthly stock issues ("consumption") are indispensable for demand analysis and forecasting future demand
If accurate and reliable data on stock receipts at healthcare facilities is available, then the stock on hand can be calculated from the stock on hand at the beginning and the end of the month.
Unfortunately, public health systems tend to collect too much logistics data which is not used for decision making and the key for reducing shortages and stockouts is collecting as little data but as accurately, timely and efficiently as possible.

###	Data use for logistics performance management
In an ideal world with perfectly functioning supply networks, where neither stockouts nor overstocking occur, monitoring and measuring the quality of logistics services would not be needed. In practice, measuring and monitoring logistics performance is critical and indispensable. Not for generating "reports" and dashboards which may or not be used but rather for informing corrective action which changes and eventually optimises all inventory control parameters in order to increase and maximise stock availability while minimising stock wastage at health care facilities.
Despite a plethora of statistics, indicators and key performance indicators, a comprehensive and complete performance management system only requires the collection of a handful of data fields at the healthcare facility level:
- Number of stock items managed (and changes over time)
- Monthly demand quantities (monthly aggregates or transaction quantities)
- Stock on hand quantities (at the end of the month or ideally in real-time)
- Stock discards quantities
- Stock correction quantities
- Date and time of completion of monthly stock data reports
- Date and time of stock transactions (where real-time systems are used)
In addition to the above, the following data fields need to be recorded and stored in the national eLMIS system for all medical stores at all levels:
 - Batch number (serial number) and expiry dates of all healthcare products
 - Inventory control parameters (and any changes over time)
 - Customer order details (customer name, date, items, quantities etc.)
 - Customer order fulfilment dates and lead times (for all of its components)
 - Consignment details (items, quantities, recipient, shipment and arrival date etc.)
 - Cost of healthcare products (at the batch level)


###	Data use for analytics and reporting
Finally, data is also needed for various analytics (other than performance management) and routine reporting. However, it should be stressed, that reports which have the sole purpose of complying with reporting requirements and do not inform or initiate any (corrective) action are just a waste of valuable resources.
Data, such as on available stocks, are useful for health workers and various managerial staff even if they are not responsible for taking corrective action and other data, such as monthly demand aggregated at facility, district, regional and national level, are required for (long-term) planning by various managers.
Typically, (monthly) stock data is reported in Pivot tables by healthcare product and reporting period (months) or line charts for time series analyses, such as determining trends.

## Logistics metrics
Xx

###	Benchmarks
Xx

###	Required logistics data
Xx

###	Source of data and calculations
Xx

###	Overview of DHIS2 logistics metrics
Xx

## DHIS2 logistics data statistics
Xx

###	Stock receipt
Xx

###	Stock distribution
Xx

###	Stock redistribution
Xx

###	Stock discard
Xx

###	Stock on hand
Xx

###	Stock correction
Xx

##	DHIS2 logistics indicators
Xx

###	Coefficient of variation (CoV)
Xx

###	Stock coverage time
Xx

###	Stock discrepancy
Xx

###	Report completeness
Xx

###	Report timeliness
Xx

## National eLMIS metrics
Xx

## LMIS performance management framework
Xx

###	General principles
Xx

###	"Manifestation" indicators ("symptoms")
Xx

###	Root cause indicators ("diagnosis")
Xx

###	Programme specific indicators
Xx

###	Corrective action ("therapy")
Xx

###	Summary with flow chart
Xx

## HMIS/LMIS triangulation
Xx

### Data triangulation
Xx
