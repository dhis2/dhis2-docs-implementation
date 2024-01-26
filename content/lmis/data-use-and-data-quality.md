# DATA USE AND DATA QUALITY

>*Table of contents for planning purposes, will be deleted in actual document*  
>LMIS data quality  
>>Data accessibility  
>>Data output quality  
>>Data process quality  
>>Institutional quality  
>>Summary of the DHIS2 contribution to data quality  
>  
>DHIS2 LMIS data quality analysis  
>>DHIS2 data validation of individual data values  
>>Completeness and timeliness of reports  
>
>LMIS data use  
>>Data use for inventory control  
>>Data use for logistics performance management  
>>Data use for analytics and reporting  
>
>LMIS logistics visualization framework
>
>DHIS2 LMIS logistics analytics
>**1 Monthly Stock Reporting**  
>>**1.1 Health facility level**  
>>>**1.1.1 Statistics**  
>>>>MSR DV 1 - Monthly Stock Reporting / Stock receipt / Last 12 months / Health facility / Pivot table
>>>>MSR DV 2 - Monthly Stock Reporting / Stock distribution / Last 12 months / Health facility / Pivot table  
>>>>MSR DV 3 - Monthly Stock Reporting / Stock redistribution / Last 12 months / Health facility / Pivot table  
>>>>MSR DV 4 - Monthly Stock Reporting / Stock discard / Last 12 months / Health facility / Pivot table  
>>>>MSR DV 5 - Monthly Stock Reporting / Stock on hand / Last 12 months / Health facility / Pivot table  
>>>>MSR DV 6 - Monthly Stock Reporting / Stock correction / Last 12 months / Health facility / Pivot table  
>>>>MSR DV 7 - Monthly Stock Reporting / Stock report complete / Last month / Health facility / Pivot table  
>>>>MSR DV 8 - Monthly Stock Reporting / Stock report complete / Last 12 month / Individual item / Health facility / Pivot table
>>>>MSR DV 9 - Monthly Stock Reporting / Stock report complete / Last 12 month / Individual item / Health facility / Column chart

>>>
>>>**1.1.2 Indicators**  
>>>>MSR DV 8 - Monthly Stock Reporting / Stock distribution / Coefficient of Variation / Last 12 months / Health facility / Pivot table  
>>>>MSR DV 9 - Monthly Stock Reporting / Stockout count / Last 12 months / Health facility / Pivot table  
>>>>MSR DV 10 - Monthly Stock Reporting / Stockout length / Last 12 months / Health facility / Pivot table  
>>>>MSR DV 11 - Monthly Stock Reporting / Stock coverage time / absolute / Last 12 months / Health facility / Pivot table  
>>>>MSR DV 12 - Monthly Stock Reporting / Stock coverage time / range / Last 12 months / Health facility / Pivot table  
>>>>MSR DV 13 - Monthly Stock Reporting / Stock coverage time / distribution / Last month / Health facility / Pivot table  
>>>>MSR DV 14 - Monthly Stock Reporting / Stock discrepancy / list / Last 12 months / Health facility / Pivot table  
>>>>MSR DV 15 - Monthly Stock Reporting / Stock discrepancy / count / Last 12 months / Health facility / Pivot table  
>>>>MSR DV 16 - Monthly Stock Reporting / Stock report complete / Last 12 months / Health facility / Pivot table  
>>
>>**1.2 District level**  
>>>**1.2.1 Statistics**  
>>>**1.2.2 Indicators**  
>>
>>**1.3 Provincial level**  
>>>**1.3.1 Statistics**  
>>>**1.3.2 Indicators**  
>>
>>**1.4 Country level**  
>>>**1.4.1 Statistics**  
>>>**1.4.2 Indicators**  
>
>**2 Real-Time Stock Management**  
>>**2.1 Health facility level**  
>>>**2.1.1 Statistics**  
>>>**2.1.2 Indicators**  
>>
>>**2.2 District level**  
>>>**2.2.1 Statistics**  
>>>**2.2.2 Indicators**  
>>
>>**2.3 Provincial level**  
>>>**2.3.1 Statistics**  
>>>**2.3.2 Indicators**  
>>
>>**2.4 Country level**  
>>>**2.4.1 Statistics**  
>>>**2.4.2 Indicators**  

<br>  
<br>  

| Visualization  | Item | Facility | District | Region | Country | Visualiations | Offline |
| :-------- | :---: | :---: | :---: | :---:| :---: |:---: | :---:|
| **STATISTICS / MONTHLY** |
| Stock receipt| Sum/Average | Sum | Sum | Sum | Sum | Pivot |
| Stock distribution| Sum/Average | Sum | Sum | Sum | Sum | Pivot |
| Stock redistribution| Sum/Average | Sum | Sum | Sum | Sum | Pivot |
| Stock discard| Sum/Average | Sum | Sum | Sum | Sum | Pivot |
| Stock on hand | Sum | Sum | Sum | Sum | Sum | Pivot |
| Stock correction | Sum/Average | Sum | Sum | Sum | Sum | Pivot |
| Stock report complete | Sum | Sum | Sum | Sum | Sum | Pivot |
| Monthly report| - | Count | Count | Count | Count | Pivot |
| Health facility| - | 1 | Count | Count | Count | Pivot |  

Stacked bar chart + line chart: receipt, distribution, correction, stock on hand

<br>  
<br>  

| Visualization  | Item | Facility | District | Region | Country | Visualiations | Offline |
| :-------- | :---: | :---: | :---: | :---:| :---: |:---: | :---:|
| **INDICATORS** |
| Stock distribution / Coefficient of Variation | List |  |   |  |  | Pivot |
| Stockout count | List | Count |  Count |Count | Count | Pivot |
| Stockout length | List | Count |  Count |Count | Count | Pivot |
| Stock coverage time / absolute | List |  |  |  |  |  |  |  |  |  |
| Stock coverage time / range | List | Count | Count | Count | Count | Pivot |  |
| Stock coverage time / distribution | List | Count | Count | Count | Count | Pivot |  |
| Stock discrepancy | List | Count |  Count |Count | Count | Pivot |

By default, all the visualizations above are shown as time series (by month/by day)
<br>  
<br>  
Some visualizations needed for each type:
Visualization
Abbr.
Pivot table
Column
Bar
Line
Pie
Gauge
Single value
Line Listing
Map
Offline analytics!!!
<br>  
For each metric:
- Definition
- Calculation
- Target ranges
- Interpretation
- Corrective action (include details here and only a summary in the performance management chapter?)
- Visualization options

Naming conventions for visualizations:
MSR - Monthly Stock Report / Distributions / Last 12 months

>**MSR DV 1 - Monthly Stock Reporting / Stock receipt / Last 12 months / Health facility / Pivot table**  
>This report provides the monthly stock receipts as reported at the end of every month.  
>
>**Name \(*)**: "MSR DV 1 - Monthly Stock Reporting / Stock distribution / Last 12 months / Health facility / Pivot table"  
>>**Columns**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 months"  
>>
>>**Rows**  
>>>**Data**  
>>>>**Data Type**: "Data elements"  
>>>>**Data element group**: select "[Stock item list] - MSR
>>>>**Disaggregation**: "Totals only"
>>>>**Selected items**: select all (->>)
>>>
>>>**Filter**: "Relative periods"  
>>>>**Organisation unit**: "User organisation unit"  
>>>>**YOUR DIMENIONS**
>>>>>**Name**: "Monthly stock report - Data recording"  
>>>>>**Selected Items**: "Stock receipt"  
>
>**MSR DV 2 - Monthly Stock Reporting / Stock distribution / Last 12 months / Health facility / Pivot table**  
>This report provides the monthly stock distributions as reported at the end of every month.  
>
>**Name \(*)**: "MSR DV 2 - Monthly Stock Reporting / Stock distribution / Last 12 months / Health facility / Pivot table"  
>>**Columns**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 months"  
>>
>>**Rows**  
>>>**Data**  
>>>>**Data Type**: "Data elements"  
>>>>**Data element group**: select "[Stock item list] - MSR
>>>>**Disaggregation**: "Totals only"
>>>>**Selected items**: select all (->>)
>>>
>>>**Filter**: "Relative periods"  
>>>>**Organisation unit**: "User organisation unit"  
>>>>>**Selected Periods**: "Last 12 months"  
>>>>**YOUR DIMENIONS**
>>>>>**Name**: "Monthly stock report - Data recording"  
>>>>>**Selected Items**: "Stock distribution"  
>
>**MSR DV 3 - Monthly Stock Reporting / Stock redistribution / Last 12 months / Health facility / Pivot table**  
>This report provides the monthly stock distributions as reported at the end of every month.
>
>**Name \(*)**: "MSR DV 1 - Monthly Stock Reporting / Stock redistributions / Last 12 months / Health facility / Pivot table"  
>>**Columns**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 months"  
>>
>>**Rows**  
>>>**Data**  
>>>>**Data Type**: "Data elements"  
>>>>**Data element group**: select "[Stock item list] - MSR
>>>>**Disaggregation**: "Totals only"
>>>>**Selected items**: select all (->>)
>>>
>>>**Filter**: "Relative periods"  
>>>>**Organisation unit**: "User organisation unit"  
>>>>>**Selected Periods**: "Last 12 months"  
>>>>**YOUR DIMENIONS**
>>>>>**Name**: "Monthly stock report - Data recording"  
>>>>>**Selected Items**: "Stock redistribution"  
>
>**MSR DV 4 - Monthly Stock Reporting / Stock discard / Last 12 months / Health facility / Pivot table**  
>This report provides the monthly stock discards as reported at the end of every month.
>
>**Name \(*)**: "MSR DV 1 - Monthly Stock Reporting / Stock discard / Last 12 months / Health facility / Pivot table"  
>>**Columns**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 months"  
>>
>>**Rows**  
>>>**Data**  
>>>>**Data Type**: "Data elements"  
>>>>**Data element group**: select "[Stock item list] - MSR
>>>>**Disaggregation**: "Totals only"
>>>>**Selected items**: select all (->>)
>>>
>>>**Filter**: "Relative periods"  
>>>>**Organisation unit**: "User organisation unit"  
>>>>>**Selected Periods**: "Last 12 months"  
>>>>**YOUR DIMENIONS**
>>>>>**Name**: "Monthly stock report - Data recording"  
>>>>>**Selected Items**: "Stock discard"  
>
>**MSR DV 5 - Monthly Stock Reporting / Stock on hand / Last 12 months / Health facility / Pivot table**  
>This report provides the monthly stock on hand as reported at the end of every month.
>
>**Name \(*)**: "MSR DV 1 - Monthly Stock Reporting / Stock on hand / Last 12 months / Health facility / Pivot table"  
>>**Columns**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 months"  
>>
>>**Rows**  
>>>**Data**  
>>>>**Data Type**: "Data elements"  
>>>>**Data element group**: select "[Stock item list] - MSR
>>>>**Disaggregation**: "Totals only"
>>>>**Selected items**: select all (->>)
>>>
>>>**Filter**: "Relative periods"  
>>>>**Organisation unit**: "User organisation unit"  
>>>>>**Selected Periods**: "Last 12 months"  
>>>>**YOUR DIMENIONS**
>>>>>**Name**: "Monthly stock report - Data recording"  
>>>>>**Selected Items**: "Stock on hand"  
>
>**MSR DV 6 - Monthly Stock Reporting / Stock correction / Last 12 months / Health facility / Pivot table**  
>This report provides the monthly Stock correction as reported at the end of every month.
>
>**Name \(*)**: "MSR DV 1 - Monthly Stock Reporting / Stock correction / Last 12 months / Health facility / Pivot table"  
>>**Columns**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 months"  
>>
>>**Rows**  
>>>**Data**  
>>>>**Data Type**: "Data elements"  
>>>>**Data element group**: select "[Stock item list] - MSR
>>>>**Disaggregation**: "Totals only"
>>>>**Selected items**: select all (->>)
>>>
>>>**Filter**: "Relative periods"  
>>>>**Organisation unit**: "User organisation unit"  
>>>>>**Selected Periods**: "Last 12 months"  
>>>>**YOUR DIMENIONS**
>>>>>**Name**: "Monthly stock report - Data recording"  
>>>>>**Selected Items**: "Stock correction"  
>
>**MSR DV 7 - Monthly Stock Reporting / Stock report complete / Last month / Health facility / Pivot table**  
>This report provides the an overview of all stock data from the previous month.
>
>**Name \(*)**: "MSR DV 1 - Monthly Stock Reporting / Stock report complete / Last month / Health facility / Pivot table"  
>>**Columns**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last month"  
>>
>>**Rows**  
>>>**Data**  
>>>>**Data Type**: "Data elements"  
>>>>**Data element group**: select "[Stock item list] - MSR
>>>>**Disaggregation**: "Totals only"
>>>>**Selected items**: select all (->>)
>>>
>>>**Filter**: "Relative periods"  
>>>>**Organisation unit**: "User organisation unit"  
>>>>>**Selected Periods**: "Last 12 months"  
>>>>**YOUR DIMENIONS**
>>>>>**Name**: "Monthly stock report - Data recording"  
>>>>>**Selected Items**: "Stock distribution"  
>
>**MSR DV 8 - Monthly Stock Reporting / Stock report complete / Last 12 month / Individual item / Health facility / Pivot table**  
>This report provides the an overview of all stock data from the previous 12 months for an individual item.
>
>**Name \(*)**: "MSR DV 8 - Monthly Stock Reporting / Stock report complete / Last 12 month / Individual item / Health facility / Pivot table"  
>>**Columns**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 month"  
>>
>>**Rows**  
>>>>**YOUR DIMENIONS**
>>>>>**Name**: "Monthly stock report - Data recording"  
>>>>>**Selected Items**:
>>>>>- "Stock receipt"  
>>>>>- "Stock distribution"  
>>>>>- "Stock redistribution"  
>>>>>- "Stock discard"  
>>>>>- "Stock on hand"  
>>>>>- "Stock correction"  
>>>
>>>**Filter**
>>>>**Organisation unit**: "User organisation unit"  
>>>>**Data**  
>>>>>**Data Type**: "Data elements"  
>>>>>**Selected items**: select the item of interest
>
>**MSR DV 9 - Monthly Stock Reporting / Stock report complete / Last 12 month / Individual item / Health facility / Column chart**  
>This report provides the an overview of all stock data from the previous 12 months for an individual item as a column chart with every transaction type presented as a separate column.
>
>**Name \(*)**: "MSR DV 9 - Monthly Stock Reporting / Stock report complete / Last 12 month / Individual item / Health facility / Column chart"  
>>**Series**  
>>>**YOUR DIMENIONS**
>>>>**Name**: "Monthly stock report - Data recording"  
>>>>**Selected Items**:
>>>>- "Stock receipt"  
>>>>- "Stock distribution"  
>>>>- "Stock redistribution"  
>>>>- "Stock discard"  
>>>>- "Stock on hand"  
>>>>- "Stock correction"  
>>>**Category**  
>>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 month"  
>>
>>>**Filter**
>>>>**Organisation unit**: "User organisation unit"  
>>>>**Data**  
>>>>>**Data Type**: "Data elements"  
>>>>>**Selected items**: select the item of interest







Naming convention for Visualizations:
- Acronym
- Acronym for visualization type (DV = Data Visualizer etc.)
- Number of visualization
- DHIS2-MSR 

xxx to be deleted xxx
>>LMIS Statistics  
>>>Item level statistics  
>>>>Monthly reporting  
>>>>>Stock on hand  
>>>>>Stock distribution ("consumption")  
>>>>  
>>>>Real-Time Stock management reporting   
>>>>>Transaction report  
>>>
>>>Health facility level aggregations  
>>>>Number of stock items  
>>>>Number of monthly reports submitted  
>>>
>>>District level aggregations
>>>>Stock on hand
>>>>Stock distributions
>>>>Number of health facilities  
>>>>Number of stock items by health facility
>>>>Number of monthly reports submitted  
>>>
>>>Provincial level aggregations  
>>>>Stock on hand
>>>>Stock distributions
>>>>Number of health facilities  
>>>>Number of stock items
>>>>Number of monthly reports submitted  
>>>LMIS Country level aggregations  
>>>>Number of health facilities  
>>>>Number of stock items
>>>>Number of monthly reports submitted  
>>
>>LMIS Indicators  
>>>Health facility level indicators  
>>>>Item level indicators  
>>>>>Stockout occurrence (by month)  
>>>>>Stockout count / absolute(number of months with stockouts)  
>>>>>Stockout count / monthly average  
>>>>>Stock coverage time / absolute number  
>>>>>Stock coverage time / range/category  
>>>>>Stock discrepancy  
>>>>>Average monthly demand  
>>>>>Coefficient of variation of monthly demand  
>>>>>Stock discrepancy count  
>>>>Health facility level aggregations  
>>>>>Number of items with complete reports  
>>>>>Number of monthly reports submitted before due data  
>>>
>>>Health facility level aggregations (across items) - indicators
>>>>Stockout count / monthly  
>>>>Stockout duration distribution  
>>>>Stock availability  
>>>>Stock coverage time range/category distributions  
>>>>Reporting rates  
>>>>Stock discrepancy count  
>>>
>>>LMIS District level aggregations
>>>>Stockout count / month  
>>>>Stockout duration distribution  
>>>>Stock availability distribution  
>>>>Stock coverage time range/category distribution  
>>>>Reporting rates distribution  
>>>>Stock discrepancy count  
>>>
>>>LMIS Provincial level aggregations  
>>>>Stockout count / month  
>>>>Stockout duration distribution  
>>>>Stock availability distribution  
>>>>Stock coverage time range/category distribution  
>>>>Reporting rates distribution  
>>>>Stock discrepancy count  
>>>
>>>LMIS National level aggregations  
>>>>Stockout count / month  
>>>>Stockout duration distribution  
>>>>Stock availability distribution  
>>>>Stock coverage time range/category distribution  
>>>>Reporting rates distribution  
>>>>Stock discrepancy count  


xxx
| Visualization  | Abbr. | Pivot table | Column | Bar | Line | Pie | Gauge | Single value | Line Listing | Map |
| :-------- | :---: | :---: | :---: | :---: | :---:| :---: | :---: | :---: | :---: | :---:|
| **STATISTICS** |
| **Item level statistics** |
| Stock on hand | X | X | X | X | X | X | X | X | X | X |
| Stock distribution | X | X | X | X | X | X | X | X | X | X |
| Transaction report | X | X | X | X | X | X | X | X | X | X |
| **Health facility level aggregation** |
| Number of stock items | X | X | X | X | X | X | X | X | X | X |
| Number of monthly reports submitted | X | X | X | X | X | X | X | X | X | X |
| **District level aggregation** |
| Stock on hand | X | X | X | X | X | X | X | X | X | X |
| Stock distributions | X | X | X | X | X | X | X | X | X | X |
| Number of health facilities | X | X | X | X | X | X | X | X | X | X |
| Number of stock items by health facility | X | X | X | X | X | X | X | X | X | X |
| Number of monthly reports submitted | X | X | X | X | X | X | X | X | X | X |
| **Province level aggregation** |
| Stock on hand | X | X | X | X | X | X | X | X | X | X |
| Stock distributions | X | X | X | X | X | X | X | X | X | X |
| Number of health facilities | X | X | X | X | X | X | X | X | X | X |
| Number of stock items by health facility | X | X | X | X | X | X | X | X | X | X |
| Number of monthly reports submitted | X | X | X | X | X | X | X | X | X | X |
| **National level aggregation** |
| Stock on hand | X | X | X | X | X | X | X | X | X | X |
| Stock distributions | X | X | X | X | X | X | X | X | X | X |
| Number of health facilities | X | X | X | X | X | X | X | X | X | X |
| Number of stock items by health facility | X | X | X | X | X | X | X | X | X | X |
| Number of monthly reports submitted | X | X | X | X | X | X | X | X | X | X |

| Visualization  | Abbr. | Pivot table | Column | Bar | Line | Pie | Gauge | Single value | Line Listing | Map |
| :--- | :---: | :---: | :---: | :---: | :---:| :---: | :---: | :---: | :---: | :---:|
| **INDICATORS** | |  |  |  |  |  |  |  |  |  |
| **Item level indicators** | |  |  |  |  |  |  |  |  |  |
| Stockout occurrence (by month) | X | X | X | X | X | X | X | X | X | X |
| Stockout count / absolute(number of months with stockouts) | X | X | X | X | X | X | X | X | X | X |
| Stockout count / monthly average | X | X | X | X | X | X | X | X | X | X |
| Stock coverage time / absolute number | X | X | X | X | X | X | X | X | X | X |
| Stock coverage time / range/category | X | X | X | X | X | X | X | X | X | X |
| Stock discrepancy | X | X | X | X | X | X | X | X | X | X |
| Average monthly demand | X | X | X | X | X | X | X | X | X | X |
| Coefficient of variation of monthly demand | X | X | X | X | X | X | X | X | X | X |
| Stock discrepancy count | X | X | X | X | X | X | X | X | X | X |
| Health facility level aggregations | X | X | X | X | X | X | X | X | X | X |
| Number of items with complete reports | X | X | X | X | X | X | X | X | X | X |
| **Health facility level aggregations (across items) - indicators** | |  |  |  |  |  |  |  |  |  |
| Stockout count / monthly | |  |  |  |  |  |  |  |  |  |
| Stockout duration distribution | |  |  |  |  |  |  |  |  |  |
| Stock availability | |  |  |  |  |  |  |  |  |  |
| Stock coverage time range/category distributions | |  |  |  |  |  |  |  |  |  |
| Reporting rates | |  |  |  |  |  |  |  |  |  |
| Stock discrepancy count | |  |  |  |  |  |  |  |  |  |
| **District level  aggregations - indicators** | |  |  |  |  |  |  |  |  |  |
| Stockout count / monthly | |  |  |  |  |  |  |  |  |  |
| Stockout duration distribution | |  |  |  |  |  |  |  |  |  |
| Stock availability | |  |  |  |  |  |  |  |  |  |
| Stock coverage time range/category distributions | |  |  |  |  |  |  |  |  |  |
| Reporting rates | |  |  |  |  |  |  |  |  |  |
| Stock discrepancy count | |  |  |  |  |  |  |  |  |  |
| **Provincial level  aggregations - indicators** | |  |  |  |  |  |  |  |  |  |
| Stockout count / monthly | |  |  |  |  |  |  |  |  |  |
| Stockout duration distribution | |  |  |  |  |  |  |  |  |  |
| Stock availability | |  |  |  |  |  |  |  |  |  |
| Stock coverage time range/category distributions | |  |  |  |  |  |  |  |  |  |
| Reporting rates | |  |  |  |  |  |  |  |  |  |
| Stock discrepancy count | |  |  |  |  |  |  |  |  |  |
| **National level  aggregations - indicators** | |  |  |  |  |  |  |  |  |  |
| Stockout count / monthly | |  |  |  |  |  |  |  |  |  |
| Stockout duration distribution | |  |  |  |  |  |  |  |  |  |
| Stock availability | |  |  |  |  |  |  |  |  |  |
| Stock coverage time range/category distributions | |  |  |  |  |  |  |  |  |  |
| Reporting rates | |  |  |  |  |  |  |  |  |  |
| Stock discrepancy count | |  |  |  |  |  |  |  |  |  |



