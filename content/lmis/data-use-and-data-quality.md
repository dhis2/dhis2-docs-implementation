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
>>>>- MSR DV 1 - Monthly Stock Reporting / Stock receipt / Last 12 months / Health facility / By item / Pivot table
>>>>- MSR DV 2 - Monthly Stock Reporting / Stock distribution / Last 12 months / Health facility / By item / Pivot table  
>>>>- MSR DV 3 - Monthly Stock Reporting / Stock redistribution / Last 12 months / Health facility / By item / Pivot table  
>>>>- MSR DV 4 - Monthly Stock Reporting / Stock discard / Last 12 months / Health facility / By item / Pivot table  
>>>>- MSR DV 5 - Monthly Stock Reporting / Stock on hand / Last 12 months / Health facility / By item / Pivot table  
>>>>- MSR DV 6 - Monthly Stock Reporting / Stock correction / Last 12 months / Health facility / By item / Pivot table  
>>>>- MSR DV 7 - Monthly Stock Reporting / Stock report complete / Last 3 month / Health facility / By item / Pivot table  
>>>>- MSR DV 8 - Monthly Stock Reporting / Stock report complete / Last 12 month / Health facility / By item / Pivot table
>>>>- MSR DV 9 - Monthly Stock Reporting / Stock report complete / Last 12 month / Health facility / Individual item / Column chart
>>>
>>>**1.1.2 Indicators**  
>>>>- MSR DV 10 - Monthly Stock Reporting / Stock distribution / Coefficient of Variation x10 / Last 12 months / Health facility / By item / Pivot table  
>>>>- MSR DV 11 - Monthly Stock Reporting / Stock distribution / Coefficient of Variation x 10 / Last 12 months / Health facility / Across items / Stacked bar chart  
>>>>- MSR DV 12 - Monthly Stock Reporting / Stock distribution / Coefficient of Variation x 10 / Last 12 months / Health facility / By item / Bar chart
>>>>- MSR DV 13 - Monthly Stock Reporting / Stock availability / Last 12 months / Health facility / By item / Pivot table  
>>>>- MSR DV 14 - Monthly Stock Reporting / Stock availability / Last 12 months / Health facility / Across items / Bar chart  
<br>
>>>>- MSR DV 15 - Monthly Stock Reporting / Stock availability / Last month / Health facility / Across items/ Single value chart  
>>>>- MSR DV 16 - Monthly Stock Reporting / Stock availability / Last month / Health facility / Across items / Gauge chart  
>>>>- MSR DV 17 - Monthly Stock Reporting / Stockout by item / Last 12 months / Health facility / By item / Stacked column chart  
>>>>- MSR DV 18 - Monthly Stock Reporting / Stockout count / Last 12 months / Health facility / By item / Pivot table  
>>>>- MSR DV 19 - Monthly Stock Reporting / Stockout count / Last 12 months / Health facility / Across items / Column chart  
>>>>- MSR DV 20 - Monthly Stock Reporting / Stockout count / Last month / Health facility / Across items / Single value chart  
>>>>- MSR DV 21 - Monthly Stock Reporting / Stockout length / Last 12 months / Health facility / By item / Pivot table  
>>>>- MSR DV 22 - Monthly Stock Reporting / Stockout length / Last 12 months / Health facility / Across items / Bar chart  
>>>>- MSR DV 23 - Monthly Stock Reporting / Stock coverage time / absolute / Last 12 months / Health facility / By item / Pivot table  
>>>>- MSR DV 24 - Monthly Stock Reporting / Stock coverage time / distribution / Last 12 month / Health facility / By item / Pivot table  
>>>>- MSR DV 25 - Monthly Stock Reporting / Stock coverage time / distribution / Last 12 month / Health facility / Across items / Column chart  
>>>>- MSR DV 26 - Monthly Stock Reporting / Stock coverage time / distribution / Last month / Health facility / Across items / Column chart  
>>>>- MSR DV 27 - Monthly Stock Reporting / Stock discrepancy / list / Last 12 months / Health facility / By item / Pivot table  
>>>>- MSR DV 28 - Monthly Stock Reporting / Stock discrepancy / count / Last 12 months / Health facility / Across items / Column chart  
>>
>>**1.2 District level**  
>>>**1.2.1 Statistics**  
>>>**1.2.2 Indicators**  
>>
XXX
For District / Regional / National (makes no sense for facility)
>>>>- MSR DV 21 - Monthly Stock Reporting / Stockout count / Last 12 months / Health facility / Map  
>>>>- MSR DV 17 - Monthly Stock Reporting / Stock availability / Last months / Health facility / Map

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
Pivot table: ok
Column: ok
Stacked column: ok
Bar: 
Stacked bar: 
Line
Pie
Gauge
Single value: ok
Line Listing
Map: ok
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

>**MSR DV 1 - Monthly Stock Reporting / Stock receipt / Last 12 months / Health facility / By item / Pivot table**  
>This report provides the monthly stock receipts as reported at the end of every month.  
>
>**Visualization type**: select "Pivot table"
>**Name \(*)**: "MSR DV 1 - Monthly Stock Reporting / Stock distribution / Last 12 months / Health facility / By item / Pivot table"  
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
>>>>>**Name**: "Monthly stock report"  
>>>>>**Selected Items**: "Stock receipt"  
>
>**MSR DV 2 - Monthly Stock Reporting / Stock distribution / Last 12 months / Health facility / By item / Pivot table**  
>This report provides the monthly stock distributions as reported at the end of every month.  
>
>**Visualization type**: select "Pivot table"
>**Name \(*)**: "MSR DV 2 - Monthly Stock Reporting / Stock distribution / Last 12 months / Health facility / By item / Pivot table"  
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
>>
>>**Filter**: "Relative periods"  
>>>**Organisation unit**: "User organisation unit"  
>>>>**Selected Periods**: "Last 12 months"  
>>>**YOUR DIMENIONS**
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stock distribution"  
>
>**MSR DV 3 - Monthly Stock Reporting / Stock redistribution / Last 12 months / Health facility / By item / Pivot table**  
>This report provides the monthly stock redistributions as reported at the end of every month.
>
>**Visualization type**: select "Pivot table"
>**Name \(*)**: "MSR DV 1 - Monthly Stock Reporting / Stock redistributions / Last 12 months / Health facility / By item / Pivot table"  
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
>>**Filter**: "Relative periods"  
>>>**Organisation unit**: "User organisation unit"  
>>>>**Selected Periods**: "Last 12 months"  
>>>**YOUR DIMENIONS**
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stock redistribution"  
>
>**MSR DV 4 - Monthly Stock Reporting / Stock discard / Last 12 months / Health facility / By item / Pivot table**  
>This report provides the monthly stock discards as reported at the end of every month.
>
>**Visualization type**: select "Pivot table"
>**Name \(*)**: "MSR DV 1 - Monthly Stock Reporting / Stock discard / Last 12 months / Health facility / By item / Pivot table"  
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
>>**Filter**: "Relative periods"  
>>>**Organisation unit**: "User organisation unit"  
>>>>**Selected Periods**: "Last 12 months"  
>>>**YOUR DIMENIONS**
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stock discard"  
>
>**MSR DV 5 - Monthly Stock Reporting / Stock on hand / Last 12 months / Health facility / By item / Pivot table**  
>This report provides the monthly stock on hand as reported at the end of every month.
>
>**Visualization type**: select "Pivot table"
>**Name \(*)**: "MSR DV 1 - Monthly Stock Reporting / Stock on hand / Last 12 months / Health facility / By item / Pivot table"  
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
>>**Filter**: "Relative periods"  
>>>**Organisation unit**: "User organisation unit"  
>>>>**Selected Periods**: "Last 12 months"  
>>>**YOUR DIMENIONS**
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stock on hand"  
>
>**MSR DV 6 - Monthly Stock Reporting / Stock correction / Last 12 months / Health facility / By item / Pivot table**  
>This report provides the monthly stock corrections as reported at the end of every month.
>
>**Visualization type**: select "Pivot table"
>**Name \(*)**: "MSR DV 1 - Monthly Stock Reporting / Stock correction / Last 12 months / Health facility / By item / Pivot table"  
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
>>**Filter**: "Relative periods"  
>>>**Organisation unit**: "User organisation unit"  
>>>>**Selected Periods**: "Last 12 months"  
>>>**YOUR DIMENIONS**
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stock correction"  
>
>**MSR DV 7 - Monthly Stock Reporting / Stock report complete / Last 3 month / Health facility / By item / Pivot table**  
>This report provides an overview of all stock data from the last month.
>
>**Visualization type**: select "Pivot table"
>**Name \(*)**: "MSR DV 1 - Monthly Stock Reporting / Stock report complete / Last 3 months / Health facility / By item / Pivot table"  
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
>>**Filter**: "Relative periods"  
>>>**Organisation unit**: "User organisation unit"  
>>>>**Selected Periods**: "Last 12 months"  
>>>**YOUR DIMENIONS**
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stock distribution"  
>
>**MSR DV 8 - Monthly Stock Reporting / Stock report complete / Last 12 month / Health facility / By item / Pivot table**  
>This report provides the an overview of all stock data from the previous 12 months.
>
>**Visualization type**: select "Pivot table"
>**Name \(*)**: "MSR DV 8 - Monthly Stock Reporting / Stock report complete / Last 12 month / Health facility / By item / Pivot table"  
>>**Columns**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 month"  
>>
>>**Rows**  
>>>>>**Selected Items**:
>>>>>- "Stock receipt"  
>>>>>- "Stock distribution"  
>>>>>- "Stock redistribution"  
>>>>>- "Stock discard"  
>>>>>- "Stock on hand"  
>>>>>- "Stock correction"  
>>>>**YOUR DIMENIONS**
>>>>>**Name**: "Monthly stock report"  
>>
>>>**Filter**
>>>**Organisation unit**: "User organisation unit"  
>>>**Data**  
>>>>**Data Type**: "Data elements"  
>>>>**Selected items**: select the item of interest
>
>**MSR DV 9 - Monthly Stock Reporting / Stock report complete / Last 12 month / Health facility / Individual item / Column chart**  
>This report provides an overview of all stock data from the past 12 months represented as a bar chart for each of the transactions only for a single item.
>
>**Visualization type**: select "Pivot table"
>**Name \(*)**: **MSR DV 9 - Monthly Stock Reporting / Stock report complete / Last 12 month / Health facility / Individual item / Column chart**  
>>**Series**  
>>>**YOUR DIMENIONS**
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**:
>>>>- "Stock receipt"  
>>>>- "Stock distribution"  
>>>>- "Stock redistribution"  
>>>>- "Stock discard"  
>>>>- "Stock on hand"  
>>>>- "Stock correction"  
>>
>>**Category**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 month"  
>>>
>>**Filter**
>>>**Organisation unit**: "User organisation unit"  
>>>**Data**  
>>>>**Data Type**: "Data elements"  
>>>>**Selected items**: select one item of interest
>
>**MSR DV 10 - Monthly Stock Reporting / Stock distribution / Coefficient of Variation x 10 / Last 12 month / Health facility / By item / Pivot table**  
>This report provides the coefficient of variation (standard deviation of stock distribution divided by the average stock distribution) which is based on the previous six months for each of the twelve month as a Pivot table. Since decimals cannot be displayed in this report, the result of the actual calculation is multiplied by 10 and rounded to the next integer.
>
>**Visualization type**: select "Pivot table"
>**Name \(*)**: "MSR DV 10 - Monthly Stock Reporting / Stock distribution / Coefficient of Variation report / Last 12 month / Health facility / By item / Pivot table"  
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
>>
>>**Filter**: "Relative periods"  
>>>**Organisation unit**: "User organisation unit"  
>>>**YOUR DIMENIONS**
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Coefficient of variation"  
>>
>>**Options**  
>>>**Legend**  
>>>>**Use legend for chart colors**: tag (appears as a white tick in a green field)  
>>>>>**Legend type**
>>>>>>**Select a legend**: tag (appears as a white tick in a green field)  
>>>>>>**Legend**: "Coefficient of variation"
>>>>>**Show legend key** tag (appears as a white tick in a green field)  
>
>**MSR DV 11 - Monthly Stock Reporting / Stock distribution / Coefficient of Variation report / Last 12 month / Health facility / By item / Stacked bar chart**  
>This report provides the coefficient of variation (standard deviation of stock distribution divided by the average stock distribution) which is based on the previous six months for each of the twelve months for each item as a stacked bar chart where each stacked bar represents the values from the past 12 months. Since decimals cannot be displayed in this report the result of the actual calculation is multiplied by 10 and rounded to the next integer.
>
>**Visualization type**: select "Stacked bar"
>**Name \(*)**: "MSR DV 11 - Monthly Stock Reporting / Stock distribution / Coefficient of Variation report / Last 12 month / Health facility / By item / Stacked bar chart"  
>>**Series**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 months"  
>>
>>**Category**  
>>>**Data**  
>>>>**Data Type**: "Data elements"  
>>>>**Data element group**: select "[Stock item list] - MSR
>>>>**Disaggregation**: "Totals only"
>>>>**Selected items**: select all (->>)
>>
>>**Filter**: "Relative periods"  
>>>**Organisation unit**: "User organisation unit"  
>>>**YOUR DIMENIONS**
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Coefficient of variation"  
>>
>>**Options**    
>>>**Data**  
>>>>**Lines**  
>>>>>**Target line**  
>>>>>>**Value**: "10"
>>>>>>**Title**: "Medium variability"
>>>>>>**Size**: "Regular"
>>>>>>**Position**: "Left"
>>>>>>**Colour**: select red
>>>>>**Base line**  
>>>>>**Value**: "5"
>>>>>**Title**: "Low variability"
>>>>>**Size**: "Regular"
>>>>>>**Position**: "Left"
>>>>>>**Colour**: select green
>>>
>>>**Legend**  
>>>>**Use legend for chart colors**: tag (appears as a white tick in a green field)  
>>>>>**Legend type**
>>>>>>**Select a legend**: tag (appears as a white tick in a green field)  
>>>>>>**Legend**: "Coefficient of variation"
>>>>>>**Show legend key** tag (appears as a white tick in a green field)  
>
>**MSR DV 12 - Monthly Stock Reporting / Stock distribution / Coefficient of Variation x 10 / Last 12 month / Health facility / By item / Column chart**  
>This report provides the coefficient of variation (standard deviation of stock distribution divided by the average stock distribution) which is based on the previous six months as a group of column charts for each of the twelve months. Since decimals cannot be displayed in this report the result of the actual calculation is multiplied by 10 and rounded to the next integer.
>
>**Visualization type**: select "Bar"
>**Name \(*)**: "MSR DV 12 - Monthly Stock Reporting / Stock distribution / Coefficient of Variation x 10 / Last 12 month / Health facility / By item / Column chart"  
>>**Series**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 months"  
>>
>>**Category**  
>>>**Data**  
>>>>**Data Type**: "Data elements"  
>>>>**Data element group**: select "[Stock item list] - MSR
>>>>**Disaggregation**: "Totals only"
>>>>**Selected items**: select all (->>)
>>
>>**Filter**: "Relative periods"  
>>>**Organisation unit**: "User organisation unit"  
>>>**YOUR DIMENIONS**
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Coefficient of variation"  
>>
>>**Options**    
>>>**Data**  
>>>>**Lines**  
>>>>>**Target line**  
>>>>>>**Value**: "120"
>>>>>>**Title**: "Medium variability"
>>>>>>**Size**: "Regular"
>>>>>>**Position**: "Left"
>>>>>>**Colour**: select red
>>>>>**Base line**  
>>>>>>**Value**: "60"
>>>>>>**Title**: "Low variability"
>>>>>>**Size**: "Regular"
>>>>>>**Position**: "Left"
>>>>>>**Colour**: select green
>>>
>>>**Legend**  
>>>>**Use legend for chart colors**: tag (appears as a white tick in a green field)  
>>>>>**Legend type**
>>>>>>**Select a legend**: tag (appears as a white tick in a green field)  
>>>>>>**Legend**: "Coefficient of variation"
>>>>>**Show legend key** tag (appears as a white tick in a green field)  
>
>**MSR DV 13 - Monthly Stock Reporting / Stock availability / Last 12 months / Health facility / By item / Pivot table**  
>This report provides the stock availability across all stock items for an individual health facility over the last 12 months with a colour legend.
>
>**Visualization type**: select "Pivot table"
>**Name \(*)**: "MSR DV 13 - Monthly Stock Reporting / Stock availability / Last 12 months / Health facility / By item / Pivot table"
>>**Columns**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 months"  
>>
>>**Rows**  
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Filter**: "Relative periods"  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Selected items**: select "Stock availability / %"
>>>>
>>**Options**  
>>>**Legend**  
>>>>**Use legend for chart colors**: tag (appears as a white tick in a green field)  
>>>>>**Legend type**
>>>>>>**Select a legend**: tag (appears as a white tick in a green field)  
>>>>>>**Legend**: "Stock availability / %"
>>>>>**Show legend key** tag (appears as a white tick in a green field)  
>
>**MSR DV 14 - Monthly Stock Reporting / Stock availability / Last 12 months / Health facility / Across items / Bar chart**  
>This report displays the stock availability (number of items with non-zero stock on hand divided by the total number of stock items) as percentage for the past 12 months as column charts with a legend.
>
>**Visualization type**: select "Bar"
>**Name \(*)**: "MSR DV 14 - Monthly Stock Reporting / Stock availability / Last 12 months / Health facility / Across items / Bar chart" 
>>**Series**  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Selected items**: select "Stock availability / %"
>>
>>**Category**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 months"  
>>
>>**Filter**: "Relative periods"  
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Options**    
>>>**Legend**  
>>>>**Use legend for chart colors**: tag (appears as a white tick in a green field)  
>>>>>**Legend type**
>>>>>>**Select a legend**: tag (appears as a white tick in a green field)  
>>>>>>**Legend**: "Stock availability / %"
>>>>>>**Show legend key** tag (appears as a white tick in a green field)  
>
>**MSR DV 15 - Monthly Stock Reporting / Stock availability / Last month / Health facility / Across items / Single value chart**  
>This report displays the stock availability (number of items with non-zero stock on hand divided by the total number of stock items) as percentage for the last month as a singel value chart with a legend.
>
>**Visualization type**: select "Single value"
>**Name \(*)**: "MSR DV 15 - Monthly Stock Reporting / Stock availability / Last month / Health facility / Across items / Single value chart"  
>>**Series**  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Selected items**: select "Stock availability / %"
>>
>>**Filter**: "Relative periods"  
>>>**Organisation unit**: "User organisation unit"  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last month"  
>>
>>**Options**    
>>>**Legend**  
>>>>**Use legend for chart colors**: tag (appears as a white tick in a green field)  
>>>>>**Legend style**
>>>>>>**Legend changes background color**: tag (appears as a white tick in a green field)  
>>>>>**Legend type**
>>>>>>**Select a legend**: tag (appears as a white tick in a green field)  
>>>>>>**Legend**: "Stock availability / %"
>>>>>>**Show legend key** tag (appears as a white tick in a green field)  
>
>**MSR DV 16 - Monthly Stock Reporting / Stock availability / Last month / Health facility / Across items / Gauge chart**  
>This report displays the stock availability (number of items with non-zero stock on hand divided by the total number of stock items) as percentage for the last month as a gauge  chart with a legend.
>
>**Visualization type**: select "Gauge"
>**Name \(*)**: "MSR DV 16 - Monthly Stock Reporting / Stock availability / Last month / Health facility / Across items / Gauge chart"  
>>**Series**  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Selected items**: select "Stock availability / %"
>>
>>**Filter**: "Relative periods"  
>>>**Organisation unit**: "User organisation unit"  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last month"  
>>
>>**Options**    
>>>**Legend**  
>>>>**Use legend for chart colors**: tag (appears as a white tick in a green field)  
>>>>>**Legend style**
>>>>>>**Legend changes background color**: tag (appears as a white tick in a green field)  
>>>>>**Legend type**
>>>>>>**Select a legend**: tag (appears as a white tick in a green field)  
>>>>>>**Legend**: "Stock availability / %"
>>>>>>**Show legend key** tag (appears as a white tick in a green field)  
>
>**MSR DV 17 - Monthly Stock Reporting / Stockout by item / Last 12 months / Health facility / By item / Stacked column chart**  
>For each of the last 12 months, this report displays a separate stacked column chart with all items which had a stockout.
>
>**Visualization type**: select "Stacked column"  
>**Name \(*)**: "MSR DV 17 - Monthly Stock Reporting / Stockout by item / Last 12 months / Health facility / By item / Stacked column chart"  
>>**Series** 
>>>**Data**  
>>>>**Data Type**: "Data elements"  
>>>>**Data element group**: select "[Stock item list] - MSR
>>>>**Disaggregation**: "Totals only"
>>>>**Selected items**: select all (->>)
>>
>>**Category**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 months"  
>>
>>**Filter**: "Relative periods"  
>>>**Organisation unit**: "User organisation unit"  
>>>**YOUR DIMENIONS**
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stockout Yes/No"  
>
>**MSR DV 18 - Monthly Stock Reporting / Stockout count / Last 12 months / Health facility / Across items / Pivot table**  
>This report displays the number of stockouts for all items across a health facility for each of the past 12 months as a Pivot table.
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR DV 18 - Monthly Stock Reporting / Stockout count / Last 12 months / Health facility / Across items / Pivot table"  
>>**Columns** 
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 months"  
>>
>>**Filter**  
>>>**Organisation unit**: "User organisation unit"  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Indicator group**: select "Stockout count"
>>>>**Selected items**: select "Stockout count"
>
>**MSR DV 19 - Monthly Stock Reporting / Stockout count / Last 12 months / Health facility / Across items / Column chart**  
>This report displays the number of stockouts for each of the past 12 months as a column chart.
>
>**Visualization type**: select "Column"  
>**Name \(*)**: "MSR DV 20 - Monthly Stock Reporting / Stockout count / Last 12 months / Health facility / Across items / Column chart"  
>>**Series** 
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 months"  
>>
>>**Category**  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Indicator group**: select "Stockout count"
>>>>**Selected items**: select "Stockout count"
>>
>>**Filter**  
>>>**Organisation unit**: "User organisation unit"  
>
>**MSR DV 20 - Monthly Stock Reporting / Stockout count / Last month / Health facility / Across items / Single value chart**  
>This report displays the number of stockouts during the last month as a single value chart.
>
>**Visualization type**: select "Single value"
>**Name \(*)**: "MSR DV 15 - Monthly Stock Reporting / Stock availability / Last month / Health facility / Across items / Single value chart"  
>>**Series**  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Selected items**: select "Stockout count"
>>
>>**Filter**: "Relative periods"  
>>>**Organisation unit**: "User organisation unit"  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last month"  
>
>**MSR DV 21 - Monthly Stock Reporting / Stockout length / Last 12 months / Health facility / Pivot table**  
>This report displays a Pivot table by item with a "1" indicating a stockout (and "0" indicating stock was available) with a total for the past 12 months.
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR DV 21 - Monthly Stock Reporting / Stockout length / Last 12 months / Health facility / By item / Pivot table"  
>>**Columns** 
>>>**YOUR DIMENIONS**
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stockout Yes/No"  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 month"  
>>
>>**Rows**  
>>>**Data**  
>>>>**Data Type**: "Data elements"  
>>>>**Data element group**: select "[Stock item list] - MSR
>>>>**Disaggregation**: "Totals only"
>>>>**Selected items**: select all (->>)
>>
>>**Filter**  
>>>**Organisation unit**: "User organisation unit"  
>
>**MSR DV 22 - Monthly Stock Reporting / Stockout length / Last 12 months / Health facility / By item / Bar chart**  
>This report displays a bar chart with the number of stockouts for each item during the past 12 months.
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR DV 22 - Monthly Stock Reporting / Stockout length / Last 12 months / Health facility / By item / Bar chart"  
>>**Series** 
>>>**YOUR DIMENIONS**
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stockout Yes/No"  
>>
>>**Category**  
>>>**Data**  
>>>>**Data Type**: "Data elements"  
>>>>**Data element group**: select "[Stock item list] - MSR
>>>>**Disaggregation**: "Totals only"
>>>>**Selected items**: select all (->>)
>>
>>**Filter**  
>>>**Organisation unit**: "User organisation unit"  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 month"  
>
>**MSR DV 23 - Monthly Stock Reporting / Stock coverage time / absolute / Last 12 months / Health facility / By item / Pivot table**  
>This report displays a Pivot table by item with the coverage time (stock on hand divided by stock distributed during the last month) for the past 12 months. A blank field is shown, if either the stock on hand or the stock distribution for a month is zero.
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR DV 23 - Monthly Stock Reporting / Stock coverage time / absolute / Last 12 months / Health facility / By item / Pivot table"  
>>**Columns** 
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 month"  
>>
>>**Rows**  
>>>**Data**  
>>>>**Data Type**: "Data elements"  
>>>>**Data element group**: select "[Stock item list] - MSR
>>>>**Disaggregation**: "Totals only"
>>>>**Selected items**: select all (->>)
>>
>>**Filter**  
>>>**Organisation unit**: "User organisation unit"  
>>>**YOUR DIMENIONS**
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stockout coverage"  
>
>**MSR DV 24 - Monthly Stock Reporting / Stock coverage time / distribution / Last 12 months / Health facility / Across items / Pivot table**  
>This report displays a Pivot table  with the number of items for which the coverage time fell into the respective coverage time bins (stockout, 1 to 12 months, 1-2 and 2-3 years or greater than or equal to 3 years) for each of the past 12 months.
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR DV 24 - Monthly Stock Reporting / Stock coverage time / distribution / Last month / Health facility / Across items / Pivot table"  
>>**Columns** 
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Data element group**: select "Stock coverage time"
>>>>**Selected items**: select the following indicators in the following order:
>>>>-  "Stockout count" 
>>>>-  "0-1 months" 
>>>>-  "1-2 months" 
>>>>-  "2-3 months" 
>>>>-  "3-4 months" 
>>>>-  "4-5 months" 
>>>>-  "5-6 months" 
>>>>-  "6-7 months" 
>>>>-  "7-8 months" 
>>>>-  "8-9 months" 
>>>>-  "9-10 months" 
>>>>-  "10-11 months" 
>>>>-  "11-12 months" 
>>>>-  "1-2 years" 
>>>>-  "2-3 years" 
>>>>-  ">=3 years" 
>>
>>**Rows**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 month"  
>>
>>**Filter**  
>>>**Organisation unit**: "User organisation unit"  
>>>**YOUR DIMENIONS**
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stockout coverage"  
>
>**MSR DV 25 - Monthly Stock Reporting / Stock coverage time / distribution / Last 12 month / Health facility / Across items / Column chart**  
>This report displays a group of column charts representing the number of items for each stock coverage time bin (in months and years) for the past 12 months.
>
>**Visualization type**: select "Column"  
>**Name \(*)**: "MSR DV 25 - Monthly Stock Reporting / Stock coverage time / distribution / Last 12 month / Health facility / Across items / Column chart"  
>>**Series** 
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Data element group**: select "Stock coverage time"
>>>>**Selected items**: select the following indicators in the following order:
>>>>-  "Stockout count" 
>>>>-  "0-1 months" 
>>>>-  "1-2 months" 
>>>>-  "2-3 months" 
>>>>-  "3-4 months" 
>>>>-  "4-5 months" 
>>>>-  "5-6 months" 
>>>>-  "6-7 months" 
>>>>-  "7-8 months" 
>>>>-  "8-9 months" 
>>>>-  "9-10 months" 
>>>>-  "10-11 months" 
>>>>-  "11-12 months" 
>>>>-  "1-2 years" 
>>>>-  "2-3 years" 
>>>>-  ">=3 years" 
>>
>>**Category**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 month"  
>>
>>**Filter**  
>>>**Organisation unit**: "User organisation unit"  
>
>>**MSR DV 26 - Monthly Stock Reporting / Stock coverage time / distribution / Last / Health facility / Across items / Column chart**  
>This report displays a group of column charts representing the stock coverage time distribution (in months and years) for the last month.
>
>**Visualization type**: select "Column"  
>**Name \(*)**: "MSR DV 24 - Monthly Stock Reporting / Stock coverage time / distribution / Last month / Health facility / Across items / Pivot table"  
>>**Series** 
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Data element group**: select "Stock coverage time"
>>>>**Selected items**: select the following indicators in the following order:
>>>>-  "Stockout count" 
>>>>-  "0-1 months" 
>>>>-  "1-2 months" 
>>>>-  "2-3 months" 
>>>>-  "3-4 months" 
>>>>-  "4-5 months" 
>>>>-  "5-6 months" 
>>>>-  "6-7 months" 
>>>>-  "7-8 months" 
>>>>-  "8-9 months" 
>>>>-  "9-10 months" 
>>>>-  "10-11 months" 
>>>>-  "11-12 months" 
>>>>-  "1-2 years" 
>>>>-  "2-3 years" 
>>>>-  ">=3 years" 
>>
>>**Category**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last month"  
>>
>>**Filter**  
>>>**Organisation unit**: "User organisation unit"
>
>**MSR DV 27 - Monthly Stock Reporting / Stock discrepancy / list / Last 12 months / Health facility / By item / Pivot table**  
>This report displays a list with the positive and negative stock discrepancy of the past 12 months. The stock discrepancy is calculated as follows
> Stock on hand from the previous month (final stock on hand)  
> + Stock receipt  
> - Stock distributed  
> - Stock redistributed  
> - Stock discard  
> - Stock correction  
> - Stock on hand  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR DV 27 - Monthly Stock Reporting / Stock discrepancy / list / Last 12 months / Health facility / By item / Pivot table"  
>>**Columns** 
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 month"  
>>
>>**Rows** 
>>>**Data**  
>>>>**Data Type**: "Data elements"  
>>>>**Data element group**: select "[Stock item list] - MSR
>>>>**Disaggregation**: "Totals only"
>>>>**Selected items**: select all (->>)
>>
>>**Filter**  
>>>**Organisation unit**: "User organisation unit"  
>>>**YOUR DIMENIONS**
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stock discrepancy count"  
>  
>**MSR DV 28 - Monthly Stock Reporting / Stock discrepancy / count / Last 12 months / Health facility / Across items / Column chart**  
>This report displays the number of stock discrepancies for the past 12 months.
>
>**Visualization type**: select "Column"  
>**Name \(*)**: "MSR DV 28 - Monthly Stock Reporting / Stock discrepancy / count / Last 12 months / Health facility / Across items / Column chart"  
>>**Series** 
>>>**YOUR DIMENIONS**
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stock discrepancy count"  
>>  
>>**Category** 
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 month"  
>>
>>**Filter**  
>>>**Organisation unit**: "User organisation unit"  
>>>**Data**  
>>>>**Data Type**: "Data elements"  
>>>>**Data element group**: select "[Stock item list] - MSR
>>>>**Disaggregation**: "Totals only"
>>>>**Selected items**: select all (->>)


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



