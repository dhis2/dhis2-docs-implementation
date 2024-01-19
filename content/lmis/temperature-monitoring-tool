# TEMPERATURE MONITORING TOOL / "Aggregate" Data Entry Form

This simple Default Data Entry allows digitizing the  twice daily manual temperature recordings on paper forms, sharing and analysing them digitally on the DHIS2 database.

## Use case

Twice a day, in the morning when starting work and in the afternoon before leaving, the storekeeper reads out the room temperature from the storeroom as well as each refrigerator and freezer used for storing vaccines and other drug products and records the minimum, current as well as maximum temperature on a mobile device. The storekeeper at the health care facility as well as cold chain technicians or biomedical engineers anywhere else can access the record and review the data table as well as the chart for assessing the cold chain.

## Maintenance Web App - DHIS2 metadata configuration

The configuration of this Default Data Entry form uses "Disaggregation categories" as this is technically the only way to display a table for recording data in the DHIS2 Capture app on a mobile device. Every refrigerator, freezer or other place (such as a store room) where temperature needs to be recorded is configured as a separate "Data element". The application uses only simple and native DHIS2 functionality.

### Metadata overview
The required metadata settings seetings are presented in the order in which it is presented in the DHIS2 Maintenance Web App.

>**1 CATEGORY**  
>>1.1 Category option  
>>1.2 Category  
>>1.3 Category combination 
> 
>**2 DATA ELEMENT**  
>>2.1 Data element - "Aggregate"  
>>2.3 Data element group  
> 
>**3 DATA SET**  
>>3.1 Data set  

### 1 CATEGORY

#### 1.1 Category option
>**1 Current**  
>>**Name \(*)**: "Current"  
>>**Short name \(*)**: "Current - TMT"  
>>**Organisation units selected**: (select as required) 
>
>**2 Maximum**  
>>**Name \(*)**: "Maximum"  
>>**Short name \(*)**: "Maximum - TMT"  
>>**Organisation units selected**: (select as required) 
>
>**3 Minimum**  
>>**Name \(*)**: "Minimum"  
>>**Short name \(*)**: "Minimum - TMT"  
>>**Organisation units selected**: (select as required) 
>
>**4 Temperature recording - afternoon**  
>>**Name \(*)**: "Temperature recording - afternoon"  
>>**Short name \(*)**: "Temperature recording - afternoon - TMT"  
>>**Organisation units selected**: (select as required) 
>
>**5 Temperature recording - morning**  
>>**Name \(*)**: "Temperature recording - morning"  
>>**Short name \(*)**: "Temperature recording - morning - TMT"  
>>**Organisation units selected**: (select as required) 

#### 1.2 Category
>**1 Temperature recording - Measurement**  
>>**Name \(*)**: "Temperature recording - Measurement"  
>>**Short name \(*)**: "Temperature recording - Measurement - TMT"  
>>**Data dimension type \(*)**: "Disaggregation"  
>>**Data dimension**: tag (appears as white tick in a blue square)  
>>**Category options**: *note the order of "Category options"*:  
>>>"Minimum"  
>>>"Current"  
>>>"Maximum"  
>
>**2 Temperature recording - Time of day**  
>>**Name \(*)**: "Temperature recording - Time of day"  
>>**Short name \(*)**: "Temperature recording - Time of day - TMT"  
>>**Data dimension type \(*)**: "Disaggregation"  
>>**Data dimension**: tag (appears as white tick in a blue square)  
>>**Category options**: *note the order of "Category options"*:  
>>>"Temperature recording - morning"  
>>>"Temperature recording - afternoon"  

#### 1.3 Category combination
>**1 Health facility - temperature recording**  
>>**Name \(*)**: **Health facility - temperature recording**  
>>**Data dimension type \(*)**: "Disaggregation"  
>>**Skip category total in report \(*)**: check (appears as white tick in a blue square)   
>>**Categories**
>>>"Temperature recording - Time of day"
>>>"Temperature recording - Measurement"

### 2 DATA ELEMENT

### 2.1 Data element
Data elements represent the cold chain equipment devices such as refrigerators or freezers. It is recommended to assign generic names such as "Refrigerator 1" and mark devices at healthcare facilities accordingly since otherwise all cold chain devices would have to be managed as separate entities with specifications and serial numbers.

>**1 Vaccine refrigerator 1**
>>**Name \(*)**: "Vaccine refrigerator 1"  
>>**Short name \(*)**: "Vaccine refrigerator 1 - TMT"
>>**Code \(*)**:  (none)
>>**Domain Type \(*)**: "Aggregate"  
>>**Value type \(*)**: "Number"  
>>**Aggregation type (*)**: "Sum"  
>>**Store zero data values**: tag (appears as white tick in a blue square) 
>>**Category combination \(*)**: "Health facility - temperature monitoring"  
>
>**2 Vaccine refrigerator 2**
>>**Name \(*)**: "Vaccine refrigerator 2"  
>>**Short name \(*)**: "Vaccine refrigerator 2 - TMT"
>>**Code \(*)**:  (none)
>>**Domain Type \(*)**: "Aggregate"  
>>**Value type \(*)**: "Number"  
>>**Aggregation type (*)**: "Sum"  
>>**Store zero data values**: tag (appears as white tick in a blue square) 
>>**Category combination \(*)**: "Health facility - temperature monitoring"  

### 2.2 Data element group

The creation of Data element groups is a DHIS2 best practice but also a precondition for using the "Group Predictor" functionality which allows using a placeholder and the Data element group ID for creating a single Predictor which is automatically applied to all Data elements in the respective Data element group. For example for calculating the stock coverage time.

>**1 [Cold chain equipment]**  
>**Name \(*)**: "[Cold chain equipment]"  
>**Short name \(*)**: "[Cold chain equipment] - TMT"
>**Data elements \(*)**
>>"Vaccine refrigerator 1"
>>"Vaccine refrigerator 2"

### 3 Data set

This Default Data Entry Form ("aggregate") allows storekeepers at health care facilities to enter temperature recordings twice a day digitally on a on- or off-line on a mobile device and synchronize the data with a central DHIS2 server for analysis, data sharing and integration with national eLMIS systems.

#### 3.1 Data set
Data sets for each Organisation unit are required for recording and storing monthly stock report data.
The sections can be displayed in the Data Entry (beta) Web App as well as in the Capture Android App either in a single table or as separate tabs.
The configuration for two Data sets are presented below, but either the one or the other should be used:
- "MSR - Monthly stock report - Data recording"
- "MSR - Monthly stock report - Data recording and calculation"

>**1 Health facility - Temperature monitoring**  
>>**Name \(*)**: "Health facility - Temperature monitoring"  
>>**Short name \(*)**: "Health facility - Temperature monitoring - TMT"
>>**Color**: "#304FFE"  
>>**Expiry days**: "1"  
>>**Open future periods for data entry**: "1"  
>>**Days after period to qualify for timely submission**: "5"  
>>**Period type**: "Daily"  
>>**Category combination**: "None"  
>>**Data elements**  
>>>"Vaccine refrigerator 1"
>>>"Vaccine refrigerator 2"
>>
>>**Organisation units selected**: (select as for the Tracker Program) 

XXXXX



Data visualizer
Name: "Temperature monitoring - Daily reporting / Table"
Visualization type: "Pivot table"
Columns:
- Data: "Vaccine refrigerator 1", "Vaccine refrigerator 2"
- Your Dimensions: 
- - "Temperature recording - Time of day": "Temperature recording - morning", "Temperature recording - afternooon"
- - "Temperature recording - Measurement": "Minimum", "Current", "Maximum"
Rows
- Period: "Last 30 days"
Filter: Organisation Unit: select Organisation units as required

## DV - Data Visualizer Web App - "Aggregate" Analytics and Visualizations

[To be added]
Name: "Temperature monitoring - Daily reporting / Chart / Vaccine refrigerator 1 / Last 30 days#"
Visualization type: "Line"
Series: "Temperature recording - Measurement": "Minimum", "Current", "Maximum"
Category:
- "Temperature recording - Time of day": "Temperature recording - morning", "Temperature recording - afternoon"
- Period: "Relative periods" / "Days" / "Last 30 days"
Filter: Organisation Unit: select Organisation units as required

3.3 DHIS2 user interfaces
Web portal / Data Entry form








