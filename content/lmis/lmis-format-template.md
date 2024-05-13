# CONSIGNMENT RECEIPT ACKNOWLEDGEMENT


## Introduction

Xx

## Use case

Xx

## Functionality and features

Xx

## DHIS2 configuration

### CATEGORY

#### Category option

#### Category

#### Category combination

#### Category option combination

#### Category option group

#### Category option group set

### DATA ELEMENT

#### Data elements
>**Name**
>>"Alarm cause" / "Long text"  
>>"Alarm corrective action" / "Long text"  
>>"Alarm escalated to supervisor" / "Yes/No"  
>>"Alarm resolved" / "Yes/No"  
>>"Alarm type" / "Long text"  
>>"Assessment of technical fault" / "Long text"  
>>“Clean refrigerator with water and mild detergent" / "Yes/No"  
>>“Clean the grill on the side of the refrigerator" / "Yes/No"  
>>"Cold chain appliance installation report" / "Long text"  
>>"Cold chain appliance product number" / "Long text"  
>>"Cold chain appliance restored to service"  / "Yes/No"  
>>"Cold chain technician" / "User name"  
>>"Daily inspection completed" / "Yes/No"  
>>"Daily tasks completed" / "Yes/No"  
>>"Defect image" / "Image"  
>>"Equipment removed from cold chain appliance inventory" / "Yes/No"  
>>"Interventions" / "Long text"  
>>“Lid gasket checked for sealing when the lid is closed” / "Yes/No"  
>>"Method of disposal" / "Long text"  
>>“Monthly tasks” / “Long text”  
>>"Reason for disposal" / "Long text"  
>>"Reason for repair request" / "Long text"  
>>"Received at" / "Organisation unit"  
>>"Received from" / "Organisation unit"  
>>"Sent from" / "Organisation unit"  
>>"Technical fault resolved" / "Yes/No"  
>>"Transferred to" / "Organisation unit"  
>>"Urgency of repair request" / "Long text"  
>>"Water droplets wiped off from the inside wall" / "Yes/No"  
>>"Water removed at the bottom of the refrigerator" / "Yes/No"  
>>"Weekly tasks" / “Text”  
>
>**Domain Type (*)**: "Tracker"  
>**Value type (*)**: see above  
>**Aggregation type (*)**: "None"

#### Data element group

#### Data element group set

### DATA SET

#### Data set notification

### INDICATOR

#### Indicator

#### Indicator type

#### Indicator group

#### Indicator group set

#### Program indicator
>**1 Program indicator details**
>>**Program \(*)**:  
>>**Name \(*)**:  
>>**Short Name \(*)**:  
>>**Aggregation type \(*)**:  
>>**Organisation unit field**:  
>>**Analytics period boundaries**  
>>> **Boundary target**: "Event date"  
>>> **Analytics period boundary target**: "After start of reporting period"  
>>> **Boundary target**: "Event date"  
>>> **Analytics period boundary target**: "Before end of reporting period"  
>>
>>**Display in form**: tag  
>
>**2 Edit expression**
>>**Expression**: 
>
>**3 Edit filter**
>>**Expression**: 

#### Program indicator group

### ORGANISATION UNIT

#### Organisation unit

>In addition to the national health facility register and structure, create a OU for the PQS catalogue repository:  
>**Name (*)**: "World Health Organization PQS catalogue"  
>**Short name (*)**: "WHO PQS catalogue"

#### Organisation unit group

#### Organisation unit group set

#### Organisation unit level

#### Hierarchy operations

### PROGRAM

#### Program
>**1 Program details**
>>**Name (*)**: "Cold chain appliance lifecycle management"  
>>**Short name (*)**: " Cold chain appliance lifecycle management"  
>>**Color**: "#64B5F6"  
>>**Icon**: "cold chain outline"  
>>**Tracked entity type (*)**: select "Cold chain appliance"  
>>**Category combination (*)**: select "None"  
>>**Display front page list**: tag  
>
>**2 Enrollment details**  
>>**Allow future enrollment dates**: do not tag  
>>**Allow future incident dates**: do not tag  
>>**Only enrol once (per tracked entity instance lifetime)**: do not tag  
>>**Show incident date**: tag  
>>**Description of incident date**: "Cold chain appliance management"  
>>**Description of enrollment date**: leave blank  
>>**Ignore overdue events**: leave untagged  
>>**Feature type**: "Point"  
>>**Related program**: (blank)  
>>
>>*Note that the "Feature type" will prompt the user to enter the geolocation during registration (by entering longitude and latitude on the web or selecting the pin icon on a mobile device).*
>
>**3 Attributes**
>>**1 Assign attributes**
>>>**Program tracked entity attributes**: select and arrange in the following order:
>>>>"Appliance image"  
>>>>"Place of installation"  
>>>>"PQS code category"  
>>>>"PQS code"  
>>>>"Type of appliance"  
>>>>“Company”  
>>>>"Manufactured in"  
>>>>"Manufacturer's reference"  
>>>>"Production date"  
>>>>"Product number"  
>>>>"GTIN"  
>>>>"Serial number"  
>>>>"GS1 GIAI"  
>>>>"Unique identifier"  
>>>
>>>**Display in list**: tag all  
>>>**Mobile render type**: see above 
>>
>>**2 Create registration form**
>>>**Name**: "Cold chain appliance lifecycle management"
>>>**ADD SECTION TO FORM**  
>>>>"Appliance image"  
>>>>"Place of installation"  
>>>>"PQS code category"  
>>>>"PQS code"  
>>>>"Type of appliance"  
>>>>“Company”  
>>>>"Manufactured in"  
>>>>"Manufacturer's reference"  
>>>>"Production date"  
>>>>"Product number"  
>>>>"GTIN"  
>>>>"Serial number"  
>>>"GS1 GIAI"  
>>>>"Unique identifier"  
>
>**4 Program stages**
>>**1 Stage details**
>>>**Name**  
>>>>"Cold chain appliance transfer" / "Repeatable"  
>>>>"Cold chain appliance installation" / "Repeatable"  
>>>>"Cold chain appliance inspection" / "Repeatable"  
>>>>"Cold chain appliance weekly preventive maintenance" / "Repeatable"  
>>>>"Cold chain appliance monthly preventive maintenance" / "Repeatable"  
>>>>"Cold chain appliance alert" / "Repeatable"  
>>>>"Cold chain appliance repair request" / "Repeatable"  
>>>>"Cold chain appliance corrective maintenance" / "Repeatable"  
>>>>"Cold chain appliance disposal" / not repeatable  
>>>
>>>**Repeatable**: see above  
>>
>>**2 Assign data elements**  
>>>**Cold chain appliance transfer**  
>>>"Sent from"  
>>>"Transferred to"  
>>>"Received from"  
>>>"Received at"  
>>>
>>>**Cold chain appliance installation**  
>>>"Cold chain appliance installation report"
>>>
>>>**Cold chain appliance inspection**  
>>>"Daily inspection completed"  
>>>"Functional status"  
>>>
>>>**Cold chain appliance weekly preventive maintenance**
>>>"Water removed at the bottom of the refrigerator"
>>>"Water droplets wiped off from the inside wall"
>>>"Lid gasket checked for sealing when the lid is closed"
>>>
>>>**Cold chain appliance monthly preventive maintenance**
>>>“Clean refrigerator with water and mild detergent”
>>>“Clean the grill on the side of the refrigerator”
>>>
>>>**Cold chain appliance alarm**  
>>>"Alarm type"  
>>>"Alarm cause"  
>>>"Alarm corrective action"  
>>>"Alarm resolved"  
>>>"Alarm escalated to supervisor" 
>>> 
>>>**Cold chain appliance repair request**  
>>>"Reason for repair request"  
>>>"Urgency of repair request"  
>>>“Defect image”  
>>>“Cold chain technician”  
>>>
>>>**Cold chain appliance corrective maintenance**  
>>>"Assessment of technical fault"  
>>>"Interventions"  
>>>"Technical fault resolved"  
>>>"Equipment restored to service"  
>>>
>>>**Cold chain appliance disposal**  
>>>"Reason for disposal"
>>>"Method of disposal"
>>>"Equipment removed from cold chain appliance inventory"
>>
>>**Display in report**: make visible for all items  
>>**Mobile render type**: "Default"  
>>**Desktop render type**: "Default"
>>
>>**3 Create data entry form**
>>>**"BASIC"** is configured by default, no configuration is needed.
>
>**5 Access**
>>**Organisation units**: tag the health care facility for assigning to the DHIS2 Capture.  
>>**Roles and access**: "Biomedical equipment life cycle management" appears by default  
>>**SELECT ALL**
>
>**6 Notifications**
>(not applicable)

#### Tracked entity attribute
>**Name (*)**:
>>"Appliance image" / "Image"  
>>"Company" / "Text"  
>>"Energy source" / "Text"  
>>"Freezer gross volume (litres)" / "Number"  
>>"GS1 GIAI" / "Text"  
>>"GTIN" / "Text"  
>>"Manufactured in" / "Text"  
>>"Manufacturer's reference" / "Text"  
>>"Place of installation" / "Text"  
>>"PQS code" / "Text"  
>>"PQS code category" / "Text"  
>>"Product number" / "Text"  
>>"Production date" / "Date"  
>>"Product number" / "Text"  
>>"Serial number" / "Text"  
>>"Type of appliance" / "Text"  
>>"Unique identifier" / "Text"  
>>"Vaccine gross volume (litres)" / "Number"  
>>"Vaccine storage capacity (litres)" / "Number" 
> 
>**Name (*)**: (see above)  
>**Short name (*)**: same as "Name ( *)"  
>**Value type**: "Text"  
>**Aggregation type**: "None"  
>**Inherit**: check (appears as a blue tag with a white tick)

#### Relationship type
>**Name (*)**: "World Health Organization PQS catalogue"  
>**Relationship name seen from initiating entity (*)**: "World Health Organization PQS catalogue"  
>**From constraint (*)**: "Tracked entity instance"  
>**Tracked entity type (*)**: "Cold chain appliance"  
>**Program**: "Cold chain appliance lifecycle management"  
>**To constraint (*)**: "Tracked entity instance"  
>**Tracked entity type (*)**: "Cold chain appliance"  
>**Program**: "Cold chain appliance lifecycle management"  

#### Tracked entity type
>**Color**: leave empty  
>**Icon**: leave empty  
>**Description**: leave empty  
>**Enable tracked entity instance audit log**: check (appears as white tick in a blue box)  
>**Minimum number of attributes required to search**: 1  
>**Tracked entity type attributes**: assign the following Tracked entity attributes in this order
>>"Appliance image" / "Image"  
>>"Place of installation" / "Text"  
>>"PQS code category" / "Text"  
>>"PQS code" / "Text"  
>>"Type of appliance" / "Text"  
>>"Company" / "Text"  
>>"Manufactured in" / "Text"  
>>"Manufacturer's reference" / "Text"  
>>"Energy source" / "Text"  
>>"Vaccine storage capacity (litres)" / "Number"  
>>"Vaccine gross volume (litres)" / "Number"  
>>"Freezer gross volume (litres)"  
>>"Production date" / "Date"  
>>"Product number" / "Text"  
>>"GTIN" / "Text"  
>>"Serial number" / "Text"  
>>"GS1 GIAI" / "Text"  
>>"Unique identifier" / "Text"  
>>"Unique identifier scan" / "Text"  
>>"Donated by" / "Text"  
>
>**Display in list**: tag all  
>**Searchable**: tag except for "Appliance image", "Manufactured in" and 
"Production date"

#### Program rule
>**1 Enter program rule details**  
>>**Program (*)**: "Cold chain appliance lifecycle management"  
>>**Name (*)**: "GS1 GIAI specifications"  
>>**Description**: "Parses the GS1 GIAI, "extracts" GTIN, serialized number and production date and writes them to the respective attribute fields".  
>
>**2 Enter program rule expression**  
>>**Condition**: "d2:hasValue(A{GS1 GIAI})"  
>
>**3 Define program rule actions**  
>>**Action details**   
>>>**GTIN**  
>>>>**Action (*)**: "Assign to"  
>>>>**Tracked entity attribute to assign to**: "GTIN"  
>>>>**Expression to evaluate and assign**: "d2:extractDataMatrixValue( 'gtin', A{GS1 GIAI})"
>>>
>>>**Production date**  
>>>>**Action (*)**: "Assign to"   
>>>>Tracked entity attribute to assign to: "Production date"  
>>>>Expression to evaluate and assign: "d2:extractDataMatrixValue( 'production date', A{GS1 GIAI})"
>>>
>>>**Serial number**
>>>>**Action (*)**: "Assign to"  
>>>>**Tracked entity attribute to assign to**: "Serial number"  
>>>>**Expression to evaluate and assign**: "d2:extractDataMatrixValue( 'serial number', A{GS1 GIAI})"

#### Program rule variable
>**Name (*)**: "GS1 GIAI"  
>**Source type (*)**: "Tracked entity attribute"  
>**Tracked entity attribute**: "Cold chain appliance lifecycle management GS1 GIAI"

### VALIDATION

#### Validation rule

#### Validation rule group

#### Validation notification

### OTHER

#### Constant

#### Attribute

#### Option set

#### Option group

#### Option group set

#### Legend

#### Predictor

#### Predictor group

#### Push analysis

#### External map layer

#### Data approval level

#### Data approval workflow

#### Locale

#### SQL View

## DHIS2 Analytics

### Analytics overview

>**1. Android Capture app - offline analytics**  
>>Working list A  
>>Working list B  
>>Working list C  
>>
>**2. Working list**  
>>Working list A  
>>Working list B  
>>Working list C  
>>
>**3. Line Listing**
>>Line listing A  
>>Line listing B  
>>Line listing C  
>>
>**4. Data visualizer**  
>>Data visualizer A  
>>Data visualizer B  
>>Data visualizer C  
>>
>**5. Event Report**  
>>Event Report A  
>>Event Report B  
>>Event Report C
>>
>**6. Maps**  
>>Map A  
>>Map B  
>>Map C
>>
>**7. Dashboard**  
>>Dashboard A  
>>Dashboard B  
>>Dashboard C
<br><br><br><br><br><br>

# [Chapter name]


## 1 Sub-chapter

Sub-level 1

### 1.1 Sub-chapter

Sub-level 2

#### 1.1.1 Sub-chapter

Sub-level 3

##### 1.1.1.1 Sub-chapter

Sub-level 4

###### 1.1.1.1.1 Sub-chapter

Sub-level 5
<br><br>

**Basic formating**

**bold text**

*italicized text*

==highlight==

[link title](https://docs.dhis2.org/en/home.html)

<br><br>

**Bulleted list**

Unordered list

- AAA
- BBB
- CCC
<br><br>

**Hyphenated list**

Hyphenated list
<br>- AAA
<br>- BBB
<br>- CCC
<br><br>

**Numbered list**

Ordered list
<br>1. AAA
<br>2. BBB
<br>3. CCC
<br><br>


**Table with two columns**

| **Column A** | **Column B** |
| --- | --- |
| > AAA | Name A:<br>- AAA<br>- BBB<br>- CCCC<br>
| > BBB | Name B:<br>- AAA<br>- BBB<br>- CCCC<br>
| > CCC | Name C:<br>- AAA<br>- BBB<br>- CCCC<br>
<br><br>

**Horizontal lines separating text**

---
AAA

---
BBB

---
CCC

---
<br><br>

**Horizontal lines separating text**

***
AAA
***
BBB
***
CCC
***
<br><br>

>  **Block quote**
>
> Text left aligned
> <br>AAA
> <br>BBB
> <br>CCC
<br><br>

>  **Code quote**
>
> Text left aligned
> ```
> Code block
> AAA
> BBB
> CCC
<br><br>

>  **Code block double indented list**
>
> Text left aligned
> ```
> AAA
>  AAA
>   AAAA
> BBB
>  BBB>
>   BBB>
> CCC
>  CCC
>   CCC
   


