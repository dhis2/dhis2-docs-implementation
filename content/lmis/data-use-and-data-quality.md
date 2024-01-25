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

>DHIS2 LMIS logistics analytics (MSR and RTS)
>
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

By default, all the visualizations above are shown as time series (by month/by day)

| Visualization  | Abbr. | Pivot table | Column | Bar | Line | Pie | Gauge | Single value | Line Listing | Map |
| :-------- | :---: | :---: | :---: | :---: | :---:| :---: | :---: | :---: | :---: | :---:|
| **STATISTICS** | |  |  |  |  |  |  |  |  |  |
| **Item level statistics** | |  |  |  |  |  |  |  |  |  |
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
| Stockout count / month | X | X | X | X | X | X | X | X | X | X |
| Stockout duration distribution | X | X | X | X | X | X | X | X | X | X |
| Stock availability distribution | X | X | X | X | X | X | X | X | X | X |
| Stock coverage time range/category distribution | X | X | X | X | X | X | X | X | X | X |
| Reporting rates distribution | X | X | X | X | X | X | X | X | X | X |
| Stock discrepancy count | X | X | X | X | X | X | X | X | X | X |
| **National level aggregation** |
| Stockout count / month | X | X | X | X | X | X | X | X | X | X |
| Stockout duration distribution | X | X | X | X | X | X | X | X | X | X |
| Stock availability distribution | X | X | X | X | X | X | X | X | X | X |
| Stock coverage time range/category distribution | X | X | X | X | X | X | X | X | X | X |
| Reporting rates distribution | X | X | X | X | X | X | X | X | X | X |
| Stock discrepancy count | X | X | X | X | X | X | X | X | X | X |

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

  
  
  





xxx
For each metric:
- Definition
- Calculation
- Target ranges
- Interpretation
- Corrective action (include details here and only a summary in the performance management chapter?)
- Visualization options




XXXXXXXXXXXX

## Introduction

This simple Tracker program allows building and digitally sharing a simple product catalogue with an image of each health care product as well as essential product information which health professionals can consult on a mobile device on- or offline. A centrally managed standard catalogue can be available to healthcare facilities or customized catalogues can be configured, for example for different levels of care.

## Use case

A health worker who requires information on what health care products are available at the respective healthcare facility in general or requires details on the product searches on- or offline in the product catalogue, views the image, consults the specifications and (where available) opens the link to more detailed information.

## Maintenance Web App - DHIS2 metadata configuration

The product catalogue is configured as a very simple "Tracker program" which uses only simple, native DHIS2 functionality but without any actual program "stages" and without allowing users to record any events.

### Metadata overview
The required metadata settings seetings are presented in the order in which it is presented in the DHIS2 Maintenance Web App.

>**1 PROGRAM**  
>>1.1 Program  
>>1.2 Tracked entity attribute  
>>1.3 Tracked entity type  

### 1 Program

#### 1.1 Program
>**1 Program details**
>>**Name \(*)**: "Health care product catalogue"  
>>**Short name (*)**: "Health care product catalogue"  
>>**Color**: "#F50057"  
>>**Icon**: "alert circle outline"  
>>**Version**: (automatically numbered by the system)
>>**Tracked entity type \(*)**: select "Healthcare product"  
>>**Category combination (*)**: select "None"  
>>**Display front page list**: tag (appears as a white tick in a blue square) 
>>**Access level**: "Open"  
>>**Completed events expiry days**: "0"  
>>**Expiry days**: "0"  
>>**Minimum number of attributes required to search**: "1"  
>>**Maximum number of treacked entity instances to return in search**: "0"  
>
>**2 Enrollment details**  
>>**Allow future enrollment dates**: do not tag  
>>**Allow future incident dates**: do not tag  
>>**Only enrol once (per tracked entity instance lifetime)**: do not tag  
>>**Show incident date**: tag (appears as a white tick in a blue square)   
>>**Description of incident date**: (blank)
>>**Ignore overdue events**: do not tag  
>>**Feature type**: (blank)
>>
>**3 Attributes**
>>**1 Assign attributes**
>>>**Program tracked entity attributes**: select and arrange in the following order:
>>>>"Item description"  
>>>>"Item code"  
>>>>"WHO EML classification description"  
>>>>"Item group code"  
>>>>"Item group description"  
>>>>"WHO EML classification number"  
>>>>"Secondary packaging quantity"  
>>>>"Required storage temperature / ° Celsis"  
>>>>"Electronic product information"  
>>>>"Item barcode image"  
>>>>"Product image"  
>>>**Display in list**: tag all  
>>>**Searchable**: tag all  
>>>**Mobile render type**: "Default" except for "Bar code" for "Item code"
>>>**Desktop render type**: "Default"
![](media/image11.png)
>>
>>**2 Create registration form**
>>>**Name**: "Healthcare product catalogue"
>>>**ADD SECTION TO FORM**: assign the following Tracked entity attributes in the following order:
>>>>"Item description"  
>>>>"Item code"  
>>>>"WHO EML classification description"  
>>>>"Item group code"  
>>>>"Item group description"  
>>>>"WHO EML classification number"  
>>>>"Secondary packaging quantity"  
>>>>"Required storage temperature / ° Celsis"  
>>>>"Regulations"  
>>>>"Electronic product information"  
>>>>"Item barcode image"  
>>>>"Product image"  
>
>**4 Program stages**
>>(leave blank)  
>
>**5 Access**
>>**Organisation units**: tag the health care facilities where the Tracker Program is used  
>>**Roles and access**: "Healthcare product catalogue" appears by default  
>>**SELECT ALL**: tag (a white tick appears in the blue square)
>
>**6 Notifications**
>(not applicable)

#### 1.2 Tracked entity attribute

>**1 Electronic product information**  
>>**Name \(*)**: "Electronic product information"  
>>**Short name (*)**: "Elctronic product information - HPC"  
>>**Value type**: "URL"  
>>**Aggregation type**: "None"  
>>**Unique**: do not tag
>>**Inherit**: do not tag
>
>**2 Item barcode image**  
>>**Name \(*)**: "Item barcode image"  
>>**Short name (*)**: "Item barcode image - HPC"  
>>**Value type**: "Image"  
>>**Aggregation type**: "None"  
>>**Unique**: do not tag
>>**Inherit**: do not tag
>
>**3 Item code**  
>>**Name \(*)**: "Item code"  
>>**Short name (*)**: "Item code - HPC"  
>>**Value type**: "Text"  
>>**Aggregation type**: "None"  
>>**Unique**: do not tag
>>**Inherit**: do not tag
>
>**4 Item description**  
>>**Name \(*)**: "Item description"  
>>**Short name (*)**: "Item description - HPC"  
>>**Value type**: "Text"  
>>**Aggregation type**: "None"  
>>**Unique**: do not tag
>>**Inherit**: do not tag
>
>**5 Item group code**  
>>**Name \(*)**: "Item group code"  
>>**Short name (*)**: "Item group code - HPC"  
>>**Value type**: "Text"  
>>**Aggregation type**: "None"  
>>**Unique**: do not tag
>>**Inherit**: do not tag
>
>**6 Item group description**  
>>**Name \(*)**: "Item group description"  
>>**Short name (*)**: "Item group description - HPC"  
>>**Value type**: "Text"  
>>**Aggregation type**: "None"  
>>**Unique**: do not tag
>>**Inherit**: do not tag
>
>**7 Product image**  
>>**Name \(*)**: "Product image"  
>>**Short name (*)**: "Product image - HPC"  
>>**Value type**: "Image"  
>>**Aggregation type**: "None"  
>>**Unique**: do not tag
>>**Inherit**: do not tag
>
>**8 Regulations**  
>>**Name \(*)**: "Regulations"  
>>**Short name (*)**: "Regulations - HPC"  
>>**Value type**: "Text"  
>>**Aggregation type**: "None"  
>>**Unique**: do not tag
>>**Inherit**: do not tag
>
>**9 Required storage temperature / ° Celsius**  
>>**Name \(*)**: "Required storage temperature / ° Celsius"  
>>**Short name (*)**: "Required storage temperature / ° Celsius - HPC"  
>>**Value type**: "Text"  
>>**Aggregation type**: "None"  
>>**Unique**: do not tag
>>**Inherit**: do not tag
>
>**10 Secondary packaging quantity**  
>>**Name \(*)**: "Secondary packaging quantity"  
>>**Short name (*)**: "Secondary packaging quantity - HPC"  
>>**Value type**: "Text"  
>>**Aggregation type**: "None"  
>>**Unique**: do not tag
>>**Inherit**: do not tag
>
>**11 WHO EML classification description**  
>>**Name \(*)**: "WHO EML classification description"  
>>**Short name (*)**: "WHO EML classification description - HPC"  
>>**Value type**: "Text"  
>>**Aggregation type**: "None"  
>>**Unique**: do not tag
>>**Inherit**: do not tag
>
>**12 WHO EML classification number**  
>>**Name \(*)**: "WHO EML classification number"  
>>**Short name (*)**: "WHO EML classification number - HPC"  
>>**Value type**: "Text"  
>>**Aggregation type**: "None"  
>>**Unique**: do not tag
>>**Inherit**: do not tag

#### 1.3 Tracked entity type
>**1 Health care product**:  
>>**Name \(*)**: "Health care product - HPB"  
>>**Enable tracked entity instance audit log**: do not tag
>>**Minimum number of attributes required to search**: 1  
>>**Maximum number of tracked entity instances to return in search**: 0  
>>**Feature type**: "None"  
>>**Tracked entity type attributes**: assign the following Tracked entity attributes in this order
>>>"Product image"  
>>>"Item description"  
>>>"Item code"  
>>>"WHO EML classification description"  
>>>"Item group code"  
>>>"Item group description"  
>>>"WHO EML classification number"  
>>>"Secondary packaging quantity"  
>>>"Required storage temperature / ° Celsis"  
>>>"Regulations"  
>>>"Electronic product information"  
>>>"Item barcode image"  
>>
>>**Display in list**: tag all  
>>**Searchable**: tag all

## DHIS2 user interfaces

**Web portal / Capture app**![](media/image73.png)

**Capture Android app**

![](media/image86.png)
