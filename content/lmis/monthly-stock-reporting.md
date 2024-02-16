# Monthly Stock Data Recording / "Aggregate" Data Entry Form

This Default Data Entry Form ("aggregate") allows storekeepers at health care facilities to enter monthly data on demand ("consumption") as well as stock on hand digitally on a on- or off-line on a mobile device and synchronize the data with a central DHIS2 server for analysis, data sharing and integration with national eLMIS systems.

## Use case

### Monthly stock report - Data recording

At the end of the month, storekeepers will count the quantity of all health care products in the medical store and record the stock on hand. Furthermore, to obtain the total amount of each health care product issued from the medical store from the first to the last day of the month and record the total monthly demand ("consumption") directly on a mobile device. The list of stock items ("Data Elements") can be adapted to each health care facility as needed and user access can be given selectively to individual storekeepers as required.

### Monthly stock report - Data recording and calculation

In addition to the above: at the end of the month after the physical stock count and all data has been entered, Predictors automatically calculate the following data:

- Opening balance: identical with the "Stock on hand" from the end of the previous month

- Closing balance: Opening balance + Stock received - Stock distributed 
- Stock redistributed - Stock discarded   

- Stock discrepancy: Stock on hand (as counted) - Closing balance

- Stock on hand Yes/No: calculates whether a stockout occurred at the end of the month (at the time of the physical stock count)  

## Maintenance Web App - DHIS2 metadata configuration

The configuration of this Default Data Entry form uses "Disaggregation categories" as this is technically the only way to display a table for recording data in the DHIS2 Android Capture App on a mobile device and relies only on basic, native DHIS2 functionality.

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
>>3.1 Monthly stock reporting
> 
>**4 INDICATOR**  
>>4.1 Indicator  
>>4.1.1 Indicator type
> 
>**5 OTHER**  
>>5.1 Legend  
>>5.2 Predictor  
>>5.3 Predictor group

### 1 Category

#### 1.1 Category option
>**1 Stock correction**  
>>**Name \(*)**: "Stock correction"  
>>**Short name \(*)**: "Stock correction"  
>>**Organisation units selected**: (select as required) 
>
>**2 Stock discarded**  
>>**Name \(*)**: "Stock discarded"  
>>**Short name \(*)**: "Stock discarded"  
>>**Organisation units selected**: (select as required) 
>
>**3 Stock distributed**  
>>**Name \(*)**: "Stock distributed"  
>>**Short name \(*)**: "Stock distributed"  
>>**Organisation units selected**: (select as required) 
>
>**4 Stock received**  
>>**Name \(*)**: "Stock received"  
>>**Short name \(*)**: "Stock received"  
>>**Organisation units selected**: (select as required) 
>
>**5 Stock redistributed**  
>>**Name \(*)**: "Stock redistributed"  
>>**Short name \(*)**: "Stock redistributed"  
>>**Organisation units selected**: (select as required) 
>
>**6 Stock correction**  
>>**Name \(*)**: "Stock on hand"  
>>**Short name \(*)**: "Stock on hand"  
>>**Organisation units selected**: (select as required) 

#### 1.2 Category
>**1 MSR - Monthly stock report - Data recording**  
>>**Name \(*)**: "MSR - Monthly stock report - Data recording"  
>>**Short name \(*)**: "Monthly stock report - Data recording"  
>>**Data dimension type \(*)**: "Disaggregation"  
>>**Data dimension**: tag (appears as white tick in a blue square)  
>>**Category options**: *note the order of "Category options"*:  
>>>"Stock received"  
>>>"Stock distributed"  
>>>"Stock redistributed"  
>>>"Stock discarded"  
>>>"Stock on hand"  
>>>"Stock correction"  
>
>**2 MSR - Monthly stock report - Data recording and calculation**  
>>**Name \(*)**: "MSR - Monthly stock report - Data recording and calculation"  
>>**Short name \(*)**: "Monthly stock report - Data recording and calculation"  
>>**Data dimension type \(*)**: "Disaggregation"  
>>**Data dimension**: tag (appears as white tick in a blue square)  
>>**Category options**: *note the order of "Category options"*:  
>>>"Opening balance"  
>>>"Stock received"  
>>>"Stock distributed"  
>>>"Stock redistributed"  
>>>"Stock discarded"
>>>"Stock on hand"  
>>>"Closing balance"  
>>>"Stock discrepancy"  
>>>"Stock correction"  
>>>"Stock on hand Yes/No"  

#### 1.3 Category combination
>**1 MSR Monthly stock report - Data recording**  
>>**Name \(*)**: **Monthly stock report - Data recording**  
>>**Data dimension type \(*)**: "Disaggregation"  
>>**Skip category total in report \(*)**: check (appears as white tick in a blue square)   
>>**Categories**: "Monthly stock report - Data recording"
>
>**2 Monthly stock report - Data recording and calculation**  
>>**Name \(*)**: **Monthly stock report - Data recording and calculation**  
>>**Data dimension type \(*)**: "Disaggregation"  
>>**Skip category total in report \(*)**: check (appears as white tick in a blue square)   
>>**Categories**: "Monthly stock report - Data recording and calculation"

### 2 Data element

### 2.1 Data element
Data elements represent the items (healthcare products) for which logistics data is recorded and managed. A separate and unique Data element needs to be configured for each item (healthcare product).

>**1 ATROPINE SULFATE, 1mg/ml, 1ml, amp. - MSR**
>>**Name \(*)**: "ATROPINE SULFATE, 1mg/ml, 1ml, amp. - MSR"  
>>**Short name \(*)**: "DINJATRO1A"  
>>**Code \(*)**:  "DINJATRO1A"  
>>**Domain Type \(*)**: "Aggregate"  
>>**Value type \(*)**: "Integer"  
>>**Aggregation type (*)**: "Sum"  
>>**Store zero data values**: tag (appears as white tick in a blue square)  
>>**Category combination \(*)**: "Monthly stock report - Data collection"  
>
>**[Number] [Item] - MSR**  
>>**Name \(*)**: "X [Item] - MSR"  
>>**Short name \(*)**: "[Item code]"  
>>**Code \(*)**:  "[Item code]"  
>>**Domain Type \(*)**: "Aggregate"  
>>**Value type \(*)**: "Integer"  
>>**Aggregation type (*)**: "Sum"  
>>**Store zero data values**: tag (appears as white tick in a blue square)  
>>**Category combination \(*)**: "Monthly stock report - Data collection"  

### 2.2 Data element group

The creation of Data element groups is a DHIS2 best practice but also a precondition for using the "Group Predictor" functionality which allows using a placeholder and the Data element group ID for creating a single Predictor which is automatically applied to all Data elements in the respective Data element group. For example for calculating the stock coverage time.

>**1 Stock item list - MSR**  
>**Name \(*)**: "Stock item list - MSR"  
>**Short name \(*)**: "Stock item list - MSR"  
>**Data elements \(*)**: *select all Data elements with the "MSR" suffix"*  

### 3 Data set

This Default Data Entry Form ("aggregate") allows storekeepers at health care facilities to enter monthly data on demand ("consumption") as well as stock on hand digitally on a on- or off-line on a mobile device and synchronize the data with a central DHIS2 server for analysis, data sharing and integration with national eLMIS systems.

#### 3.1 Data set
Data sets for each Organisation unit are required for recording and storing monthly stock report data.
The sections can be displayed in the Data Entry (beta) Web App as well as in the Capture Android App either in a single table or as separate tabs.
The configuration for two Data sets are presented below, but either the one or the other should be used:
- "MSR - Monthly stock report - Data recording"
- "MSR - Monthly stock report - Data recording and calculation"

>**1 MSR - Monthly stock report - Data recording**  
>>**Name \(*)**: "MSR - Monthly stock report - Data recording"  
>>**Short name \(*)**: "Monthly stock report - Data recording"  
>>**Color**: "#00ACC1"  
>>**Expiry days**: "5"  
>>**Open future periods for data entry**: "1"  
>>**Days after period to qualify for timely submission**: "5"  
>>**Period type**: "Monthly"  
>>**Category combination**: "None"  
>>**Render sections as tabs**: tag (appears as white tick in a blue square)  
>>**Data elements**  
>>>*Add all Data elements with the suffix "MSR" required for the respective health facility*.
>>
>>**Organisation units selected**: (select as for the Tracker Program) 
>>
>>**Actions**
>>>**Manage sections**
>>>>**Name**
>>>>>**1 DASD**
>>>>>>**DASD**
>>>>>>**Data elements**
>>>>>>>CHLORHEXIDINE DIGLUCONATE 5% , solution, 1L, btl. - MSR  
>>>>>>>IODINE POVIDONE, 10%, solution, 1L, btl. - MSR  
>>>>>**2 [Section 2]**  
>>>>>>**[Section 2]**  
>>>>>>**Data elements**  
>>>>>>>[Data element]  

### 4 Indicator

#### 4.1 Indicator

Indicators are used for calculating the following logistics metrics:

- Number of items in stock coverage bins (0-1, 1-2, 2-3 months etc.) for visualizing the stock coverage time distribution 

- Stock coverage time (stock on hand / average monthly demand)

- Stock availability (percentage of items which are on hand)

- Stockout count (number of items which are out of stock)

For the "Stock coverage time" indicator it would in principle be preferable to configure the "Stock coverage time" as Predictor (as it would allow using the "Group predictor" function) but because the "Stock coverage time" requires displaying decimals and the Data Entry form only allows a single number format for all Category Options, an indicator is used instead. This approach allows freely setting the number of decimals in the Indicator settings. Note that items will have to be added and removed individually if the stock item list is changed.

>**1 0-1 months - MSR**  
>For each item the Indicator returns "1" if the item has stock and stock coverage time is less than 1 and otherwise returns "0" and then adds up these results for calculating the number of items with a stock coverage time of 0-1 months. 
>>**Name \(*)**: "0-1 months - MSR"  
>>**Short Name \(*)**: "0-1 months"  
>>**Description**: "Number of items with a coverage time of 0-1 months"  
>>**Decimals in data output**: "0"  
>>**Indicator type \(*)**: "Number (Factor 1)"  
>>**Edit numerator**:
>>>**Description**: "O-1 months - MSR - Numerator"  
>>>**Calculation**:  
if(#{LNAkkMTxqEW.iIC4YhgrxQY}/#{LNAkkMTxqEW.zogrUrI7Crs}>0 && #{LNAkkMTxqEW.iIC4YhgrxQY}/#{LNAkkMTxqEW.zogrUrI7Crs}<=1,1,0)+
if(#{WyDZKSw82X6.iIC4YhgrxQY}/#{WyDZKSw82X6.zogrUrI7Crs}>0 && #{WyDZKSw82X6.iIC4YhgrxQY}/#{WyDZKSw82X6.zogrUrI7Crs}<=1,1,0)+
if(#{JPccVwAGRq9.iIC4YhgrxQY}/#{JPccVwAGRq9.zogrUrI7Crs}>0 && #{JPccVwAGRq9.iIC4YhgrxQY}/#{JPccVwAGRq9.zogrUrI7Crs}<=1,1,0)+
if(#{smxJz7Mt6ia.iIC4YhgrxQY}/#{smxJz7Mt6ia.zogrUrI7Crs}>0 && #{smxJz7Mt6ia.iIC4YhgrxQY}/#{smxJz7Mt6ia.zogrUrI7Crs}<=1,1,0)+
if(#{AaIApgGQM6t.iIC4YhgrxQY}/#{AaIApgGQM6t.zogrUrI7Crs}>0 && #{AaIApgGQM6t.iIC4YhgrxQY}/#{AaIApgGQM6t.zogrUrI7Crs}<=1,1,0)+
if(#{vCTrmv52APd.iIC4YhgrxQY}/#{vCTrmv52APd.zogrUrI7Crs}>0 && #{vCTrmv52APd.iIC4YhgrxQY}/#{vCTrmv52APd.zogrUrI7Crs}<=1,1,0)+
if(#{SOw2TcuFFH2.iIC4YhgrxQY}/#{SOw2TcuFFH2.zogrUrI7Crs}>0 && #{SOw2TcuFFH2.iIC4YhgrxQY}/#{SOw2TcuFFH2.zogrUrI7Crs}<=1,1,0)+
if(#{RSIOx2u07Ln.iIC4YhgrxQY}/#{RSIOx2u07Ln.zogrUrI7Crs}>0 && #{RSIOx2u07Ln.iIC4YhgrxQY}/#{RSIOx2u07Ln.zogrUrI7Crs}<=1,1,0)+
if(#{JStiDyaPfqy.iIC4YhgrxQY}/#{JStiDyaPfqy.zogrUrI7Crs}>0 && #{JStiDyaPfqy.iIC4YhgrxQY}/#{JStiDyaPfqy.zogrUrI7Crs}<=1,1,0)+
if(#{hZ1YvdcTDQM.iIC4YhgrxQY}/#{hZ1YvdcTDQM.zogrUrI7Crs}>0 && #{hZ1YvdcTDQM.iIC4YhgrxQY}/#{hZ1YvdcTDQM.zogrUrI7Crs}<=1,1,0)+
if(#{tsi32D8HQd5.iIC4YhgrxQY}/#{tsi32D8HQd5.zogrUrI7Crs}>0 && #{tsi32D8HQd5.iIC4YhgrxQY}/#{tsi32D8HQd5.zogrUrI7Crs}<=1,1,0)+
if(#{QWlPF8S0gCc.iIC4YhgrxQY}/#{QWlPF8S0gCc.zogrUrI7Crs}>0 && #{QWlPF8S0gCc.iIC4YhgrxQY}/#{QWlPF8S0gCc.zogrUrI7Crs}<=1,1,0)+
if(#{a5uLTDt12eT.iIC4YhgrxQY}/#{a5uLTDt12eT.zogrUrI7Crs}>0 && #{a5uLTDt12eT.iIC4YhgrxQY}/#{a5uLTDt12eT.zogrUrI7Crs}<=1,1,0)+
if(#{U0AfOOyJMy2.iIC4YhgrxQY}/#{U0AfOOyJMy2.zogrUrI7Crs}>0 && #{U0AfOOyJMy2.iIC4YhgrxQY}/#{U0AfOOyJMy2.zogrUrI7Crs}<=1,1,0)+
if(#{cyf6UdScfFM.iIC4YhgrxQY}/#{cyf6UdScfFM.zogrUrI7Crs}>0 && #{cyf6UdScfFM.iIC4YhgrxQY}/#{cyf6UdScfFM.zogrUrI7Crs}<=1,1,0)+
if(#{FeUTTNHpVzD.iIC4YhgrxQY}/#{FeUTTNHpVzD.zogrUrI7Crs}>0 && #{FeUTTNHpVzD.iIC4YhgrxQY}/#{FeUTTNHpVzD.zogrUrI7Crs}<=1,1,0)+
if(#{mKSICD1rxG4.iIC4YhgrxQY}/#{mKSICD1rxG4.zogrUrI7Crs}>0 && #{mKSICD1rxG4.iIC4YhgrxQY}/#{mKSICD1rxG4.zogrUrI7Crs}<=1,1,0)+
if(#{mVNe1aS1pGl.iIC4YhgrxQY}/#{mVNe1aS1pGl.zogrUrI7Crs}>0 && #{mVNe1aS1pGl.iIC4YhgrxQY}/#{mVNe1aS1pGl.zogrUrI7Crs}<=1,1,0)+
if(#{oLAXTZY6ken.iIC4YhgrxQY}/#{oLAXTZY6ken.zogrUrI7Crs}>0 && #{oLAXTZY6ken.iIC4YhgrxQY}/#{oLAXTZY6ken.zogrUrI7Crs}<=1,1,0)+
if(#{YYaRDUZyH9L.iIC4YhgrxQY}/#{YYaRDUZyH9L.zogrUrI7Crs}>0 && #{YYaRDUZyH9L.iIC4YhgrxQY}/#{YYaRDUZyH9L.zogrUrI7Crs}<=1,1,0)+
if(#{HVteopBt0jr.iIC4YhgrxQY}/#{HVteopBt0jr.zogrUrI7Crs}>0 && #{HVteopBt0jr.iIC4YhgrxQY}/#{HVteopBt0jr.zogrUrI7Crs}<=1,1,0)+
if(#{sWodd2tbjgZ.iIC4YhgrxQY}/#{sWodd2tbjgZ.zogrUrI7Crs}>0 && #{sWodd2tbjgZ.iIC4YhgrxQY}/#{sWodd2tbjgZ.zogrUrI7Crs}<=1,1,0)+
if(#{yVYajDDYUfX.iIC4YhgrxQY}/#{yVYajDDYUfX.zogrUrI7Crs}>0 && #{yVYajDDYUfX.iIC4YhgrxQY}/#{yVYajDDYUfX.zogrUrI7Crs}<=1,1,0)+
if(#{eTJAr4sc83v.iIC4YhgrxQY}/#{eTJAr4sc83v.zogrUrI7Crs}>0 && #{eTJAr4sc83v.iIC4YhgrxQY}/#{eTJAr4sc83v.zogrUrI7Crs}<=1,1,0)+
if(#{U4KSmanl4JP.iIC4YhgrxQY}/#{U4KSmanl4JP.zogrUrI7Crs}>0 && #{U4KSmanl4JP.iIC4YhgrxQY}/#{U4KSmanl4JP.zogrUrI7Crs}<=1,1,0)+
if(#{FXsa5uG3IGn.iIC4YhgrxQY}/#{FXsa5uG3IGn.zogrUrI7Crs}>0 && #{FXsa5uG3IGn.iIC4YhgrxQY}/#{FXsa5uG3IGn.zogrUrI7Crs}<=1,1,0)+
if(#{L34T9YDtCor.iIC4YhgrxQY}/#{L34T9YDtCor.zogrUrI7Crs}>0 && #{L34T9YDtCor.iIC4YhgrxQY}/#{L34T9YDtCor.zogrUrI7Crs}<=1,1,0)+
if(#{W5mHXhSYFfQ.iIC4YhgrxQY}/#{W5mHXhSYFfQ.zogrUrI7Crs}>0 && #{W5mHXhSYFfQ.iIC4YhgrxQY}/#{W5mHXhSYFfQ.zogrUrI7Crs}<=1,1,0)+
if(#{cmSUyJOZwyl.iIC4YhgrxQY}/#{cmSUyJOZwyl.zogrUrI7Crs}>0 && #{cmSUyJOZwyl.iIC4YhgrxQY}/#{cmSUyJOZwyl.zogrUrI7Crs}<=1,1,0)+
if(#{cT8sfosRXvU.iIC4YhgrxQY}/#{cT8sfosRXvU.zogrUrI7Crs}>0 && #{cT8sfosRXvU.iIC4YhgrxQY}/#{cT8sfosRXvU.zogrUrI7Crs}<=1,1,0)+
if(#{OaWKnMS7say.iIC4YhgrxQY}/#{OaWKnMS7say.zogrUrI7Crs}>0 && #{OaWKnMS7say.iIC4YhgrxQY}/#{OaWKnMS7say.zogrUrI7Crs}<=1,1,0)+
if(#{Z4bjHvGS6aH.iIC4YhgrxQY}/#{Z4bjHvGS6aH.zogrUrI7Crs}>0 && #{Z4bjHvGS6aH.iIC4YhgrxQY}/#{Z4bjHvGS6aH.zogrUrI7Crs}<=1,1,0)+
if(#{Nn1L7CNEtC8.iIC4YhgrxQY}/#{Nn1L7CNEtC8.zogrUrI7Crs}>0 && #{Nn1L7CNEtC8.iIC4YhgrxQY}/#{Nn1L7CNEtC8.zogrUrI7Crs}<=1,1,0)+
if(#{RNYKSc3nAUg.iIC4YhgrxQY}/#{RNYKSc3nAUg.zogrUrI7Crs}>0 && #{RNYKSc3nAUg.iIC4YhgrxQY}/#{RNYKSc3nAUg.zogrUrI7Crs}<=1,1,0)+
if(#{PtmZ9XqpPKi.iIC4YhgrxQY}/#{PtmZ9XqpPKi.zogrUrI7Crs}>0 && #{PtmZ9XqpPKi.iIC4YhgrxQY}/#{PtmZ9XqpPKi.zogrUrI7Crs}<=1,1,0)+
if(#{CohlLHi54B0.iIC4YhgrxQY}/#{CohlLHi54B0.zogrUrI7Crs}>0 && #{CohlLHi54B0.iIC4YhgrxQY}/#{CohlLHi54B0.zogrUrI7Crs}<=1,1,0)+
if(#{Gu6u82RD9OW.iIC4YhgrxQY}/#{Gu6u82RD9OW.zogrUrI7Crs}>0 && #{Gu6u82RD9OW.iIC4YhgrxQY}/#{Gu6u82RD9OW.zogrUrI7Crs}<=1,1,0)+
if(#{LiuYzxYr4Pt.iIC4YhgrxQY}/#{LiuYzxYr4Pt.zogrUrI7Crs}>0 && #{LiuYzxYr4Pt.iIC4YhgrxQY}/#{LiuYzxYr4Pt.zogrUrI7Crs}<=1,1,0)+
if(#{Tje33nJAG55.iIC4YhgrxQY}/#{Tje33nJAG55.zogrUrI7Crs}>0 && #{Tje33nJAG55.iIC4YhgrxQY}/#{Tje33nJAG55.zogrUrI7Crs}<=1,1,0)+
if(#{euM2dlqleYH.iIC4YhgrxQY}/#{euM2dlqleYH.zogrUrI7Crs}>0 && #{euM2dlqleYH.iIC4YhgrxQY}/#{euM2dlqleYH.zogrUrI7Crs}<=1,1,0)+
if(#{dASLmBTEehF.iIC4YhgrxQY}/#{dASLmBTEehF.zogrUrI7Crs}>0 && #{dASLmBTEehF.iIC4YhgrxQY}/#{dASLmBTEehF.zogrUrI7Crs}<=1,1,0)+
if(#{qU2LvzoPn1z.iIC4YhgrxQY}/#{qU2LvzoPn1z.zogrUrI7Crs}>0 && #{qU2LvzoPn1z.iIC4YhgrxQY}/#{qU2LvzoPn1z.zogrUrI7Crs}<=1,1,0)+
if(#{OkWaFxdUQY2.iIC4YhgrxQY}/#{OkWaFxdUQY2.zogrUrI7Crs}>0 && #{OkWaFxdUQY2.iIC4YhgrxQY}/#{OkWaFxdUQY2.zogrUrI7Crs}<=1,1,0)+
if(#{YHIv7KQc2e7.iIC4YhgrxQY}/#{YHIv7KQc2e7.zogrUrI7Crs}>0 && #{YHIv7KQc2e7.iIC4YhgrxQY}/#{YHIv7KQc2e7.zogrUrI7Crs}<=1,1,0)+
if(#{rt9D47Inb49.iIC4YhgrxQY}/#{rt9D47Inb49.zogrUrI7Crs}>0 && #{rt9D47Inb49.iIC4YhgrxQY}/#{rt9D47Inb49.zogrUrI7Crs}<=1,1,0)+
if(#{i1iXbquZ5iv.iIC4YhgrxQY}/#{i1iXbquZ5iv.zogrUrI7Crs}>0 && #{i1iXbquZ5iv.iIC4YhgrxQY}/#{i1iXbquZ5iv.zogrUrI7Crs}<=1,1,0)+
if(#{RcE30WBKrXI.iIC4YhgrxQY}/#{RcE30WBKrXI.zogrUrI7Crs}>0 && #{RcE30WBKrXI.iIC4YhgrxQY}/#{RcE30WBKrXI.zogrUrI7Crs}<=1,1,0)+
if(#{EAG0GfdSMAs.iIC4YhgrxQY}/#{EAG0GfdSMAs.zogrUrI7Crs}>0 && #{EAG0GfdSMAs.iIC4YhgrxQY}/#{EAG0GfdSMAs.zogrUrI7Crs}<=1,1,0)+
if(#{N2aXs7VlJdJ.iIC4YhgrxQY}/#{N2aXs7VlJdJ.zogrUrI7Crs}>0 && #{N2aXs7VlJdJ.iIC4YhgrxQY}/#{N2aXs7VlJdJ.zogrUrI7Crs}<=1,1,0)+
if(#{xrjnOtFFTRC.iIC4YhgrxQY}/#{xrjnOtFFTRC.zogrUrI7Crs}>0 && #{xrjnOtFFTRC.iIC4YhgrxQY}/#{xrjnOtFFTRC.zogrUrI7Crs}<1,1,0)
>>
>>**Edit denominator**:  
>>>**Description**: "O-1 months - MSR - Denominator"  
>>>**Calculation**: "1"  
>
>**2 1-2 months - MSR**  
>For each item the Indicator returns "1" if the stock coverage time is greater than or equal to 1 but less than 2 and otherwise returns 0and then adds up these results for calculating the number of items with a stock coverage time greater of 1-2 months.
>>**Name \(*)**: "1-2 months - MSR"  
>>**Short Name \(*)**: "1-2 months"  
>>**Description**: "Number of items with a coverage time of 1-2 months"  
>>**Decimals in data output**: "0"  
>>**Indicator type \(*)**: "Number (Factor 1)"  
>>**Edit numerator**:
>>>**Description**: "1-2 months - MSR - Numerator"  
>>>**Calculation**:  
>>>if(#{LNAkkMTxqEW.iIC4YhgrxQY}/#{LNAkkMTxqEW.zogrUrI7Crs}>1 && #{LNAkkMTxqEW.iIC4YhgrxQY}/#{LNAkkMTxqEW.zogrUrI7Crs}<=2,1,0)+
if(#{WyDZKSw82X6.iIC4YhgrxQY}/#{WyDZKSw82X6.zogrUrI7Crs}>1 && #{WyDZKSw82X6.iIC4YhgrxQY}/#{WyDZKSw82X6.zogrUrI7Crs}<=2,1,0)+
if(#{JPccVwAGRq9.iIC4YhgrxQY}/#{JPccVwAGRq9.zogrUrI7Crs}>1 && #{JPccVwAGRq9.iIC4YhgrxQY}/#{JPccVwAGRq9.zogrUrI7Crs}<=2,1,0)+
if(#{smxJz7Mt6ia.iIC4YhgrxQY}/#{smxJz7Mt6ia.zogrUrI7Crs}>1 && #{smxJz7Mt6ia.iIC4YhgrxQY}/#{smxJz7Mt6ia.zogrUrI7Crs}<=2,1,0)+
if(#{AaIApgGQM6t.iIC4YhgrxQY}/#{AaIApgGQM6t.zogrUrI7Crs}>1 && #{AaIApgGQM6t.iIC4YhgrxQY}/#{AaIApgGQM6t.zogrUrI7Crs}<=2,1,0)+
if(#{vCTrmv52APd.iIC4YhgrxQY}/#{vCTrmv52APd.zogrUrI7Crs}>1 && #{vCTrmv52APd.iIC4YhgrxQY}/#{vCTrmv52APd.zogrUrI7Crs}<=2,1,0)+
if(#{SOw2TcuFFH2.iIC4YhgrxQY}/#{SOw2TcuFFH2.zogrUrI7Crs}>1 && #{SOw2TcuFFH2.iIC4YhgrxQY}/#{SOw2TcuFFH2.zogrUrI7Crs}<=2,1,0)+
if(#{RSIOx2u07Ln.iIC4YhgrxQY}/#{RSIOx2u07Ln.zogrUrI7Crs}>1 && #{RSIOx2u07Ln.iIC4YhgrxQY}/#{RSIOx2u07Ln.zogrUrI7Crs}<=2,1,0)+
if(#{JStiDyaPfqy.iIC4YhgrxQY}/#{JStiDyaPfqy.zogrUrI7Crs}>1 && #{JStiDyaPfqy.iIC4YhgrxQY}/#{JStiDyaPfqy.zogrUrI7Crs}<=2,1,0)+
if(#{hZ1YvdcTDQM.iIC4YhgrxQY}/#{hZ1YvdcTDQM.zogrUrI7Crs}>1 && #{hZ1YvdcTDQM.iIC4YhgrxQY}/#{hZ1YvdcTDQM.zogrUrI7Crs}<=2,1,0)+
if(#{tsi32D8HQd5.iIC4YhgrxQY}/#{tsi32D8HQd5.zogrUrI7Crs}>1 && #{tsi32D8HQd5.iIC4YhgrxQY}/#{tsi32D8HQd5.zogrUrI7Crs}<=2,1,0)+
if(#{QWlPF8S0gCc.iIC4YhgrxQY}/#{QWlPF8S0gCc.zogrUrI7Crs}>1 && #{QWlPF8S0gCc.iIC4YhgrxQY}/#{QWlPF8S0gCc.zogrUrI7Crs}<=2,1,0)+
if(#{a5uLTDt12eT.iIC4YhgrxQY}/#{a5uLTDt12eT.zogrUrI7Crs}>1 && #{a5uLTDt12eT.iIC4YhgrxQY}/#{a5uLTDt12eT.zogrUrI7Crs}<=2,1,0)+
if(#{U0AfOOyJMy2.iIC4YhgrxQY}/#{U0AfOOyJMy2.zogrUrI7Crs}>1 && #{U0AfOOyJMy2.iIC4YhgrxQY}/#{U0AfOOyJMy2.zogrUrI7Crs}<=2,1,0)+
if(#{cyf6UdScfFM.iIC4YhgrxQY}/#{cyf6UdScfFM.zogrUrI7Crs}>1 && #{cyf6UdScfFM.iIC4YhgrxQY}/#{cyf6UdScfFM.zogrUrI7Crs}<=2,1,0)+
if(#{FeUTTNHpVzD.iIC4YhgrxQY}/#{FeUTTNHpVzD.zogrUrI7Crs}>1 && #{FeUTTNHpVzD.iIC4YhgrxQY}/#{FeUTTNHpVzD.zogrUrI7Crs}<=2,1,0)+
if(#{mKSICD1rxG4.iIC4YhgrxQY}/#{mKSICD1rxG4.zogrUrI7Crs}>1 && #{mKSICD1rxG4.iIC4YhgrxQY}/#{mKSICD1rxG4.zogrUrI7Crs}<=2,1,0)+
if(#{mVNe1aS1pGl.iIC4YhgrxQY}/#{mVNe1aS1pGl.zogrUrI7Crs}>1 && #{mVNe1aS1pGl.iIC4YhgrxQY}/#{mVNe1aS1pGl.zogrUrI7Crs}<=2,1,0)+
if(#{oLAXTZY6ken.iIC4YhgrxQY}/#{oLAXTZY6ken.zogrUrI7Crs}>1 && #{oLAXTZY6ken.iIC4YhgrxQY}/#{oLAXTZY6ken.zogrUrI7Crs}<=2,1,0)+
if(#{YYaRDUZyH9L.iIC4YhgrxQY}/#{YYaRDUZyH9L.zogrUrI7Crs}>1 && #{YYaRDUZyH9L.iIC4YhgrxQY}/#{YYaRDUZyH9L.zogrUrI7Crs}<=2,1,0)+
if(#{HVteopBt0jr.iIC4YhgrxQY}/#{HVteopBt0jr.zogrUrI7Crs}>1 && #{HVteopBt0jr.iIC4YhgrxQY}/#{HVteopBt0jr.zogrUrI7Crs}<=2,1,0)+
if(#{sWodd2tbjgZ.iIC4YhgrxQY}/#{sWodd2tbjgZ.zogrUrI7Crs}>1 && #{sWodd2tbjgZ.iIC4YhgrxQY}/#{sWodd2tbjgZ.zogrUrI7Crs}<=2,1,0)+
if(#{yVYajDDYUfX.iIC4YhgrxQY}/#{yVYajDDYUfX.zogrUrI7Crs}>1 && #{yVYajDDYUfX.iIC4YhgrxQY}/#{yVYajDDYUfX.zogrUrI7Crs}<=2,1,0)+
if(#{eTJAr4sc83v.iIC4YhgrxQY}/#{eTJAr4sc83v.zogrUrI7Crs}>1 && #{eTJAr4sc83v.iIC4YhgrxQY}/#{eTJAr4sc83v.zogrUrI7Crs}<=2,1,0)+
if(#{U4KSmanl4JP.iIC4YhgrxQY}/#{U4KSmanl4JP.zogrUrI7Crs}>1 && #{U4KSmanl4JP.iIC4YhgrxQY}/#{U4KSmanl4JP.zogrUrI7Crs}<=2,1,0)+
if(#{FXsa5uG3IGn.iIC4YhgrxQY}/#{FXsa5uG3IGn.zogrUrI7Crs}>1 && #{FXsa5uG3IGn.iIC4YhgrxQY}/#{FXsa5uG3IGn.zogrUrI7Crs}<=2,1,0)+
if(#{L34T9YDtCor.iIC4YhgrxQY}/#{L34T9YDtCor.zogrUrI7Crs}>1 && #{L34T9YDtCor.iIC4YhgrxQY}/#{L34T9YDtCor.zogrUrI7Crs}<=2,1,0)+
if(#{W5mHXhSYFfQ.iIC4YhgrxQY}/#{W5mHXhSYFfQ.zogrUrI7Crs}>1 && #{W5mHXhSYFfQ.iIC4YhgrxQY}/#{W5mHXhSYFfQ.zogrUrI7Crs}<=2,1,0)+
if(#{cmSUyJOZwyl.iIC4YhgrxQY}/#{cmSUyJOZwyl.zogrUrI7Crs}>1 && #{cmSUyJOZwyl.iIC4YhgrxQY}/#{cmSUyJOZwyl.zogrUrI7Crs}<=2,1,0)+
if(#{cT8sfosRXvU.iIC4YhgrxQY}/#{cT8sfosRXvU.zogrUrI7Crs}>1 && #{cT8sfosRXvU.iIC4YhgrxQY}/#{cT8sfosRXvU.zogrUrI7Crs}<=2,1,0)+
if(#{OaWKnMS7say.iIC4YhgrxQY}/#{OaWKnMS7say.zogrUrI7Crs}>1 && #{OaWKnMS7say.iIC4YhgrxQY}/#{OaWKnMS7say.zogrUrI7Crs}<=2,1,0)+
if(#{Z4bjHvGS6aH.iIC4YhgrxQY}/#{Z4bjHvGS6aH.zogrUrI7Crs}>1 && #{Z4bjHvGS6aH.iIC4YhgrxQY}/#{Z4bjHvGS6aH.zogrUrI7Crs}<=2,1,0)+
if(#{Nn1L7CNEtC8.iIC4YhgrxQY}/#{Nn1L7CNEtC8.zogrUrI7Crs}>1 && #{Nn1L7CNEtC8.iIC4YhgrxQY}/#{Nn1L7CNEtC8.zogrUrI7Crs}<=2,1,0)+
if(#{RNYKSc3nAUg.iIC4YhgrxQY}/#{RNYKSc3nAUg.zogrUrI7Crs}>1 && #{RNYKSc3nAUg.iIC4YhgrxQY}/#{RNYKSc3nAUg.zogrUrI7Crs}<=2,1,0)+
if(#{PtmZ9XqpPKi.iIC4YhgrxQY}/#{PtmZ9XqpPKi.zogrUrI7Crs}>1 && #{PtmZ9XqpPKi.iIC4YhgrxQY}/#{PtmZ9XqpPKi.zogrUrI7Crs}<=2,1,0)+
if(#{CohlLHi54B0.iIC4YhgrxQY}/#{CohlLHi54B0.zogrUrI7Crs}>1 && #{CohlLHi54B0.iIC4YhgrxQY}/#{CohlLHi54B0.zogrUrI7Crs}<=2,1,0)+
if(#{Gu6u82RD9OW.iIC4YhgrxQY}/#{Gu6u82RD9OW.zogrUrI7Crs}>1 && #{Gu6u82RD9OW.iIC4YhgrxQY}/#{Gu6u82RD9OW.zogrUrI7Crs}<=2,1,0)+
if(#{LiuYzxYr4Pt.iIC4YhgrxQY}/#{LiuYzxYr4Pt.zogrUrI7Crs}>1 && #{LiuYzxYr4Pt.iIC4YhgrxQY}/#{LiuYzxYr4Pt.zogrUrI7Crs}<=2,1,0)+
if(#{Tje33nJAG55.iIC4YhgrxQY}/#{Tje33nJAG55.zogrUrI7Crs}>1 && #{Tje33nJAG55.iIC4YhgrxQY}/#{Tje33nJAG55.zogrUrI7Crs}<=2,1,0)+
if(#{euM2dlqleYH.iIC4YhgrxQY}/#{euM2dlqleYH.zogrUrI7Crs}>1 && #{euM2dlqleYH.iIC4YhgrxQY}/#{euM2dlqleYH.zogrUrI7Crs}<=2,1,0)+
if(#{dASLmBTEehF.iIC4YhgrxQY}/#{dASLmBTEehF.zogrUrI7Crs}>1 && #{dASLmBTEehF.iIC4YhgrxQY}/#{dASLmBTEehF.zogrUrI7Crs}<=2,1,0)+
if(#{qU2LvzoPn1z.iIC4YhgrxQY}/#{qU2LvzoPn1z.zogrUrI7Crs}>1 && #{qU2LvzoPn1z.iIC4YhgrxQY}/#{qU2LvzoPn1z.zogrUrI7Crs}<=2,1,0)+
if(#{OkWaFxdUQY2.iIC4YhgrxQY}/#{OkWaFxdUQY2.zogrUrI7Crs}>1 && #{OkWaFxdUQY2.iIC4YhgrxQY}/#{OkWaFxdUQY2.zogrUrI7Crs}<=2,1,0)+
if(#{YHIv7KQc2e7.iIC4YhgrxQY}/#{YHIv7KQc2e7.zogrUrI7Crs}>1 && #{YHIv7KQc2e7.iIC4YhgrxQY}/#{YHIv7KQc2e7.zogrUrI7Crs}<=2,1,0)+
if(#{rt9D47Inb49.iIC4YhgrxQY}/#{rt9D47Inb49.zogrUrI7Crs}>1 && #{rt9D47Inb49.iIC4YhgrxQY}/#{rt9D47Inb49.zogrUrI7Crs}<=2,1,0)+
if(#{i1iXbquZ5iv.iIC4YhgrxQY}/#{i1iXbquZ5iv.zogrUrI7Crs}>1 && #{i1iXbquZ5iv.iIC4YhgrxQY}/#{i1iXbquZ5iv.zogrUrI7Crs}<=2,1,0)+
if(#{RcE30WBKrXI.iIC4YhgrxQY}/#{RcE30WBKrXI.zogrUrI7Crs}>1 && #{RcE30WBKrXI.iIC4YhgrxQY}/#{RcE30WBKrXI.zogrUrI7Crs}<=2,1,0)+
if(#{EAG0GfdSMAs.iIC4YhgrxQY}/#{EAG0GfdSMAs.zogrUrI7Crs}>1 && #{EAG0GfdSMAs.iIC4YhgrxQY}/#{EAG0GfdSMAs.zogrUrI7Crs}<=2,1,0)+
if(#{N2aXs7VlJdJ.iIC4YhgrxQY}/#{N2aXs7VlJdJ.zogrUrI7Crs}>1 && #{N2aXs7VlJdJ.iIC4YhgrxQY}/#{N2aXs7VlJdJ.zogrUrI7Crs}<=2,1,0)+
if(#{xrjnOtFFTRC.iIC4YhgrxQY}/#{xrjnOtFFTRC.zogrUrI7Crs}>1 && #{xrjnOtFFTRC.iIC4YhgrxQY}/#{xrjnOtFFTRC.zogrUrI7Crs}<=2,1,0)
>>
>>**Edit denominator**:  
>>>**Description**: "1-2 months - MSR - Denominator"  
>>>**Calculation**: "1"  
>
>**3 2-3 months - MSR**  
>For each item the Indicator returns "1" if the stock coverage time is greater than or equal to 2 but less than 3 and otherwise returns 0and then adds up these results for calculating the number of items with a stock coverage time greater of 2-3 months.
>>**Name \(*)**: "2-3 months"  
>>**Short Name \(*)**: "2-3 months - MSR"  
>>**Description**: "Number of items with a coverage time of 2-3 months"  
>>**Decimals in data output**: "0"  
>>**Indicator type \(*)**: "Number (Factor 1)"  
>>**Edit numerator**:  
>>>**Description**: "1-2 months - MSR - Numerator"  
>>>**Calculation**:  
if(#{LNAkkMTxqEW.iIC4YhgrxQY}/#{LNAkkMTxqEW.zogrUrI7Crs}>2 && #{LNAkkMTxqEW.iIC4YhgrxQY}/#{LNAkkMTxqEW.zogrUrI7Crs}<=3,1,0)+
if(#{WyDZKSw82X6.iIC4YhgrxQY}/#{WyDZKSw82X6.zogrUrI7Crs}>2 && #{WyDZKSw82X6.iIC4YhgrxQY}/#{WyDZKSw82X6.zogrUrI7Crs}<=3,1,0)+
if(#{JPccVwAGRq9.iIC4YhgrxQY}/#{JPccVwAGRq9.zogrUrI7Crs}>2 && #{JPccVwAGRq9.iIC4YhgrxQY}/#{JPccVwAGRq9.zogrUrI7Crs}<=3,1,0)+
if(#{smxJz7Mt6ia.iIC4YhgrxQY}/#{smxJz7Mt6ia.zogrUrI7Crs}>2 && #{smxJz7Mt6ia.iIC4YhgrxQY}/#{smxJz7Mt6ia.zogrUrI7Crs}<=3,1,0)+
if(#{AaIApgGQM6t.iIC4YhgrxQY}/#{AaIApgGQM6t.zogrUrI7Crs}>2 && #{AaIApgGQM6t.iIC4YhgrxQY}/#{AaIApgGQM6t.zogrUrI7Crs}<=3,1,0)+
if(#{vCTrmv52APd.iIC4YhgrxQY}/#{vCTrmv52APd.zogrUrI7Crs}>2 && #{vCTrmv52APd.iIC4YhgrxQY}/#{vCTrmv52APd.zogrUrI7Crs}<=3,1,0)+
if(#{SOw2TcuFFH2.iIC4YhgrxQY}/#{SOw2TcuFFH2.zogrUrI7Crs}>2 && #{SOw2TcuFFH2.iIC4YhgrxQY}/#{SOw2TcuFFH2.zogrUrI7Crs}<=3,1,0)+
if(#{RSIOx2u07Ln.iIC4YhgrxQY}/#{RSIOx2u07Ln.zogrUrI7Crs}>2 && #{RSIOx2u07Ln.iIC4YhgrxQY}/#{RSIOx2u07Ln.zogrUrI7Crs}<=3,1,0)+
if(#{JStiDyaPfqy.iIC4YhgrxQY}/#{JStiDyaPfqy.zogrUrI7Crs}>2 && #{JStiDyaPfqy.iIC4YhgrxQY}/#{JStiDyaPfqy.zogrUrI7Crs}<=3,1,0)+
if(#{hZ1YvdcTDQM.iIC4YhgrxQY}/#{hZ1YvdcTDQM.zogrUrI7Crs}>2 && #{hZ1YvdcTDQM.iIC4YhgrxQY}/#{hZ1YvdcTDQM.zogrUrI7Crs}<=3,1,0)+
if(#{tsi32D8HQd5.iIC4YhgrxQY}/#{tsi32D8HQd5.zogrUrI7Crs}>2 && #{tsi32D8HQd5.iIC4YhgrxQY}/#{tsi32D8HQd5.zogrUrI7Crs}<=3,1,0)+
if(#{QWlPF8S0gCc.iIC4YhgrxQY}/#{QWlPF8S0gCc.zogrUrI7Crs}>2 && #{QWlPF8S0gCc.iIC4YhgrxQY}/#{QWlPF8S0gCc.zogrUrI7Crs}<=3,1,0)+
if(#{a5uLTDt12eT.iIC4YhgrxQY}/#{a5uLTDt12eT.zogrUrI7Crs}>2 && #{a5uLTDt12eT.iIC4YhgrxQY}/#{a5uLTDt12eT.zogrUrI7Crs}<=3,1,0)+
if(#{U0AfOOyJMy2.iIC4YhgrxQY}/#{U0AfOOyJMy2.zogrUrI7Crs}>2 && #{U0AfOOyJMy2.iIC4YhgrxQY}/#{U0AfOOyJMy2.zogrUrI7Crs}<=3,1,0)+
if(#{cyf6UdScfFM.iIC4YhgrxQY}/#{cyf6UdScfFM.zogrUrI7Crs}>2 && #{cyf6UdScfFM.iIC4YhgrxQY}/#{cyf6UdScfFM.zogrUrI7Crs}<=3,1,0)+
if(#{FeUTTNHpVzD.iIC4YhgrxQY}/#{FeUTTNHpVzD.zogrUrI7Crs}>2 && #{FeUTTNHpVzD.iIC4YhgrxQY}/#{FeUTTNHpVzD.zogrUrI7Crs}<=3,1,0)+
if(#{mKSICD1rxG4.iIC4YhgrxQY}/#{mKSICD1rxG4.zogrUrI7Crs}>2 && #{mKSICD1rxG4.iIC4YhgrxQY}/#{mKSICD1rxG4.zogrUrI7Crs}<=3,1,0)+
if(#{mVNe1aS1pGl.iIC4YhgrxQY}/#{mVNe1aS1pGl.zogrUrI7Crs}>2 && #{mVNe1aS1pGl.iIC4YhgrxQY}/#{mVNe1aS1pGl.zogrUrI7Crs}<=3,1,0)+
if(#{oLAXTZY6ken.iIC4YhgrxQY}/#{oLAXTZY6ken.zogrUrI7Crs}>2 && #{oLAXTZY6ken.iIC4YhgrxQY}/#{oLAXTZY6ken.zogrUrI7Crs}<=3,1,0)+
if(#{YYaRDUZyH9L.iIC4YhgrxQY}/#{YYaRDUZyH9L.zogrUrI7Crs}>2 && #{YYaRDUZyH9L.iIC4YhgrxQY}/#{YYaRDUZyH9L.zogrUrI7Crs}<=3,1,0)+
if(#{HVteopBt0jr.iIC4YhgrxQY}/#{HVteopBt0jr.zogrUrI7Crs}>2 && #{HVteopBt0jr.iIC4YhgrxQY}/#{HVteopBt0jr.zogrUrI7Crs}<=3,1,0)+
if(#{sWodd2tbjgZ.iIC4YhgrxQY}/#{sWodd2tbjgZ.zogrUrI7Crs}>2 && #{sWodd2tbjgZ.iIC4YhgrxQY}/#{sWodd2tbjgZ.zogrUrI7Crs}<=3,1,0)+
if(#{yVYajDDYUfX.iIC4YhgrxQY}/#{yVYajDDYUfX.zogrUrI7Crs}>2 && #{yVYajDDYUfX.iIC4YhgrxQY}/#{yVYajDDYUfX.zogrUrI7Crs}<=3,1,0)+
if(#{eTJAr4sc83v.iIC4YhgrxQY}/#{eTJAr4sc83v.zogrUrI7Crs}>2 && #{eTJAr4sc83v.iIC4YhgrxQY}/#{eTJAr4sc83v.zogrUrI7Crs}<=3,1,0)+
if(#{U4KSmanl4JP.iIC4YhgrxQY}/#{U4KSmanl4JP.zogrUrI7Crs}>2 && #{U4KSmanl4JP.iIC4YhgrxQY}/#{U4KSmanl4JP.zogrUrI7Crs}<=3,1,0)+
if(#{FXsa5uG3IGn.iIC4YhgrxQY}/#{FXsa5uG3IGn.zogrUrI7Crs}>2 && #{FXsa5uG3IGn.iIC4YhgrxQY}/#{FXsa5uG3IGn.zogrUrI7Crs}<=3,1,0)+
if(#{L34T9YDtCor.iIC4YhgrxQY}/#{L34T9YDtCor.zogrUrI7Crs}>2 && #{L34T9YDtCor.iIC4YhgrxQY}/#{L34T9YDtCor.zogrUrI7Crs}<=3,1,0)+
if(#{W5mHXhSYFfQ.iIC4YhgrxQY}/#{W5mHXhSYFfQ.zogrUrI7Crs}>2 && #{W5mHXhSYFfQ.iIC4YhgrxQY}/#{W5mHXhSYFfQ.zogrUrI7Crs}<=3,1,0)+
if(#{cmSUyJOZwyl.iIC4YhgrxQY}/#{cmSUyJOZwyl.zogrUrI7Crs}>2 && #{cmSUyJOZwyl.iIC4YhgrxQY}/#{cmSUyJOZwyl.zogrUrI7Crs}<=3,1,0)+
if(#{cT8sfosRXvU.iIC4YhgrxQY}/#{cT8sfosRXvU.zogrUrI7Crs}>2 && #{cT8sfosRXvU.iIC4YhgrxQY}/#{cT8sfosRXvU.zogrUrI7Crs}<=3,1,0)+
if(#{OaWKnMS7say.iIC4YhgrxQY}/#{OaWKnMS7say.zogrUrI7Crs}>2 && #{OaWKnMS7say.iIC4YhgrxQY}/#{OaWKnMS7say.zogrUrI7Crs}<=3,1,0)+
if(#{Z4bjHvGS6aH.iIC4YhgrxQY}/#{Z4bjHvGS6aH.zogrUrI7Crs}>2 && #{Z4bjHvGS6aH.iIC4YhgrxQY}/#{Z4bjHvGS6aH.zogrUrI7Crs}<=3,1,0)+
if(#{Nn1L7CNEtC8.iIC4YhgrxQY}/#{Nn1L7CNEtC8.zogrUrI7Crs}>2 && #{Nn1L7CNEtC8.iIC4YhgrxQY}/#{Nn1L7CNEtC8.zogrUrI7Crs}<=3,1,0)+
if(#{RNYKSc3nAUg.iIC4YhgrxQY}/#{RNYKSc3nAUg.zogrUrI7Crs}>2 && #{RNYKSc3nAUg.iIC4YhgrxQY}/#{RNYKSc3nAUg.zogrUrI7Crs}<=3,1,0)+
if(#{PtmZ9XqpPKi.iIC4YhgrxQY}/#{PtmZ9XqpPKi.zogrUrI7Crs}>2 && #{PtmZ9XqpPKi.iIC4YhgrxQY}/#{PtmZ9XqpPKi.zogrUrI7Crs}<=3,1,0)+
if(#{CohlLHi54B0.iIC4YhgrxQY}/#{CohlLHi54B0.zogrUrI7Crs}>2 && #{CohlLHi54B0.iIC4YhgrxQY}/#{CohlLHi54B0.zogrUrI7Crs}<=3,1,0)+
if(#{Gu6u82RD9OW.iIC4YhgrxQY}/#{Gu6u82RD9OW.zogrUrI7Crs}>2 && #{Gu6u82RD9OW.iIC4YhgrxQY}/#{Gu6u82RD9OW.zogrUrI7Crs}<=3,1,0)+
if(#{LiuYzxYr4Pt.iIC4YhgrxQY}/#{LiuYzxYr4Pt.zogrUrI7Crs}>2 && #{LiuYzxYr4Pt.iIC4YhgrxQY}/#{LiuYzxYr4Pt.zogrUrI7Crs}<=3,1,0)+
if(#{Tje33nJAG55.iIC4YhgrxQY}/#{Tje33nJAG55.zogrUrI7Crs}>2 && #{Tje33nJAG55.iIC4YhgrxQY}/#{Tje33nJAG55.zogrUrI7Crs}<=3,1,0)+
if(#{euM2dlqleYH.iIC4YhgrxQY}/#{euM2dlqleYH.zogrUrI7Crs}>2 && #{euM2dlqleYH.iIC4YhgrxQY}/#{euM2dlqleYH.zogrUrI7Crs}<=3,1,0)+
if(#{dASLmBTEehF.iIC4YhgrxQY}/#{dASLmBTEehF.zogrUrI7Crs}>2 && #{dASLmBTEehF.iIC4YhgrxQY}/#{dASLmBTEehF.zogrUrI7Crs}<=3,1,0)+
if(#{qU2LvzoPn1z.iIC4YhgrxQY}/#{qU2LvzoPn1z.zogrUrI7Crs}>2 && #{qU2LvzoPn1z.iIC4YhgrxQY}/#{qU2LvzoPn1z.zogrUrI7Crs}<=3,1,0)+
if(#{OkWaFxdUQY2.iIC4YhgrxQY}/#{OkWaFxdUQY2.zogrUrI7Crs}>2 && #{OkWaFxdUQY2.iIC4YhgrxQY}/#{OkWaFxdUQY2.zogrUrI7Crs}<=3,1,0)+
if(#{YHIv7KQc2e7.iIC4YhgrxQY}/#{YHIv7KQc2e7.zogrUrI7Crs}>2 && #{YHIv7KQc2e7.iIC4YhgrxQY}/#{YHIv7KQc2e7.zogrUrI7Crs}<=3,1,0)+
if(#{rt9D47Inb49.iIC4YhgrxQY}/#{rt9D47Inb49.zogrUrI7Crs}>2 && #{rt9D47Inb49.iIC4YhgrxQY}/#{rt9D47Inb49.zogrUrI7Crs}<=3,1,0)+
if(#{i1iXbquZ5iv.iIC4YhgrxQY}/#{i1iXbquZ5iv.zogrUrI7Crs}>2 && #{i1iXbquZ5iv.iIC4YhgrxQY}/#{i1iXbquZ5iv.zogrUrI7Crs}<=3,1,0)+
if(#{RcE30WBKrXI.iIC4YhgrxQY}/#{RcE30WBKrXI.zogrUrI7Crs}>2 && #{RcE30WBKrXI.iIC4YhgrxQY}/#{RcE30WBKrXI.zogrUrI7Crs}<=3,1,0)+
if(#{EAG0GfdSMAs.iIC4YhgrxQY}/#{EAG0GfdSMAs.zogrUrI7Crs}>2 && #{EAG0GfdSMAs.iIC4YhgrxQY}/#{EAG0GfdSMAs.zogrUrI7Crs}<=3,1,0)+
if(#{N2aXs7VlJdJ.iIC4YhgrxQY}/#{N2aXs7VlJdJ.zogrUrI7Crs}>2 && #{N2aXs7VlJdJ.iIC4YhgrxQY}/#{N2aXs7VlJdJ.zogrUrI7Crs}<=3,1,0)+
if(#{xrjnOtFFTRC.iIC4YhgrxQY}/#{xrjnOtFFTRC.zogrUrI7Crs}>2 && #{xrjnOtFFTRC.iIC4YhgrxQY}/#{xrjnOtFFTRC.zogrUrI7Crs}<=3,1,0)
>>
>>**Edit denominator**:  
>>>**Description**: "2-3 months - MSR - Denominator"  
>>>**Calculation**: "1"  
>
>**4 3-4 months - MSR**  
>For each item the Indicator returns "1" if the stock coverage time is greater than or equal to 3 but less than 4 and otherwise returns 0and then adds up these results for calculating the number of items with a stock coverage time of 3-4 months. 
>>**Name \(*)**: "3-4 months - MSR"  
>>**Short Name \(*)**: "3-4 months - MSR"  
>>**Description**: "Number of items with a coverage time of 3-4 months"  
>>**Decimals in data output**: "0"  
>>**Indicator type \(*)**: "Number (Factor 1)"  
>>**Edit numerator**:  
>>>**Description**: "3-4 months - MSR - Numerator"  
>>>**Calculation**:  
if(#{LNAkkMTxqEW.iIC4YhgrxQY}/#{LNAkkMTxqEW.zogrUrI7Crs}>3 && #{LNAkkMTxqEW.iIC4YhgrxQY}/#{LNAkkMTxqEW.zogrUrI7Crs}<=4,1,0)+
if(#{WyDZKSw82X6.iIC4YhgrxQY}/#{WyDZKSw82X6.zogrUrI7Crs}>3 && #{WyDZKSw82X6.iIC4YhgrxQY}/#{WyDZKSw82X6.zogrUrI7Crs}<=4,1,0)+
if(#{JPccVwAGRq9.iIC4YhgrxQY}/#{JPccVwAGRq9.zogrUrI7Crs}>3 && #{JPccVwAGRq9.iIC4YhgrxQY}/#{JPccVwAGRq9.zogrUrI7Crs}<=4,1,0)+
if(#{smxJz7Mt6ia.iIC4YhgrxQY}/#{smxJz7Mt6ia.zogrUrI7Crs}>3 && #{smxJz7Mt6ia.iIC4YhgrxQY}/#{smxJz7Mt6ia.zogrUrI7Crs}<=4,1,0)+
if(#{AaIApgGQM6t.iIC4YhgrxQY}/#{AaIApgGQM6t.zogrUrI7Crs}>3 && #{AaIApgGQM6t.iIC4YhgrxQY}/#{AaIApgGQM6t.zogrUrI7Crs}<=4,1,0)+
if(#{vCTrmv52APd.iIC4YhgrxQY}/#{vCTrmv52APd.zogrUrI7Crs}>3 && #{vCTrmv52APd.iIC4YhgrxQY}/#{vCTrmv52APd.zogrUrI7Crs}<=4,1,0)+
if(#{SOw2TcuFFH2.iIC4YhgrxQY}/#{SOw2TcuFFH2.zogrUrI7Crs}>3 && #{SOw2TcuFFH2.iIC4YhgrxQY}/#{SOw2TcuFFH2.zogrUrI7Crs}<=4,1,0)+
if(#{RSIOx2u07Ln.iIC4YhgrxQY}/#{RSIOx2u07Ln.zogrUrI7Crs}>3 && #{RSIOx2u07Ln.iIC4YhgrxQY}/#{RSIOx2u07Ln.zogrUrI7Crs}<=4,1,0)+
if(#{JStiDyaPfqy.iIC4YhgrxQY}/#{JStiDyaPfqy.zogrUrI7Crs}>3 && #{JStiDyaPfqy.iIC4YhgrxQY}/#{JStiDyaPfqy.zogrUrI7Crs}<=4,1,0)+
if(#{hZ1YvdcTDQM.iIC4YhgrxQY}/#{hZ1YvdcTDQM.zogrUrI7Crs}>3 && #{hZ1YvdcTDQM.iIC4YhgrxQY}/#{hZ1YvdcTDQM.zogrUrI7Crs}<=4,1,0)+
if(#{tsi32D8HQd5.iIC4YhgrxQY}/#{tsi32D8HQd5.zogrUrI7Crs}>3 && #{tsi32D8HQd5.iIC4YhgrxQY}/#{tsi32D8HQd5.zogrUrI7Crs}<=4,1,0)+
if(#{QWlPF8S0gCc.iIC4YhgrxQY}/#{QWlPF8S0gCc.zogrUrI7Crs}>3 && #{QWlPF8S0gCc.iIC4YhgrxQY}/#{QWlPF8S0gCc.zogrUrI7Crs}<=4,1,0)+
if(#{a5uLTDt12eT.iIC4YhgrxQY}/#{a5uLTDt12eT.zogrUrI7Crs}>3 && #{a5uLTDt12eT.iIC4YhgrxQY}/#{a5uLTDt12eT.zogrUrI7Crs}<=4,1,0)+
if(#{U0AfOOyJMy2.iIC4YhgrxQY}/#{U0AfOOyJMy2.zogrUrI7Crs}>3 && #{U0AfOOyJMy2.iIC4YhgrxQY}/#{U0AfOOyJMy2.zogrUrI7Crs}<=4,1,0)+
if(#{cyf6UdScfFM.iIC4YhgrxQY}/#{cyf6UdScfFM.zogrUrI7Crs}>3 && #{cyf6UdScfFM.iIC4YhgrxQY}/#{cyf6UdScfFM.zogrUrI7Crs}<=4,1,0)+
if(#{FeUTTNHpVzD.iIC4YhgrxQY}/#{FeUTTNHpVzD.zogrUrI7Crs}>3 && #{FeUTTNHpVzD.iIC4YhgrxQY}/#{FeUTTNHpVzD.zogrUrI7Crs}<=4,1,0)+
if(#{mKSICD1rxG4.iIC4YhgrxQY}/#{mKSICD1rxG4.zogrUrI7Crs}>3 && #{mKSICD1rxG4.iIC4YhgrxQY}/#{mKSICD1rxG4.zogrUrI7Crs}<=4,1,0)+
if(#{mVNe1aS1pGl.iIC4YhgrxQY}/#{mVNe1aS1pGl.zogrUrI7Crs}>3 && #{mVNe1aS1pGl.iIC4YhgrxQY}/#{mVNe1aS1pGl.zogrUrI7Crs}<=4,1,0)+
if(#{oLAXTZY6ken.iIC4YhgrxQY}/#{oLAXTZY6ken.zogrUrI7Crs}>3 && #{oLAXTZY6ken.iIC4YhgrxQY}/#{oLAXTZY6ken.zogrUrI7Crs}<=4,1,0)+
if(#{YYaRDUZyH9L.iIC4YhgrxQY}/#{YYaRDUZyH9L.zogrUrI7Crs}>3 && #{YYaRDUZyH9L.iIC4YhgrxQY}/#{YYaRDUZyH9L.zogrUrI7Crs}<=4,1,0)+
if(#{HVteopBt0jr.iIC4YhgrxQY}/#{HVteopBt0jr.zogrUrI7Crs}>3 && #{HVteopBt0jr.iIC4YhgrxQY}/#{HVteopBt0jr.zogrUrI7Crs}<=4,1,0)+
if(#{sWodd2tbjgZ.iIC4YhgrxQY}/#{sWodd2tbjgZ.zogrUrI7Crs}>3 && #{sWodd2tbjgZ.iIC4YhgrxQY}/#{sWodd2tbjgZ.zogrUrI7Crs}<=4,1,0)+
if(#{yVYajDDYUfX.iIC4YhgrxQY}/#{yVYajDDYUfX.zogrUrI7Crs}>3 && #{yVYajDDYUfX.iIC4YhgrxQY}/#{yVYajDDYUfX.zogrUrI7Crs}<=4,1,0)+
if(#{eTJAr4sc83v.iIC4YhgrxQY}/#{eTJAr4sc83v.zogrUrI7Crs}>3 && #{eTJAr4sc83v.iIC4YhgrxQY}/#{eTJAr4sc83v.zogrUrI7Crs}<=4,1,0)+
if(#{U4KSmanl4JP.iIC4YhgrxQY}/#{U4KSmanl4JP.zogrUrI7Crs}>3 && #{U4KSmanl4JP.iIC4YhgrxQY}/#{U4KSmanl4JP.zogrUrI7Crs}<=4,1,0)+
if(#{FXsa5uG3IGn.iIC4YhgrxQY}/#{FXsa5uG3IGn.zogrUrI7Crs}>3 && #{FXsa5uG3IGn.iIC4YhgrxQY}/#{FXsa5uG3IGn.zogrUrI7Crs}<=4,1,0)+
if(#{L34T9YDtCor.iIC4YhgrxQY}/#{L34T9YDtCor.zogrUrI7Crs}>3 && #{L34T9YDtCor.iIC4YhgrxQY}/#{L34T9YDtCor.zogrUrI7Crs}<=4,1,0)+
if(#{W5mHXhSYFfQ.iIC4YhgrxQY}/#{W5mHXhSYFfQ.zogrUrI7Crs}>3 && #{W5mHXhSYFfQ.iIC4YhgrxQY}/#{W5mHXhSYFfQ.zogrUrI7Crs}<=4,1,0)+
if(#{cmSUyJOZwyl.iIC4YhgrxQY}/#{cmSUyJOZwyl.zogrUrI7Crs}>3 && #{cmSUyJOZwyl.iIC4YhgrxQY}/#{cmSUyJOZwyl.zogrUrI7Crs}<=4,1,0)+
if(#{cT8sfosRXvU.iIC4YhgrxQY}/#{cT8sfosRXvU.zogrUrI7Crs}>3 && #{cT8sfosRXvU.iIC4YhgrxQY}/#{cT8sfosRXvU.zogrUrI7Crs}<=4,1,0)+
if(#{OaWKnMS7say.iIC4YhgrxQY}/#{OaWKnMS7say.zogrUrI7Crs}>3 && #{OaWKnMS7say.iIC4YhgrxQY}/#{OaWKnMS7say.zogrUrI7Crs}<=4,1,0)+
if(#{Z4bjHvGS6aH.iIC4YhgrxQY}/#{Z4bjHvGS6aH.zogrUrI7Crs}>3 && #{Z4bjHvGS6aH.iIC4YhgrxQY}/#{Z4bjHvGS6aH.zogrUrI7Crs}<=4,1,0)+
if(#{Nn1L7CNEtC8.iIC4YhgrxQY}/#{Nn1L7CNEtC8.zogrUrI7Crs}>3 && #{Nn1L7CNEtC8.iIC4YhgrxQY}/#{Nn1L7CNEtC8.zogrUrI7Crs}<=4,1,0)+
if(#{RNYKSc3nAUg.iIC4YhgrxQY}/#{RNYKSc3nAUg.zogrUrI7Crs}>3 && #{RNYKSc3nAUg.iIC4YhgrxQY}/#{RNYKSc3nAUg.zogrUrI7Crs}<=4,1,0)+
if(#{PtmZ9XqpPKi.iIC4YhgrxQY}/#{PtmZ9XqpPKi.zogrUrI7Crs}>3 && #{PtmZ9XqpPKi.iIC4YhgrxQY}/#{PtmZ9XqpPKi.zogrUrI7Crs}<=4,1,0)+
if(#{CohlLHi54B0.iIC4YhgrxQY}/#{CohlLHi54B0.zogrUrI7Crs}>3 && #{CohlLHi54B0.iIC4YhgrxQY}/#{CohlLHi54B0.zogrUrI7Crs}<=4,1,0)+
if(#{Gu6u82RD9OW.iIC4YhgrxQY}/#{Gu6u82RD9OW.zogrUrI7Crs}>3 && #{Gu6u82RD9OW.iIC4YhgrxQY}/#{Gu6u82RD9OW.zogrUrI7Crs}<=4,1,0)+
if(#{LiuYzxYr4Pt.iIC4YhgrxQY}/#{LiuYzxYr4Pt.zogrUrI7Crs}>3 && #{LiuYzxYr4Pt.iIC4YhgrxQY}/#{LiuYzxYr4Pt.zogrUrI7Crs}<=4,1,0)+
if(#{Tje33nJAG55.iIC4YhgrxQY}/#{Tje33nJAG55.zogrUrI7Crs}>3 && #{Tje33nJAG55.iIC4YhgrxQY}/#{Tje33nJAG55.zogrUrI7Crs}<=4,1,0)+
if(#{euM2dlqleYH.iIC4YhgrxQY}/#{euM2dlqleYH.zogrUrI7Crs}>3 && #{euM2dlqleYH.iIC4YhgrxQY}/#{euM2dlqleYH.zogrUrI7Crs}<=4,1,0)+
if(#{dASLmBTEehF.iIC4YhgrxQY}/#{dASLmBTEehF.zogrUrI7Crs}>3 && #{dASLmBTEehF.iIC4YhgrxQY}/#{dASLmBTEehF.zogrUrI7Crs}<=4,1,0)+
if(#{qU2LvzoPn1z.iIC4YhgrxQY}/#{qU2LvzoPn1z.zogrUrI7Crs}>3 && #{qU2LvzoPn1z.iIC4YhgrxQY}/#{qU2LvzoPn1z.zogrUrI7Crs}<=4,1,0)+
if(#{OkWaFxdUQY2.iIC4YhgrxQY}/#{OkWaFxdUQY2.zogrUrI7Crs}>3 && #{OkWaFxdUQY2.iIC4YhgrxQY}/#{OkWaFxdUQY2.zogrUrI7Crs}<=4,1,0)+
if(#{YHIv7KQc2e7.iIC4YhgrxQY}/#{YHIv7KQc2e7.zogrUrI7Crs}>3 && #{YHIv7KQc2e7.iIC4YhgrxQY}/#{YHIv7KQc2e7.zogrUrI7Crs}<=4,1,0)+
if(#{rt9D47Inb49.iIC4YhgrxQY}/#{rt9D47Inb49.zogrUrI7Crs}>3 && #{rt9D47Inb49.iIC4YhgrxQY}/#{rt9D47Inb49.zogrUrI7Crs}<=4,1,0)+
if(#{i1iXbquZ5iv.iIC4YhgrxQY}/#{i1iXbquZ5iv.zogrUrI7Crs}>3 && #{i1iXbquZ5iv.iIC4YhgrxQY}/#{i1iXbquZ5iv.zogrUrI7Crs}<=4,1,0)+
if(#{RcE30WBKrXI.iIC4YhgrxQY}/#{RcE30WBKrXI.zogrUrI7Crs}>3 && #{RcE30WBKrXI.iIC4YhgrxQY}/#{RcE30WBKrXI.zogrUrI7Crs}<=4,1,0)+
if(#{EAG0GfdSMAs.iIC4YhgrxQY}/#{EAG0GfdSMAs.zogrUrI7Crs}>3 && #{EAG0GfdSMAs.iIC4YhgrxQY}/#{EAG0GfdSMAs.zogrUrI7Crs}<=4,1,0)+
if(#{N2aXs7VlJdJ.iIC4YhgrxQY}/#{N2aXs7VlJdJ.zogrUrI7Crs}>3 && #{N2aXs7VlJdJ.iIC4YhgrxQY}/#{N2aXs7VlJdJ.zogrUrI7Crs}<=4,1,0)+
if(#{xrjnOtFFTRC.iIC4YhgrxQY}/#{xrjnOtFFTRC.zogrUrI7Crs}>3 && #{xrjnOtFFTRC.iIC4YhgrxQY}/#{xrjnOtFFTRC.zogrUrI7Crs}<=4,1,0)>>
>>
>>**Edit denominator**:  
>>>**Description**: "3-4 months - MSR - Denominator"  
>>>**Calculation**: "1"  
>
>**5 4-5 months - MSR**  
>For each item the Indicator returns "1" if the stock coverage time is greater than or equal to 4 but less than 5 and otherwise returns 0and then adds up these results for calculating the number of items with a stock coverage time greater of 4-5 months.   
>>**Name \(*)**: "4-5 months - MSR"  
>>**Short Name \(*)**: "4-5 months - MSR"  
>>**Description**: "Number of items with a coverage time of 4-5 months"  
>>**Decimals in data output**: "0"  
>>**Indicator type \(*)**: "Number (Factor 1)"  
>>**Edit numerator**:  
>>>**Description**: "4-5 months - MSR - Numerator"  
>>>**Calculation**:  if(#{LNAkkMTxqEW.iIC4YhgrxQY}/#{LNAkkMTxqEW.zogrUrI7Crs}>4 && #{LNAkkMTxqEW.iIC4YhgrxQY}/#{LNAkkMTxqEW.zogrUrI7Crs}<=5,1,0)+
if(#{WyDZKSw82X6.iIC4YhgrxQY}/#{WyDZKSw82X6.zogrUrI7Crs}>4 && #{WyDZKSw82X6.iIC4YhgrxQY}/#{WyDZKSw82X6.zogrUrI7Crs}<=5,1,0)+
if(#{JPccVwAGRq9.iIC4YhgrxQY}/#{JPccVwAGRq9.zogrUrI7Crs}>4 && #{JPccVwAGRq9.iIC4YhgrxQY}/#{JPccVwAGRq9.zogrUrI7Crs}<=5,1,0)+
if(#{smxJz7Mt6ia.iIC4YhgrxQY}/#{smxJz7Mt6ia.zogrUrI7Crs}>4 && #{smxJz7Mt6ia.iIC4YhgrxQY}/#{smxJz7Mt6ia.zogrUrI7Crs}<=5,1,0)+
if(#{AaIApgGQM6t.iIC4YhgrxQY}/#{AaIApgGQM6t.zogrUrI7Crs}>4 && #{AaIApgGQM6t.iIC4YhgrxQY}/#{AaIApgGQM6t.zogrUrI7Crs}<=5,1,0)+
if(#{vCTrmv52APd.iIC4YhgrxQY}/#{vCTrmv52APd.zogrUrI7Crs}>4 && #{vCTrmv52APd.iIC4YhgrxQY}/#{vCTrmv52APd.zogrUrI7Crs}<=5,1,0)+
if(#{SOw2TcuFFH2.iIC4YhgrxQY}/#{SOw2TcuFFH2.zogrUrI7Crs}>4 && #{SOw2TcuFFH2.iIC4YhgrxQY}/#{SOw2TcuFFH2.zogrUrI7Crs}<=5,1,0)+
if(#{RSIOx2u07Ln.iIC4YhgrxQY}/#{RSIOx2u07Ln.zogrUrI7Crs}>4 && #{RSIOx2u07Ln.iIC4YhgrxQY}/#{RSIOx2u07Ln.zogrUrI7Crs}<=5,1,0)+
if(#{JStiDyaPfqy.iIC4YhgrxQY}/#{JStiDyaPfqy.zogrUrI7Crs}>4 && #{JStiDyaPfqy.iIC4YhgrxQY}/#{JStiDyaPfqy.zogrUrI7Crs}<=5,1,0)+
if(#{hZ1YvdcTDQM.iIC4YhgrxQY}/#{hZ1YvdcTDQM.zogrUrI7Crs}>4 && #{hZ1YvdcTDQM.iIC4YhgrxQY}/#{hZ1YvdcTDQM.zogrUrI7Crs}<=5,1,0)+
if(#{tsi32D8HQd5.iIC4YhgrxQY}/#{tsi32D8HQd5.zogrUrI7Crs}>4 && #{tsi32D8HQd5.iIC4YhgrxQY}/#{tsi32D8HQd5.zogrUrI7Crs}<=5,1,0)+
if(#{QWlPF8S0gCc.iIC4YhgrxQY}/#{QWlPF8S0gCc.zogrUrI7Crs}>4 && #{QWlPF8S0gCc.iIC4YhgrxQY}/#{QWlPF8S0gCc.zogrUrI7Crs}<=5,1,0)+
if(#{a5uLTDt12eT.iIC4YhgrxQY}/#{a5uLTDt12eT.zogrUrI7Crs}>4 && #{a5uLTDt12eT.iIC4YhgrxQY}/#{a5uLTDt12eT.zogrUrI7Crs}<=5,1,0)+
if(#{U0AfOOyJMy2.iIC4YhgrxQY}/#{U0AfOOyJMy2.zogrUrI7Crs}>4 && #{U0AfOOyJMy2.iIC4YhgrxQY}/#{U0AfOOyJMy2.zogrUrI7Crs}<=5,1,0)+
if(#{cyf6UdScfFM.iIC4YhgrxQY}/#{cyf6UdScfFM.zogrUrI7Crs}>4 && #{cyf6UdScfFM.iIC4YhgrxQY}/#{cyf6UdScfFM.zogrUrI7Crs}<=5,1,0)+
if(#{FeUTTNHpVzD.iIC4YhgrxQY}/#{FeUTTNHpVzD.zogrUrI7Crs}>4 && #{FeUTTNHpVzD.iIC4YhgrxQY}/#{FeUTTNHpVzD.zogrUrI7Crs}<=5,1,0)+
if(#{mKSICD1rxG4.iIC4YhgrxQY}/#{mKSICD1rxG4.zogrUrI7Crs}>4 && #{mKSICD1rxG4.iIC4YhgrxQY}/#{mKSICD1rxG4.zogrUrI7Crs}<=5,1,0)+
if(#{mVNe1aS1pGl.iIC4YhgrxQY}/#{mVNe1aS1pGl.zogrUrI7Crs}>4 && #{mVNe1aS1pGl.iIC4YhgrxQY}/#{mVNe1aS1pGl.zogrUrI7Crs}<=5,1,0)+
if(#{oLAXTZY6ken.iIC4YhgrxQY}/#{oLAXTZY6ken.zogrUrI7Crs}>4 && #{oLAXTZY6ken.iIC4YhgrxQY}/#{oLAXTZY6ken.zogrUrI7Crs}<=5,1,0)+
if(#{YYaRDUZyH9L.iIC4YhgrxQY}/#{YYaRDUZyH9L.zogrUrI7Crs}>4 && #{YYaRDUZyH9L.iIC4YhgrxQY}/#{YYaRDUZyH9L.zogrUrI7Crs}<=5,1,0)+
if(#{HVteopBt0jr.iIC4YhgrxQY}/#{HVteopBt0jr.zogrUrI7Crs}>4 && #{HVteopBt0jr.iIC4YhgrxQY}/#{HVteopBt0jr.zogrUrI7Crs}<=5,1,0)+
if(#{sWodd2tbjgZ.iIC4YhgrxQY}/#{sWodd2tbjgZ.zogrUrI7Crs}>4 && #{sWodd2tbjgZ.iIC4YhgrxQY}/#{sWodd2tbjgZ.zogrUrI7Crs}<=5,1,0)+
if(#{yVYajDDYUfX.iIC4YhgrxQY}/#{yVYajDDYUfX.zogrUrI7Crs}>4 && #{yVYajDDYUfX.iIC4YhgrxQY}/#{yVYajDDYUfX.zogrUrI7Crs}<=5,1,0)+
if(#{eTJAr4sc83v.iIC4YhgrxQY}/#{eTJAr4sc83v.zogrUrI7Crs}>4 && #{eTJAr4sc83v.iIC4YhgrxQY}/#{eTJAr4sc83v.zogrUrI7Crs}<=5,1,0)+
if(#{U4KSmanl4JP.iIC4YhgrxQY}/#{U4KSmanl4JP.zogrUrI7Crs}>4 && #{U4KSmanl4JP.iIC4YhgrxQY}/#{U4KSmanl4JP.zogrUrI7Crs}<=5,1,0)+
if(#{FXsa5uG3IGn.iIC4YhgrxQY}/#{FXsa5uG3IGn.zogrUrI7Crs}>4 && #{FXsa5uG3IGn.iIC4YhgrxQY}/#{FXsa5uG3IGn.zogrUrI7Crs}<=5,1,0)+
if(#{L34T9YDtCor.iIC4YhgrxQY}/#{L34T9YDtCor.zogrUrI7Crs}>4 && #{L34T9YDtCor.iIC4YhgrxQY}/#{L34T9YDtCor.zogrUrI7Crs}<=5,1,0)+
if(#{W5mHXhSYFfQ.iIC4YhgrxQY}/#{W5mHXhSYFfQ.zogrUrI7Crs}>4 && #{W5mHXhSYFfQ.iIC4YhgrxQY}/#{W5mHXhSYFfQ.zogrUrI7Crs}<=5,1,0)+
if(#{cmSUyJOZwyl.iIC4YhgrxQY}/#{cmSUyJOZwyl.zogrUrI7Crs}>4 && #{cmSUyJOZwyl.iIC4YhgrxQY}/#{cmSUyJOZwyl.zogrUrI7Crs}<=5,1,0)+
if(#{cT8sfosRXvU.iIC4YhgrxQY}/#{cT8sfosRXvU.zogrUrI7Crs}>4 && #{cT8sfosRXvU.iIC4YhgrxQY}/#{cT8sfosRXvU.zogrUrI7Crs}<=5,1,0)+
if(#{OaWKnMS7say.iIC4YhgrxQY}/#{OaWKnMS7say.zogrUrI7Crs}>4 && #{OaWKnMS7say.iIC4YhgrxQY}/#{OaWKnMS7say.zogrUrI7Crs}<=5,1,0)+
if(#{Z4bjHvGS6aH.iIC4YhgrxQY}/#{Z4bjHvGS6aH.zogrUrI7Crs}>4 && #{Z4bjHvGS6aH.iIC4YhgrxQY}/#{Z4bjHvGS6aH.zogrUrI7Crs}<=5,1,0)+
if(#{Nn1L7CNEtC8.iIC4YhgrxQY}/#{Nn1L7CNEtC8.zogrUrI7Crs}>4 && #{Nn1L7CNEtC8.iIC4YhgrxQY}/#{Nn1L7CNEtC8.zogrUrI7Crs}<=5,1,0)+
if(#{RNYKSc3nAUg.iIC4YhgrxQY}/#{RNYKSc3nAUg.zogrUrI7Crs}>4 && #{RNYKSc3nAUg.iIC4YhgrxQY}/#{RNYKSc3nAUg.zogrUrI7Crs}<=5,1,0)+
if(#{PtmZ9XqpPKi.iIC4YhgrxQY}/#{PtmZ9XqpPKi.zogrUrI7Crs}>4 && #{PtmZ9XqpPKi.iIC4YhgrxQY}/#{PtmZ9XqpPKi.zogrUrI7Crs}<=5,1,0)+
if(#{CohlLHi54B0.iIC4YhgrxQY}/#{CohlLHi54B0.zogrUrI7Crs}>4 && #{CohlLHi54B0.iIC4YhgrxQY}/#{CohlLHi54B0.zogrUrI7Crs}<=5,1,0)+
if(#{Gu6u82RD9OW.iIC4YhgrxQY}/#{Gu6u82RD9OW.zogrUrI7Crs}>4 && #{Gu6u82RD9OW.iIC4YhgrxQY}/#{Gu6u82RD9OW.zogrUrI7Crs}<=5,1,0)+
if(#{LiuYzxYr4Pt.iIC4YhgrxQY}/#{LiuYzxYr4Pt.zogrUrI7Crs}>4 && #{LiuYzxYr4Pt.iIC4YhgrxQY}/#{LiuYzxYr4Pt.zogrUrI7Crs}<=5,1,0)+
if(#{Tje33nJAG55.iIC4YhgrxQY}/#{Tje33nJAG55.zogrUrI7Crs}>4 && #{Tje33nJAG55.iIC4YhgrxQY}/#{Tje33nJAG55.zogrUrI7Crs}<=5,1,0)+
if(#{euM2dlqleYH.iIC4YhgrxQY}/#{euM2dlqleYH.zogrUrI7Crs}>4 && #{euM2dlqleYH.iIC4YhgrxQY}/#{euM2dlqleYH.zogrUrI7Crs}<=5,1,0)+
if(#{dASLmBTEehF.iIC4YhgrxQY}/#{dASLmBTEehF.zogrUrI7Crs}>4 && #{dASLmBTEehF.iIC4YhgrxQY}/#{dASLmBTEehF.zogrUrI7Crs}<=5,1,0)+
if(#{qU2LvzoPn1z.iIC4YhgrxQY}/#{qU2LvzoPn1z.zogrUrI7Crs}>4 && #{qU2LvzoPn1z.iIC4YhgrxQY}/#{qU2LvzoPn1z.zogrUrI7Crs}<=5,1,0)+
if(#{OkWaFxdUQY2.iIC4YhgrxQY}/#{OkWaFxdUQY2.zogrUrI7Crs}>4 && #{OkWaFxdUQY2.iIC4YhgrxQY}/#{OkWaFxdUQY2.zogrUrI7Crs}<=5,1,0)+
if(#{YHIv7KQc2e7.iIC4YhgrxQY}/#{YHIv7KQc2e7.zogrUrI7Crs}>4 && #{YHIv7KQc2e7.iIC4YhgrxQY}/#{YHIv7KQc2e7.zogrUrI7Crs}<=5,1,0)+
if(#{rt9D47Inb49.iIC4YhgrxQY}/#{rt9D47Inb49.zogrUrI7Crs}>4 && #{rt9D47Inb49.iIC4YhgrxQY}/#{rt9D47Inb49.zogrUrI7Crs}<=5,1,0)+
if(#{i1iXbquZ5iv.iIC4YhgrxQY}/#{i1iXbquZ5iv.zogrUrI7Crs}>4 && #{i1iXbquZ5iv.iIC4YhgrxQY}/#{i1iXbquZ5iv.zogrUrI7Crs}<=5,1,0)+
if(#{RcE30WBKrXI.iIC4YhgrxQY}/#{RcE30WBKrXI.zogrUrI7Crs}>4 && #{RcE30WBKrXI.iIC4YhgrxQY}/#{RcE30WBKrXI.zogrUrI7Crs}<=5,1,0)+
if(#{EAG0GfdSMAs.iIC4YhgrxQY}/#{EAG0GfdSMAs.zogrUrI7Crs}>4 && #{EAG0GfdSMAs.iIC4YhgrxQY}/#{EAG0GfdSMAs.zogrUrI7Crs}<=5,1,0)+
if(#{N2aXs7VlJdJ.iIC4YhgrxQY}/#{N2aXs7VlJdJ.zogrUrI7Crs}>4 && #{N2aXs7VlJdJ.iIC4YhgrxQY}/#{N2aXs7VlJdJ.zogrUrI7Crs}<=5,1,0)+
if(#{xrjnOtFFTRC.iIC4YhgrxQY}/#{xrjnOtFFTRC.zogrUrI7Crs}>4 && #{xrjnOtFFTRC.iIC4YhgrxQY}/#{xrjnOtFFTRC.zogrUrI7Crs}<=5,1,0)
>>
>>**Edit denominator**:
>>>**Description**: "4-5 months - MSR - Denominator"
>>>**Calculation**: "1"
>
>**6 5-6 months - MSR**  
>For each item the Indicator returns "1" if the stock coverage time is greater than or equal to 5 but less than 6 and otherwise returns 0 and then adds up these results for calculating the number of items with a stock coverage of 5-6 months. 
>>**Name \(*)**: "5-6 months"  
>>**Short Name \(*)**: "5-6 months - MSR"  
>>**Description**: "Number of items with a coverage time of 5-6 months"  
>>**Decimals in data output**: "0"  
>>**Indicator type \(*)**: "Number (Factor 1)"  
>>**Edit numerator**:  
>>>**Description**: "O-1 months - MSR - Numerator"  
>>>**Calculation**:  if(#{LNAkkMTxqEW.iIC4YhgrxQY}/#{LNAkkMTxqEW.zogrUrI7Crs}>5 && #{LNAkkMTxqEW.iIC4YhgrxQY}/#{LNAkkMTxqEW.zogrUrI7Crs}<=6,1,0)+
if(#{WyDZKSw82X6.iIC4YhgrxQY}/#{WyDZKSw82X6.zogrUrI7Crs}>5 && #{WyDZKSw82X6.iIC4YhgrxQY}/#{WyDZKSw82X6.zogrUrI7Crs}<=6,1,0)+
if(#{JPccVwAGRq9.iIC4YhgrxQY}/#{JPccVwAGRq9.zogrUrI7Crs}>5 && #{JPccVwAGRq9.iIC4YhgrxQY}/#{JPccVwAGRq9.zogrUrI7Crs}<=6,1,0)+
if(#{smxJz7Mt6ia.iIC4YhgrxQY}/#{smxJz7Mt6ia.zogrUrI7Crs}>5 && #{smxJz7Mt6ia.iIC4YhgrxQY}/#{smxJz7Mt6ia.zogrUrI7Crs}<=6,1,0)+
if(#{AaIApgGQM6t.iIC4YhgrxQY}/#{AaIApgGQM6t.zogrUrI7Crs}>5 && #{AaIApgGQM6t.iIC4YhgrxQY}/#{AaIApgGQM6t.zogrUrI7Crs}<=6,1,0)+
if(#{vCTrmv52APd.iIC4YhgrxQY}/#{vCTrmv52APd.zogrUrI7Crs}>5 && #{vCTrmv52APd.iIC4YhgrxQY}/#{vCTrmv52APd.zogrUrI7Crs}<=6,1,0)+
if(#{SOw2TcuFFH2.iIC4YhgrxQY}/#{SOw2TcuFFH2.zogrUrI7Crs}>5 && #{SOw2TcuFFH2.iIC4YhgrxQY}/#{SOw2TcuFFH2.zogrUrI7Crs}<=6,1,0)+
if(#{RSIOx2u07Ln.iIC4YhgrxQY}/#{RSIOx2u07Ln.zogrUrI7Crs}>5 && #{RSIOx2u07Ln.iIC4YhgrxQY}/#{RSIOx2u07Ln.zogrUrI7Crs}<=6,1,0)+
if(#{JStiDyaPfqy.iIC4YhgrxQY}/#{JStiDyaPfqy.zogrUrI7Crs}>5 && #{JStiDyaPfqy.iIC4YhgrxQY}/#{JStiDyaPfqy.zogrUrI7Crs}<=6,1,0)+
if(#{hZ1YvdcTDQM.iIC4YhgrxQY}/#{hZ1YvdcTDQM.zogrUrI7Crs}>5 && #{hZ1YvdcTDQM.iIC4YhgrxQY}/#{hZ1YvdcTDQM.zogrUrI7Crs}<=6,1,0)+
if(#{tsi32D8HQd5.iIC4YhgrxQY}/#{tsi32D8HQd5.zogrUrI7Crs}>5 && #{tsi32D8HQd5.iIC4YhgrxQY}/#{tsi32D8HQd5.zogrUrI7Crs}<=6,1,0)+
if(#{QWlPF8S0gCc.iIC4YhgrxQY}/#{QWlPF8S0gCc.zogrUrI7Crs}>5 && #{QWlPF8S0gCc.iIC4YhgrxQY}/#{QWlPF8S0gCc.zogrUrI7Crs}<=6,1,0)+
if(#{a5uLTDt12eT.iIC4YhgrxQY}/#{a5uLTDt12eT.zogrUrI7Crs}>5 && #{a5uLTDt12eT.iIC4YhgrxQY}/#{a5uLTDt12eT.zogrUrI7Crs}<=6,1,0)+
if(#{U0AfOOyJMy2.iIC4YhgrxQY}/#{U0AfOOyJMy2.zogrUrI7Crs}>5 && #{U0AfOOyJMy2.iIC4YhgrxQY}/#{U0AfOOyJMy2.zogrUrI7Crs}<=6,1,0)+
if(#{cyf6UdScfFM.iIC4YhgrxQY}/#{cyf6UdScfFM.zogrUrI7Crs}>5 && #{cyf6UdScfFM.iIC4YhgrxQY}/#{cyf6UdScfFM.zogrUrI7Crs}<=6,1,0)+
if(#{FeUTTNHpVzD.iIC4YhgrxQY}/#{FeUTTNHpVzD.zogrUrI7Crs}>5 && #{FeUTTNHpVzD.iIC4YhgrxQY}/#{FeUTTNHpVzD.zogrUrI7Crs}<=6,1,0)+
if(#{mKSICD1rxG4.iIC4YhgrxQY}/#{mKSICD1rxG4.zogrUrI7Crs}>5 && #{mKSICD1rxG4.iIC4YhgrxQY}/#{mKSICD1rxG4.zogrUrI7Crs}<=6,1,0)+
if(#{mVNe1aS1pGl.iIC4YhgrxQY}/#{mVNe1aS1pGl.zogrUrI7Crs}>5 && #{mVNe1aS1pGl.iIC4YhgrxQY}/#{mVNe1aS1pGl.zogrUrI7Crs}<=6,1,0)+
if(#{oLAXTZY6ken.iIC4YhgrxQY}/#{oLAXTZY6ken.zogrUrI7Crs}>5 && #{oLAXTZY6ken.iIC4YhgrxQY}/#{oLAXTZY6ken.zogrUrI7Crs}<=6,1,0)+
if(#{YYaRDUZyH9L.iIC4YhgrxQY}/#{YYaRDUZyH9L.zogrUrI7Crs}>5 && #{YYaRDUZyH9L.iIC4YhgrxQY}/#{YYaRDUZyH9L.zogrUrI7Crs}<=6,1,0)+
if(#{HVteopBt0jr.iIC4YhgrxQY}/#{HVteopBt0jr.zogrUrI7Crs}>5 && #{HVteopBt0jr.iIC4YhgrxQY}/#{HVteopBt0jr.zogrUrI7Crs}<=6,1,0)+
if(#{sWodd2tbjgZ.iIC4YhgrxQY}/#{sWodd2tbjgZ.zogrUrI7Crs}>5 && #{sWodd2tbjgZ.iIC4YhgrxQY}/#{sWodd2tbjgZ.zogrUrI7Crs}<=6,1,0)+
if(#{yVYajDDYUfX.iIC4YhgrxQY}/#{yVYajDDYUfX.zogrUrI7Crs}>5 && #{yVYajDDYUfX.iIC4YhgrxQY}/#{yVYajDDYUfX.zogrUrI7Crs}<=6,1,0)+
if(#{eTJAr4sc83v.iIC4YhgrxQY}/#{eTJAr4sc83v.zogrUrI7Crs}>5 && #{eTJAr4sc83v.iIC4YhgrxQY}/#{eTJAr4sc83v.zogrUrI7Crs}<=6,1,0)+
if(#{U4KSmanl4JP.iIC4YhgrxQY}/#{U4KSmanl4JP.zogrUrI7Crs}>5 && #{U4KSmanl4JP.iIC4YhgrxQY}/#{U4KSmanl4JP.zogrUrI7Crs}<=6,1,0)+
if(#{FXsa5uG3IGn.iIC4YhgrxQY}/#{FXsa5uG3IGn.zogrUrI7Crs}>5 && #{FXsa5uG3IGn.iIC4YhgrxQY}/#{FXsa5uG3IGn.zogrUrI7Crs}<=6,1,0)+
if(#{L34T9YDtCor.iIC4YhgrxQY}/#{L34T9YDtCor.zogrUrI7Crs}>5 && #{L34T9YDtCor.iIC4YhgrxQY}/#{L34T9YDtCor.zogrUrI7Crs}<=6,1,0)+
if(#{W5mHXhSYFfQ.iIC4YhgrxQY}/#{W5mHXhSYFfQ.zogrUrI7Crs}>5 && #{W5mHXhSYFfQ.iIC4YhgrxQY}/#{W5mHXhSYFfQ.zogrUrI7Crs}<=6,1,0)+
if(#{cmSUyJOZwyl.iIC4YhgrxQY}/#{cmSUyJOZwyl.zogrUrI7Crs}>5 && #{cmSUyJOZwyl.iIC4YhgrxQY}/#{cmSUyJOZwyl.zogrUrI7Crs}<=6,1,0)+
if(#{cT8sfosRXvU.iIC4YhgrxQY}/#{cT8sfosRXvU.zogrUrI7Crs}>5 && #{cT8sfosRXvU.iIC4YhgrxQY}/#{cT8sfosRXvU.zogrUrI7Crs}<=6,1,0)+
if(#{OaWKnMS7say.iIC4YhgrxQY}/#{OaWKnMS7say.zogrUrI7Crs}>5 && #{OaWKnMS7say.iIC4YhgrxQY}/#{OaWKnMS7say.zogrUrI7Crs}<=6,1,0)+
if(#{Z4bjHvGS6aH.iIC4YhgrxQY}/#{Z4bjHvGS6aH.zogrUrI7Crs}>5 && #{Z4bjHvGS6aH.iIC4YhgrxQY}/#{Z4bjHvGS6aH.zogrUrI7Crs}<=6,1,0)+
if(#{Nn1L7CNEtC8.iIC4YhgrxQY}/#{Nn1L7CNEtC8.zogrUrI7Crs}>5 && #{Nn1L7CNEtC8.iIC4YhgrxQY}/#{Nn1L7CNEtC8.zogrUrI7Crs}<=6,1,0)+
if(#{RNYKSc3nAUg.iIC4YhgrxQY}/#{RNYKSc3nAUg.zogrUrI7Crs}>5 && #{RNYKSc3nAUg.iIC4YhgrxQY}/#{RNYKSc3nAUg.zogrUrI7Crs}<=6,1,0)+
if(#{PtmZ9XqpPKi.iIC4YhgrxQY}/#{PtmZ9XqpPKi.zogrUrI7Crs}>5 && #{PtmZ9XqpPKi.iIC4YhgrxQY}/#{PtmZ9XqpPKi.zogrUrI7Crs}<=6,1,0)+
if(#{CohlLHi54B0.iIC4YhgrxQY}/#{CohlLHi54B0.zogrUrI7Crs}>5 && #{CohlLHi54B0.iIC4YhgrxQY}/#{CohlLHi54B0.zogrUrI7Crs}<=6,1,0)+
if(#{Gu6u82RD9OW.iIC4YhgrxQY}/#{Gu6u82RD9OW.zogrUrI7Crs}>5 && #{Gu6u82RD9OW.iIC4YhgrxQY}/#{Gu6u82RD9OW.zogrUrI7Crs}<=6,1,0)+
if(#{LiuYzxYr4Pt.iIC4YhgrxQY}/#{LiuYzxYr4Pt.zogrUrI7Crs}>5 && #{LiuYzxYr4Pt.iIC4YhgrxQY}/#{LiuYzxYr4Pt.zogrUrI7Crs}<=6,1,0)+
if(#{Tje33nJAG55.iIC4YhgrxQY}/#{Tje33nJAG55.zogrUrI7Crs}>5 && #{Tje33nJAG55.iIC4YhgrxQY}/#{Tje33nJAG55.zogrUrI7Crs}<=6,1,0)+
if(#{euM2dlqleYH.iIC4YhgrxQY}/#{euM2dlqleYH.zogrUrI7Crs}>5 && #{euM2dlqleYH.iIC4YhgrxQY}/#{euM2dlqleYH.zogrUrI7Crs}<=6,1,0)+
if(#{dASLmBTEehF.iIC4YhgrxQY}/#{dASLmBTEehF.zogrUrI7Crs}>5 && #{dASLmBTEehF.iIC4YhgrxQY}/#{dASLmBTEehF.zogrUrI7Crs}<=6,1,0)+
if(#{qU2LvzoPn1z.iIC4YhgrxQY}/#{qU2LvzoPn1z.zogrUrI7Crs}>5 && #{qU2LvzoPn1z.iIC4YhgrxQY}/#{qU2LvzoPn1z.zogrUrI7Crs}<=6,1,0)+
if(#{OkWaFxdUQY2.iIC4YhgrxQY}/#{OkWaFxdUQY2.zogrUrI7Crs}>5 && #{OkWaFxdUQY2.iIC4YhgrxQY}/#{OkWaFxdUQY2.zogrUrI7Crs}<=6,1,0)+
if(#{YHIv7KQc2e7.iIC4YhgrxQY}/#{YHIv7KQc2e7.zogrUrI7Crs}>5 && #{YHIv7KQc2e7.iIC4YhgrxQY}/#{YHIv7KQc2e7.zogrUrI7Crs}<=6,1,0)+
if(#{rt9D47Inb49.iIC4YhgrxQY}/#{rt9D47Inb49.zogrUrI7Crs}>5 && #{rt9D47Inb49.iIC4YhgrxQY}/#{rt9D47Inb49.zogrUrI7Crs}<=6,1,0)+
if(#{i1iXbquZ5iv.iIC4YhgrxQY}/#{i1iXbquZ5iv.zogrUrI7Crs}>5 && #{i1iXbquZ5iv.iIC4YhgrxQY}/#{i1iXbquZ5iv.zogrUrI7Crs}<=6,1,0)+
if(#{RcE30WBKrXI.iIC4YhgrxQY}/#{RcE30WBKrXI.zogrUrI7Crs}>5 && #{RcE30WBKrXI.iIC4YhgrxQY}/#{RcE30WBKrXI.zogrUrI7Crs}<=6,1,0)+
if(#{EAG0GfdSMAs.iIC4YhgrxQY}/#{EAG0GfdSMAs.zogrUrI7Crs}>5 && #{EAG0GfdSMAs.iIC4YhgrxQY}/#{EAG0GfdSMAs.zogrUrI7Crs}<=6,1,0)+
if(#{N2aXs7VlJdJ.iIC4YhgrxQY}/#{N2aXs7VlJdJ.zogrUrI7Crs}>5 && #{N2aXs7VlJdJ.iIC4YhgrxQY}/#{N2aXs7VlJdJ.zogrUrI7Crs}<=6,1,0)+
if(#{xrjnOtFFTRC.iIC4YhgrxQY}/#{xrjnOtFFTRC.zogrUrI7Crs}>5 && #{xrjnOtFFTRC.iIC4YhgrxQY}/#{xrjnOtFFTRC.zogrUrI7Crs}<=6,1,0)
>>
>>**Edit denominator**:  
>>>**Description**: "5-6 months - MSR - Denominator"  
>>>**Calculation**: "1"  
>
>**7 6-7 months - MSR**  
>For each item the Indicator returns "1" if the stock coverage time is greater than or equal to 6 but less than 7 and otherwise returns 0and then adds up these results for calculating the number of items with a stock coverage time of 6-7 months. 
>>**Name \(*)**: "6-7 months - MSR"  
>>**Short Name \(*)**: "6-7 months - MSR"  
>>**Description**: "Number of items with a coverage time of 6-7 months"  
>>**Decimals in data output**: "0"  
>>**Indicator type \(*)**: "Number (Factor 1)"  
>>**Edit numerator**:  
>>>**Description**: "6-7 months - MSR - Numerator"  
>>>**Calculation**:  if(#{LNAkkMTxqEW.iIC4YhgrxQY}/#{LNAkkMTxqEW.zogrUrI7Crs}>6 && #{LNAkkMTxqEW.iIC4YhgrxQY}/#{LNAkkMTxqEW.zogrUrI7Crs}<=7,1,0)+
if(#{WyDZKSw82X6.iIC4YhgrxQY}/#{WyDZKSw82X6.zogrUrI7Crs}>6 && #{WyDZKSw82X6.iIC4YhgrxQY}/#{WyDZKSw82X6.zogrUrI7Crs}<=7,1,0)+
if(#{JPccVwAGRq9.iIC4YhgrxQY}/#{JPccVwAGRq9.zogrUrI7Crs}>6 && #{JPccVwAGRq9.iIC4YhgrxQY}/#{JPccVwAGRq9.zogrUrI7Crs}<=7,1,0)+
if(#{smxJz7Mt6ia.iIC4YhgrxQY}/#{smxJz7Mt6ia.zogrUrI7Crs}>6 && #{smxJz7Mt6ia.iIC4YhgrxQY}/#{smxJz7Mt6ia.zogrUrI7Crs}<=7,1,0)+
if(#{AaIApgGQM6t.iIC4YhgrxQY}/#{AaIApgGQM6t.zogrUrI7Crs}>6 && #{AaIApgGQM6t.iIC4YhgrxQY}/#{AaIApgGQM6t.zogrUrI7Crs}<=7,1,0)+
if(#{vCTrmv52APd.iIC4YhgrxQY}/#{vCTrmv52APd.zogrUrI7Crs}>6 && #{vCTrmv52APd.iIC4YhgrxQY}/#{vCTrmv52APd.zogrUrI7Crs}<=7,1,0)+
if(#{SOw2TcuFFH2.iIC4YhgrxQY}/#{SOw2TcuFFH2.zogrUrI7Crs}>6 && #{SOw2TcuFFH2.iIC4YhgrxQY}/#{SOw2TcuFFH2.zogrUrI7Crs}<=7,1,0)+
if(#{RSIOx2u07Ln.iIC4YhgrxQY}/#{RSIOx2u07Ln.zogrUrI7Crs}>6 && #{RSIOx2u07Ln.iIC4YhgrxQY}/#{RSIOx2u07Ln.zogrUrI7Crs}<=7,1,0)+
if(#{JStiDyaPfqy.iIC4YhgrxQY}/#{JStiDyaPfqy.zogrUrI7Crs}>6 && #{JStiDyaPfqy.iIC4YhgrxQY}/#{JStiDyaPfqy.zogrUrI7Crs}<=7,1,0)+
if(#{hZ1YvdcTDQM.iIC4YhgrxQY}/#{hZ1YvdcTDQM.zogrUrI7Crs}>6 && #{hZ1YvdcTDQM.iIC4YhgrxQY}/#{hZ1YvdcTDQM.zogrUrI7Crs}<=7,1,0)+
if(#{tsi32D8HQd5.iIC4YhgrxQY}/#{tsi32D8HQd5.zogrUrI7Crs}>6 && #{tsi32D8HQd5.iIC4YhgrxQY}/#{tsi32D8HQd5.zogrUrI7Crs}<=7,1,0)+
if(#{QWlPF8S0gCc.iIC4YhgrxQY}/#{QWlPF8S0gCc.zogrUrI7Crs}>6 && #{QWlPF8S0gCc.iIC4YhgrxQY}/#{QWlPF8S0gCc.zogrUrI7Crs}<=7,1,0)+
if(#{a5uLTDt12eT.iIC4YhgrxQY}/#{a5uLTDt12eT.zogrUrI7Crs}>6 && #{a5uLTDt12eT.iIC4YhgrxQY}/#{a5uLTDt12eT.zogrUrI7Crs}<=7,1,0)+
if(#{U0AfOOyJMy2.iIC4YhgrxQY}/#{U0AfOOyJMy2.zogrUrI7Crs}>6 && #{U0AfOOyJMy2.iIC4YhgrxQY}/#{U0AfOOyJMy2.zogrUrI7Crs}<=7,1,0)+
if(#{cyf6UdScfFM.iIC4YhgrxQY}/#{cyf6UdScfFM.zogrUrI7Crs}>6 && #{cyf6UdScfFM.iIC4YhgrxQY}/#{cyf6UdScfFM.zogrUrI7Crs}<=7,1,0)+
if(#{FeUTTNHpVzD.iIC4YhgrxQY}/#{FeUTTNHpVzD.zogrUrI7Crs}>6 && #{FeUTTNHpVzD.iIC4YhgrxQY}/#{FeUTTNHpVzD.zogrUrI7Crs}<=7,1,0)+
if(#{mKSICD1rxG4.iIC4YhgrxQY}/#{mKSICD1rxG4.zogrUrI7Crs}>6 && #{mKSICD1rxG4.iIC4YhgrxQY}/#{mKSICD1rxG4.zogrUrI7Crs}<=7,1,0)+
if(#{mVNe1aS1pGl.iIC4YhgrxQY}/#{mVNe1aS1pGl.zogrUrI7Crs}>6 && #{mVNe1aS1pGl.iIC4YhgrxQY}/#{mVNe1aS1pGl.zogrUrI7Crs}<=7,1,0)+
if(#{oLAXTZY6ken.iIC4YhgrxQY}/#{oLAXTZY6ken.zogrUrI7Crs}>6 && #{oLAXTZY6ken.iIC4YhgrxQY}/#{oLAXTZY6ken.zogrUrI7Crs}<=7,1,0)+
if(#{YYaRDUZyH9L.iIC4YhgrxQY}/#{YYaRDUZyH9L.zogrUrI7Crs}>6 && #{YYaRDUZyH9L.iIC4YhgrxQY}/#{YYaRDUZyH9L.zogrUrI7Crs}<=7,1,0)+
if(#{HVteopBt0jr.iIC4YhgrxQY}/#{HVteopBt0jr.zogrUrI7Crs}>6 && #{HVteopBt0jr.iIC4YhgrxQY}/#{HVteopBt0jr.zogrUrI7Crs}<=7,1,0)+
if(#{sWodd2tbjgZ.iIC4YhgrxQY}/#{sWodd2tbjgZ.zogrUrI7Crs}>6 && #{sWodd2tbjgZ.iIC4YhgrxQY}/#{sWodd2tbjgZ.zogrUrI7Crs}<=7,1,0)+
if(#{yVYajDDYUfX.iIC4YhgrxQY}/#{yVYajDDYUfX.zogrUrI7Crs}>6 && #{yVYajDDYUfX.iIC4YhgrxQY}/#{yVYajDDYUfX.zogrUrI7Crs}<=7,1,0)+
if(#{eTJAr4sc83v.iIC4YhgrxQY}/#{eTJAr4sc83v.zogrUrI7Crs}>6 && #{eTJAr4sc83v.iIC4YhgrxQY}/#{eTJAr4sc83v.zogrUrI7Crs}<=7,1,0)+
if(#{U4KSmanl4JP.iIC4YhgrxQY}/#{U4KSmanl4JP.zogrUrI7Crs}>6 && #{U4KSmanl4JP.iIC4YhgrxQY}/#{U4KSmanl4JP.zogrUrI7Crs}<=7,1,0)+
if(#{FXsa5uG3IGn.iIC4YhgrxQY}/#{FXsa5uG3IGn.zogrUrI7Crs}>6 && #{FXsa5uG3IGn.iIC4YhgrxQY}/#{FXsa5uG3IGn.zogrUrI7Crs}<=7,1,0)+
if(#{L34T9YDtCor.iIC4YhgrxQY}/#{L34T9YDtCor.zogrUrI7Crs}>6 && #{L34T9YDtCor.iIC4YhgrxQY}/#{L34T9YDtCor.zogrUrI7Crs}<=7,1,0)+
if(#{W5mHXhSYFfQ.iIC4YhgrxQY}/#{W5mHXhSYFfQ.zogrUrI7Crs}>6 && #{W5mHXhSYFfQ.iIC4YhgrxQY}/#{W5mHXhSYFfQ.zogrUrI7Crs}<=7,1,0)+
if(#{cmSUyJOZwyl.iIC4YhgrxQY}/#{cmSUyJOZwyl.zogrUrI7Crs}>6 && #{cmSUyJOZwyl.iIC4YhgrxQY}/#{cmSUyJOZwyl.zogrUrI7Crs}<=7,1,0)+
if(#{cT8sfosRXvU.iIC4YhgrxQY}/#{cT8sfosRXvU.zogrUrI7Crs}>6 && #{cT8sfosRXvU.iIC4YhgrxQY}/#{cT8sfosRXvU.zogrUrI7Crs}<=7,1,0)+
if(#{OaWKnMS7say.iIC4YhgrxQY}/#{OaWKnMS7say.zogrUrI7Crs}>6 && #{OaWKnMS7say.iIC4YhgrxQY}/#{OaWKnMS7say.zogrUrI7Crs}<=7,1,0)+
if(#{Z4bjHvGS6aH.iIC4YhgrxQY}/#{Z4bjHvGS6aH.zogrUrI7Crs}>6 && #{Z4bjHvGS6aH.iIC4YhgrxQY}/#{Z4bjHvGS6aH.zogrUrI7Crs}<=7,1,0)+
if(#{Nn1L7CNEtC8.iIC4YhgrxQY}/#{Nn1L7CNEtC8.zogrUrI7Crs}>6 && #{Nn1L7CNEtC8.iIC4YhgrxQY}/#{Nn1L7CNEtC8.zogrUrI7Crs}<=7,1,0)+
if(#{RNYKSc3nAUg.iIC4YhgrxQY}/#{RNYKSc3nAUg.zogrUrI7Crs}>6 && #{RNYKSc3nAUg.iIC4YhgrxQY}/#{RNYKSc3nAUg.zogrUrI7Crs}<=7,1,0)+
if(#{PtmZ9XqpPKi.iIC4YhgrxQY}/#{PtmZ9XqpPKi.zogrUrI7Crs}>6 && #{PtmZ9XqpPKi.iIC4YhgrxQY}/#{PtmZ9XqpPKi.zogrUrI7Crs}<=7,1,0)+
if(#{CohlLHi54B0.iIC4YhgrxQY}/#{CohlLHi54B0.zogrUrI7Crs}>6 && #{CohlLHi54B0.iIC4YhgrxQY}/#{CohlLHi54B0.zogrUrI7Crs}<=7,1,0)+
if(#{Gu6u82RD9OW.iIC4YhgrxQY}/#{Gu6u82RD9OW.zogrUrI7Crs}>6 && #{Gu6u82RD9OW.iIC4YhgrxQY}/#{Gu6u82RD9OW.zogrUrI7Crs}<=7,1,0)+
if(#{LiuYzxYr4Pt.iIC4YhgrxQY}/#{LiuYzxYr4Pt.zogrUrI7Crs}>6 && #{LiuYzxYr4Pt.iIC4YhgrxQY}/#{LiuYzxYr4Pt.zogrUrI7Crs}<=7,1,0)+
if(#{Tje33nJAG55.iIC4YhgrxQY}/#{Tje33nJAG55.zogrUrI7Crs}>6 && #{Tje33nJAG55.iIC4YhgrxQY}/#{Tje33nJAG55.zogrUrI7Crs}<=7,1,0)+
if(#{euM2dlqleYH.iIC4YhgrxQY}/#{euM2dlqleYH.zogrUrI7Crs}>6 && #{euM2dlqleYH.iIC4YhgrxQY}/#{euM2dlqleYH.zogrUrI7Crs}<=7,1,0)+
if(#{dASLmBTEehF.iIC4YhgrxQY}/#{dASLmBTEehF.zogrUrI7Crs}>6 && #{dASLmBTEehF.iIC4YhgrxQY}/#{dASLmBTEehF.zogrUrI7Crs}<=7,1,0)+
if(#{qU2LvzoPn1z.iIC4YhgrxQY}/#{qU2LvzoPn1z.zogrUrI7Crs}>6 && #{qU2LvzoPn1z.iIC4YhgrxQY}/#{qU2LvzoPn1z.zogrUrI7Crs}<=7,1,0)+
if(#{OkWaFxdUQY2.iIC4YhgrxQY}/#{OkWaFxdUQY2.zogrUrI7Crs}>6 && #{OkWaFxdUQY2.iIC4YhgrxQY}/#{OkWaFxdUQY2.zogrUrI7Crs}<=7,1,0)+
if(#{YHIv7KQc2e7.iIC4YhgrxQY}/#{YHIv7KQc2e7.zogrUrI7Crs}>6 && #{YHIv7KQc2e7.iIC4YhgrxQY}/#{YHIv7KQc2e7.zogrUrI7Crs}<=7,1,0)+
if(#{rt9D47Inb49.iIC4YhgrxQY}/#{rt9D47Inb49.zogrUrI7Crs}>6 && #{rt9D47Inb49.iIC4YhgrxQY}/#{rt9D47Inb49.zogrUrI7Crs}<=7,1,0)+
if(#{i1iXbquZ5iv.iIC4YhgrxQY}/#{i1iXbquZ5iv.zogrUrI7Crs}>6 && #{i1iXbquZ5iv.iIC4YhgrxQY}/#{i1iXbquZ5iv.zogrUrI7Crs}<=7,1,0)+
if(#{RcE30WBKrXI.iIC4YhgrxQY}/#{RcE30WBKrXI.zogrUrI7Crs}>6 && #{RcE30WBKrXI.iIC4YhgrxQY}/#{RcE30WBKrXI.zogrUrI7Crs}<=7,1,0)+
if(#{EAG0GfdSMAs.iIC4YhgrxQY}/#{EAG0GfdSMAs.zogrUrI7Crs}>6 && #{EAG0GfdSMAs.iIC4YhgrxQY}/#{EAG0GfdSMAs.zogrUrI7Crs}<=7,1,0)+
if(#{N2aXs7VlJdJ.iIC4YhgrxQY}/#{N2aXs7VlJdJ.zogrUrI7Crs}>6 && #{N2aXs7VlJdJ.iIC4YhgrxQY}/#{N2aXs7VlJdJ.zogrUrI7Crs}<=7,1,0)+
if(#{xrjnOtFFTRC.iIC4YhgrxQY}/#{xrjnOtFFTRC.zogrUrI7Crs}>6 && #{xrjnOtFFTRC.iIC4YhgrxQY}/#{xrjnOtFFTRC.zogrUrI7Crs}<=7,1,0)
>>
>>**Edit denominator**:  
>>>**Description**: "6-7 months - MSR - Denominator"  
>>>**Calculation**: "1"  
>
>**8 7-8 months - MSR**  
>For each item the Indicator returns "1" if the stock coverage time is greater than or equal to 1 but less than 2 and otherwise returns 0and then adds up these results for calculating the number of items with a stock coverage time of 7-8 months. 
>>**Name \(*)**: "7-8 months - MSR"  
>>**Short Name \(*)**: "7-8 months - MSR"  
>>**Description**: "Number of items with a coverage time of 7-8 months"  
>>**Decimals in data output**: "0"  
>>**Indicator type \(*)**: "Number (Factor 1)"  
>>**Edit numerator**:  
>>>**Description**: "7-8 months - MSR - Numerator"  
>>>**Calculation**:  if(#{LNAkkMTxqEW.iIC4YhgrxQY}/#{LNAkkMTxqEW.zogrUrI7Crs}>7 && #{LNAkkMTxqEW.iIC4YhgrxQY}/#{LNAkkMTxqEW.zogrUrI7Crs}<=8,1,0)+
if(#{WyDZKSw82X6.iIC4YhgrxQY}/#{WyDZKSw82X6.zogrUrI7Crs}>7 && #{WyDZKSw82X6.iIC4YhgrxQY}/#{WyDZKSw82X6.zogrUrI7Crs}<=8,1,0)+
if(#{JPccVwAGRq9.iIC4YhgrxQY}/#{JPccVwAGRq9.zogrUrI7Crs}>7 && #{JPccVwAGRq9.iIC4YhgrxQY}/#{JPccVwAGRq9.zogrUrI7Crs}<=8,1,0)+
if(#{smxJz7Mt6ia.iIC4YhgrxQY}/#{smxJz7Mt6ia.zogrUrI7Crs}>7 && #{smxJz7Mt6ia.iIC4YhgrxQY}/#{smxJz7Mt6ia.zogrUrI7Crs}<=8,1,0)+
if(#{AaIApgGQM6t.iIC4YhgrxQY}/#{AaIApgGQM6t.zogrUrI7Crs}>7 && #{AaIApgGQM6t.iIC4YhgrxQY}/#{AaIApgGQM6t.zogrUrI7Crs}<=8,1,0)+
if(#{vCTrmv52APd.iIC4YhgrxQY}/#{vCTrmv52APd.zogrUrI7Crs}>7 && #{vCTrmv52APd.iIC4YhgrxQY}/#{vCTrmv52APd.zogrUrI7Crs}<=8,1,0)+
if(#{SOw2TcuFFH2.iIC4YhgrxQY}/#{SOw2TcuFFH2.zogrUrI7Crs}>7 && #{SOw2TcuFFH2.iIC4YhgrxQY}/#{SOw2TcuFFH2.zogrUrI7Crs}<=8,1,0)+
if(#{RSIOx2u07Ln.iIC4YhgrxQY}/#{RSIOx2u07Ln.zogrUrI7Crs}>7 && #{RSIOx2u07Ln.iIC4YhgrxQY}/#{RSIOx2u07Ln.zogrUrI7Crs}<=8,1,0)+
if(#{JStiDyaPfqy.iIC4YhgrxQY}/#{JStiDyaPfqy.zogrUrI7Crs}>7 && #{JStiDyaPfqy.iIC4YhgrxQY}/#{JStiDyaPfqy.zogrUrI7Crs}<=8,1,0)+
if(#{hZ1YvdcTDQM.iIC4YhgrxQY}/#{hZ1YvdcTDQM.zogrUrI7Crs}>7 && #{hZ1YvdcTDQM.iIC4YhgrxQY}/#{hZ1YvdcTDQM.zogrUrI7Crs}<=8,1,0)+
if(#{tsi32D8HQd5.iIC4YhgrxQY}/#{tsi32D8HQd5.zogrUrI7Crs}>7 && #{tsi32D8HQd5.iIC4YhgrxQY}/#{tsi32D8HQd5.zogrUrI7Crs}<=8,1,0)+
if(#{QWlPF8S0gCc.iIC4YhgrxQY}/#{QWlPF8S0gCc.zogrUrI7Crs}>7 && #{QWlPF8S0gCc.iIC4YhgrxQY}/#{QWlPF8S0gCc.zogrUrI7Crs}<=8,1,0)+
if(#{a5uLTDt12eT.iIC4YhgrxQY}/#{a5uLTDt12eT.zogrUrI7Crs}>7 && #{a5uLTDt12eT.iIC4YhgrxQY}/#{a5uLTDt12eT.zogrUrI7Crs}<=8,1,0)+
if(#{U0AfOOyJMy2.iIC4YhgrxQY}/#{U0AfOOyJMy2.zogrUrI7Crs}>7 && #{U0AfOOyJMy2.iIC4YhgrxQY}/#{U0AfOOyJMy2.zogrUrI7Crs}<=8,1,0)+
if(#{cyf6UdScfFM.iIC4YhgrxQY}/#{cyf6UdScfFM.zogrUrI7Crs}>7 && #{cyf6UdScfFM.iIC4YhgrxQY}/#{cyf6UdScfFM.zogrUrI7Crs}<=8,1,0)+
if(#{FeUTTNHpVzD.iIC4YhgrxQY}/#{FeUTTNHpVzD.zogrUrI7Crs}>7 && #{FeUTTNHpVzD.iIC4YhgrxQY}/#{FeUTTNHpVzD.zogrUrI7Crs}<=8,1,0)+
if(#{mKSICD1rxG4.iIC4YhgrxQY}/#{mKSICD1rxG4.zogrUrI7Crs}>7 && #{mKSICD1rxG4.iIC4YhgrxQY}/#{mKSICD1rxG4.zogrUrI7Crs}<=8,1,0)+
if(#{mVNe1aS1pGl.iIC4YhgrxQY}/#{mVNe1aS1pGl.zogrUrI7Crs}>7 && #{mVNe1aS1pGl.iIC4YhgrxQY}/#{mVNe1aS1pGl.zogrUrI7Crs}<=8,1,0)+
if(#{oLAXTZY6ken.iIC4YhgrxQY}/#{oLAXTZY6ken.zogrUrI7Crs}>7 && #{oLAXTZY6ken.iIC4YhgrxQY}/#{oLAXTZY6ken.zogrUrI7Crs}<=8,1,0)+
if(#{YYaRDUZyH9L.iIC4YhgrxQY}/#{YYaRDUZyH9L.zogrUrI7Crs}>7 && #{YYaRDUZyH9L.iIC4YhgrxQY}/#{YYaRDUZyH9L.zogrUrI7Crs}<=8,1,0)+
if(#{HVteopBt0jr.iIC4YhgrxQY}/#{HVteopBt0jr.zogrUrI7Crs}>7 && #{HVteopBt0jr.iIC4YhgrxQY}/#{HVteopBt0jr.zogrUrI7Crs}<=8,1,0)+
if(#{sWodd2tbjgZ.iIC4YhgrxQY}/#{sWodd2tbjgZ.zogrUrI7Crs}>7 && #{sWodd2tbjgZ.iIC4YhgrxQY}/#{sWodd2tbjgZ.zogrUrI7Crs}<=8,1,0)+
if(#{yVYajDDYUfX.iIC4YhgrxQY}/#{yVYajDDYUfX.zogrUrI7Crs}>7 && #{yVYajDDYUfX.iIC4YhgrxQY}/#{yVYajDDYUfX.zogrUrI7Crs}<=8,1,0)+
if(#{eTJAr4sc83v.iIC4YhgrxQY}/#{eTJAr4sc83v.zogrUrI7Crs}>7 && #{eTJAr4sc83v.iIC4YhgrxQY}/#{eTJAr4sc83v.zogrUrI7Crs}<=8,1,0)+
if(#{U4KSmanl4JP.iIC4YhgrxQY}/#{U4KSmanl4JP.zogrUrI7Crs}>7 && #{U4KSmanl4JP.iIC4YhgrxQY}/#{U4KSmanl4JP.zogrUrI7Crs}<=8,1,0)+
if(#{FXsa5uG3IGn.iIC4YhgrxQY}/#{FXsa5uG3IGn.zogrUrI7Crs}>7 && #{FXsa5uG3IGn.iIC4YhgrxQY}/#{FXsa5uG3IGn.zogrUrI7Crs}<=8,1,0)+
if(#{L34T9YDtCor.iIC4YhgrxQY}/#{L34T9YDtCor.zogrUrI7Crs}>7 && #{L34T9YDtCor.iIC4YhgrxQY}/#{L34T9YDtCor.zogrUrI7Crs}<=8,1,0)+
if(#{W5mHXhSYFfQ.iIC4YhgrxQY}/#{W5mHXhSYFfQ.zogrUrI7Crs}>7 && #{W5mHXhSYFfQ.iIC4YhgrxQY}/#{W5mHXhSYFfQ.zogrUrI7Crs}<=8,1,0)+
if(#{cmSUyJOZwyl.iIC4YhgrxQY}/#{cmSUyJOZwyl.zogrUrI7Crs}>7 && #{cmSUyJOZwyl.iIC4YhgrxQY}/#{cmSUyJOZwyl.zogrUrI7Crs}<=8,1,0)+
if(#{cT8sfosRXvU.iIC4YhgrxQY}/#{cT8sfosRXvU.zogrUrI7Crs}>7 && #{cT8sfosRXvU.iIC4YhgrxQY}/#{cT8sfosRXvU.zogrUrI7Crs}<=8,1,0)+
if(#{OaWKnMS7say.iIC4YhgrxQY}/#{OaWKnMS7say.zogrUrI7Crs}>7 && #{OaWKnMS7say.iIC4YhgrxQY}/#{OaWKnMS7say.zogrUrI7Crs}<=8,1,0)+
if(#{Z4bjHvGS6aH.iIC4YhgrxQY}/#{Z4bjHvGS6aH.zogrUrI7Crs}>7 && #{Z4bjHvGS6aH.iIC4YhgrxQY}/#{Z4bjHvGS6aH.zogrUrI7Crs}<=8,1,0)+
if(#{Nn1L7CNEtC8.iIC4YhgrxQY}/#{Nn1L7CNEtC8.zogrUrI7Crs}>7 && #{Nn1L7CNEtC8.iIC4YhgrxQY}/#{Nn1L7CNEtC8.zogrUrI7Crs}<=8,1,0)+
if(#{RNYKSc3nAUg.iIC4YhgrxQY}/#{RNYKSc3nAUg.zogrUrI7Crs}>7 && #{RNYKSc3nAUg.iIC4YhgrxQY}/#{RNYKSc3nAUg.zogrUrI7Crs}<=8,1,0)+
if(#{PtmZ9XqpPKi.iIC4YhgrxQY}/#{PtmZ9XqpPKi.zogrUrI7Crs}>7 && #{PtmZ9XqpPKi.iIC4YhgrxQY}/#{PtmZ9XqpPKi.zogrUrI7Crs}<=8,1,0)+
if(#{CohlLHi54B0.iIC4YhgrxQY}/#{CohlLHi54B0.zogrUrI7Crs}>7 && #{CohlLHi54B0.iIC4YhgrxQY}/#{CohlLHi54B0.zogrUrI7Crs}<=8,1,0)+
if(#{Gu6u82RD9OW.iIC4YhgrxQY}/#{Gu6u82RD9OW.zogrUrI7Crs}>7 && #{Gu6u82RD9OW.iIC4YhgrxQY}/#{Gu6u82RD9OW.zogrUrI7Crs}<=8,1,0)+
if(#{LiuYzxYr4Pt.iIC4YhgrxQY}/#{LiuYzxYr4Pt.zogrUrI7Crs}>7 && #{LiuYzxYr4Pt.iIC4YhgrxQY}/#{LiuYzxYr4Pt.zogrUrI7Crs}<=8,1,0)+
if(#{Tje33nJAG55.iIC4YhgrxQY}/#{Tje33nJAG55.zogrUrI7Crs}>7 && #{Tje33nJAG55.iIC4YhgrxQY}/#{Tje33nJAG55.zogrUrI7Crs}<=8,1,0)+
if(#{euM2dlqleYH.iIC4YhgrxQY}/#{euM2dlqleYH.zogrUrI7Crs}>7 && #{euM2dlqleYH.iIC4YhgrxQY}/#{euM2dlqleYH.zogrUrI7Crs}<=8,1,0)+
if(#{dASLmBTEehF.iIC4YhgrxQY}/#{dASLmBTEehF.zogrUrI7Crs}>7 && #{dASLmBTEehF.iIC4YhgrxQY}/#{dASLmBTEehF.zogrUrI7Crs}<=8,1,0)+
if(#{qU2LvzoPn1z.iIC4YhgrxQY}/#{qU2LvzoPn1z.zogrUrI7Crs}>7 && #{qU2LvzoPn1z.iIC4YhgrxQY}/#{qU2LvzoPn1z.zogrUrI7Crs}<=8,1,0)+
if(#{OkWaFxdUQY2.iIC4YhgrxQY}/#{OkWaFxdUQY2.zogrUrI7Crs}>7 && #{OkWaFxdUQY2.iIC4YhgrxQY}/#{OkWaFxdUQY2.zogrUrI7Crs}<=8,1,0)+
if(#{YHIv7KQc2e7.iIC4YhgrxQY}/#{YHIv7KQc2e7.zogrUrI7Crs}>7 && #{YHIv7KQc2e7.iIC4YhgrxQY}/#{YHIv7KQc2e7.zogrUrI7Crs}<=8,1,0)+
if(#{rt9D47Inb49.iIC4YhgrxQY}/#{rt9D47Inb49.zogrUrI7Crs}>7 && #{rt9D47Inb49.iIC4YhgrxQY}/#{rt9D47Inb49.zogrUrI7Crs}<=8,1,0)+
if(#{i1iXbquZ5iv.iIC4YhgrxQY}/#{i1iXbquZ5iv.zogrUrI7Crs}>7 && #{i1iXbquZ5iv.iIC4YhgrxQY}/#{i1iXbquZ5iv.zogrUrI7Crs}<=8,1,0)+
if(#{RcE30WBKrXI.iIC4YhgrxQY}/#{RcE30WBKrXI.zogrUrI7Crs}>7 && #{RcE30WBKrXI.iIC4YhgrxQY}/#{RcE30WBKrXI.zogrUrI7Crs}<=8,1,0)+
if(#{EAG0GfdSMAs.iIC4YhgrxQY}/#{EAG0GfdSMAs.zogrUrI7Crs}>7 && #{EAG0GfdSMAs.iIC4YhgrxQY}/#{EAG0GfdSMAs.zogrUrI7Crs}<=8,1,0)+
if(#{N2aXs7VlJdJ.iIC4YhgrxQY}/#{N2aXs7VlJdJ.zogrUrI7Crs}>7 && #{N2aXs7VlJdJ.iIC4YhgrxQY}/#{N2aXs7VlJdJ.zogrUrI7Crs}<=8,1,0)+
if(#{xrjnOtFFTRC.iIC4YhgrxQY}/#{xrjnOtFFTRC.zogrUrI7Crs}>7 && #{xrjnOtFFTRC.iIC4YhgrxQY}/#{xrjnOtFFTRC.zogrUrI7Crs}<=8,1,0)
>>
>>**Edit denominator**:  
>>>**Description**: "7-8 months - MSR - Denominator"  
>>>**Calculation**: "1"  
>
>**9 8-9 months - MSR**  
>For each item the Indicator returns "1" if the stock coverage time is greater than or equal to 8 but less than 9 and otherwise returns 0and then adds up these results for calculating the number of items with a stock coverage time of 8-9 months. 
>>**Name \(*)**: "8-9 months - MSR"  
>>**Short Name \(*)**: "8-9 months - MSR"  
>>**Description**: "Number of items with a coverage time of 8-9 months"  
>>**Decimals in data output**: "0"  
>>**Indicator type \(*)**: "Number (Factor 1)"  
>>**Edit numerator**:  
>>>**Description**: "8-9 months - MSR - Numerator"  
>>>**Calculation**:  if(#{LNAkkMTxqEW.iIC4YhgrxQY}/#{LNAkkMTxqEW.zogrUrI7Crs}>7 && #{LNAkkMTxqEW.iIC4YhgrxQY}/#{LNAkkMTxqEW.zogrUrI7Crs}<=8,1,0)+
if(#{WyDZKSw82X6.iIC4YhgrxQY}/#{WyDZKSw82X6.zogrUrI7Crs}>7 && #{WyDZKSw82X6.iIC4YhgrxQY}/#{WyDZKSw82X6.zogrUrI7Crs}<=8,1,0)+
if(#{JPccVwAGRq9.iIC4YhgrxQY}/#{JPccVwAGRq9.zogrUrI7Crs}>7 && #{JPccVwAGRq9.iIC4YhgrxQY}/#{JPccVwAGRq9.zogrUrI7Crs}<=8,1,0)+
if(#{smxJz7Mt6ia.iIC4YhgrxQY}/#{smxJz7Mt6ia.zogrUrI7Crs}>7 && #{smxJz7Mt6ia.iIC4YhgrxQY}/#{smxJz7Mt6ia.zogrUrI7Crs}<=8,1,0)+
if(#{AaIApgGQM6t.iIC4YhgrxQY}/#{AaIApgGQM6t.zogrUrI7Crs}>7 && #{AaIApgGQM6t.iIC4YhgrxQY}/#{AaIApgGQM6t.zogrUrI7Crs}<=8,1,0)+
if(#{vCTrmv52APd.iIC4YhgrxQY}/#{vCTrmv52APd.zogrUrI7Crs}>7 && #{vCTrmv52APd.iIC4YhgrxQY}/#{vCTrmv52APd.zogrUrI7Crs}<=8,1,0)+
if(#{SOw2TcuFFH2.iIC4YhgrxQY}/#{SOw2TcuFFH2.zogrUrI7Crs}>7 && #{SOw2TcuFFH2.iIC4YhgrxQY}/#{SOw2TcuFFH2.zogrUrI7Crs}<=8,1,0)+
if(#{RSIOx2u07Ln.iIC4YhgrxQY}/#{RSIOx2u07Ln.zogrUrI7Crs}>7 && #{RSIOx2u07Ln.iIC4YhgrxQY}/#{RSIOx2u07Ln.zogrUrI7Crs}<=8,1,0)+
if(#{JStiDyaPfqy.iIC4YhgrxQY}/#{JStiDyaPfqy.zogrUrI7Crs}>7 && #{JStiDyaPfqy.iIC4YhgrxQY}/#{JStiDyaPfqy.zogrUrI7Crs}<=8,1,0)+
if(#{hZ1YvdcTDQM.iIC4YhgrxQY}/#{hZ1YvdcTDQM.zogrUrI7Crs}>7 && #{hZ1YvdcTDQM.iIC4YhgrxQY}/#{hZ1YvdcTDQM.zogrUrI7Crs}<=8,1,0)+
if(#{tsi32D8HQd5.iIC4YhgrxQY}/#{tsi32D8HQd5.zogrUrI7Crs}>7 && #{tsi32D8HQd5.iIC4YhgrxQY}/#{tsi32D8HQd5.zogrUrI7Crs}<=8,1,0)+
if(#{QWlPF8S0gCc.iIC4YhgrxQY}/#{QWlPF8S0gCc.zogrUrI7Crs}>7 && #{QWlPF8S0gCc.iIC4YhgrxQY}/#{QWlPF8S0gCc.zogrUrI7Crs}<=8,1,0)+
if(#{a5uLTDt12eT.iIC4YhgrxQY}/#{a5uLTDt12eT.zogrUrI7Crs}>7 && #{a5uLTDt12eT.iIC4YhgrxQY}/#{a5uLTDt12eT.zogrUrI7Crs}<=8,1,0)+
if(#{U0AfOOyJMy2.iIC4YhgrxQY}/#{U0AfOOyJMy2.zogrUrI7Crs}>7 && #{U0AfOOyJMy2.iIC4YhgrxQY}/#{U0AfOOyJMy2.zogrUrI7Crs}<=8,1,0)+
if(#{cyf6UdScfFM.iIC4YhgrxQY}/#{cyf6UdScfFM.zogrUrI7Crs}>7 && #{cyf6UdScfFM.iIC4YhgrxQY}/#{cyf6UdScfFM.zogrUrI7Crs}<=8,1,0)+
if(#{FeUTTNHpVzD.iIC4YhgrxQY}/#{FeUTTNHpVzD.zogrUrI7Crs}>7 && #{FeUTTNHpVzD.iIC4YhgrxQY}/#{FeUTTNHpVzD.zogrUrI7Crs}<=8,1,0)+
if(#{mKSICD1rxG4.iIC4YhgrxQY}/#{mKSICD1rxG4.zogrUrI7Crs}>7 && #{mKSICD1rxG4.iIC4YhgrxQY}/#{mKSICD1rxG4.zogrUrI7Crs}<=8,1,0)+
if(#{mVNe1aS1pGl.iIC4YhgrxQY}/#{mVNe1aS1pGl.zogrUrI7Crs}>7 && #{mVNe1aS1pGl.iIC4YhgrxQY}/#{mVNe1aS1pGl.zogrUrI7Crs}<=8,1,0)+
if(#{oLAXTZY6ken.iIC4YhgrxQY}/#{oLAXTZY6ken.zogrUrI7Crs}>7 && #{oLAXTZY6ken.iIC4YhgrxQY}/#{oLAXTZY6ken.zogrUrI7Crs}<=8,1,0)+
if(#{YYaRDUZyH9L.iIC4YhgrxQY}/#{YYaRDUZyH9L.zogrUrI7Crs}>7 && #{YYaRDUZyH9L.iIC4YhgrxQY}/#{YYaRDUZyH9L.zogrUrI7Crs}<=8,1,0)+
if(#{HVteopBt0jr.iIC4YhgrxQY}/#{HVteopBt0jr.zogrUrI7Crs}>7 && #{HVteopBt0jr.iIC4YhgrxQY}/#{HVteopBt0jr.zogrUrI7Crs}<=8,1,0)+
if(#{sWodd2tbjgZ.iIC4YhgrxQY}/#{sWodd2tbjgZ.zogrUrI7Crs}>7 && #{sWodd2tbjgZ.iIC4YhgrxQY}/#{sWodd2tbjgZ.zogrUrI7Crs}<=8,1,0)+
if(#{yVYajDDYUfX.iIC4YhgrxQY}/#{yVYajDDYUfX.zogrUrI7Crs}>7 && #{yVYajDDYUfX.iIC4YhgrxQY}/#{yVYajDDYUfX.zogrUrI7Crs}<=8,1,0)+
if(#{eTJAr4sc83v.iIC4YhgrxQY}/#{eTJAr4sc83v.zogrUrI7Crs}>7 && #{eTJAr4sc83v.iIC4YhgrxQY}/#{eTJAr4sc83v.zogrUrI7Crs}<=8,1,0)+
if(#{U4KSmanl4JP.iIC4YhgrxQY}/#{U4KSmanl4JP.zogrUrI7Crs}>7 && #{U4KSmanl4JP.iIC4YhgrxQY}/#{U4KSmanl4JP.zogrUrI7Crs}<=8,1,0)+
if(#{FXsa5uG3IGn.iIC4YhgrxQY}/#{FXsa5uG3IGn.zogrUrI7Crs}>7 && #{FXsa5uG3IGn.iIC4YhgrxQY}/#{FXsa5uG3IGn.zogrUrI7Crs}<=8,1,0)+
if(#{L34T9YDtCor.iIC4YhgrxQY}/#{L34T9YDtCor.zogrUrI7Crs}>7 && #{L34T9YDtCor.iIC4YhgrxQY}/#{L34T9YDtCor.zogrUrI7Crs}<=8,1,0)+
if(#{W5mHXhSYFfQ.iIC4YhgrxQY}/#{W5mHXhSYFfQ.zogrUrI7Crs}>7 && #{W5mHXhSYFfQ.iIC4YhgrxQY}/#{W5mHXhSYFfQ.zogrUrI7Crs}<=8,1,0)+
if(#{cmSUyJOZwyl.iIC4YhgrxQY}/#{cmSUyJOZwyl.zogrUrI7Crs}>7 && #{cmSUyJOZwyl.iIC4YhgrxQY}/#{cmSUyJOZwyl.zogrUrI7Crs}<=8,1,0)+
if(#{cT8sfosRXvU.iIC4YhgrxQY}/#{cT8sfosRXvU.zogrUrI7Crs}>7 && #{cT8sfosRXvU.iIC4YhgrxQY}/#{cT8sfosRXvU.zogrUrI7Crs}<=8,1,0)+
if(#{OaWKnMS7say.iIC4YhgrxQY}/#{OaWKnMS7say.zogrUrI7Crs}>7 && #{OaWKnMS7say.iIC4YhgrxQY}/#{OaWKnMS7say.zogrUrI7Crs}<=8,1,0)+
if(#{Z4bjHvGS6aH.iIC4YhgrxQY}/#{Z4bjHvGS6aH.zogrUrI7Crs}>7 && #{Z4bjHvGS6aH.iIC4YhgrxQY}/#{Z4bjHvGS6aH.zogrUrI7Crs}<=8,1,0)+
if(#{Nn1L7CNEtC8.iIC4YhgrxQY}/#{Nn1L7CNEtC8.zogrUrI7Crs}>7 && #{Nn1L7CNEtC8.iIC4YhgrxQY}/#{Nn1L7CNEtC8.zogrUrI7Crs}<=8,1,0)+
if(#{RNYKSc3nAUg.iIC4YhgrxQY}/#{RNYKSc3nAUg.zogrUrI7Crs}>7 && #{RNYKSc3nAUg.iIC4YhgrxQY}/#{RNYKSc3nAUg.zogrUrI7Crs}<=8,1,0)+
if(#{PtmZ9XqpPKi.iIC4YhgrxQY}/#{PtmZ9XqpPKi.zogrUrI7Crs}>7 && #{PtmZ9XqpPKi.iIC4YhgrxQY}/#{PtmZ9XqpPKi.zogrUrI7Crs}<=8,1,0)+
if(#{CohlLHi54B0.iIC4YhgrxQY}/#{CohlLHi54B0.zogrUrI7Crs}>7 && #{CohlLHi54B0.iIC4YhgrxQY}/#{CohlLHi54B0.zogrUrI7Crs}<=8,1,0)+
if(#{Gu6u82RD9OW.iIC4YhgrxQY}/#{Gu6u82RD9OW.zogrUrI7Crs}>7 && #{Gu6u82RD9OW.iIC4YhgrxQY}/#{Gu6u82RD9OW.zogrUrI7Crs}<=8,1,0)+
if(#{LiuYzxYr4Pt.iIC4YhgrxQY}/#{LiuYzxYr4Pt.zogrUrI7Crs}>7 && #{LiuYzxYr4Pt.iIC4YhgrxQY}/#{LiuYzxYr4Pt.zogrUrI7Crs}<=8,1,0)+
if(#{Tje33nJAG55.iIC4YhgrxQY}/#{Tje33nJAG55.zogrUrI7Crs}>7 && #{Tje33nJAG55.iIC4YhgrxQY}/#{Tje33nJAG55.zogrUrI7Crs}<=8,1,0)+
if(#{euM2dlqleYH.iIC4YhgrxQY}/#{euM2dlqleYH.zogrUrI7Crs}>7 && #{euM2dlqleYH.iIC4YhgrxQY}/#{euM2dlqleYH.zogrUrI7Crs}<=8,1,0)+
if(#{dASLmBTEehF.iIC4YhgrxQY}/#{dASLmBTEehF.zogrUrI7Crs}>7 && #{dASLmBTEehF.iIC4YhgrxQY}/#{dASLmBTEehF.zogrUrI7Crs}<=8,1,0)+
if(#{qU2LvzoPn1z.iIC4YhgrxQY}/#{qU2LvzoPn1z.zogrUrI7Crs}>7 && #{qU2LvzoPn1z.iIC4YhgrxQY}/#{qU2LvzoPn1z.zogrUrI7Crs}<=8,1,0)+
if(#{OkWaFxdUQY2.iIC4YhgrxQY}/#{OkWaFxdUQY2.zogrUrI7Crs}>7 && #{OkWaFxdUQY2.iIC4YhgrxQY}/#{OkWaFxdUQY2.zogrUrI7Crs}<=8,1,0)+
if(#{YHIv7KQc2e7.iIC4YhgrxQY}/#{YHIv7KQc2e7.zogrUrI7Crs}>7 && #{YHIv7KQc2e7.iIC4YhgrxQY}/#{YHIv7KQc2e7.zogrUrI7Crs}<=8,1,0)+
if(#{rt9D47Inb49.iIC4YhgrxQY}/#{rt9D47Inb49.zogrUrI7Crs}>7 && #{rt9D47Inb49.iIC4YhgrxQY}/#{rt9D47Inb49.zogrUrI7Crs}<=8,1,0)+
if(#{i1iXbquZ5iv.iIC4YhgrxQY}/#{i1iXbquZ5iv.zogrUrI7Crs}>7 && #{i1iXbquZ5iv.iIC4YhgrxQY}/#{i1iXbquZ5iv.zogrUrI7Crs}<=8,1,0)+
if(#{RcE30WBKrXI.iIC4YhgrxQY}/#{RcE30WBKrXI.zogrUrI7Crs}>7 && #{RcE30WBKrXI.iIC4YhgrxQY}/#{RcE30WBKrXI.zogrUrI7Crs}<=8,1,0)+
if(#{EAG0GfdSMAs.iIC4YhgrxQY}/#{EAG0GfdSMAs.zogrUrI7Crs}>7 && #{EAG0GfdSMAs.iIC4YhgrxQY}/#{EAG0GfdSMAs.zogrUrI7Crs}<=8,1,0)+
if(#{N2aXs7VlJdJ.iIC4YhgrxQY}/#{N2aXs7VlJdJ.zogrUrI7Crs}>7 && #{N2aXs7VlJdJ.iIC4YhgrxQY}/#{N2aXs7VlJdJ.zogrUrI7Crs}<=8,1,0)+
if(#{xrjnOtFFTRC.iIC4YhgrxQY}/#{xrjnOtFFTRC.zogrUrI7Crs}>7 && #{xrjnOtFFTRC.iIC4YhgrxQY}/#{xrjnOtFFTRC.zogrUrI7Crs}<=8,1,0)
>>
>>**Edit denominator**:  
>>>**Description**: "8-9 months - MSR - Denominator"  
>>>**Calculation**: "1"  
>
>**10 9-10 months - MSR**  
>For each item the Indicator returns "1" if the stock coverage time is greater than or equal to 9 but less than 10 and otherwise returns 0 and then adds up these results for calculating the number of items with a stock coverage time of 9-10 months. 
>>**Name \(*)**: "9-10 months - MSR"  
>>**Short Name \(*)**: "9-10 months - MSR"  
>>**Description**: "Number of items with a coverage time of 9-10 months"  
>>**Decimals in data output**: "0"  
>>**Indicator type \(*)**: "Number (Factor 1)"  
>>**Edit numerator**:  
>>>**Description**: "9-10 months - MSR - Numerator"  
>>>**Calculation**:  if(#{LNAkkMTxqEW.iIC4YhgrxQY}/#{LNAkkMTxqEW.zogrUrI7Crs}>9 && #{LNAkkMTxqEW.iIC4YhgrxQY}/#{LNAkkMTxqEW.zogrUrI7Crs}<=10,1,0)+
if(#{WyDZKSw82X6.iIC4YhgrxQY}/#{WyDZKSw82X6.zogrUrI7Crs}>9 && #{WyDZKSw82X6.iIC4YhgrxQY}/#{WyDZKSw82X6.zogrUrI7Crs}<=10,1,0)+
if(#{JPccVwAGRq9.iIC4YhgrxQY}/#{JPccVwAGRq9.zogrUrI7Crs}>9 && #{JPccVwAGRq9.iIC4YhgrxQY}/#{JPccVwAGRq9.zogrUrI7Crs}<=10,1,0)+
if(#{smxJz7Mt6ia.iIC4YhgrxQY}/#{smxJz7Mt6ia.zogrUrI7Crs}>9 && #{smxJz7Mt6ia.iIC4YhgrxQY}/#{smxJz7Mt6ia.zogrUrI7Crs}<=10,1,0)+
if(#{AaIApgGQM6t.iIC4YhgrxQY}/#{AaIApgGQM6t.zogrUrI7Crs}>9 && #{AaIApgGQM6t.iIC4YhgrxQY}/#{AaIApgGQM6t.zogrUrI7Crs}<=10,1,0)+
if(#{vCTrmv52APd.iIC4YhgrxQY}/#{vCTrmv52APd.zogrUrI7Crs}>9 && #{vCTrmv52APd.iIC4YhgrxQY}/#{vCTrmv52APd.zogrUrI7Crs}<=10,1,0)+
if(#{SOw2TcuFFH2.iIC4YhgrxQY}/#{SOw2TcuFFH2.zogrUrI7Crs}>9 && #{SOw2TcuFFH2.iIC4YhgrxQY}/#{SOw2TcuFFH2.zogrUrI7Crs}<=10,1,0)+
if(#{RSIOx2u07Ln.iIC4YhgrxQY}/#{RSIOx2u07Ln.zogrUrI7Crs}>9 && #{RSIOx2u07Ln.iIC4YhgrxQY}/#{RSIOx2u07Ln.zogrUrI7Crs}<=10,1,0)+
if(#{JStiDyaPfqy.iIC4YhgrxQY}/#{JStiDyaPfqy.zogrUrI7Crs}>9 && #{JStiDyaPfqy.iIC4YhgrxQY}/#{JStiDyaPfqy.zogrUrI7Crs}<=10,1,0)+
if(#{hZ1YvdcTDQM.iIC4YhgrxQY}/#{hZ1YvdcTDQM.zogrUrI7Crs}>9 && #{hZ1YvdcTDQM.iIC4YhgrxQY}/#{hZ1YvdcTDQM.zogrUrI7Crs}<=10,1,0)+
if(#{tsi32D8HQd5.iIC4YhgrxQY}/#{tsi32D8HQd5.zogrUrI7Crs}>9 && #{tsi32D8HQd5.iIC4YhgrxQY}/#{tsi32D8HQd5.zogrUrI7Crs}<=10,1,0)+
if(#{QWlPF8S0gCc.iIC4YhgrxQY}/#{QWlPF8S0gCc.zogrUrI7Crs}>9 && #{QWlPF8S0gCc.iIC4YhgrxQY}/#{QWlPF8S0gCc.zogrUrI7Crs}<=10,1,0)+
if(#{a5uLTDt12eT.iIC4YhgrxQY}/#{a5uLTDt12eT.zogrUrI7Crs}>9 && #{a5uLTDt12eT.iIC4YhgrxQY}/#{a5uLTDt12eT.zogrUrI7Crs}<=10,1,0)+
if(#{U0AfOOyJMy2.iIC4YhgrxQY}/#{U0AfOOyJMy2.zogrUrI7Crs}>9 && #{U0AfOOyJMy2.iIC4YhgrxQY}/#{U0AfOOyJMy2.zogrUrI7Crs}<=10,1,0)+
if(#{cyf6UdScfFM.iIC4YhgrxQY}/#{cyf6UdScfFM.zogrUrI7Crs}>9 && #{cyf6UdScfFM.iIC4YhgrxQY}/#{cyf6UdScfFM.zogrUrI7Crs}<=10,1,0)+
if(#{FeUTTNHpVzD.iIC4YhgrxQY}/#{FeUTTNHpVzD.zogrUrI7Crs}>9 && #{FeUTTNHpVzD.iIC4YhgrxQY}/#{FeUTTNHpVzD.zogrUrI7Crs}<=10,1,0)+
if(#{mKSICD1rxG4.iIC4YhgrxQY}/#{mKSICD1rxG4.zogrUrI7Crs}>9 && #{mKSICD1rxG4.iIC4YhgrxQY}/#{mKSICD1rxG4.zogrUrI7Crs}<=10,1,0)+
if(#{mVNe1aS1pGl.iIC4YhgrxQY}/#{mVNe1aS1pGl.zogrUrI7Crs}>9 && #{mVNe1aS1pGl.iIC4YhgrxQY}/#{mVNe1aS1pGl.zogrUrI7Crs}<=10,1,0)+
if(#{oLAXTZY6ken.iIC4YhgrxQY}/#{oLAXTZY6ken.zogrUrI7Crs}>9 && #{oLAXTZY6ken.iIC4YhgrxQY}/#{oLAXTZY6ken.zogrUrI7Crs}<=10,1,0)+
if(#{YYaRDUZyH9L.iIC4YhgrxQY}/#{YYaRDUZyH9L.zogrUrI7Crs}>9 && #{YYaRDUZyH9L.iIC4YhgrxQY}/#{YYaRDUZyH9L.zogrUrI7Crs}<=10,1,0)+
if(#{HVteopBt0jr.iIC4YhgrxQY}/#{HVteopBt0jr.zogrUrI7Crs}>9 && #{HVteopBt0jr.iIC4YhgrxQY}/#{HVteopBt0jr.zogrUrI7Crs}<=10,1,0)+
if(#{sWodd2tbjgZ.iIC4YhgrxQY}/#{sWodd2tbjgZ.zogrUrI7Crs}>9 && #{sWodd2tbjgZ.iIC4YhgrxQY}/#{sWodd2tbjgZ.zogrUrI7Crs}<=10,1,0)+
if(#{yVYajDDYUfX.iIC4YhgrxQY}/#{yVYajDDYUfX.zogrUrI7Crs}>9 && #{yVYajDDYUfX.iIC4YhgrxQY}/#{yVYajDDYUfX.zogrUrI7Crs}<=10,1,0)+
if(#{eTJAr4sc83v.iIC4YhgrxQY}/#{eTJAr4sc83v.zogrUrI7Crs}>9 && #{eTJAr4sc83v.iIC4YhgrxQY}/#{eTJAr4sc83v.zogrUrI7Crs}<=10,1,0)+
if(#{U4KSmanl4JP.iIC4YhgrxQY}/#{U4KSmanl4JP.zogrUrI7Crs}>9 && #{U4KSmanl4JP.iIC4YhgrxQY}/#{U4KSmanl4JP.zogrUrI7Crs}<=10,1,0)+
if(#{FXsa5uG3IGn.iIC4YhgrxQY}/#{FXsa5uG3IGn.zogrUrI7Crs}>9 && #{FXsa5uG3IGn.iIC4YhgrxQY}/#{FXsa5uG3IGn.zogrUrI7Crs}<=10,1,0)+
if(#{L34T9YDtCor.iIC4YhgrxQY}/#{L34T9YDtCor.zogrUrI7Crs}>9 && #{L34T9YDtCor.iIC4YhgrxQY}/#{L34T9YDtCor.zogrUrI7Crs}<=10,1,0)+
if(#{W5mHXhSYFfQ.iIC4YhgrxQY}/#{W5mHXhSYFfQ.zogrUrI7Crs}>9 && #{W5mHXhSYFfQ.iIC4YhgrxQY}/#{W5mHXhSYFfQ.zogrUrI7Crs}<=10,1,0)+
if(#{cmSUyJOZwyl.iIC4YhgrxQY}/#{cmSUyJOZwyl.zogrUrI7Crs}>9 && #{cmSUyJOZwyl.iIC4YhgrxQY}/#{cmSUyJOZwyl.zogrUrI7Crs}<=10,1,0)+
if(#{cT8sfosRXvU.iIC4YhgrxQY}/#{cT8sfosRXvU.zogrUrI7Crs}>9 && #{cT8sfosRXvU.iIC4YhgrxQY}/#{cT8sfosRXvU.zogrUrI7Crs}<=10,1,0)+
if(#{OaWKnMS7say.iIC4YhgrxQY}/#{OaWKnMS7say.zogrUrI7Crs}>9 && #{OaWKnMS7say.iIC4YhgrxQY}/#{OaWKnMS7say.zogrUrI7Crs}<=10,1,0)+
if(#{Z4bjHvGS6aH.iIC4YhgrxQY}/#{Z4bjHvGS6aH.zogrUrI7Crs}>9 && #{Z4bjHvGS6aH.iIC4YhgrxQY}/#{Z4bjHvGS6aH.zogrUrI7Crs}<=10,1,0)+
if(#{Nn1L7CNEtC8.iIC4YhgrxQY}/#{Nn1L7CNEtC8.zogrUrI7Crs}>9 && #{Nn1L7CNEtC8.iIC4YhgrxQY}/#{Nn1L7CNEtC8.zogrUrI7Crs}<=10,1,0)+
if(#{RNYKSc3nAUg.iIC4YhgrxQY}/#{RNYKSc3nAUg.zogrUrI7Crs}>9 && #{RNYKSc3nAUg.iIC4YhgrxQY}/#{RNYKSc3nAUg.zogrUrI7Crs}<=10,1,0)+
if(#{PtmZ9XqpPKi.iIC4YhgrxQY}/#{PtmZ9XqpPKi.zogrUrI7Crs}>9 && #{PtmZ9XqpPKi.iIC4YhgrxQY}/#{PtmZ9XqpPKi.zogrUrI7Crs}<=10,1,0)+
if(#{CohlLHi54B0.iIC4YhgrxQY}/#{CohlLHi54B0.zogrUrI7Crs}>9 && #{CohlLHi54B0.iIC4YhgrxQY}/#{CohlLHi54B0.zogrUrI7Crs}<=10,1,0)+
if(#{Gu6u82RD9OW.iIC4YhgrxQY}/#{Gu6u82RD9OW.zogrUrI7Crs}>9 && #{Gu6u82RD9OW.iIC4YhgrxQY}/#{Gu6u82RD9OW.zogrUrI7Crs}<=10,1,0)+
if(#{LiuYzxYr4Pt.iIC4YhgrxQY}/#{LiuYzxYr4Pt.zogrUrI7Crs}>9 && #{LiuYzxYr4Pt.iIC4YhgrxQY}/#{LiuYzxYr4Pt.zogrUrI7Crs}<=10,1,0)+
if(#{Tje33nJAG55.iIC4YhgrxQY}/#{Tje33nJAG55.zogrUrI7Crs}>9 && #{Tje33nJAG55.iIC4YhgrxQY}/#{Tje33nJAG55.zogrUrI7Crs}<=10,1,0)+
if(#{euM2dlqleYH.iIC4YhgrxQY}/#{euM2dlqleYH.zogrUrI7Crs}>9 && #{euM2dlqleYH.iIC4YhgrxQY}/#{euM2dlqleYH.zogrUrI7Crs}<=10,1,0)+
if(#{dASLmBTEehF.iIC4YhgrxQY}/#{dASLmBTEehF.zogrUrI7Crs}>9 && #{dASLmBTEehF.iIC4YhgrxQY}/#{dASLmBTEehF.zogrUrI7Crs}<=10,1,0)+
if(#{qU2LvzoPn1z.iIC4YhgrxQY}/#{qU2LvzoPn1z.zogrUrI7Crs}>9 && #{qU2LvzoPn1z.iIC4YhgrxQY}/#{qU2LvzoPn1z.zogrUrI7Crs}<=10,1,0)+
if(#{OkWaFxdUQY2.iIC4YhgrxQY}/#{OkWaFxdUQY2.zogrUrI7Crs}>9 && #{OkWaFxdUQY2.iIC4YhgrxQY}/#{OkWaFxdUQY2.zogrUrI7Crs}<=10,1,0)+
if(#{YHIv7KQc2e7.iIC4YhgrxQY}/#{YHIv7KQc2e7.zogrUrI7Crs}>9 && #{YHIv7KQc2e7.iIC4YhgrxQY}/#{YHIv7KQc2e7.zogrUrI7Crs}<=10,1,0)+
if(#{rt9D47Inb49.iIC4YhgrxQY}/#{rt9D47Inb49.zogrUrI7Crs}>9 && #{rt9D47Inb49.iIC4YhgrxQY}/#{rt9D47Inb49.zogrUrI7Crs}<=10,1,0)+
if(#{i1iXbquZ5iv.iIC4YhgrxQY}/#{i1iXbquZ5iv.zogrUrI7Crs}>9 && #{i1iXbquZ5iv.iIC4YhgrxQY}/#{i1iXbquZ5iv.zogrUrI7Crs}<=10,1,0)+
if(#{RcE30WBKrXI.iIC4YhgrxQY}/#{RcE30WBKrXI.zogrUrI7Crs}>9 && #{RcE30WBKrXI.iIC4YhgrxQY}/#{RcE30WBKrXI.zogrUrI7Crs}<=10,1,0)+
if(#{EAG0GfdSMAs.iIC4YhgrxQY}/#{EAG0GfdSMAs.zogrUrI7Crs}>9 && #{EAG0GfdSMAs.iIC4YhgrxQY}/#{EAG0GfdSMAs.zogrUrI7Crs}<=10,1,0)+
if(#{N2aXs7VlJdJ.iIC4YhgrxQY}/#{N2aXs7VlJdJ.zogrUrI7Crs}>9 && #{N2aXs7VlJdJ.iIC4YhgrxQY}/#{N2aXs7VlJdJ.zogrUrI7Crs}<=10,1,0)+
if(#{xrjnOtFFTRC.iIC4YhgrxQY}/#{xrjnOtFFTRC.zogrUrI7Crs}>9 && #{xrjnOtFFTRC.iIC4YhgrxQY}/#{xrjnOtFFTRC.zogrUrI7Crs}<=10,1,0)
>>
>>**Edit denominator**:  
>>>**Description**: "9-10 months - MSR - Denominator"  
>>>**Calculation**: "1"  
>
>**11 10-11 months - MSR**  
>For each item the Indicator returns "1" if the stock coverage time is greater or equal to 10 but less than 11 and otherwise returns 0 and then adds up these results for calculating the number of items with a stock coverage time of 10-11 months. 
>>**Name \(*)**: "10-11 months - MSR"  
>>**Short Name \(*)**: "10-11 months - MSR"  
>>**Description**: "Number of items with a coverage time of 10-11 months"  
>>**Decimals in data output**: "0"  
>>**Indicator type \(*)**: "Number (Factor 1)"  
>>**Edit numerator**:  
>>>**Description**: "1O-11 months - MSR - Numerator"  
>>>**Calculation**:  if(#{LNAkkMTxqEW.iIC4YhgrxQY}/#{LNAkkMTxqEW.zogrUrI7Crs}>10 && #{LNAkkMTxqEW.iIC4YhgrxQY}/#{LNAkkMTxqEW.zogrUrI7Crs}<=11,1,0)+
if(#{WyDZKSw82X6.iIC4YhgrxQY}/#{WyDZKSw82X6.zogrUrI7Crs}>10 && #{WyDZKSw82X6.iIC4YhgrxQY}/#{WyDZKSw82X6.zogrUrI7Crs}<=11,1,0)+
if(#{JPccVwAGRq9.iIC4YhgrxQY}/#{JPccVwAGRq9.zogrUrI7Crs}>10 && #{JPccVwAGRq9.iIC4YhgrxQY}/#{JPccVwAGRq9.zogrUrI7Crs}<=11,1,0)+
if(#{smxJz7Mt6ia.iIC4YhgrxQY}/#{smxJz7Mt6ia.zogrUrI7Crs}>10 && #{smxJz7Mt6ia.iIC4YhgrxQY}/#{smxJz7Mt6ia.zogrUrI7Crs}<=11,1,0)+
if(#{AaIApgGQM6t.iIC4YhgrxQY}/#{AaIApgGQM6t.zogrUrI7Crs}>10 && #{AaIApgGQM6t.iIC4YhgrxQY}/#{AaIApgGQM6t.zogrUrI7Crs}<=11,1,0)+
if(#{vCTrmv52APd.iIC4YhgrxQY}/#{vCTrmv52APd.zogrUrI7Crs}>10 && #{vCTrmv52APd.iIC4YhgrxQY}/#{vCTrmv52APd.zogrUrI7Crs}<=11,1,0)+
if(#{SOw2TcuFFH2.iIC4YhgrxQY}/#{SOw2TcuFFH2.zogrUrI7Crs}>10 && #{SOw2TcuFFH2.iIC4YhgrxQY}/#{SOw2TcuFFH2.zogrUrI7Crs}<=11,1,0)+
if(#{RSIOx2u07Ln.iIC4YhgrxQY}/#{RSIOx2u07Ln.zogrUrI7Crs}>10 && #{RSIOx2u07Ln.iIC4YhgrxQY}/#{RSIOx2u07Ln.zogrUrI7Crs}<=11,1,0)+
if(#{JStiDyaPfqy.iIC4YhgrxQY}/#{JStiDyaPfqy.zogrUrI7Crs}>10 && #{JStiDyaPfqy.iIC4YhgrxQY}/#{JStiDyaPfqy.zogrUrI7Crs}<=11,1,0)+
if(#{hZ1YvdcTDQM.iIC4YhgrxQY}/#{hZ1YvdcTDQM.zogrUrI7Crs}>10 && #{hZ1YvdcTDQM.iIC4YhgrxQY}/#{hZ1YvdcTDQM.zogrUrI7Crs}<=11,1,0)+
if(#{tsi32D8HQd5.iIC4YhgrxQY}/#{tsi32D8HQd5.zogrUrI7Crs}>10 && #{tsi32D8HQd5.iIC4YhgrxQY}/#{tsi32D8HQd5.zogrUrI7Crs}<=11,1,0)+
if(#{QWlPF8S0gCc.iIC4YhgrxQY}/#{QWlPF8S0gCc.zogrUrI7Crs}>10 && #{QWlPF8S0gCc.iIC4YhgrxQY}/#{QWlPF8S0gCc.zogrUrI7Crs}<=11,1,0)+
if(#{a5uLTDt12eT.iIC4YhgrxQY}/#{a5uLTDt12eT.zogrUrI7Crs}>10 && #{a5uLTDt12eT.iIC4YhgrxQY}/#{a5uLTDt12eT.zogrUrI7Crs}<=11,1,0)+
if(#{U0AfOOyJMy2.iIC4YhgrxQY}/#{U0AfOOyJMy2.zogrUrI7Crs}>10 && #{U0AfOOyJMy2.iIC4YhgrxQY}/#{U0AfOOyJMy2.zogrUrI7Crs}<=11,1,0)+
if(#{cyf6UdScfFM.iIC4YhgrxQY}/#{cyf6UdScfFM.zogrUrI7Crs}>10 && #{cyf6UdScfFM.iIC4YhgrxQY}/#{cyf6UdScfFM.zogrUrI7Crs}<=11,1,0)+
if(#{FeUTTNHpVzD.iIC4YhgrxQY}/#{FeUTTNHpVzD.zogrUrI7Crs}>10 && #{FeUTTNHpVzD.iIC4YhgrxQY}/#{FeUTTNHpVzD.zogrUrI7Crs}<=11,1,0)+
if(#{mKSICD1rxG4.iIC4YhgrxQY}/#{mKSICD1rxG4.zogrUrI7Crs}>10 && #{mKSICD1rxG4.iIC4YhgrxQY}/#{mKSICD1rxG4.zogrUrI7Crs}<=11,1,0)+
if(#{mVNe1aS1pGl.iIC4YhgrxQY}/#{mVNe1aS1pGl.zogrUrI7Crs}>10 && #{mVNe1aS1pGl.iIC4YhgrxQY}/#{mVNe1aS1pGl.zogrUrI7Crs}<=11,1,0)+
if(#{oLAXTZY6ken.iIC4YhgrxQY}/#{oLAXTZY6ken.zogrUrI7Crs}>10 && #{oLAXTZY6ken.iIC4YhgrxQY}/#{oLAXTZY6ken.zogrUrI7Crs}<=11,1,0)+
if(#{YYaRDUZyH9L.iIC4YhgrxQY}/#{YYaRDUZyH9L.zogrUrI7Crs}>10 && #{YYaRDUZyH9L.iIC4YhgrxQY}/#{YYaRDUZyH9L.zogrUrI7Crs}<=11,1,0)+
if(#{HVteopBt0jr.iIC4YhgrxQY}/#{HVteopBt0jr.zogrUrI7Crs}>10 && #{HVteopBt0jr.iIC4YhgrxQY}/#{HVteopBt0jr.zogrUrI7Crs}<=11,1,0)+
if(#{sWodd2tbjgZ.iIC4YhgrxQY}/#{sWodd2tbjgZ.zogrUrI7Crs}>10 && #{sWodd2tbjgZ.iIC4YhgrxQY}/#{sWodd2tbjgZ.zogrUrI7Crs}<=11,1,0)+
if(#{yVYajDDYUfX.iIC4YhgrxQY}/#{yVYajDDYUfX.zogrUrI7Crs}>10 && #{yVYajDDYUfX.iIC4YhgrxQY}/#{yVYajDDYUfX.zogrUrI7Crs}<=11,1,0)+
if(#{eTJAr4sc83v.iIC4YhgrxQY}/#{eTJAr4sc83v.zogrUrI7Crs}>10 && #{eTJAr4sc83v.iIC4YhgrxQY}/#{eTJAr4sc83v.zogrUrI7Crs}<=11,1,0)+
if(#{U4KSmanl4JP.iIC4YhgrxQY}/#{U4KSmanl4JP.zogrUrI7Crs}>10 && #{U4KSmanl4JP.iIC4YhgrxQY}/#{U4KSmanl4JP.zogrUrI7Crs}<=11,1,0)+
if(#{FXsa5uG3IGn.iIC4YhgrxQY}/#{FXsa5uG3IGn.zogrUrI7Crs}>10 && #{FXsa5uG3IGn.iIC4YhgrxQY}/#{FXsa5uG3IGn.zogrUrI7Crs}<=11,1,0)+
if(#{L34T9YDtCor.iIC4YhgrxQY}/#{L34T9YDtCor.zogrUrI7Crs}>10 && #{L34T9YDtCor.iIC4YhgrxQY}/#{L34T9YDtCor.zogrUrI7Crs}<=11,1,0)+
if(#{W5mHXhSYFfQ.iIC4YhgrxQY}/#{W5mHXhSYFfQ.zogrUrI7Crs}>10 && #{W5mHXhSYFfQ.iIC4YhgrxQY}/#{W5mHXhSYFfQ.zogrUrI7Crs}<=11,1,0)+
if(#{cmSUyJOZwyl.iIC4YhgrxQY}/#{cmSUyJOZwyl.zogrUrI7Crs}>10 && #{cmSUyJOZwyl.iIC4YhgrxQY}/#{cmSUyJOZwyl.zogrUrI7Crs}<=11,1,0)+
if(#{cT8sfosRXvU.iIC4YhgrxQY}/#{cT8sfosRXvU.zogrUrI7Crs}>10 && #{cT8sfosRXvU.iIC4YhgrxQY}/#{cT8sfosRXvU.zogrUrI7Crs}<=11,1,0)+
if(#{OaWKnMS7say.iIC4YhgrxQY}/#{OaWKnMS7say.zogrUrI7Crs}>10 && #{OaWKnMS7say.iIC4YhgrxQY}/#{OaWKnMS7say.zogrUrI7Crs}<=11,1,0)+
if(#{Z4bjHvGS6aH.iIC4YhgrxQY}/#{Z4bjHvGS6aH.zogrUrI7Crs}>10 && #{Z4bjHvGS6aH.iIC4YhgrxQY}/#{Z4bjHvGS6aH.zogrUrI7Crs}<=11,1,0)+
if(#{Nn1L7CNEtC8.iIC4YhgrxQY}/#{Nn1L7CNEtC8.zogrUrI7Crs}>10 && #{Nn1L7CNEtC8.iIC4YhgrxQY}/#{Nn1L7CNEtC8.zogrUrI7Crs}<=11,1,0)+
if(#{RNYKSc3nAUg.iIC4YhgrxQY}/#{RNYKSc3nAUg.zogrUrI7Crs}>10 && #{RNYKSc3nAUg.iIC4YhgrxQY}/#{RNYKSc3nAUg.zogrUrI7Crs}<=11,1,0)+
if(#{PtmZ9XqpPKi.iIC4YhgrxQY}/#{PtmZ9XqpPKi.zogrUrI7Crs}>10 && #{PtmZ9XqpPKi.iIC4YhgrxQY}/#{PtmZ9XqpPKi.zogrUrI7Crs}<=11,1,0)+
if(#{CohlLHi54B0.iIC4YhgrxQY}/#{CohlLHi54B0.zogrUrI7Crs}>10 && #{CohlLHi54B0.iIC4YhgrxQY}/#{CohlLHi54B0.zogrUrI7Crs}<=11,1,0)+
if(#{Gu6u82RD9OW.iIC4YhgrxQY}/#{Gu6u82RD9OW.zogrUrI7Crs}>10 && #{Gu6u82RD9OW.iIC4YhgrxQY}/#{Gu6u82RD9OW.zogrUrI7Crs}<=11,1,0)+
if(#{LiuYzxYr4Pt.iIC4YhgrxQY}/#{LiuYzxYr4Pt.zogrUrI7Crs}>10 && #{LiuYzxYr4Pt.iIC4YhgrxQY}/#{LiuYzxYr4Pt.zogrUrI7Crs}<=11,1,0)+
if(#{Tje33nJAG55.iIC4YhgrxQY}/#{Tje33nJAG55.zogrUrI7Crs}>10 && #{Tje33nJAG55.iIC4YhgrxQY}/#{Tje33nJAG55.zogrUrI7Crs}<=11,1,0)+
if(#{euM2dlqleYH.iIC4YhgrxQY}/#{euM2dlqleYH.zogrUrI7Crs}>10 && #{euM2dlqleYH.iIC4YhgrxQY}/#{euM2dlqleYH.zogrUrI7Crs}<=11,1,0)+
if(#{dASLmBTEehF.iIC4YhgrxQY}/#{dASLmBTEehF.zogrUrI7Crs}>10 && #{dASLmBTEehF.iIC4YhgrxQY}/#{dASLmBTEehF.zogrUrI7Crs}<=11,1,0)+
if(#{qU2LvzoPn1z.iIC4YhgrxQY}/#{qU2LvzoPn1z.zogrUrI7Crs}>10 && #{qU2LvzoPn1z.iIC4YhgrxQY}/#{qU2LvzoPn1z.zogrUrI7Crs}<=11,1,0)+
if(#{OkWaFxdUQY2.iIC4YhgrxQY}/#{OkWaFxdUQY2.zogrUrI7Crs}>10 && #{OkWaFxdUQY2.iIC4YhgrxQY}/#{OkWaFxdUQY2.zogrUrI7Crs}<=11,1,0)+
if(#{YHIv7KQc2e7.iIC4YhgrxQY}/#{YHIv7KQc2e7.zogrUrI7Crs}>10 && #{YHIv7KQc2e7.iIC4YhgrxQY}/#{YHIv7KQc2e7.zogrUrI7Crs}<=11,1,0)+
if(#{rt9D47Inb49.iIC4YhgrxQY}/#{rt9D47Inb49.zogrUrI7Crs}>10 && #{rt9D47Inb49.iIC4YhgrxQY}/#{rt9D47Inb49.zogrUrI7Crs}<=11,1,0)+
if(#{i1iXbquZ5iv.iIC4YhgrxQY}/#{i1iXbquZ5iv.zogrUrI7Crs}>10 && #{i1iXbquZ5iv.iIC4YhgrxQY}/#{i1iXbquZ5iv.zogrUrI7Crs}<=11,1,0)+
if(#{RcE30WBKrXI.iIC4YhgrxQY}/#{RcE30WBKrXI.zogrUrI7Crs}>10 && #{RcE30WBKrXI.iIC4YhgrxQY}/#{RcE30WBKrXI.zogrUrI7Crs}<=11,1,0)+
if(#{EAG0GfdSMAs.iIC4YhgrxQY}/#{EAG0GfdSMAs.zogrUrI7Crs}>10 && #{EAG0GfdSMAs.iIC4YhgrxQY}/#{EAG0GfdSMAs.zogrUrI7Crs}<=11,1,0)+
if(#{N2aXs7VlJdJ.iIC4YhgrxQY}/#{N2aXs7VlJdJ.zogrUrI7Crs}>10 && #{N2aXs7VlJdJ.iIC4YhgrxQY}/#{N2aXs7VlJdJ.zogrUrI7Crs}<=11,1,0)+
if(#{xrjnOtFFTRC.iIC4YhgrxQY}/#{xrjnOtFFTRC.zogrUrI7Crs}>10 && #{xrjnOtFFTRC.iIC4YhgrxQY}/#{xrjnOtFFTRC.zogrUrI7Crs}<=11,1,0)
>>
>>**Edit denominator**:  
>>>**Description**: "1O-11 months - MSR - Denominator"  
>>>**Calculation**: "1"  
>
>**12 11-12 months - MSR**  
>For each item the Indicator returns "1" if the stock coverage time is greater than or equal to 11 but less than 12 and otherwise returns 0 and then adds up these results for calculating the number of items with a stock coverage time of 11-12 months. 
>>**Name \(*)**: "11-12 months - MSR"  
>>**Short Name \(*)**: "11-12 months - MSR"  
>>**Description**: "Number of items with a coverage time of 11-12 months"  
>>**Decimals in data output**: "0"  
>>**Indicator type \(*)**: "Number (Factor 1)"  
>>**Edit numerator**:  
>>>**Description**: "11-12 months - MSR - Numerator"  
>>>**Calculation**:  if(#{LNAkkMTxqEW.iIC4YhgrxQY}/#{LNAkkMTxqEW.zogrUrI7Crs}>11 && #{LNAkkMTxqEW.iIC4YhgrxQY}/#{LNAkkMTxqEW.zogrUrI7Crs}<=12,1,0)+
if(#{WyDZKSw82X6.iIC4YhgrxQY}/#{WyDZKSw82X6.zogrUrI7Crs}>11 && #{WyDZKSw82X6.iIC4YhgrxQY}/#{WyDZKSw82X6.zogrUrI7Crs}<=12,1,0)+
if(#{JPccVwAGRq9.iIC4YhgrxQY}/#{JPccVwAGRq9.zogrUrI7Crs}>11 && #{JPccVwAGRq9.iIC4YhgrxQY}/#{JPccVwAGRq9.zogrUrI7Crs}<=12,1,0)+
if(#{smxJz7Mt6ia.iIC4YhgrxQY}/#{smxJz7Mt6ia.zogrUrI7Crs}>11 && #{smxJz7Mt6ia.iIC4YhgrxQY}/#{smxJz7Mt6ia.zogrUrI7Crs}<=12,1,0)+
if(#{AaIApgGQM6t.iIC4YhgrxQY}/#{AaIApgGQM6t.zogrUrI7Crs}>11 && #{AaIApgGQM6t.iIC4YhgrxQY}/#{AaIApgGQM6t.zogrUrI7Crs}<=12,1,0)+
if(#{vCTrmv52APd.iIC4YhgrxQY}/#{vCTrmv52APd.zogrUrI7Crs}>11 && #{vCTrmv52APd.iIC4YhgrxQY}/#{vCTrmv52APd.zogrUrI7Crs}<=12,1,0)+
if(#{SOw2TcuFFH2.iIC4YhgrxQY}/#{SOw2TcuFFH2.zogrUrI7Crs}>11 && #{SOw2TcuFFH2.iIC4YhgrxQY}/#{SOw2TcuFFH2.zogrUrI7Crs}<=12,1,0)+
if(#{RSIOx2u07Ln.iIC4YhgrxQY}/#{RSIOx2u07Ln.zogrUrI7Crs}>11 && #{RSIOx2u07Ln.iIC4YhgrxQY}/#{RSIOx2u07Ln.zogrUrI7Crs}<=12,1,0)+
if(#{JStiDyaPfqy.iIC4YhgrxQY}/#{JStiDyaPfqy.zogrUrI7Crs}>11 && #{JStiDyaPfqy.iIC4YhgrxQY}/#{JStiDyaPfqy.zogrUrI7Crs}<=12,1,0)+
if(#{hZ1YvdcTDQM.iIC4YhgrxQY}/#{hZ1YvdcTDQM.zogrUrI7Crs}>11 && #{hZ1YvdcTDQM.iIC4YhgrxQY}/#{hZ1YvdcTDQM.zogrUrI7Crs}<=12,1,0)+
if(#{tsi32D8HQd5.iIC4YhgrxQY}/#{tsi32D8HQd5.zogrUrI7Crs}>11 && #{tsi32D8HQd5.iIC4YhgrxQY}/#{tsi32D8HQd5.zogrUrI7Crs}<=12,1,0)+
if(#{QWlPF8S0gCc.iIC4YhgrxQY}/#{QWlPF8S0gCc.zogrUrI7Crs}>11 && #{QWlPF8S0gCc.iIC4YhgrxQY}/#{QWlPF8S0gCc.zogrUrI7Crs}<=12,1,0)+
if(#{a5uLTDt12eT.iIC4YhgrxQY}/#{a5uLTDt12eT.zogrUrI7Crs}>11 && #{a5uLTDt12eT.iIC4YhgrxQY}/#{a5uLTDt12eT.zogrUrI7Crs}<=12,1,0)+
if(#{U0AfOOyJMy2.iIC4YhgrxQY}/#{U0AfOOyJMy2.zogrUrI7Crs}>11 && #{U0AfOOyJMy2.iIC4YhgrxQY}/#{U0AfOOyJMy2.zogrUrI7Crs}<=12,1,0)+
if(#{cyf6UdScfFM.iIC4YhgrxQY}/#{cyf6UdScfFM.zogrUrI7Crs}>11 && #{cyf6UdScfFM.iIC4YhgrxQY}/#{cyf6UdScfFM.zogrUrI7Crs}<=12,1,0)+
if(#{FeUTTNHpVzD.iIC4YhgrxQY}/#{FeUTTNHpVzD.zogrUrI7Crs}>11 && #{FeUTTNHpVzD.iIC4YhgrxQY}/#{FeUTTNHpVzD.zogrUrI7Crs}<=12,1,0)+
if(#{mKSICD1rxG4.iIC4YhgrxQY}/#{mKSICD1rxG4.zogrUrI7Crs}>11 && #{mKSICD1rxG4.iIC4YhgrxQY}/#{mKSICD1rxG4.zogrUrI7Crs}<=12,1,0)+
if(#{mVNe1aS1pGl.iIC4YhgrxQY}/#{mVNe1aS1pGl.zogrUrI7Crs}>11 && #{mVNe1aS1pGl.iIC4YhgrxQY}/#{mVNe1aS1pGl.zogrUrI7Crs}<=12,1,0)+
if(#{oLAXTZY6ken.iIC4YhgrxQY}/#{oLAXTZY6ken.zogrUrI7Crs}>11 && #{oLAXTZY6ken.iIC4YhgrxQY}/#{oLAXTZY6ken.zogrUrI7Crs}<=12,1,0)+
if(#{YYaRDUZyH9L.iIC4YhgrxQY}/#{YYaRDUZyH9L.zogrUrI7Crs}>11 && #{YYaRDUZyH9L.iIC4YhgrxQY}/#{YYaRDUZyH9L.zogrUrI7Crs}<=12,1,0)+
if(#{HVteopBt0jr.iIC4YhgrxQY}/#{HVteopBt0jr.zogrUrI7Crs}>11 && #{HVteopBt0jr.iIC4YhgrxQY}/#{HVteopBt0jr.zogrUrI7Crs}<=12,1,0)+
if(#{sWodd2tbjgZ.iIC4YhgrxQY}/#{sWodd2tbjgZ.zogrUrI7Crs}>11 && #{sWodd2tbjgZ.iIC4YhgrxQY}/#{sWodd2tbjgZ.zogrUrI7Crs}<=12,1,0)+
if(#{yVYajDDYUfX.iIC4YhgrxQY}/#{yVYajDDYUfX.zogrUrI7Crs}>11 && #{yVYajDDYUfX.iIC4YhgrxQY}/#{yVYajDDYUfX.zogrUrI7Crs}<=12,1,0)+
if(#{eTJAr4sc83v.iIC4YhgrxQY}/#{eTJAr4sc83v.zogrUrI7Crs}>11 && #{eTJAr4sc83v.iIC4YhgrxQY}/#{eTJAr4sc83v.zogrUrI7Crs}<=12,1,0)+
if(#{U4KSmanl4JP.iIC4YhgrxQY}/#{U4KSmanl4JP.zogrUrI7Crs}>11 && #{U4KSmanl4JP.iIC4YhgrxQY}/#{U4KSmanl4JP.zogrUrI7Crs}<=12,1,0)+
if(#{FXsa5uG3IGn.iIC4YhgrxQY}/#{FXsa5uG3IGn.zogrUrI7Crs}>11 && #{FXsa5uG3IGn.iIC4YhgrxQY}/#{FXsa5uG3IGn.zogrUrI7Crs}<=12,1,0)+
if(#{L34T9YDtCor.iIC4YhgrxQY}/#{L34T9YDtCor.zogrUrI7Crs}>11 && #{L34T9YDtCor.iIC4YhgrxQY}/#{L34T9YDtCor.zogrUrI7Crs}<=12,1,0)+
if(#{W5mHXhSYFfQ.iIC4YhgrxQY}/#{W5mHXhSYFfQ.zogrUrI7Crs}>11 && #{W5mHXhSYFfQ.iIC4YhgrxQY}/#{W5mHXhSYFfQ.zogrUrI7Crs}<=12,1,0)+
if(#{cmSUyJOZwyl.iIC4YhgrxQY}/#{cmSUyJOZwyl.zogrUrI7Crs}>11 && #{cmSUyJOZwyl.iIC4YhgrxQY}/#{cmSUyJOZwyl.zogrUrI7Crs}<=12,1,0)+
if(#{cT8sfosRXvU.iIC4YhgrxQY}/#{cT8sfosRXvU.zogrUrI7Crs}>11 && #{cT8sfosRXvU.iIC4YhgrxQY}/#{cT8sfosRXvU.zogrUrI7Crs}<=12,1,0)+
if(#{OaWKnMS7say.iIC4YhgrxQY}/#{OaWKnMS7say.zogrUrI7Crs}>11 && #{OaWKnMS7say.iIC4YhgrxQY}/#{OaWKnMS7say.zogrUrI7Crs}<=12,1,0)+
if(#{Z4bjHvGS6aH.iIC4YhgrxQY}/#{Z4bjHvGS6aH.zogrUrI7Crs}>11 && #{Z4bjHvGS6aH.iIC4YhgrxQY}/#{Z4bjHvGS6aH.zogrUrI7Crs}<=12,1,0)+
if(#{Nn1L7CNEtC8.iIC4YhgrxQY}/#{Nn1L7CNEtC8.zogrUrI7Crs}>11 && #{Nn1L7CNEtC8.iIC4YhgrxQY}/#{Nn1L7CNEtC8.zogrUrI7Crs}<=12,1,0)+
if(#{RNYKSc3nAUg.iIC4YhgrxQY}/#{RNYKSc3nAUg.zogrUrI7Crs}>11 && #{RNYKSc3nAUg.iIC4YhgrxQY}/#{RNYKSc3nAUg.zogrUrI7Crs}<=12,1,0)+
if(#{PtmZ9XqpPKi.iIC4YhgrxQY}/#{PtmZ9XqpPKi.zogrUrI7Crs}>11 && #{PtmZ9XqpPKi.iIC4YhgrxQY}/#{PtmZ9XqpPKi.zogrUrI7Crs}<=12,1,0)+
if(#{CohlLHi54B0.iIC4YhgrxQY}/#{CohlLHi54B0.zogrUrI7Crs}>11 && #{CohlLHi54B0.iIC4YhgrxQY}/#{CohlLHi54B0.zogrUrI7Crs}<=12,1,0)+
if(#{Gu6u82RD9OW.iIC4YhgrxQY}/#{Gu6u82RD9OW.zogrUrI7Crs}>11 && #{Gu6u82RD9OW.iIC4YhgrxQY}/#{Gu6u82RD9OW.zogrUrI7Crs}<=12,1,0)+
if(#{LiuYzxYr4Pt.iIC4YhgrxQY}/#{LiuYzxYr4Pt.zogrUrI7Crs}>11 && #{LiuYzxYr4Pt.iIC4YhgrxQY}/#{LiuYzxYr4Pt.zogrUrI7Crs}<=12,1,0)+
if(#{Tje33nJAG55.iIC4YhgrxQY}/#{Tje33nJAG55.zogrUrI7Crs}>11 && #{Tje33nJAG55.iIC4YhgrxQY}/#{Tje33nJAG55.zogrUrI7Crs}<=12,1,0)+
if(#{euM2dlqleYH.iIC4YhgrxQY}/#{euM2dlqleYH.zogrUrI7Crs}>11 && #{euM2dlqleYH.iIC4YhgrxQY}/#{euM2dlqleYH.zogrUrI7Crs}<=12,1,0)+
if(#{dASLmBTEehF.iIC4YhgrxQY}/#{dASLmBTEehF.zogrUrI7Crs}>11 && #{dASLmBTEehF.iIC4YhgrxQY}/#{dASLmBTEehF.zogrUrI7Crs}<=12,1,0)+
if(#{qU2LvzoPn1z.iIC4YhgrxQY}/#{qU2LvzoPn1z.zogrUrI7Crs}>11 && #{qU2LvzoPn1z.iIC4YhgrxQY}/#{qU2LvzoPn1z.zogrUrI7Crs}<=12,1,0)+
if(#{OkWaFxdUQY2.iIC4YhgrxQY}/#{OkWaFxdUQY2.zogrUrI7Crs}>11 && #{OkWaFxdUQY2.iIC4YhgrxQY}/#{OkWaFxdUQY2.zogrUrI7Crs}<=12,1,0)+
if(#{YHIv7KQc2e7.iIC4YhgrxQY}/#{YHIv7KQc2e7.zogrUrI7Crs}>11 && #{YHIv7KQc2e7.iIC4YhgrxQY}/#{YHIv7KQc2e7.zogrUrI7Crs}<=12,1,0)+
if(#{rt9D47Inb49.iIC4YhgrxQY}/#{rt9D47Inb49.zogrUrI7Crs}>11 && #{rt9D47Inb49.iIC4YhgrxQY}/#{rt9D47Inb49.zogrUrI7Crs}<=12,1,0)+
if(#{i1iXbquZ5iv.iIC4YhgrxQY}/#{i1iXbquZ5iv.zogrUrI7Crs}>11 && #{i1iXbquZ5iv.iIC4YhgrxQY}/#{i1iXbquZ5iv.zogrUrI7Crs}<=12,1,0)+
if(#{RcE30WBKrXI.iIC4YhgrxQY}/#{RcE30WBKrXI.zogrUrI7Crs}>11 && #{RcE30WBKrXI.iIC4YhgrxQY}/#{RcE30WBKrXI.zogrUrI7Crs}<=12,1,0)+
if(#{EAG0GfdSMAs.iIC4YhgrxQY}/#{EAG0GfdSMAs.zogrUrI7Crs}>11 && #{EAG0GfdSMAs.iIC4YhgrxQY}/#{EAG0GfdSMAs.zogrUrI7Crs}<=12,1,0)+
if(#{N2aXs7VlJdJ.iIC4YhgrxQY}/#{N2aXs7VlJdJ.zogrUrI7Crs}>11 && #{N2aXs7VlJdJ.iIC4YhgrxQY}/#{N2aXs7VlJdJ.zogrUrI7Crs}<=12,1,0)+
if(#{xrjnOtFFTRC.iIC4YhgrxQY}/#{xrjnOtFFTRC.zogrUrI7Crs}>11 && #{xrjnOtFFTRC.iIC4YhgrxQY}/#{xrjnOtFFTRC.zogrUrI7Crs}<=12,1,0)
>>
>>**Edit denominator**:  
>>>**Description**: "11-12 months - MSR - Denominator"  
>>>**Calculation**: "1"  
>
>**13 1-2 years - MSR**  
>For each item the Indicator returns "1" if the stock coverage time is greater rhan or equal to 12 but less than 24 and otherwise returns 0and then adds up these results for calculating the number of items with a stock coverage time of 12-24 months. 
>>**Name \(*)**: "1-2 years - MSR"  
>>**Short Name \(*)**: "1-2 years - MSR"  
>>**Description**: "Number of items with a coverage time of 1-2 years"  
>>**Decimals in data output**: "0"  
>>**Indicator type \(*)**: "Number (Factor 1)"  
>>**Edit numerator**:  
>>>**Description**: "1-2 years - MSR - Numerator"  
>>>**Calculation**:  if(#{LNAkkMTxqEW.iIC4YhgrxQY}/#{LNAkkMTxqEW.zogrUrI7Crs}>12 && #{LNAkkMTxqEW.iIC4YhgrxQY}/#{LNAkkMTxqEW.zogrUrI7Crs}<=24,1,0)+
if(#{WyDZKSw82X6.iIC4YhgrxQY}/#{WyDZKSw82X6.zogrUrI7Crs}>12 && #{WyDZKSw82X6.iIC4YhgrxQY}/#{WyDZKSw82X6.zogrUrI7Crs}<=24,1,0)+
if(#{JPccVwAGRq9.iIC4YhgrxQY}/#{JPccVwAGRq9.zogrUrI7Crs}>12 && #{JPccVwAGRq9.iIC4YhgrxQY}/#{JPccVwAGRq9.zogrUrI7Crs}<=24,1,0)+
if(#{smxJz7Mt6ia.iIC4YhgrxQY}/#{smxJz7Mt6ia.zogrUrI7Crs}>12 && #{smxJz7Mt6ia.iIC4YhgrxQY}/#{smxJz7Mt6ia.zogrUrI7Crs}<=24,1,0)+
if(#{AaIApgGQM6t.iIC4YhgrxQY}/#{AaIApgGQM6t.zogrUrI7Crs}>12 && #{AaIApgGQM6t.iIC4YhgrxQY}/#{AaIApgGQM6t.zogrUrI7Crs}<=24,1,0)+
if(#{vCTrmv52APd.iIC4YhgrxQY}/#{vCTrmv52APd.zogrUrI7Crs}>12 && #{vCTrmv52APd.iIC4YhgrxQY}/#{vCTrmv52APd.zogrUrI7Crs}<=24,1,0)+
if(#{SOw2TcuFFH2.iIC4YhgrxQY}/#{SOw2TcuFFH2.zogrUrI7Crs}>12 && #{SOw2TcuFFH2.iIC4YhgrxQY}/#{SOw2TcuFFH2.zogrUrI7Crs}<=24,1,0)+
if(#{RSIOx2u07Ln.iIC4YhgrxQY}/#{RSIOx2u07Ln.zogrUrI7Crs}>12 && #{RSIOx2u07Ln.iIC4YhgrxQY}/#{RSIOx2u07Ln.zogrUrI7Crs}<=24,1,0)+
if(#{JStiDyaPfqy.iIC4YhgrxQY}/#{JStiDyaPfqy.zogrUrI7Crs}>12 && #{JStiDyaPfqy.iIC4YhgrxQY}/#{JStiDyaPfqy.zogrUrI7Crs}<=24,1,0)+
if(#{hZ1YvdcTDQM.iIC4YhgrxQY}/#{hZ1YvdcTDQM.zogrUrI7Crs}>12 && #{hZ1YvdcTDQM.iIC4YhgrxQY}/#{hZ1YvdcTDQM.zogrUrI7Crs}<=24,1,0)+
if(#{tsi32D8HQd5.iIC4YhgrxQY}/#{tsi32D8HQd5.zogrUrI7Crs}>12 && #{tsi32D8HQd5.iIC4YhgrxQY}/#{tsi32D8HQd5.zogrUrI7Crs}<=24,1,0)+
if(#{QWlPF8S0gCc.iIC4YhgrxQY}/#{QWlPF8S0gCc.zogrUrI7Crs}>12 && #{QWlPF8S0gCc.iIC4YhgrxQY}/#{QWlPF8S0gCc.zogrUrI7Crs}<=24,1,0)+
if(#{a5uLTDt12eT.iIC4YhgrxQY}/#{a5uLTDt12eT.zogrUrI7Crs}>12 && #{a5uLTDt12eT.iIC4YhgrxQY}/#{a5uLTDt12eT.zogrUrI7Crs}<=24,1,0)+
if(#{U0AfOOyJMy2.iIC4YhgrxQY}/#{U0AfOOyJMy2.zogrUrI7Crs}>12 && #{U0AfOOyJMy2.iIC4YhgrxQY}/#{U0AfOOyJMy2.zogrUrI7Crs}<=24,1,0)+
if(#{cyf6UdScfFM.iIC4YhgrxQY}/#{cyf6UdScfFM.zogrUrI7Crs}>12 && #{cyf6UdScfFM.iIC4YhgrxQY}/#{cyf6UdScfFM.zogrUrI7Crs}<=24,1,0)+
if(#{FeUTTNHpVzD.iIC4YhgrxQY}/#{FeUTTNHpVzD.zogrUrI7Crs}>12 && #{FeUTTNHpVzD.iIC4YhgrxQY}/#{FeUTTNHpVzD.zogrUrI7Crs}<=24,1,0)+
if(#{mKSICD1rxG4.iIC4YhgrxQY}/#{mKSICD1rxG4.zogrUrI7Crs}>12 && #{mKSICD1rxG4.iIC4YhgrxQY}/#{mKSICD1rxG4.zogrUrI7Crs}<=24,1,0)+
if(#{mVNe1aS1pGl.iIC4YhgrxQY}/#{mVNe1aS1pGl.zogrUrI7Crs}>12 && #{mVNe1aS1pGl.iIC4YhgrxQY}/#{mVNe1aS1pGl.zogrUrI7Crs}<=24,1,0)+
if(#{oLAXTZY6ken.iIC4YhgrxQY}/#{oLAXTZY6ken.zogrUrI7Crs}>12 && #{oLAXTZY6ken.iIC4YhgrxQY}/#{oLAXTZY6ken.zogrUrI7Crs}<=24,1,0)+
if(#{YYaRDUZyH9L.iIC4YhgrxQY}/#{YYaRDUZyH9L.zogrUrI7Crs}>12 && #{YYaRDUZyH9L.iIC4YhgrxQY}/#{YYaRDUZyH9L.zogrUrI7Crs}<=24,1,0)+
if(#{HVteopBt0jr.iIC4YhgrxQY}/#{HVteopBt0jr.zogrUrI7Crs}>12 && #{HVteopBt0jr.iIC4YhgrxQY}/#{HVteopBt0jr.zogrUrI7Crs}<=24,1,0)+
if(#{sWodd2tbjgZ.iIC4YhgrxQY}/#{sWodd2tbjgZ.zogrUrI7Crs}>12 && #{sWodd2tbjgZ.iIC4YhgrxQY}/#{sWodd2tbjgZ.zogrUrI7Crs}<=24,1,0)+
if(#{yVYajDDYUfX.iIC4YhgrxQY}/#{yVYajDDYUfX.zogrUrI7Crs}>12 && #{yVYajDDYUfX.iIC4YhgrxQY}/#{yVYajDDYUfX.zogrUrI7Crs}<=24,1,0)+
if(#{eTJAr4sc83v.iIC4YhgrxQY}/#{eTJAr4sc83v.zogrUrI7Crs}>12 && #{eTJAr4sc83v.iIC4YhgrxQY}/#{eTJAr4sc83v.zogrUrI7Crs}<=24,1,0)+
if(#{U4KSmanl4JP.iIC4YhgrxQY}/#{U4KSmanl4JP.zogrUrI7Crs}>12 && #{U4KSmanl4JP.iIC4YhgrxQY}/#{U4KSmanl4JP.zogrUrI7Crs}<=24,1,0)+
if(#{FXsa5uG3IGn.iIC4YhgrxQY}/#{FXsa5uG3IGn.zogrUrI7Crs}>12 && #{FXsa5uG3IGn.iIC4YhgrxQY}/#{FXsa5uG3IGn.zogrUrI7Crs}<=24,1,0)+
if(#{L34T9YDtCor.iIC4YhgrxQY}/#{L34T9YDtCor.zogrUrI7Crs}>12 && #{L34T9YDtCor.iIC4YhgrxQY}/#{L34T9YDtCor.zogrUrI7Crs}<=24,1,0)+
if(#{W5mHXhSYFfQ.iIC4YhgrxQY}/#{W5mHXhSYFfQ.zogrUrI7Crs}>12 && #{W5mHXhSYFfQ.iIC4YhgrxQY}/#{W5mHXhSYFfQ.zogrUrI7Crs}<=24,1,0)+
if(#{cmSUyJOZwyl.iIC4YhgrxQY}/#{cmSUyJOZwyl.zogrUrI7Crs}>12 && #{cmSUyJOZwyl.iIC4YhgrxQY}/#{cmSUyJOZwyl.zogrUrI7Crs}<=24,1,0)+
if(#{cT8sfosRXvU.iIC4YhgrxQY}/#{cT8sfosRXvU.zogrUrI7Crs}>12 && #{cT8sfosRXvU.iIC4YhgrxQY}/#{cT8sfosRXvU.zogrUrI7Crs}<=24,1,0)+
if(#{OaWKnMS7say.iIC4YhgrxQY}/#{OaWKnMS7say.zogrUrI7Crs}>12 && #{OaWKnMS7say.iIC4YhgrxQY}/#{OaWKnMS7say.zogrUrI7Crs}<=24,1,0)+
if(#{Z4bjHvGS6aH.iIC4YhgrxQY}/#{Z4bjHvGS6aH.zogrUrI7Crs}>12 && #{Z4bjHvGS6aH.iIC4YhgrxQY}/#{Z4bjHvGS6aH.zogrUrI7Crs}<=24,1,0)+
if(#{Nn1L7CNEtC8.iIC4YhgrxQY}/#{Nn1L7CNEtC8.zogrUrI7Crs}>12 && #{Nn1L7CNEtC8.iIC4YhgrxQY}/#{Nn1L7CNEtC8.zogrUrI7Crs}<=24,1,0)+
if(#{RNYKSc3nAUg.iIC4YhgrxQY}/#{RNYKSc3nAUg.zogrUrI7Crs}>12 && #{RNYKSc3nAUg.iIC4YhgrxQY}/#{RNYKSc3nAUg.zogrUrI7Crs}<=24,1,0)+
if(#{PtmZ9XqpPKi.iIC4YhgrxQY}/#{PtmZ9XqpPKi.zogrUrI7Crs}>12 && #{PtmZ9XqpPKi.iIC4YhgrxQY}/#{PtmZ9XqpPKi.zogrUrI7Crs}<=24,1,0)+
if(#{CohlLHi54B0.iIC4YhgrxQY}/#{CohlLHi54B0.zogrUrI7Crs}>12 && #{CohlLHi54B0.iIC4YhgrxQY}/#{CohlLHi54B0.zogrUrI7Crs}<=24,1,0)+
if(#{Gu6u82RD9OW.iIC4YhgrxQY}/#{Gu6u82RD9OW.zogrUrI7Crs}>12 && #{Gu6u82RD9OW.iIC4YhgrxQY}/#{Gu6u82RD9OW.zogrUrI7Crs}<=24,1,0)+
if(#{LiuYzxYr4Pt.iIC4YhgrxQY}/#{LiuYzxYr4Pt.zogrUrI7Crs}>12 && #{LiuYzxYr4Pt.iIC4YhgrxQY}/#{LiuYzxYr4Pt.zogrUrI7Crs}<=24,1,0)+
if(#{Tje33nJAG55.iIC4YhgrxQY}/#{Tje33nJAG55.zogrUrI7Crs}>12 && #{Tje33nJAG55.iIC4YhgrxQY}/#{Tje33nJAG55.zogrUrI7Crs}<=24,1,0)+
if(#{euM2dlqleYH.iIC4YhgrxQY}/#{euM2dlqleYH.zogrUrI7Crs}>12 && #{euM2dlqleYH.iIC4YhgrxQY}/#{euM2dlqleYH.zogrUrI7Crs}<=24,1,0)+
if(#{dASLmBTEehF.iIC4YhgrxQY}/#{dASLmBTEehF.zogrUrI7Crs}>12 && #{dASLmBTEehF.iIC4YhgrxQY}/#{dASLmBTEehF.zogrUrI7Crs}<=24,1,0)+
if(#{qU2LvzoPn1z.iIC4YhgrxQY}/#{qU2LvzoPn1z.zogrUrI7Crs}>12 && #{qU2LvzoPn1z.iIC4YhgrxQY}/#{qU2LvzoPn1z.zogrUrI7Crs}<=24,1,0)+
if(#{OkWaFxdUQY2.iIC4YhgrxQY}/#{OkWaFxdUQY2.zogrUrI7Crs}>12 && #{OkWaFxdUQY2.iIC4YhgrxQY}/#{OkWaFxdUQY2.zogrUrI7Crs}<=24,1,0)+
if(#{YHIv7KQc2e7.iIC4YhgrxQY}/#{YHIv7KQc2e7.zogrUrI7Crs}>12 && #{YHIv7KQc2e7.iIC4YhgrxQY}/#{YHIv7KQc2e7.zogrUrI7Crs}<=24,1,0)+
if(#{rt9D47Inb49.iIC4YhgrxQY}/#{rt9D47Inb49.zogrUrI7Crs}>12 && #{rt9D47Inb49.iIC4YhgrxQY}/#{rt9D47Inb49.zogrUrI7Crs}<=24,1,0)+
if(#{i1iXbquZ5iv.iIC4YhgrxQY}/#{i1iXbquZ5iv.zogrUrI7Crs}>12 && #{i1iXbquZ5iv.iIC4YhgrxQY}/#{i1iXbquZ5iv.zogrUrI7Crs}<=24,1,0)+
if(#{RcE30WBKrXI.iIC4YhgrxQY}/#{RcE30WBKrXI.zogrUrI7Crs}>12 && #{RcE30WBKrXI.iIC4YhgrxQY}/#{RcE30WBKrXI.zogrUrI7Crs}<=24,1,0)+
if(#{EAG0GfdSMAs.iIC4YhgrxQY}/#{EAG0GfdSMAs.zogrUrI7Crs}>12 && #{EAG0GfdSMAs.iIC4YhgrxQY}/#{EAG0GfdSMAs.zogrUrI7Crs}<=24,1,0)+
if(#{N2aXs7VlJdJ.iIC4YhgrxQY}/#{N2aXs7VlJdJ.zogrUrI7Crs}>12 && #{N2aXs7VlJdJ.iIC4YhgrxQY}/#{N2aXs7VlJdJ.zogrUrI7Crs}<=24,1,0)+
if(#{xrjnOtFFTRC.iIC4YhgrxQY}/#{xrjnOtFFTRC.zogrUrI7Crs}>12 && #{xrjnOtFFTRC.iIC4YhgrxQY}/#{xrjnOtFFTRC.zogrUrI7Crs}<=24,1,0)
>>
>>**Edit denominator**:  
>>>**Description**: "12-24 months - MSR - Denominator"  
>>>**Calculation**: "1"  
>
>**14 2-3 years - MSR**  
>For each item the Indicator returns "1" if the stock coverage time is greater than or equal to 24 but less than 36 and otherwise returns 0 and then adds up these results for calculating the number of items with a stock coverage time of 24-36 months. 
>>**Name \(*)**: "2-3 years - MSR"  
>>**Short Name \(*)**: "2-3 years - MSR"  
>>**Description**: "Number of items with a coverage time of 2-3 years"  
>>**Decimals in data output**: "0"  
>>**Indicator type \(*)**: "Number (Factor 1)"  
>>**Edit numerator**:  
>>>**Description**: "2-3 years - MSR - Numerator"  
>>>**Calculation**:
>>>if(#{LNAkkMTxqEW.iIC4YhgrxQY}/#{LNAkkMTxqEW.zogrUrI7Crs}>24 && #{LNAkkMTxqEW.iIC4YhgrxQY}/#{LNAkkMTxqEW.zogrUrI7Crs}<=36,1,0)+
if(#{WyDZKSw82X6.iIC4YhgrxQY}/#{WyDZKSw82X6.zogrUrI7Crs}>24 && #{WyDZKSw82X6.iIC4YhgrxQY}/#{WyDZKSw82X6.zogrUrI7Crs}<=36,1,0)+
if(#{JPccVwAGRq9.iIC4YhgrxQY}/#{JPccVwAGRq9.zogrUrI7Crs}>24 && #{JPccVwAGRq9.iIC4YhgrxQY}/#{JPccVwAGRq9.zogrUrI7Crs}<=36,1,0)+
if(#{smxJz7Mt6ia.iIC4YhgrxQY}/#{smxJz7Mt6ia.zogrUrI7Crs}>24 && #{smxJz7Mt6ia.iIC4YhgrxQY}/#{smxJz7Mt6ia.zogrUrI7Crs}<=36,1,0)+
if(#{AaIApgGQM6t.iIC4YhgrxQY}/#{AaIApgGQM6t.zogrUrI7Crs}>24 && #{AaIApgGQM6t.iIC4YhgrxQY}/#{AaIApgGQM6t.zogrUrI7Crs}<=36,1,0)+
if(#{vCTrmv52APd.iIC4YhgrxQY}/#{vCTrmv52APd.zogrUrI7Crs}>24 && #{vCTrmv52APd.iIC4YhgrxQY}/#{vCTrmv52APd.zogrUrI7Crs}<=36,1,0)+
if(#{SOw2TcuFFH2.iIC4YhgrxQY}/#{SOw2TcuFFH2.zogrUrI7Crs}>24 && #{SOw2TcuFFH2.iIC4YhgrxQY}/#{SOw2TcuFFH2.zogrUrI7Crs}<=36,1,0)+
if(#{RSIOx2u07Ln.iIC4YhgrxQY}/#{RSIOx2u07Ln.zogrUrI7Crs}>24 && #{RSIOx2u07Ln.iIC4YhgrxQY}/#{RSIOx2u07Ln.zogrUrI7Crs}<=36,1,0)+
if(#{JStiDyaPfqy.iIC4YhgrxQY}/#{JStiDyaPfqy.zogrUrI7Crs}>24 && #{JStiDyaPfqy.iIC4YhgrxQY}/#{JStiDyaPfqy.zogrUrI7Crs}<=36,1,0)+
if(#{hZ1YvdcTDQM.iIC4YhgrxQY}/#{hZ1YvdcTDQM.zogrUrI7Crs}>24 && #{hZ1YvdcTDQM.iIC4YhgrxQY}/#{hZ1YvdcTDQM.zogrUrI7Crs}<=36,1,0)+
if(#{tsi32D8HQd5.iIC4YhgrxQY}/#{tsi32D8HQd5.zogrUrI7Crs}>24 && #{tsi32D8HQd5.iIC4YhgrxQY}/#{tsi32D8HQd5.zogrUrI7Crs}<=36,1,0)+
if(#{QWlPF8S0gCc.iIC4YhgrxQY}/#{QWlPF8S0gCc.zogrUrI7Crs}>24 && #{QWlPF8S0gCc.iIC4YhgrxQY}/#{QWlPF8S0gCc.zogrUrI7Crs}<=36,1,0)+
if(#{a5uLTDt12eT.iIC4YhgrxQY}/#{a5uLTDt12eT.zogrUrI7Crs}>24 && #{a5uLTDt12eT.iIC4YhgrxQY}/#{a5uLTDt12eT.zogrUrI7Crs}<=36,1,0)+
if(#{U0AfOOyJMy2.iIC4YhgrxQY}/#{U0AfOOyJMy2.zogrUrI7Crs}>24 && #{U0AfOOyJMy2.iIC4YhgrxQY}/#{U0AfOOyJMy2.zogrUrI7Crs}<=36,1,0)+
if(#{cyf6UdScfFM.iIC4YhgrxQY}/#{cyf6UdScfFM.zogrUrI7Crs}>24 && #{cyf6UdScfFM.iIC4YhgrxQY}/#{cyf6UdScfFM.zogrUrI7Crs}<=36,1,0)+
if(#{FeUTTNHpVzD.iIC4YhgrxQY}/#{FeUTTNHpVzD.zogrUrI7Crs}>24 && #{FeUTTNHpVzD.iIC4YhgrxQY}/#{FeUTTNHpVzD.zogrUrI7Crs}<=36,1,0)+
if(#{mKSICD1rxG4.iIC4YhgrxQY}/#{mKSICD1rxG4.zogrUrI7Crs}>24 && #{mKSICD1rxG4.iIC4YhgrxQY}/#{mKSICD1rxG4.zogrUrI7Crs}<=36,1,0)+
if(#{mVNe1aS1pGl.iIC4YhgrxQY}/#{mVNe1aS1pGl.zogrUrI7Crs}>24 && #{mVNe1aS1pGl.iIC4YhgrxQY}/#{mVNe1aS1pGl.zogrUrI7Crs}<=36,1,0)+
if(#{oLAXTZY6ken.iIC4YhgrxQY}/#{oLAXTZY6ken.zogrUrI7Crs}>24 && #{oLAXTZY6ken.iIC4YhgrxQY}/#{oLAXTZY6ken.zogrUrI7Crs}<=36,1,0)+
if(#{YYaRDUZyH9L.iIC4YhgrxQY}/#{YYaRDUZyH9L.zogrUrI7Crs}>24 && #{YYaRDUZyH9L.iIC4YhgrxQY}/#{YYaRDUZyH9L.zogrUrI7Crs}<=36,1,0)+
if(#{HVteopBt0jr.iIC4YhgrxQY}/#{HVteopBt0jr.zogrUrI7Crs}>24 && #{HVteopBt0jr.iIC4YhgrxQY}/#{HVteopBt0jr.zogrUrI7Crs}<=36,1,0)+
if(#{sWodd2tbjgZ.iIC4YhgrxQY}/#{sWodd2tbjgZ.zogrUrI7Crs}>24 && #{sWodd2tbjgZ.iIC4YhgrxQY}/#{sWodd2tbjgZ.zogrUrI7Crs}<=36,1,0)+
if(#{yVYajDDYUfX.iIC4YhgrxQY}/#{yVYajDDYUfX.zogrUrI7Crs}>24 && #{yVYajDDYUfX.iIC4YhgrxQY}/#{yVYajDDYUfX.zogrUrI7Crs}<=36,1,0)+
if(#{eTJAr4sc83v.iIC4YhgrxQY}/#{eTJAr4sc83v.zogrUrI7Crs}>24 && #{eTJAr4sc83v.iIC4YhgrxQY}/#{eTJAr4sc83v.zogrUrI7Crs}<=36,1,0)+
if(#{U4KSmanl4JP.iIC4YhgrxQY}/#{U4KSmanl4JP.zogrUrI7Crs}>24 && #{U4KSmanl4JP.iIC4YhgrxQY}/#{U4KSmanl4JP.zogrUrI7Crs}<=36,1,0)+
if(#{FXsa5uG3IGn.iIC4YhgrxQY}/#{FXsa5uG3IGn.zogrUrI7Crs}>24 && #{FXsa5uG3IGn.iIC4YhgrxQY}/#{FXsa5uG3IGn.zogrUrI7Crs}<=36,1,0)+
if(#{L34T9YDtCor.iIC4YhgrxQY}/#{L34T9YDtCor.zogrUrI7Crs}>24 && #{L34T9YDtCor.iIC4YhgrxQY}/#{L34T9YDtCor.zogrUrI7Crs}<=36,1,0)+
if(#{W5mHXhSYFfQ.iIC4YhgrxQY}/#{W5mHXhSYFfQ.zogrUrI7Crs}>24 && #{W5mHXhSYFfQ.iIC4YhgrxQY}/#{W5mHXhSYFfQ.zogrUrI7Crs}<=36,1,0)+
if(#{cmSUyJOZwyl.iIC4YhgrxQY}/#{cmSUyJOZwyl.zogrUrI7Crs}>24 && #{cmSUyJOZwyl.iIC4YhgrxQY}/#{cmSUyJOZwyl.zogrUrI7Crs}<=36,1,0)+
if(#{cT8sfosRXvU.iIC4YhgrxQY}/#{cT8sfosRXvU.zogrUrI7Crs}>24 && #{cT8sfosRXvU.iIC4YhgrxQY}/#{cT8sfosRXvU.zogrUrI7Crs}<=36,1,0)+
if(#{OaWKnMS7say.iIC4YhgrxQY}/#{OaWKnMS7say.zogrUrI7Crs}>24 && #{OaWKnMS7say.iIC4YhgrxQY}/#{OaWKnMS7say.zogrUrI7Crs}<=36,1,0)+
if(#{Z4bjHvGS6aH.iIC4YhgrxQY}/#{Z4bjHvGS6aH.zogrUrI7Crs}>24 && #{Z4bjHvGS6aH.iIC4YhgrxQY}/#{Z4bjHvGS6aH.zogrUrI7Crs}<=36,1,0)+
if(#{Nn1L7CNEtC8.iIC4YhgrxQY}/#{Nn1L7CNEtC8.zogrUrI7Crs}>24 && #{Nn1L7CNEtC8.iIC4YhgrxQY}/#{Nn1L7CNEtC8.zogrUrI7Crs}<=36,1,0)+
if(#{RNYKSc3nAUg.iIC4YhgrxQY}/#{RNYKSc3nAUg.zogrUrI7Crs}>24 && #{RNYKSc3nAUg.iIC4YhgrxQY}/#{RNYKSc3nAUg.zogrUrI7Crs}<=36,1,0)+
if(#{PtmZ9XqpPKi.iIC4YhgrxQY}/#{PtmZ9XqpPKi.zogrUrI7Crs}>24 && #{PtmZ9XqpPKi.iIC4YhgrxQY}/#{PtmZ9XqpPKi.zogrUrI7Crs}<=36,1,0)+
if(#{CohlLHi54B0.iIC4YhgrxQY}/#{CohlLHi54B0.zogrUrI7Crs}>24 && #{CohlLHi54B0.iIC4YhgrxQY}/#{CohlLHi54B0.zogrUrI7Crs}<=36,1,0)+
if(#{Gu6u82RD9OW.iIC4YhgrxQY}/#{Gu6u82RD9OW.zogrUrI7Crs}>24 && #{Gu6u82RD9OW.iIC4YhgrxQY}/#{Gu6u82RD9OW.zogrUrI7Crs}<=36,1,0)+
if(#{LiuYzxYr4Pt.iIC4YhgrxQY}/#{LiuYzxYr4Pt.zogrUrI7Crs}>24 && #{LiuYzxYr4Pt.iIC4YhgrxQY}/#{LiuYzxYr4Pt.zogrUrI7Crs}<=36,1,0)+
if(#{Tje33nJAG55.iIC4YhgrxQY}/#{Tje33nJAG55.zogrUrI7Crs}>24 && #{Tje33nJAG55.iIC4YhgrxQY}/#{Tje33nJAG55.zogrUrI7Crs}<=36,1,0)+
if(#{euM2dlqleYH.iIC4YhgrxQY}/#{euM2dlqleYH.zogrUrI7Crs}>24 && #{euM2dlqleYH.iIC4YhgrxQY}/#{euM2dlqleYH.zogrUrI7Crs}<=36,1,0)+
if(#{dASLmBTEehF.iIC4YhgrxQY}/#{dASLmBTEehF.zogrUrI7Crs}>24 && #{dASLmBTEehF.iIC4YhgrxQY}/#{dASLmBTEehF.zogrUrI7Crs}<=36,1,0)+
if(#{qU2LvzoPn1z.iIC4YhgrxQY}/#{qU2LvzoPn1z.zogrUrI7Crs}>24 && #{qU2LvzoPn1z.iIC4YhgrxQY}/#{qU2LvzoPn1z.zogrUrI7Crs}<=36,1,0)+
if(#{OkWaFxdUQY2.iIC4YhgrxQY}/#{OkWaFxdUQY2.zogrUrI7Crs}>24 && #{OkWaFxdUQY2.iIC4YhgrxQY}/#{OkWaFxdUQY2.zogrUrI7Crs}<=36,1,0)+
if(#{YHIv7KQc2e7.iIC4YhgrxQY}/#{YHIv7KQc2e7.zogrUrI7Crs}>24 && #{YHIv7KQc2e7.iIC4YhgrxQY}/#{YHIv7KQc2e7.zogrUrI7Crs}<=36,1,0)+
if(#{rt9D47Inb49.iIC4YhgrxQY}/#{rt9D47Inb49.zogrUrI7Crs}>24 && #{rt9D47Inb49.iIC4YhgrxQY}/#{rt9D47Inb49.zogrUrI7Crs}<=36,1,0)+
if(#{i1iXbquZ5iv.iIC4YhgrxQY}/#{i1iXbquZ5iv.zogrUrI7Crs}>24 && #{i1iXbquZ5iv.iIC4YhgrxQY}/#{i1iXbquZ5iv.zogrUrI7Crs}<=36,1,0)+
if(#{RcE30WBKrXI.iIC4YhgrxQY}/#{RcE30WBKrXI.zogrUrI7Crs}>24 && #{RcE30WBKrXI.iIC4YhgrxQY}/#{RcE30WBKrXI.zogrUrI7Crs}<=36,1,0)+
if(#{EAG0GfdSMAs.iIC4YhgrxQY}/#{EAG0GfdSMAs.zogrUrI7Crs}>24 && #{EAG0GfdSMAs.iIC4YhgrxQY}/#{EAG0GfdSMAs.zogrUrI7Crs}<=36,1,0)+
if(#{N2aXs7VlJdJ.iIC4YhgrxQY}/#{N2aXs7VlJdJ.zogrUrI7Crs}>24 && #{N2aXs7VlJdJ.iIC4YhgrxQY}/#{N2aXs7VlJdJ.zogrUrI7Crs}<=36,1,0)+
if(#{xrjnOtFFTRC.iIC4YhgrxQY}/#{xrjnOtFFTRC.zogrUrI7Crs}>24 && #{xrjnOtFFTRC.iIC4YhgrxQY}/#{xrjnOtFFTRC.zogrUrI7Crs}<=36,1,0)
>>
>>**Edit denominator**:  
>>>**Description**: "2-3 years - MSR - Denominator"  
>>>**Calculation**: "1"  
>
>**15 >3 years - MSR**  
>For each item the Indicator returns "1" if the stock coverage time is greater than 36 and otherwise returns 0 and then adds up these results for calculating the number of items with a stock coverage time of 36 months or greater. 
>>**Name \(*)**: ">=3 years - MSR"  
>>**Short Name \(*)**: ">=3 years - MSR"  
>>**Description**: "Number of items with a coverage time greater than 3 years"  
>>**Decimals in data output**: "0"  
>>**Indicator type \(*)**: "Number (Factor 1)"  
>>**Edit numerator**:  
>>>**Description**: ">03 years - MSR - Numerator"  
>>>**Calculation**:  if(#{LNAkkMTxqEW.iIC4YhgrxQY}/#{LNAkkMTxqEW.zogrUrI7Crs}>36,1,0)+
if(#{WyDZKSw82X6.iIC4YhgrxQY}/#{WyDZKSw82X6.zogrUrI7Crs}>36,1,0)+
if(#{JPccVwAGRq9.iIC4YhgrxQY}/#{JPccVwAGRq9.zogrUrI7Crs}>36,1,0)+
if(#{smxJz7Mt6ia.iIC4YhgrxQY}/#{smxJz7Mt6ia.zogrUrI7Crs}>36,1,0)+
if(#{AaIApgGQM6t.iIC4YhgrxQY}/#{AaIApgGQM6t.zogrUrI7Crs}>36,1,0)+
if(#{vCTrmv52APd.iIC4YhgrxQY}/#{vCTrmv52APd.zogrUrI7Crs}>36,1,0)+
if(#{SOw2TcuFFH2.iIC4YhgrxQY}/#{SOw2TcuFFH2.zogrUrI7Crs}>36,1,0)+
if(#{RSIOx2u07Ln.iIC4YhgrxQY}/#{RSIOx2u07Ln.zogrUrI7Crs}>36,1,0)+
if(#{JStiDyaPfqy.iIC4YhgrxQY}/#{JStiDyaPfqy.zogrUrI7Crs}>36,1,0)+
if(#{hZ1YvdcTDQM.iIC4YhgrxQY}/#{hZ1YvdcTDQM.zogrUrI7Crs}>36,1,0)+
if(#{tsi32D8HQd5.iIC4YhgrxQY}/#{tsi32D8HQd5.zogrUrI7Crs}>36,1,0)+
if(#{QWlPF8S0gCc.iIC4YhgrxQY}/#{QWlPF8S0gCc.zogrUrI7Crs}>36,1,0)+
if(#{a5uLTDt12eT.iIC4YhgrxQY}/#{a5uLTDt12eT.zogrUrI7Crs}>36,1,0)+
if(#{U0AfOOyJMy2.iIC4YhgrxQY}/#{U0AfOOyJMy2.zogrUrI7Crs}>36,1,0)+
if(#{cyf6UdScfFM.iIC4YhgrxQY}/#{cyf6UdScfFM.zogrUrI7Crs}>36,1,0)+
if(#{FeUTTNHpVzD.iIC4YhgrxQY}/#{FeUTTNHpVzD.zogrUrI7Crs}>36,1,0)+
if(#{mKSICD1rxG4.iIC4YhgrxQY}/#{mKSICD1rxG4.zogrUrI7Crs}>36,1,0)+
if(#{mVNe1aS1pGl.iIC4YhgrxQY}/#{mVNe1aS1pGl.zogrUrI7Crs}>36,1,0)+
if(#{oLAXTZY6ken.iIC4YhgrxQY}/#{oLAXTZY6ken.zogrUrI7Crs}>36,1,0)+
if(#{YYaRDUZyH9L.iIC4YhgrxQY}/#{YYaRDUZyH9L.zogrUrI7Crs}>36,1,0)+
if(#{HVteopBt0jr.iIC4YhgrxQY}/#{HVteopBt0jr.zogrUrI7Crs}>36,1,0)+
if(#{sWodd2tbjgZ.iIC4YhgrxQY}/#{sWodd2tbjgZ.zogrUrI7Crs}>36,1,0)+
if(#{yVYajDDYUfX.iIC4YhgrxQY}/#{yVYajDDYUfX.zogrUrI7Crs}>36,1,0)+
if(#{eTJAr4sc83v.iIC4YhgrxQY}/#{eTJAr4sc83v.zogrUrI7Crs}>36,1,0)+
if(#{U4KSmanl4JP.iIC4YhgrxQY}/#{U4KSmanl4JP.zogrUrI7Crs}>36,1,0)+
if(#{FXsa5uG3IGn.iIC4YhgrxQY}/#{FXsa5uG3IGn.zogrUrI7Crs}>36,1,0)+
if(#{L34T9YDtCor.iIC4YhgrxQY}/#{L34T9YDtCor.zogrUrI7Crs}>36,1,0)+
if(#{W5mHXhSYFfQ.iIC4YhgrxQY}/#{W5mHXhSYFfQ.zogrUrI7Crs}>36,1,0)+
if(#{cmSUyJOZwyl.iIC4YhgrxQY}/#{cmSUyJOZwyl.zogrUrI7Crs}>36,1,0)+
if(#{cT8sfosRXvU.iIC4YhgrxQY}/#{cT8sfosRXvU.zogrUrI7Crs}>36,1,0)+
if(#{OaWKnMS7say.iIC4YhgrxQY}/#{OaWKnMS7say.zogrUrI7Crs}>36,1,0)+
if(#{Z4bjHvGS6aH.iIC4YhgrxQY}/#{Z4bjHvGS6aH.zogrUrI7Crs}>36,1,0)+
if(#{Nn1L7CNEtC8.iIC4YhgrxQY}/#{Nn1L7CNEtC8.zogrUrI7Crs}>36,1,0)+
if(#{RNYKSc3nAUg.iIC4YhgrxQY}/#{RNYKSc3nAUg.zogrUrI7Crs}>36,1,0)+
if(#{PtmZ9XqpPKi.iIC4YhgrxQY}/#{PtmZ9XqpPKi.zogrUrI7Crs}>36,1,0)+
if(#{CohlLHi54B0.iIC4YhgrxQY}/#{CohlLHi54B0.zogrUrI7Crs}>36,1,0)+
if(#{Gu6u82RD9OW.iIC4YhgrxQY}/#{Gu6u82RD9OW.zogrUrI7Crs}>36,1,0)+
if(#{LiuYzxYr4Pt.iIC4YhgrxQY}/#{LiuYzxYr4Pt.zogrUrI7Crs}>36,1,0)+
if(#{Tje33nJAG55.iIC4YhgrxQY}/#{Tje33nJAG55.zogrUrI7Crs}>36,1,0)+
if(#{euM2dlqleYH.iIC4YhgrxQY}/#{euM2dlqleYH.zogrUrI7Crs}>36,1,0)+
if(#{dASLmBTEehF.iIC4YhgrxQY}/#{dASLmBTEehF.zogrUrI7Crs}>36,1,0)+
if(#{qU2LvzoPn1z.iIC4YhgrxQY}/#{qU2LvzoPn1z.zogrUrI7Crs}>36,1,0)+
if(#{OkWaFxdUQY2.iIC4YhgrxQY}/#{OkWaFxdUQY2.zogrUrI7Crs}>36,1,0)+
if(#{YHIv7KQc2e7.iIC4YhgrxQY}/#{YHIv7KQc2e7.zogrUrI7Crs}>36,1,0)+
if(#{rt9D47Inb49.iIC4YhgrxQY}/#{rt9D47Inb49.zogrUrI7Crs}>36,1,0)+
if(#{i1iXbquZ5iv.iIC4YhgrxQY}/#{i1iXbquZ5iv.zogrUrI7Crs}>36,1,0)+
if(#{RcE30WBKrXI.iIC4YhgrxQY}/#{RcE30WBKrXI.zogrUrI7Crs}>36,1,0)+
if(#{EAG0GfdSMAs.iIC4YhgrxQY}/#{EAG0GfdSMAs.zogrUrI7Crs}>36,1,0)+
if(#{N2aXs7VlJdJ.iIC4YhgrxQY}/#{N2aXs7VlJdJ.zogrUrI7Crs}>36,1,0)+
if(#{xrjnOtFFTRC.iIC4YhgrxQY}/#{xrjnOtFFTRC.zogrUrI7Crs}>36,1,0)
>>
>>**Edit denominator**:  
>>>**Description**: ">= 3 years - MSR - Denominator"  
>>>**Calculation**: "1"  
>
>**16 High variability**  
>For each item the Indicator returns "1" if the coefficient of variation is greater than 10 and otherwise returns 0 and then adds up these results for calculating the number of items with a coefficient of variation of more than 10 (high variability). Note that the actual coefficient of variation is multiplied by 10.
>>**Name \(*)**: "High variability"  
>>**Short Name \(*)**: "High variability - MSR"    
>>**Description**: "Number of items with a coefficient of variation between 0 and 5."  
>>**Decimals in data output**: "0"  
>>**Indicator type \(*)**: "Number (Factor 1)"  
>>**Edit numerator**:  
>>>**Description**: "HIgh variability - Numerator"  
>>>**Calculation**:  
>>>if(#{LNAkkMTxqEW.U2tBADVisKH}>10,1,0)+
if(#{WyDZKSw82X6.U2tBADVisKH}>10,1,0)+
if(#{JPccVwAGRq9.U2tBADVisKH}>10,1,0)+
if(#{smxJz7Mt6ia.U2tBADVisKH}>10,1,0)+
if(#{AaIApgGQM6t.U2tBADVisKH}>10,1,0)+
if(#{vCTrmv52APd.U2tBADVisKH}>10,1,0)+
if(#{SOw2TcuFFH2.U2tBADVisKH}>10,1,0)+
if(#{RSIOx2u07Ln.U2tBADVisKH}>10,1,0)+
if(#{JStiDyaPfqy.U2tBADVisKH}>10,1,0)+
if(#{hZ1YvdcTDQM.U2tBADVisKH}>10,1,0)+
if(#{tsi32D8HQd5.U2tBADVisKH}>10,1,0)+
if(#{QWlPF8S0gCc.U2tBADVisKH}>10,1,0)+
if(#{a5uLTDt12eT.U2tBADVisKH}>10,1,0)+
if(#{U0AfOOyJMy2.U2tBADVisKH}>10,1,0)+
if(#{cyf6UdScfFM.U2tBADVisKH}>10,1,0)+
if(#{FeUTTNHpVzD.U2tBADVisKH}>10,1,0)+
if(#{mKSICD1rxG4.U2tBADVisKH}>10,1,0)+
if(#{mVNe1aS1pGl.U2tBADVisKH}>10,1,0)+
if(#{oLAXTZY6ken.U2tBADVisKH}>10,1,0)+
if(#{YYaRDUZyH9L.U2tBADVisKH}>10,1,0)+
if(#{HVteopBt0jr.U2tBADVisKH}>10,1,0)+
if(#{sWodd2tbjgZ.U2tBADVisKH}>10,1,0)+
if(#{yVYajDDYUfX.U2tBADVisKH}>10,1,0)+
if(#{eTJAr4sc83v.U2tBADVisKH}>10,1,0)+
if(#{U4KSmanl4JP.U2tBADVisKH}>10,1,0)+
if(#{FXsa5uG3IGn.U2tBADVisKH}>10,1,0)+
if(#{L34T9YDtCor.U2tBADVisKH}>10,1,0)+
if(#{W5mHXhSYFfQ.U2tBADVisKH}>10,1,0)+
if(#{cmSUyJOZwyl.U2tBADVisKH}>10,1,0)+
if(#{cT8sfosRXvU.U2tBADVisKH}>10,1,0)+
if(#{OaWKnMS7say.U2tBADVisKH}>10,1,0)+
if(#{Z4bjHvGS6aH.U2tBADVisKH}>10,1,0)+
if(#{Nn1L7CNEtC8.U2tBADVisKH}>10,1,0)+
if(#{RNYKSc3nAUg.U2tBADVisKH}>10,1,0)+
if(#{PtmZ9XqpPKi.U2tBADVisKH}>10,1,0)+
if(#{CohlLHi54B0.U2tBADVisKH}>10,1,0)+
if(#{Gu6u82RD9OW.U2tBADVisKH}>10,1,0)+
if(#{LiuYzxYr4Pt.U2tBADVisKH}>10,1,0)+
if(#{Tje33nJAG55.U2tBADVisKH}>10,1,0)+
if(#{euM2dlqleYH.U2tBADVisKH}>10,1,0)+
if(#{dASLmBTEehF.U2tBADVisKH}>10,1,0)+
if(#{qU2LvzoPn1z.U2tBADVisKH}>10,1,0)+
if(#{OkWaFxdUQY2.U2tBADVisKH}>10,1,0)+
if(#{YHIv7KQc2e7.U2tBADVisKH}>10,1,0)+
if(#{rt9D47Inb49.U2tBADVisKH}>10,1,0)+
if(#{i1iXbquZ5iv.U2tBADVisKH}>10,1,0)+
if(#{RcE30WBKrXI.U2tBADVisKH}>10,1,0)+
if(#{EAG0GfdSMAs.U2tBADVisKH}>10,1,0)+
if(#{N2aXs7VlJdJ.U2tBADVisKH}>10,1,0)+
if(#{xrjnOtFFTRC.U2tBADVisKH}>10,1,0)
>
>**17 Low variability**  
>For each item the Indicator returns "1" if the coefficient of variation is less than 5 and otherwise returns 0 and then adds up these results for calculating the number of items with a coefficient of variation of less than 5 (low variability). Note that the actual coefficient of variation is multiplied by 10.
>>**Name \(*)**: "Low variability"  
>>**Short Name \(*)**: "Low variability - MSR"    
>>**Description**: "Number of items with a coefficient of variation between 0 and 5."  
>>**Decimals in data output**: "0"  
>>**Indicator type \(*)**: "Number (Factor 1)"  
>>**Edit numerator**:  
>>>**Description**: "High variability - Numerator"  
>>>**Calculation**:  
>>>if(#{LNAkkMTxqEW.U2tBADVisKH}<5,1,0)+
if(#{WyDZKSw82X6.U2tBADVisKH}<5,1,0)+
if(#{JPccVwAGRq9.U2tBADVisKH}<5,1,0)+
if(#{smxJz7Mt6ia.U2tBADVisKH}<5,1,0)+
if(#{AaIApgGQM6t.U2tBADVisKH}<5,1,0)+
if(#{vCTrmv52APd.U2tBADVisKH}<5,1,0)+
if(#{SOw2TcuFFH2.U2tBADVisKH}<5,1,0)+
if(#{RSIOx2u07Ln.U2tBADVisKH}<5,1,0)+
if(#{JStiDyaPfqy.U2tBADVisKH}<5,1,0)+
if(#{hZ1YvdcTDQM.U2tBADVisKH}<5,1,0)+
if(#{tsi32D8HQd5.U2tBADVisKH}<5,1,0)+
if(#{QWlPF8S0gCc.U2tBADVisKH}<5,1,0)+
if(#{a5uLTDt12eT.U2tBADVisKH}<5,1,0)+
if(#{U0AfOOyJMy2.U2tBADVisKH}<5,1,0)+
if(#{cyf6UdScfFM.U2tBADVisKH}<5,1,0)+
if(#{FeUTTNHpVzD.U2tBADVisKH}<5,1,0)+
if(#{mKSICD1rxG4.U2tBADVisKH}<5,1,0)+
if(#{mVNe1aS1pGl.U2tBADVisKH}<5,1,0)+
if(#{oLAXTZY6ken.U2tBADVisKH}<5,1,0)+
if(#{YYaRDUZyH9L.U2tBADVisKH}<5,1,0)+
if(#{HVteopBt0jr.U2tBADVisKH}<5,1,0)+
if(#{sWodd2tbjgZ.U2tBADVisKH}<5,1,0)+
if(#{yVYajDDYUfX.U2tBADVisKH}<5,1,0)+
if(#{eTJAr4sc83v.U2tBADVisKH}<5,1,0)+
if(#{U4KSmanl4JP.U2tBADVisKH}<5,1,0)+
if(#{FXsa5uG3IGn.U2tBADVisKH}<5,1,0)+
if(#{L34T9YDtCor.U2tBADVisKH}<5,1,0)+
if(#{W5mHXhSYFfQ.U2tBADVisKH}<5,1,0)+
if(#{cmSUyJOZwyl.U2tBADVisKH}<5,1,0)+
if(#{cT8sfosRXvU.U2tBADVisKH}<5,1,0)+
if(#{OaWKnMS7say.U2tBADVisKH}<5,1,0)+
if(#{Z4bjHvGS6aH.U2tBADVisKH}<5,1,0)+
if(#{Nn1L7CNEtC8.U2tBADVisKH}<5,1,0)+
if(#{RNYKSc3nAUg.U2tBADVisKH}<5,1,0)+
if(#{PtmZ9XqpPKi.U2tBADVisKH}<5,1,0)+
if(#{CohlLHi54B0.U2tBADVisKH}<5,1,0)+
if(#{Gu6u82RD9OW.U2tBADVisKH}<5,1,0)+
if(#{LiuYzxYr4Pt.U2tBADVisKH}<5,1,0)+
if(#{Tje33nJAG55.U2tBADVisKH}<5,1,0)+
if(#{euM2dlqleYH.U2tBADVisKH}<5,1,0)+
if(#{dASLmBTEehF.U2tBADVisKH}<5,1,0)+
if(#{qU2LvzoPn1z.U2tBADVisKH}<5,1,0)+
if(#{OkWaFxdUQY2.U2tBADVisKH}<5,1,0)+
if(#{YHIv7KQc2e7.U2tBADVisKH}<5,1,0)+
if(#{rt9D47Inb49.U2tBADVisKH}<5,1,0)+
if(#{i1iXbquZ5iv.U2tBADVisKH}<5,1,0)+
if(#{RcE30WBKrXI.U2tBADVisKH}<5,1,0)+
if(#{EAG0GfdSMAs.U2tBADVisKH}<5,1,0)+
if(#{N2aXs7VlJdJ.U2tBADVisKH}<5,1,0)+
if(#{xrjnOtFFTRC.U2tBADVisKH}<5,1,0)
>
>**18 Medium variability**  
>For each item the Indicator returns "1" if the coefficient of variation is greater than 5 but less or equal to 10 and otherwise returns 0 and then adds up these results for calculating the number of items with a coefficient of between 5 and 10 (medium variability). Note that the actual coefficient of variation is multiplied by 10.
>>**Name \(*)**: "Medium variability"  
>>**Short Name \(*)**: "Medium variability - MSR"    
>>**Description**: "Number of items with a coefficient of variation between 5 and 10."  
>>**Decimals in data output**: "0"  
>>**Indicator type \(*)**: "Number (Factor 1)"  
>>**Edit numerator**:  
>>>**Description**: "Medium variability - Numerator"  
>>>**Calculation**:  
>>>if(#{LNAkkMTxqEW.U2tBADVisKH}<5,1,0)+
if(#{WyDZKSw82X6.U2tBADVisKH}<5,1,0)+
if(#{JPccVwAGRq9.U2tBADVisKH}<5,1,0)+
if(#{smxJz7Mt6ia.U2tBADVisKH}<5,1,0)+
if(#{AaIApgGQM6t.U2tBADVisKH}<5,1,0)+
if(#{vCTrmv52APd.U2tBADVisKH}<5,1,0)+
if(#{SOw2TcuFFH2.U2tBADVisKH}<5,1,0)+
if(#{RSIOx2u07Ln.U2tBADVisKH}<5,1,0)+
if(#{JStiDyaPfqy.U2tBADVisKH}<5,1,0)+
if(#{hZ1YvdcTDQM.U2tBADVisKH}<5,1,0)+
if(#{tsi32D8HQd5.U2tBADVisKH}<5,1,0)+
if(#{QWlPF8S0gCc.U2tBADVisKH}<5,1,0)+
if(#{a5uLTDt12eT.U2tBADVisKH}<5,1,0)+
if(#{U0AfOOyJMy2.U2tBADVisKH}<5,1,0)+
if(#{cyf6UdScfFM.U2tBADVisKH}<5,1,0)+
if(#{FeUTTNHpVzD.U2tBADVisKH}<5,1,0)+
if(#{mKSICD1rxG4.U2tBADVisKH}<5,1,0)+
if(#{mVNe1aS1pGl.U2tBADVisKH}<5,1,0)+
if(#{oLAXTZY6ken.U2tBADVisKH}<5,1,0)+
if(#{YYaRDUZyH9L.U2tBADVisKH}<5,1,0)+
if(#{HVteopBt0jr.U2tBADVisKH}<5,1,0)+
if(#{sWodd2tbjgZ.U2tBADVisKH}<5,1,0)+
if(#{yVYajDDYUfX.U2tBADVisKH}<5,1,0)+
if(#{eTJAr4sc83v.U2tBADVisKH}<5,1,0)+
if(#{U4KSmanl4JP.U2tBADVisKH}<5,1,0)+
if(#{FXsa5uG3IGn.U2tBADVisKH}<5,1,0)+
if(#{L34T9YDtCor.U2tBADVisKH}<5,1,0)+
if(#{W5mHXhSYFfQ.U2tBADVisKH}<5,1,0)+
if(#{cmSUyJOZwyl.U2tBADVisKH}<5,1,0)+
if(#{cT8sfosRXvU.U2tBADVisKH}<5,1,0)+
if(#{OaWKnMS7say.U2tBADVisKH}<5,1,0)+
if(#{Z4bjHvGS6aH.U2tBADVisKH}<5,1,0)+
if(#{Nn1L7CNEtC8.U2tBADVisKH}<5,1,0)+
if(#{RNYKSc3nAUg.U2tBADVisKH}<5,1,0)+
if(#{PtmZ9XqpPKi.U2tBADVisKH}<5,1,0)+
if(#{CohlLHi54B0.U2tBADVisKH}<5,1,0)+
if(#{Gu6u82RD9OW.U2tBADVisKH}<5,1,0)+
if(#{LiuYzxYr4Pt.U2tBADVisKH}<5,1,0)+
if(#{Tje33nJAG55.U2tBADVisKH}<5,1,0)+
if(#{euM2dlqleYH.U2tBADVisKH}<5,1,0)+
if(#{dASLmBTEehF.U2tBADVisKH}<5,1,0)+
if(#{qU2LvzoPn1z.U2tBADVisKH}<5,1,0)+
if(#{OkWaFxdUQY2.U2tBADVisKH}<5,1,0)+
if(#{YHIv7KQc2e7.U2tBADVisKH}<5,1,0)+
if(#{rt9D47Inb49.U2tBADVisKH}<5,1,0)+
if(#{i1iXbquZ5iv.U2tBADVisKH}<5,1,0)+
if(#{RcE30WBKrXI.U2tBADVisKH}<5,1,0)+
if(#{EAG0GfdSMAs.U2tBADVisKH}<5,1,0)+
if(#{N2aXs7VlJdJ.U2tBADVisKH}<5,1,0)+
if(#{xrjnOtFFTRC.U2tBADVisKH}<5,1,0)
>
>**19 Stock availability / %**  
>This indicator counts the number of items with non-zero stock, divides them by the number of items and multiplies the result by 100 in order to present the result as percentage. Note that items have to be added and removed manually when the stock item list is changed and the denominator also has to be adjusted accordingly.
>>**Name \(*)**: "Stock availability / %"  
>>**Short Name \(*)**: "Stock availability / % - MSR"  
>>**Description**: "Percentage of items with non-zero stock"  
>>**Decimals in data output**: "0"  
>>**Indicator type \(*)**: "Number (Factor 1)"  
>>**Edit numerator**:  
>>>**Description**: "Stock availability - MSR - Numerator"  
>>>**Calculation**:  
>>>if(#{LNAkkMTxqEW.iIC4YhgrxQY}==0,0,1)+
if(#{WyDZKSw82X6.iIC4YhgrxQY}==0,0,1)+
if(#{JPccVwAGRq9.iIC4YhgrxQY}==0,0,1)+
if(#{smxJz7Mt6ia.iIC4YhgrxQY}==0,0,1)+
if(#{AaIApgGQM6t.iIC4YhgrxQY}==0,0,1)+
if(#{vCTrmv52APd.iIC4YhgrxQY}==0,0,1)+
if(#{SOw2TcuFFH2.iIC4YhgrxQY}==0,0,1)+
if(#{RSIOx2u07Ln.iIC4YhgrxQY}==0,0,1)+
if(#{JStiDyaPfqy.iIC4YhgrxQY}==0,0,1)+
if(#{hZ1YvdcTDQM.iIC4YhgrxQY}==0,0,1)+
if(#{tsi32D8HQd5.iIC4YhgrxQY}==0,0,1)+
if(#{QWlPF8S0gCc.iIC4YhgrxQY}==0,0,1)+
if(#{a5uLTDt12eT.iIC4YhgrxQY}==0,0,1)+
if(#{U0AfOOyJMy2.iIC4YhgrxQY}==0,0,1)+
if(#{cyf6UdScfFM.iIC4YhgrxQY}==0,0,1)+
if(#{FeUTTNHpVzD.iIC4YhgrxQY}==0,0,1)+
if(#{mKSICD1rxG4.iIC4YhgrxQY}==0,0,1)+
if(#{mVNe1aS1pGl.iIC4YhgrxQY}==0,0,1)+
if(#{oLAXTZY6ken.iIC4YhgrxQY}==0,0,1)+
if(#{YYaRDUZyH9L.iIC4YhgrxQY}==0,0,1)+
if(#{HVteopBt0jr.iIC4YhgrxQY}==0,0,1)+
if(#{sWodd2tbjgZ.iIC4YhgrxQY}==0,0,1)+
if(#{yVYajDDYUfX.iIC4YhgrxQY}==0,0,1)+
if(#{eTJAr4sc83v.iIC4YhgrxQY}==0,0,1)+
if(#{U4KSmanl4JP.iIC4YhgrxQY}==0,0,1)+
if(#{FXsa5uG3IGn.iIC4YhgrxQY}==0,0,1)+
if(#{L34T9YDtCor.iIC4YhgrxQY}==0,0,1)+
if(#{W5mHXhSYFfQ.iIC4YhgrxQY}==0,0,1)+
if(#{cmSUyJOZwyl.iIC4YhgrxQY}==0,0,1)+
if(#{cT8sfosRXvU.iIC4YhgrxQY}==0,0,1)+
if(#{OaWKnMS7say.iIC4YhgrxQY}==0,0,1)+
if(#{Z4bjHvGS6aH.iIC4YhgrxQY}==0,0,1)+
if(#{Nn1L7CNEtC8.iIC4YhgrxQY}==0,0,1)+
if(#{RNYKSc3nAUg.iIC4YhgrxQY}==0,0,1)+
if(#{PtmZ9XqpPKi.iIC4YhgrxQY}==0,0,1)+
if(#{CohlLHi54B0.iIC4YhgrxQY}==0,0,1)+
if(#{Gu6u82RD9OW.iIC4YhgrxQY}==0,0,1)+
if(#{LiuYzxYr4Pt.iIC4YhgrxQY}==0,0,1)+
if(#{Tje33nJAG55.iIC4YhgrxQY}==0,0,1)+
if(#{euM2dlqleYH.iIC4YhgrxQY}==0,0,1)+
if(#{dASLmBTEehF.iIC4YhgrxQY}==0,0,1)+
if(#{qU2LvzoPn1z.iIC4YhgrxQY}==0,0,1)+
if(#{OkWaFxdUQY2.iIC4YhgrxQY}==0,0,1)+
if(#{YHIv7KQc2e7.iIC4YhgrxQY}==0,0,1)+
if(#{rt9D47Inb49.iIC4YhgrxQY}==0,0,1)+
if(#{i1iXbquZ5iv.iIC4YhgrxQY}==0,0,1)+
if(#{RcE30WBKrXI.iIC4YhgrxQY}==0,0,1)+
if(#{EAG0GfdSMAs.iIC4YhgrxQY}==0,0,1)+
if(#{N2aXs7VlJdJ.iIC4YhgrxQY}==0,0,1)+
if(#{xrjnOtFFTRC.iIC4YhgrxQY}==0,0,1)
>>
>>**Edit denominator**:  
>>>**Description**: "Stock availability - MSR - Denominator"  
>>>**Calculation**: "0.06"  
>
>**20 Stockout count**  
>This indicator counts the number of items with a stockout.
>>**Name \(*)**: "Stockout count"  
>>**Short Name \(*)**: "Stockout count - MSR"  
>>**Description**: "Number of items with a stock discrepancy"  
>>**Decimals in data output**: "0"  
>>**Indicator type \(*)**: "Number (Factor 1)"  
>>**Edit numerator**:  
>>>**Description**: "Stock discrepancy count - Numerator"  
>>>**Calculation**:  
>>>if(#{LNAkkMTxqEW.iIC4YhgrxQY}==0,1,0)+
if(#{WyDZKSw82X6.iIC4YhgrxQY}==0,1,0)+
if(#{JPccVwAGRq9.iIC4YhgrxQY}==0,1,0)+
if(#{smxJz7Mt6ia.iIC4YhgrxQY}==0,1,0)+
if(#{AaIApgGQM6t.iIC4YhgrxQY}==0,1,0)+
if(#{vCTrmv52APd.iIC4YhgrxQY}==0,1,0)+
if(#{SOw2TcuFFH2.iIC4YhgrxQY}==0,1,0)+
if(#{RSIOx2u07Ln.iIC4YhgrxQY}==0,1,0)+
if(#{JStiDyaPfqy.iIC4YhgrxQY}==0,1,0)+
if(#{hZ1YvdcTDQM.iIC4YhgrxQY}==0,1,0)+
if(#{tsi32D8HQd5.iIC4YhgrxQY}==0,1,0)+
if(#{QWlPF8S0gCc.iIC4YhgrxQY}==0,1,0)+
if(#{a5uLTDt12eT.iIC4YhgrxQY}==0,1,0)+
if(#{U0AfOOyJMy2.iIC4YhgrxQY}==0,1,0)+
if(#{cyf6UdScfFM.iIC4YhgrxQY}==0,1,0)+
if(#{FeUTTNHpVzD.iIC4YhgrxQY}==0,1,0)+
if(#{mKSICD1rxG4.iIC4YhgrxQY}==0,1,0)+
if(#{mVNe1aS1pGl.iIC4YhgrxQY}==0,1,0)+
if(#{oLAXTZY6ken.iIC4YhgrxQY}==0,1,0)+
if(#{YYaRDUZyH9L.iIC4YhgrxQY}==0,1,0)+
if(#{HVteopBt0jr.iIC4YhgrxQY}==0,1,0)+
if(#{sWodd2tbjgZ.iIC4YhgrxQY}==0,1,0)+
if(#{yVYajDDYUfX.iIC4YhgrxQY}==0,1,0)+
if(#{eTJAr4sc83v.iIC4YhgrxQY}==0,1,0)+
if(#{U4KSmanl4JP.iIC4YhgrxQY}==0,1,0)+
if(#{FXsa5uG3IGn.iIC4YhgrxQY}==0,1,0)+
if(#{L34T9YDtCor.iIC4YhgrxQY}==0,1,0)+
if(#{W5mHXhSYFfQ.iIC4YhgrxQY}==0,1,0)+
if(#{cmSUyJOZwyl.iIC4YhgrxQY}==0,1,0)+
if(#{cT8sfosRXvU.iIC4YhgrxQY}==0,1,0)+
if(#{OaWKnMS7say.iIC4YhgrxQY}==0,1,0)+
if(#{Z4bjHvGS6aH.iIC4YhgrxQY}==0,1,0)+
if(#{Nn1L7CNEtC8.iIC4YhgrxQY}==0,1,0)+
if(#{RNYKSc3nAUg.iIC4YhgrxQY}==0,1,0)+
if(#{PtmZ9XqpPKi.iIC4YhgrxQY}==0,1,0)+
if(#{CohlLHi54B0.iIC4YhgrxQY}==0,1,0)+
if(#{Gu6u82RD9OW.iIC4YhgrxQY}==0,1,0)+
if(#{LiuYzxYr4Pt.iIC4YhgrxQY}==0,1,0)+
if(#{Tje33nJAG55.iIC4YhgrxQY}==0,1,0)+
if(#{euM2dlqleYH.iIC4YhgrxQY}==0,1,0)+
if(#{dASLmBTEehF.iIC4YhgrxQY}==0,1,0)+
if(#{qU2LvzoPn1z.iIC4YhgrxQY}==0,1,0)+
if(#{OkWaFxdUQY2.iIC4YhgrxQY}==0,1,0)+
if(#{YHIv7KQc2e7.iIC4YhgrxQY}==0,1,0)+
if(#{rt9D47Inb49.iIC4YhgrxQY}==0,1,0)+
if(#{i1iXbquZ5iv.iIC4YhgrxQY}==0,1,0)+
if(#{RcE30WBKrXI.iIC4YhgrxQY}==0,1,0)+
if(#{EAG0GfdSMAs.iIC4YhgrxQY}==0,1,0)+
if(#{N2aXs7VlJdJ.iIC4YhgrxQY}==0,1,0)+
if(#{xrjnOtFFTRC.iIC4YhgrxQY}==0,1,0)
>>
>>**Edit denominator**:  
>>>**Description**: "Stockouts - MSR - Denominator"  
>>>**Calculation**: "1"  
>
>**21 Stock discrepancy count**  
>>**Name \(*)**: "Stock discrepancy count"  
>>**Short Name \(*)**: "Stock discrepancy count - MSR"  
>>**Description**: "Number of items with a stock discrepancy"  
>>**Decimals in data output**: "0"  
>>**Indicator type \(*)**: "Number (Factor 1)"  
>>**Edit numerator**:  
>>>**Description**: "Stock discrepancy count - Numerator"  
>>>**Calculation**:  
>>>#{LNAkkMTxqEW.cD8WZyjlq9C}+
#{WyDZKSw82X6.cD8WZyjlq9C}+
#{JPccVwAGRq9.cD8WZyjlq9C}+
#{smxJz7Mt6ia.cD8WZyjlq9C}+
#{AaIApgGQM6t.cD8WZyjlq9C}+
#{vCTrmv52APd.cD8WZyjlq9C}+
#{SOw2TcuFFH2.cD8WZyjlq9C}+
#{RSIOx2u07Ln.cD8WZyjlq9C}+
#{JStiDyaPfqy.cD8WZyjlq9C}+
#{hZ1YvdcTDQM.cD8WZyjlq9C}+
#{tsi32D8HQd5.cD8WZyjlq9C}+
#{QWlPF8S0gCc.cD8WZyjlq9C}+
#{a5uLTDt12eT.cD8WZyjlq9C}+
#{U0AfOOyJMy2.cD8WZyjlq9C}+
#{cyf6UdScfFM.cD8WZyjlq9C}+
#{FeUTTNHpVzD.cD8WZyjlq9C}+
#{mKSICD1rxG4.cD8WZyjlq9C}+
#{mVNe1aS1pGl.cD8WZyjlq9C}+
#{oLAXTZY6ken.cD8WZyjlq9C}+
#{YYaRDUZyH9L.cD8WZyjlq9C}+
#{HVteopBt0jr.cD8WZyjlq9C}+
#{sWodd2tbjgZ.cD8WZyjlq9C}+
#{yVYajDDYUfX.cD8WZyjlq9C}+
#{eTJAr4sc83v.cD8WZyjlq9C}+
#{U4KSmanl4JP.cD8WZyjlq9C}+
#{FXsa5uG3IGn.cD8WZyjlq9C}+
#{L34T9YDtCor.cD8WZyjlq9C}+
#{W5mHXhSYFfQ.cD8WZyjlq9C}+
#{cmSUyJOZwyl.cD8WZyjlq9C}+
#{cT8sfosRXvU.cD8WZyjlq9C}+
#{OaWKnMS7say.cD8WZyjlq9C}+
#{Z4bjHvGS6aH.cD8WZyjlq9C}+
#{Nn1L7CNEtC8.cD8WZyjlq9C}+
#{RNYKSc3nAUg.cD8WZyjlq9C}+
#{PtmZ9XqpPKi.cD8WZyjlq9C}+
#{CohlLHi54B0.cD8WZyjlq9C}+
#{Gu6u82RD9OW.cD8WZyjlq9C}+
#{LiuYzxYr4Pt.cD8WZyjlq9C}+
#{Tje33nJAG55.cD8WZyjlq9C}+
#{euM2dlqleYH.cD8WZyjlq9C}+
#{dASLmBTEehF.cD8WZyjlq9C}+
#{qU2LvzoPn1z.cD8WZyjlq9C}+
#{OkWaFxdUQY2.cD8WZyjlq9C}+
#{YHIv7KQc2e7.cD8WZyjlq9C}+
#{rt9D47Inb49.cD8WZyjlq9C}+
#{i1iXbquZ5iv.cD8WZyjlq9C}+
#{RcE30WBKrXI.cD8WZyjlq9C}+
#{EAG0GfdSMAs.cD8WZyjlq9C}+
#{N2aXs7VlJdJ.cD8WZyjlq9C}+
#{xrjnOtFFTRC.cD8WZyjlq9C}
>>
>>**Edit denominator**:  
>>>**Description**: "Stock discrepancy count - Denominator"  
>>>**Calculation**: "1"  

#### 4.2 Indicator type
The "Indicator type" is a precondition for configuring any "Indicator".
>**1 Number (Factor 1)**  
>>**Name \(*)**: "Number (Factor 1)"  
>>**Factor \(*)**: "1"  

### 5 Other

#### 5.1 Legend

The following legends are applied to some visualizations:

- Stock coverage time: indicates stockouts, shortages, appropriate and overstocks

- Stock discrepancy: indicates correct stocks, positive or negative discrepancies

>**1 Coefficient of variation**  
>>**Name \(*)**: "Coefficient of variation**  
>>**Code**: "COEFFICIENT_OF_VARIATIONS"  
>>**Name**  
>>>**Name**: "Low variability"  
>>>**Start value**: "0  
>>>**End value**: "5"  
>>>**Color code**: "#41F80E" (Green)  
>>
>>>**Name**: "Medium variability"  
>>>**Start value**: "5"  
>>>**End value**: "10"  
>>>**Color code**: "#FEB24C" (yellow)  
>>
>>>**Name**: "Erratic variability"  
>>>**Start value**: "10"  
>>>**End value**: "25"  
>>>**Color code**: "#F03B20" (red)  
>
>**2 Stock coverage time**  
>>**Name \(*)**: "Stock coverage time**  
>>**Code**: "STOCK_COVERAGE_TIME"  
>>**Name**  
>>>**Name**: "Stockout"  
>>>**Start value**: "0  
>>>**End value**: "0.0001"  
>>>**Color code**: "#EE391E" (red)  
>>
>>>**Name**: "Understock"  
>>>**Start value**: "0.0001"  
>>>**End value**: "3"  
>>>**Color code**: "#FEFB08" (yellow)  
>>
>>>**Name**: "Adequate stock"  
>>>**Start value**: "3"  
>>>**End value**: "4" 
>>>**Color code**: "#0BFF00" (green)  
>>
>>>**Name**: "Overstock"  
>>>**Start value**: "4"  
>>>**End value**: "12"  
>>>**Color code**: "#0011FF" (blue)  
>>
>>>**Name**: "Excessive stock"  
>>>**Start value**: "12"  
>>>**End value**: "1000" 
>>>**Color code**: "#DC00FF" (purple)  
>
>**3 Stock discrepancy**  
>>**Name \(*)**:"Stock discrepancy"  
>>**Code**: "STOCK_DISCREPANCY"  
>>**Name**  
>>>**Name**: "Negative"  
>>>**Start value**: "-1000000"  
>>>**End value**: "0"  
>>>**Color code**: "#8411D7" (purple)  
>>>
>>>**Name**: "Correct stock"  
>>>**Start value**: "0"  
>>>**End value**: "1"  
>>>**Color code**: "#68FE4C" (green)  
>>>
>>>**Name**: "Positive"  
>>>**Start value**: "1"  
>>>**End value**: "1000000"  
>>>**Color code**: "#FF2000" (red)  
>
>**4 Stockout count**
This "Legend" is created for selecting a specific colour for column charts instead of a colour scheme being automatically assigned by the system.
>>**Name \(*)**: "Stockout count"  
>>**Code**: "STOCKOUT_COUNT"  
>>**Name**  
>>>**Name**: "No stockouts"  
>>>**Start value**: "0"  
>>>**End value**: "0.5"  
>>>**Color code**: "#2CFF00" (green)  
>>>**Name**: "Stockouts"  
>>>**Start value**: "0.5"  
>>>**End value**: "1000000"  
>>>**Color code**: "#F31812" (red)  

#### 5.2 Predictor

The following 3 Predictors need to be created for each item (Data element) separately:

- Opening balance: identical with the "Stock on hand" from the end of the previous month

- Closing balance: Opening balance + Stock received - Stock distributed 
- Stock redistributed - Stock discarded   

- Stock discrepancy: Stock on hand (as counted) - Closing balance

>**1 [Stock list] - Coefficient of variation - MSR**  
>>**Name \(*)**: "[Item] - Stock discrepancy - MSR"  
>>**Short name \(*)**: "[Item] - Stock discrepancy"
>>**Output data element \(*)**: "[Item]" (select any item from the Data set)  
>>**Output category option combo** "Coefficient of variation"  
>>**Period type \(*)**: "Monthly"  
>>**Organisation unit levels** "Facility"  
>>**Organisation units providing data \(*)** "At selected level(s) only"  
*THIS IS ABSOLUTELY CRITICAL and the lowest level in the hierarchy must be selected (and not "Country") otherwise Predictors are generated but the values are blank*  
>>**Generator \(*)**  
>>>**Description**: "[Stock list] - Coefficient of variation"  
>>>**Expression**: "forEach ?de in :DEG:nYcQWVqVsjx -->
stddevSamp(#{?de.zogrUrI7Crs})/avg(#{?de.zogrUrI7Crs})*10"
>>
>>**Sequential sample count \(*)**: "6"  
>>**Annual sample count \(*)**: "0"  
>
>**2 [Stock list] - Stock coverage time - MSR**  
>>**Name \(*)**: "[Stock list] - Stock coverage - MSR"  
>>**Short name \(*)**: "[Stock list] - Stock coverage - MSR"  
>>**Output data element \(*)**: "[Item]" (select any item from the Data set)  
>>**Output category option combo** "Stock coverage"  
>>**Period type \(*)**: "Monthly"  
>>**Organisation unit levels** "Facility"  
>>**Organisation units providing data \(*)** "At selected level(s) only"  
*THIS IS ABSOLUTELY CRITICAL and the lowest level in the hierarchy must be selected (and not "Country") otherwise Predictors are generated but the values are blank*  
>>**Generator \(*)**  
>>>**Description**: "[Stock list] - Stock coverage time"  
>>>**Expression**: "forEach ?de in :DEG:nYcQWVqVsjx -->
\#{?de.iIC4YhgrxQY}/#{?de.zogrUrI7Crs}"  
>>
>>**Sequential sample count \(*)**: "0"  
>>**Annual sample count \(*)**: "0"  
>
>**3 [Stock list] - Stock discrepancy - MSR**  
>>**Name \(*)**: "[Stock list] - Stock discrepancy - MSR"  
>>**Short name \(*)**: "[Stock list] - Stock discrepancy - MSR"  
>>**Output data element \(*)**: "[Item]" (select any item from the Data set)  
>>**Output category option combo** "Stock discrepancy"  
>>**Period type \(*)**: "Monthly"  
>>**Organisation unit levels** "Facility"  
>>**Organisation units providing data \(*)** "At selected level(s) only"  
*THIS IS ABSOLUTELY CRITICAL and the lowest level in the hierarchy must be selected (and not "Country") otherwise Predictors are generated but the values are blank*  
>>**Generator \(*)**  
>>>**Description**: "[Stock list] - Stock discrepancy"  
>>>**Expression**: "forEach ?de in :DEG:nYcQWVqVsjx -->
>>>avg(#{?de.iIC4YhgrxQY})
>>>+#{?de.PnxWz4HI5V0}
>>>-#{?de.zogrUrI7Crs}
>>>-#{?de.Q1Wh1szjrkC}
>>>-#{?de.CE1WL7cxNry}
>>>-#{?de.ERgIsOh37NR}
>>>-#{?de.iIC4YhgrxQY}"
>>
>>**Sequential sample count \(*)**: "1"  
>>**Annual sample count \(*)**: "0"  
>
>**4 [Stock list] - Stockout Yes/No - MSR**  
>>**Name \(*)**: "[Stock list] - Stockout Yes/No - MSR"  
>>**Short name \(*)**: "[Stock list] - Stockout Yes/No - MSR"  
>>**Output data element \(*)**: "[Item]" (select any item from the Data set)  
>>**Output category option combo** "Stockout Yes/No"  
>>**Period type \(*)**: "Monthly"  
>>**Organisation unit levels** "Facility"  
>>**Organisation units providing data \(*)** "At selected level(s) only"  
*THIS IS ABSOLUTELY CRITICAL and the lowest level in the hierarchy must be selected (and not "Country") otherwise Predictors are generated but the values are blank*  
>>**Generator \(*)**  
>>>**Description**: "[Stock list] - Stockout Yes/No"  
>>>**Expression**: "forEach ?de in :DEG:nYcQWVqVsjx -->
if(#{?de.iIC4YhgrxQY}==0,1,0)"
>>
>>**Sequential sample count \(*)**: "0"  
>>**Annual sample count \(*)**: "0"  

#### 5.3 Predictor group

The "Predictor group" is required in order to allow running all Predictors periodically and together by the "Scheduler" rather than having to prompt them one by one. All Predictors required for the DHIS2-RTS can be grouped together and be run together in the Scheduler App.

>**1 Monthly stock report - Stock calculations**  
>**Name \(*)**: "Monthly stock report - Stock calculations - MSR"  
>**Predictors**
>>"[Item - MSR] - Closing balance"  
>>"[Item - MSR] - Opening balance"  
>>"[Item - MSR] - Stock discrepancy"  

## Android Settings Web App - Offline Analytics

[To be completed]

## Data Entry (Beta) App - Data entry

[Explanation]

![](image-3.png)

## Capture Android App - Data entry

Xx
[Screenshot]

## Data Visualizer App - Analytics

>**1 Health facility level**  
>>**1.1 Statistics**  
>>>- 1 MSR - Stock receipt - Pivot table
>>>- 2 MSR - Stock distribution - Pivot table  
>>>- 3 MSR - Stock redistribution - Pivot table  
>>>- 4 MSR - Stock discard - Pivot table  
>>>- 5 MSR - Stock on hand - Pivot table  
>>>- 6 MSR - Stock correction - Pivot table  
>>>- 7 MSR - Stock report complete - Last 3 months - Pivot table  
>>>- 8 MSR - Stock report complete - Last 12 months - Pivot table  
>>>- 9 MSR - Stock report complete - Column chart
>>
>>**1.2 Indicators**  
>>>- 10 MSR - Coefficient of Variation x 10 - Pivot table  
>>>- 11 MSR - Coefficient of Variation x 10 - Stacked bar chart  
>>>- 12 MSR - Coefficient of Variation x 10 - Bar chart  
>>>- 13 MSR - Coefficient of Variation x 10 distribution - Pivot table  
>>>- 14 MSR - Coefficient of Variation x 10 distribution - Stacked Column chart  
>>>- 15 MSR - Coefficient of Variation x 10 distribution - Column chart  
>>>- 16 MSR - Stock availability - Pivot table  
>>>- 17 MSR - Stock availability - Column chart  
>>>- 18 MSR - Stock availability - Single value chart  
>>>- 19 MSR - Stock availability - Gauge chart  
>>>- **xx** MSR - Stockout percentage - Bar chart
>>>- **xx** MSR - Stock availability and stockout percentage - Bar chart
>>>- 20 MSR - Stockouts - Stacked column chart  
>>>- 21 MSR - Stockout count - Pivot table  
>>>- 22 MSR - Stockout count - Column chart  
>>>- 23 MSR - Stockout count - Single value chart  
>>>- 24 MSR - Stockout length - Pivot table  
>>>- 25 MSR - Stockout length - Bar chart  
>>>- 26 MSR - Stock coverage time - Pivot table  
>>>- 27 MSR - Stock coverage time distribution - Pivot table  
>>>- 28 MSR - Stock coverage time distribution - Stacked Column chart  
>>>- 29 MSR - Stock coverage time distribution - Column chart  
>>>- **xx** MSR - Stock coverage time ranges - Column chart
>>>- **xx** MSR - Stock coverage time ranges - Stacked column chart
>>>- 30 MSR - Stock discrepancy - Pivot table  
>>>- 31 MSR - Stock discrepancy count - Column chart  
>>>- **xx** MSR - Stock discrepancy count - Percentage - Column chart  
>
>**2 District level**  
>>**2.1 Statistics**  
>>>- 32 MSR - Stock receipt - District - Pivot table  
>>>- 33 MSR - Stock distribution - District - Pivot table  
>>>- 34 MSR - Stock redistribution - District - Pivot table  
>>>- 35 MSR - Stock discard - District - Pivot table  
>>>- 36 MSR - Stock on hand - District - Pivot table  
>>>- 37 MSR - Stock correction - District - Pivot table  
>>>- 38 MSR - Stock report complete - District - Pivot table  
>>
>>**2.2 Indicators**  
>>>- 39 MSR - Coefficient of Variation x 10 - District - Pivot table  
>>>- 40 MSR - Coefficient of Variation x 10 - District - Stacked bar chart  
>>>- 41 MSR - Coefficient of Variation x 10 - District - Bar chart  
>>>- 42 MSR - Coefficient of Variation x 10 distribution - District - Pivot table  
>>>- 43 MSR - Coefficient of Variation x 10 distribution - District - Stacked Column chart  
>>>- 44 MSR - Coefficient of Variation x 10 distribution - District - Column chart  
>>>- 45 MSR - Stock availability - District - Pivot table  
>>>- 46 MSR - Stock availability - District - Column chart - Last month  
>>>- 47 MSR - Stock availability - District - Column chart - Last 12  
>>>- **xx** MSR - Stockout percentage - District - Column chart
>>>- **xx** MSR - Stock availability and stockout percentage - District - Stacked column chart
>>>- 48 MSR - Stockouts - District - Pivot table  
>>>- 49 MSR - Stockout count - District - Pivot table  
>>>- 50 MSR - Stockout count - District - Column chart  
>>>- 51 MSR - Stockout count - District - Single value chart  
>>>- 52 MSR - Stockout length - District - Pivot table  
>>>- 53 MSR - Stockout length - District - Stacked bar chart  
>>>- 54 MSR - Stock coverage time - District - Pivot table  
>>>- 55 MSR - Stock coverage time distribution - District - Pivot table  
>>>- 56 MSR - Stock coverage time distribution - District - Stacked column chart  
>>>- 57 MSR - Stock coverage time distribution - District - Stacked column chart  
>>>- **xx** MSR - Stock coverage time ranges - District - Stacked column chart - Last month
>>>- **xx** MSR - Stock coverage time ranges - District - Stacked column chart - Last 12 months  
>>>- 58 MSR - Stock discrepancy - District - Pivot table  
>>>- 59 MSR - Stock discrepancy count - District - Stacked column chart  
>>>- **xx** MSR - Stock discrepancy count - Percentage - District - Column chart  
>
>**3 Province level**  
>>**3.1 Statistics**  
>>>- 60 MSR - Stock receipt - Province - Pivot table  
>>>- 61 MSR - Stock distribution - Province - Pivot table  
>>>- 62 MSR - Stock redistribution - Province - Pivot table  
>>>- 63 MSR - Stock discard - Province - Pivot table  
>>>- 64 MSR - Stock on hand - Province - Pivot table  
>>>- 65 MSR - Stock correction - Province - Pivot table  
>>>- 66 MSR - Stock report complete - Province - Pivot table  
>>
>>**3.2 Indicators**  
>>>- 7x MSR - Coefficient of Variation x 10 - Province - Stacked bar chart
>>>- 7x MSR - Coefficient of Variation x 10 distribution - Province - Pivot table: requires additional Predictor  
>>>- 7x MSR - Coefficient of Variation x 10 distribution - Province - Stacked Column chart: requires additional Predictor  
>>>- 7x MSR - Coefficient of Variation x 10 distribution - Province - Column chart: requires additional Predictor  
>>>- 7x MSR - Stock availability - Province - Pivot table  
>>>- 7x MSR - Stock availability - Province - Column chart  
>>>- 7x MSR - Stockout percentage - Province - Column chart
>>>- 7x MSR - Stock availability and stockout percentage - Province - Stacked column chart
>>>- 7x MSR - Stockouts - Province - Pivot table - Item - Last month  
>>>- 7x MSR - Stockout count - Province - Pivot table  
>>>- 7x MSR - Stockout count - Province - Stacked column chart  
>>>- 7x MSR - Stockout count - Province - Column chart  
>>>- 7x MSR - Stockout length - Province - Pivot table  
>>>- 7x MSR - Stockout length - Province - Stacked bar chart  


xxxxxxxxxxxxxxxxxxxxxxxxx

>>>- 7x MSR - Stock coverage time distribution - Province - Pivot table
>>>- 7x MSR - Stock coverage time distribution- Province - Stacked column chart - Last month:  
>>>- **xx** MSR - Stock coverage time ranges - Province - Last month:  
>>>- **xx** MSR - Stock coverage time ranges - Province - Last 12 months: 
>>>- 7x MSR - Stock discrepancy count - Province - Stacked column chart:  

XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
>
>**4 Country level**  
>>**4.1 Statistics**  
>>**4.2 Indicators**  
>
>**5 Visualization overview**  
>
<br>  

| Visualization  |  Facility | District | Region | Country | Visualiations | Offline |
| :-------- | :---: | :---: | :---:| :---: |:---: | :---:|
| **STATISTICS / MONTHLY** |
| Stock receipt| Sum | Sum | Sum | Sum | Pivot table, Column |
| Stock distribution| Sum | Sum | Sum | Sum | Pivot table, Column |
| Stock redistribution| Sum | Sum | Sum | Sum | Pivot table, Column |
| Stock discard| Sum | Sum | Sum | Sum | Pivot table, Column |
| Stock on hand | Sum | Sum | Sum | Sum | Pivot table, Column |
| Stock correction | Sum | Sum | Sum | Sum | Pivot table, Column |
| Stock report complete | Sum | Sum | Sum | Sum | Pivot table, Column |
| Monthly report| Count | Count | Count | Count | Pivot |
| Health facility| 1 | Count | Count | Count | Pivot |  

<br>  

| Visualization  | Facility | District | Region | Country | Visualiations | Offline |
| :-------- |  :---: | :---: | :---:| :---: |:---: | :---:|
| **INDICATORS** |
| Stock distribution / Coefficient of Variation | Calculation | -  | - | - | Pivot, Bar, Stacked bar |
| Stock distribution / Coefficient of Variation / distribution | Count | Count | Count | Count | Pivot Column |
| Stockout count | Count |  Count |Count | Count | Pivot, Column, Single value |
| Stockout length | Count |  Count |Count | Count | Pivot, Bar |
| Stock coverage time | Calculation |  |  |  |  |  |  |  | Pivot |
| Stock coverage time / Range | Calculation, Count | Count | Count | Count | Pivot |  |
| Stock coverage time / distribution | Count | Count | Count | Count | Pivot, Column |  |
| Stock discrepancy | Count |  Count |Count | Count | Pivot, Column |

By default, all the visualizations above are shown as time series (by month/by day)
<br>  

### Health facility level

#### Statistics

>**1 MSR - Stock receipt - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock receipt - Pivot table"  
>**Description**: "MSR DV 1 - Monthly Stock Reporting / Stock receipt / Last 12 months / Health facility / By item / Pivot table  
This report provides the monthly stock receipts as reported at the end of every month."  
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
>>**Filter**:  
>>>**Organisation unit**: "User organisation unit"  
>>>**YOUR DIMENIONS**
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stock receipt"  
>>
>>**Options**    
>>>**Data**  
>>>>**Totals**  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  

![](image-5.png)

>**2 MSR - Stock distribution - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock distribution - Pivot table"  
>**Description**: "MSR DV 2 - Monthly Stock Reporting / Stock distribution / Last 12 months / Health facility / By item / Pivot table  
This report provides the monthly stock distributions as reported at the end of every month."
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
>>
>>**Options**    
>>>**Data**  
>>>>**Totals**  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  

![](image-6.png)

>**3 MSR - Stock redistribution - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock redistribution - Pivot table"  
>**Description**: "MSR DV 3 - Monthly Stock Reporting / Stock redistribution / Last 12 months / Health facility / By item / Pivot table.    
This report provides the monthly stock redistributions as reported at the end of every month."
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
>>>>**Selected Items**: "Stock redistribution"  
>>
>>**Options**    
>>>**Data**  
>>>>**Totals**  
>>>>>**Column sub-totals**: tag (appears as a white tick in a green field)  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  

![](image-7.png)

>**4 MSR - Stock discard - Pivot table**  
>
>**Visualization type**: select "Pivot table"
>**Name \(*)**: "MSR - Stock discard - Pivot table"  
>**Description**: "MSR DV 4 - Monthly Stock Reporting / Stock discard / Last 12 months / Health facility / By item / Pivot table  
This report provides the monthly stock discards as reported at the end of every month."
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
>>>>**Selected Items**: "Stock discard"  
>>  
>>**Options**    
>>>**Data**  
>>>>**Totals**  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  

![](image-8.png)

>**5 MSR - Stock on hand - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock on hand - Pivot table"  
>**Description**: "MSR DV 5 - Monthly Stock Reporting / Stock on hand / Last 12 months / Health facility / By item / Pivot table  
This report provides the monthly stock on hand as reported at the end of every month.  
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
>>>>**Selected Items**: "Stock on hand"  
>>
>>**Options**    
>>>**Data**  
>>>>**Totals**  
>>>>>**Column sub-totals**: tag (appears as a white tick in a green field)  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  

![](image-9.png)

>**6 MSR - Stock correction - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock correction - Pivot table"  
>**Description**: "MSR DV 6 - Monthly Stock Reporting / Stock correction / Last 12 months / Health facility / By item / Pivot table
This report provides the monthly stock corrections as reported at the end of every month."  
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
>>>>**Selected Items**: "Stock correction"  
>>
>>**Options**  
>>>**Data**  
>>>>**Totals**  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  

![](image-10.png)

>**7 MSR - Stock report complete - Last 3 months - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock report complete - Last 3 months - Pivot table"  
>**Description**: "MSR DV 7 - Monthly Stock Reporting / Stock report complete / Last 3 month / Health facility / By item / Pivot table
This report provides an overview of all stock data from the last month."  
>>**Columns**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last month"  
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**:  
>>>>>- "Stock receipt"  
>>>>>- "Stock distribution"  
>>>>>- "Stock redistribution"  
>>>>>- "Stock discard"  
>>>>>- "Stock on hand"  
>>>>>- "Stock correction"  
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

![](image-12.png)

>**8 MSR - Stock report complete - Last 12 months - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock report complete - Last 12 months - Pivot table"  
>**Description**: "MSR DV 8 - Monthly Stock Reporting / Stock report complete / Last 12 month / Health facility / By item / Pivot table
This report provides the an overview of all stock data from the previous 12 months."   
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
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**:  
>>>>>- "Stock receipt"  
>>>>>- "Stock distribution"  
>>>>>- "Stock redistribution"    
>>>>>- "Stock discard"  
>>>>>- "Stock on hand"  
>>>>>- "Stock correction"  
>>
>>>**Filter**  
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Options**    
>>>**Data**  
>>>>**Totals**  
>>>>>**Column sub-totals**: tag (appears as a white tick in a green field)  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  

![](image-13.png)

>**9 MSR - Stock report complete - Column chart**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: **MSR - Stock report complete - Column chart**  
>**Description**: "MSR DV 9 - Monthly Stock Reporting / Stock report complete / Last 12 month / Health facility / Individual item / Column chart
This report provides an overview of all stock data from the past 12 months represented as a bar chart for each of the transactions only for a single item."  
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
>>
>>**Filter**  
>>>**Organisation unit**: "User organisation unit"  
>>>**Data**  
>>>>**Data Type**: "Data elements"  
>>>>**Data element group**: select "[Stock item list] - MSR  
>>>>**Disaggregation**: "Totals only"  
>>>>**Selected items**: select all (->>)  

![](image-16.png)

#### Indicators

>**10 MSR - Coefficient of Variation x 10 - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Coefficient of Variation x 10 - Pivot table"  
>**Description**: "MSR DV 10 - Monthly Stock Reporting / Stock distribution / Coefficient of Variation x 10 / Last 12 months / Health facility / By item / Pivot table
This report provides the coefficient of variation (standard deviation of stock distribution divided by the average stock distribution) which is based on the previous six months for each of the twelve month as a Pivot table. Since decimals cannot be displayed in this report, the result of the actual calculation is multiplied by 10 and rounded to the next integer."  
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
>>>**Data**  
>>>>**Totals**  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  
>>>**Legend**  
>>>>**Use legend for chart colors**: tag (appears as a white tick in a green field)  
>>>>>**Legend type**  
>>>>>>**Select a legend**: tag (appears as a white tick in a green field)  
>>>>>>**Legend**: "Coefficient of variation"  
>>>>>**Show legend key** tag (appears as a white tick in a green field)  

![](image-17.png)

>**11 MSR - Coefficient of Variation x 10 - Stacked bar chart**  
>
>**Visualization type**: select "Stacked bar"  
>**Name \(*)**: "MSR - Coefficient of Variation x 10 - Stacked bar chart"  
>**Description**: "MSR DV 11 - Monthly Stock Reporting / Stock distribution / Coefficient of Variation x 10 / Last 12 months / Health facility / Across items / Stacked bar chart
This report provides the coefficient of variation (standard deviation of stock distribution divided by the average stock distribution) which is based on the previous six months as a group of column charts for each of the twelve months. Since decimals cannot be displayed in this report the result of the actual calculation is multiplied by 10 and rounded to the next integer."  
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
>>>**Legend**  
>>>>**Use legend for chart colors**: tag (appears as a white tick in a green field)  
>>>>>**Legend type**  
>>>>>>**Select a legend**: tag (appears as a white tick in a green field)  
>>>>>>**Legend**: "Coefficient of variation"  
>>>>>>**Show legend key** tag (appears as a white tick in a green field)  
>
![](image-18.png)

>**12 MSR - Coefficient of Variation x 10 - Column chart**  
>
>**Visualization type**: select "Column"  
>**Name \(*)**: "MSR - Coefficient of Variation x 10 - Column chart"  
>**Description** "MSR DV 12 - Monthly Stock Reporting / Stock distribution / Coefficient of Variation x 10 / Last 12 months / Health facility / By item / Bar chart
This report provides the coefficient of variation (standard deviation of stock distribution divided by the average stock distribution) which is based on the previous six months as a group of column charts for each of the twelve months. Since decimals cannot be displayed in this report the result of the actual calculation is multiplied by 10 and rounded to the next integer."  
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
>>>>>>**Value**: "5"  
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
![](image-19.png)

>**13 MSR - Coefficient of Variation x 10 distribution - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "13 MSR - Coefficient of Variation x 10 distribution - Pivot table"  
>**Description**: "MSR DV 13 - Monthly Stock Reporting / Coefficient of Variation x 10 distribution / Last 12 months / Health facility / By item / Pivot table
This report provides the coefficient of variation (standard deviation of stock distribution divided by average stock distribution) for each item at a health facility over the last 12 months with a colour legend."  
>>**Columns**  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Indicator group**: "Coefficient of variation"  
>>>>**Selected items**: select the following items in the following order:  
>>>>- Low variability  
>>>>- Medium variability  
>>>>- High variability  
>>**Rows**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 months"  
>>
>>**Filter**: "Relative periods"  
>>>**Organisation unit**: "User organisation unit"  

![](image-38.png)

>**14 MSR - Coefficient of Variation x 10 distribution - Last 12 months - Stacked column chart**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "14 MSR - Coefficient of Variation x 10 distribution - Last 12 months - Stacked column chart"  
>**Description**: "MSR DV 14 - Monthly Stock Reporting / Coefficient of Variation x 10 distribution / Last 12 months / Health facility / By item / Stacked column chart
This report provides the number of items which fall into the respective coefficient of variation (standard deviation of stock distribution divided by average stock distribution) ranges (low, medium and high) across all items at a health facility over the last 12 months."  
>>**Series**  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Indicator group**: "Coefficient of variation"  
>>>>**Selected items**: select the following items in the following order:  
>>>>- Low variability  
>>>>- Medium variability  
>>>>- High variability  
>>
>>**Category**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 months"  
>>
>>**Filter**  
>>>**Organisation unit**: "User organisation unit"  

![](image-39.png)

>**15 MSR - MSR - Coefficient of Variation x 10 distribution - Last month - Column chart**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Coefficient of Variation x 10 distribution - Last month - Column chart"  
>**Description**: "MSR DV 15 - Monthly Stock Reporting / Coefficient of Variation x 10 distribution / Last month / Health facility / By item / Column chart
This report provides the number of items which fall into the respective coefficient of variation (standard deviation of stock distribution divided by average stock distribution) ranges (low, medium and high) across all items at a health facility for the last month."  
>>**Series**  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Indicator group**: "Coefficient of variation"  
>>>>**Selected items**: select the following items in the following order:  
>>>>- Low variability  
>>>>- Medium variability  
>>>>- High variability  
>>
>>**Category**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last month"  
>>
>>**Filter**  
>>>**Organisation unit**: "User organisation unit"  

![](image-40.png)

>**16 MSR - Stock availability - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock availability - Pivot table"  
>**Description**: "MSR DV 16 - Monthly Stock Reporting / Stock availability / Last 12 months / Health facility / By item / Pivot table
This report provides the stock availability across all stock items for an individual health facility over the last 12 months with a colour legend."  
>>**Columns**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 months"  
>>
>>**Rows**  
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Filter**  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Selected items**: select "Stock availability / %"  
>>
>>**Options**  
>>>**Legend**  
>>>>**Use legend for chart colors**: tag (appears as a white tick in a green field)  
>>>>>**Legend type**  
>>>>>>**Select a legend**: tag (appears as a white tick in a green field)  
>>>>>>**Legend**: "Stock availability / %"  
>>>>>**Show legend key** tag (appears as a white tick in a green field)  

![](image-20.png)

>**17 MSR - Stock availability - Column chart**  
>
>**Visualization type**: select "Bar"  
>**Name \(*)**: "MSR - Stock availability - Column chart"  
>**Description**: "MSR DV 17 - Monthly Stock Reporting / Stock availability / Last 12 months / Health facility / Bar chart
This report displays the stock availability (number of items with non-zero stock on hand divided by the total number of stock items) as percentage for the past 12 months as column charts with a legend."  
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

![](image-22.png)

>**18 MSR - Stock availability - Single value chart**  
>
>**Visualization type**: select "Single value"  
>**Name \(*)**: "MSR - Stock availability - Single value chart"  
>**Description**: "MSR DV 18 - Monthly Stock Reporting / Stock availability / Last month / Health facility / Single value chart
This report displays the stock availability (number of items with non-zero stock on hand divided by the total number of stock items) as percentage for the last month as a single value chart with a legend."  
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
![](image-23.png)

>**19 MSR - Stock availability - Gauge chart**  
>
>**Visualization type**: select "Gauge"  
>**Name \(*)**: "MSR - Stock availability - Gauge chart"  
>**Description**: "MSR DV 19 - Monthly Stock Reporting / Stock availability / Last month / Health facility / Gauge chart
This report displays the stock availability (number of items with non-zero stock on hand divided by the total number of stock items) as percentage for the last month as a gauge  chart with a legend."  
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

![](image-24.png)

>**xx MSR - Stockout percentage - Column chart**  
>
>**Visualization type**: select "Column"  
>**Name \(*)**: "MSR - Stockout percentage - Column chart"  
>**Description**: "MSR DV xx - Monthly Stock Reporting / Stockout percentage / Last 12 months / Health facility / Column chart
This report displays a bar chart with the percentage of items with a stockout for the past 12 months."  
>>**Series**  
>>>>**Data Type**: "Indicators"  
>>>>**Selected items**: "Stockout percentage"
>>
>>**Category**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 month"  
>>
>>**Filter**  
>>>**Organisation unit**: "User organisation unit"  

![](image-101.png)

>**xx MSR - Stock availability and stockout percentage - Stacked column chart**  
>
>**Visualization type**: select "Stacked column"  
>**Name \(*)**: "MSR - Stock availability and stockout percentage - Stacked column chart"  
>**Description**: "MSR DV xx - Monthly Stock Reporting / Stock availability and stockout percentage / Last 12 months / Health facility / Stacked column chart
This report displays the stock availability (as percentage) and the stockout percentage (which by definition must add up to 100%) as a Stacked column chart."  
>>**Series**  
>>>>**Data Type**: "Indicators"  
>>>>**Indicator group**: "Stockout count"  
>>>>**Selected items**:
>>>>>- "Stock availability / %"  
>>>>>- "Stockout percentage"  
>>
>>**Category**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 month"  
>>
>>**Filter**  
>>>**Organisation unit**: "User organisation unit"  

![](image-102.png)

>**20 MSR - Stockouts - Stacked column chart**  
>
>**Visualization type**: select "Stacked column"    
>**Name \(*)**: "MSR - Stockouts - Stacked column chart"  
>**Description**: "MSR DV 20 - Monthly Stock Reporting / Stockout by item / Last 12 months / Health facility / By item / Stacked column chart
For each of the last 12 months, this report displays a separate stacked column chart with all items which had a stockout."    
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
![](image-25.png)

>**21 MSR - Stockout count - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stockout count - Pivot table"  
>**Description**: "MSR DV 21 - Monthly Stock Reporting / Stockout count / Last 12 months / Health facility / Pivot table
This report displays the number of stockouts for all items across a health facility for each of the past 12 months as a Pivot table."  
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
>>
>>**Options**  
>>>**Data**  
>>>>**Totals**  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  
>>
>>**Options**  
>>>**Legend**  
>>>>**Use legend for chart colors**: tag (appears as a white tick in a green field)  
>>>>>**Legend style**  
>>>>>>**Legend changes background color**: tag (appears as a white tick in a green field)  
>>>>>
>>>>>**Legend type**  
>>>>>>**Select a legend**: tag (appears as a white tick in a green field)  
>>>>>>**Legend**: "Stockout count"  

![](image-80.png)

>**22 MSR - Stockout count - Column chart**  
>
>**Visualization type**: select "Column"  
>**Name \(*)**: "MSR DV 22 - Monthly Stock Reporting / Stockout count / Last 12 months / Health facility / Column chart
This report displays the number of stockouts for each of the past 12 months as a column chart."  
>>**Series**  
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stockout Yes/No"  
>>**Category**  
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
>>
>>**Options**  
>>>**Legend**  
>>>>**Use legend for chart colors**: tag (appears as a white tick in a green field)  
>>>>>**Legend type**  
>>>>>>**Legend changes background color**: tag (appears as a white tick in a green field)  
>>>>>>**Select a legend**: "Stockout count"  

![](image-27.png)

>**23 MSR - Stockout count - Single value chart**  
>
>**Visualization type**: select "Single value"  
>**Name \(*)**: "MSR - Stockout count - Single value chart"  
>**Description**: "MSR DV 23 - Monthly Stock Reporting / Stockout count / Last month / Health facility / Single value chart
This report displays the number of stockouts during the last month as a single value chart."  
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
>>
>>**Options**  
>>>**Legend**  
>>>>**Use legend for chart colors**: tag (appears as a white tick in a green field)  
>>>>>**Legend style**  
>>>>>>**Legend changes background color**: tag (appears as a white tick in a green field)  
>>>>>
>>>>>**Legend type**  
>>>>>>**Select a legend**: tag (appears as a white tick in a green field)  
>>>>>>**Legend**: "Stockout count"  

![](image-29.png)

>**24 MSR - Stockout length - Pivot table**  
>
>**Visualization type**: select "Pivot table"    
>**Name \(*)**: "MSR - Stockout length - Pivot table"  
>**Descriptions**: "MSR DV 24 - Monthly Stock Reporting / Stockout length / Last 12 months / Health facility / Pivot table 
This report displays a Pivot table by item with a "1" indicating a stockout (and "0" indicating stock was available) with a total for the past 12 months."  
>>
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
>>
>>**Options**  
>>>**Data**  
>>>>**Totals**  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  
>>>
>>>**Legend**  
>>>>**Use legend for chart colors**: tag (appears as a white tick in a green field)  
>>>>>**Legend style**  
>>>>>>**Legend changes background color**: tag (appears as a white tick in a green field)  
>>>>>
>>>>>**Legend type**  
>>>>>>**Select a legend**: tag (appears as a white tick in a green field)  
>>>>>>**Legend**: "Stockout count"  

![](image-81.png)

>**25 MSR - Stockout length - Bar chart**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stockout length - Bar chart"  
>**Description**: "MSR DV 25 - Monthly Stock Reporting / Stockout length / Last 12 months / Health facility / Bar chart
This report displays a bar chart with the number of stockouts for each item during the past 12 months."  
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

![](image-31.png)

>**26 MSR - Stock coverage time - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock coverage time - Pivot table"  
>**Description**: "MSR DV 26 - Monthly Stock Reporting / Stock coverage time / absolute / Last 12 months / Health facility / Pivot table  
This report displays a Pivot table by item with the coverage time (stock on hand divided by stock distributed during the last month) for the past 12 months. A blank field is shown, if either the stock on hand or the stock distribution for a month is zero."  
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
>>
>>**Options**  
>>>**Legend**  
>>>>**Use legend for chart colors**: tag (appears as a white tick in a green field)  
>>>>>**Legend style**  
>>>>>>**Legend changes background color**: tag (appears as a white tick in a green field)  
>>>>>
>>>>>**Legend type**  
>>>>>>**Select a legend**: tag (appears as a white tick in a green field)  
>>>>>>**Legend**: "Stock coverage time"  
>>>>>>**Show legend key** tag (appears as a white tick in a green field)  

![](image-32.png)

>**27 MSR - Stock coverage time distribution - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock coverage time distribution - Pivot table"  
>**Description**: "MSR DV 27 - Monthly Stock Reporting / Stock coverage time / distribution / Last 12 months / Health facility / Column chart
This report displays a Pivot table  with the number of items for which the coverage time fell into the respective coverage time bins (stockout, 1 to 12 months, 1-2 and 2-3 years or greater than or equal to 3 years) for each of the past 12 months."  
>>**Columns**  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Indicator group**: select "Stock coverage time"  
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
>>
>>**Options**  
>>>**Data**  
>>>>**Totals**  
>>>>>**Columns totals**: tag (appears as a white tick in a green field)  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  

![](image-52.png)

>**28 MSR - Stock coverage time distribution - Last 12 months - Stacked Column chart**  
>
>**Visualization type**: select "Stacked column"  
>**Name \(*)**: "MSR - Stock coverage time distribution - Last 12 months - Stacked column chart"  
>**Description**: "MSR DV 28 - Monthly Stock Reporting / Stock coverage time / distribution / Last 12 months / Health facility / Stocked column chart
This report displays a group of column charts representing the number of items for each stock coverage time bin (in months and years) for the past 12 months."  
>>**Series**  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Indicator group**: select "Stock coverage time"  
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

![](image-34.png)

>>**29 MSR - Stock coverage time distribution - Last month - Column chart**  
>
>**Visualization type**: select "Column"  
>**Name \(*)**: "MSR - Stock coverage time distribution - Last month - Column chart"  
>**Description**: "MSR DV 29 - Monthly Stock Reporting / Stock coverage time / distribution / Last month / Health facility / Column chart
This report displays a group of column charts representing the stock coverage time distribution (in months and years) for the last month."  
>>**Series**  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Indicator group**: select "Stock coverage time"  
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

![](image-35.png)

>>**xx MSR - Stock coverage time ranges - Last month - Column chart**  
>
>**Visualization type**: select "Column"  
>**Name \(*)**: "MSR DV xx - Monthly Stock Reporting / Stock coverage time ranges / Last month / Health facility / Stacked column chart
For each of the last month, this report displays a stacked column chart with the number of items for each stock coverage time range (stockout, understock, appropriate stock, overstock and excessive stock) for the health facility."  
>>**Series**  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Indicator group**: select "Stock coverage time"  
>>>>**Selected items**: select the following indicators in the following order:  
>>>>- "Stockout count"  
>>>>- "Understock (0-3 months)"  
>>>>- "Appropriate stock (3-6 months)"  
>>>>- "Overstock (6-12 months)"  
>>>>- "Excessive stock (> 12 months)"  
>>
>>**Category**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last month"  
>>
>>**Filter**  
>>>**Organisation unit**: "User organisation unit"  

![](image-103.png)

>>**xx MSR - Stock coverage time ranges - Last 12 months - Stacked column chart**  
>
>**Visualization type**: select "Stacked column"  
>**Name \(*)**: "MSR DV xx - Monthly Stock Reporting / Stock coverage time ranges / Last 12 months / Health facility / Stacked column chart
For each of the 12 past months, this report displays a stacked column chart with the number of items for each stock coverage time range (stockout, understock, appropriate stock, overstock and excessive stock) for the health facility."  
>>**Series**  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Indicator group**: select "Stock coverage time"  
>>>>**Selected items**: select the following indicators in the following order:  
>>>>- "Stockout count"  
>>>>- "Understock (0-3 months)"  
>>>>- "Appropriate stock (3-6 months)"  
>>>>- "Overstock (6-12 months)"  
>>>>- "Excessive stock (> 12 months)"  
>>
>>**Category**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 months"  
>>
>>**Filter**  
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Options**  
>>>**Data**  
>>>>**Display**  
>>>>>**Stacked values add up to 100%**  

![](image-104.png)

>**30 MSR - Stock discrepancy - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock discrepancy - Pivot table"  
>**Description**: ">MSR DV 30 - Monthly Stock Reporting / Stock discrepancy / list / Last 12 months / Health facility / Pivot table  
This report displays a list with the positive and negative stock discrepancy of the past 12 months. The stock discrepancy is calculated as follows  
> Stock on hand from the previous month (final stock on hand)  
> + Stock receipt  
> - Stock distributed  
> - Stock redistributed  
> - Stock discard  
> - Stock correction  
> - Stock on hand"  
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
>>  
>>**Options**  
>>>**Data**  
>>>>**Totals**  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  

![](image-54.png)

>**31 MSR - Stock discrepancy count - Column chart**  
>
>**Visualization type**: select "Column"  
>**Name \(*)**: "MSR - Stock discrepancy count - Column chart"  
>**Visualization type**: "MSR DV 31 - Monthly Stock Reporting / Stock discrepancy / count / Last 12 months / Health facility / Pivot table
This report displays the number of stock discrepancies for the past 12 months."  
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
>
![](image-37.png)

>**31 MSR - Stock discrepancy count - Percentage - Column chart**  
>
>**Visualization type**: select "Column"  
>**Name \(*)**: "MSR - Stock discrepancy count - Percentage - Column chart"  
>**Visualization type**: "MSR DV xx - Monthly Stock Reporting / Stock discrepancy / Percentage / Last 12 months / Health facility / Column chart
This report displays the percentage of all items with a stock discrepancies for the past 12 months."  
>>
>>**Series**  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Indicator group**: select "Stockout discrepancy"  
>>>>**Selected items**: "Stock discrepancy percentage"
>>  
>>**Category**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 month"  
>>
>>**Filter**  
>>>**Organisation unit**: "User organisation unit"  
>>  
>>**Options**  
>>>**Axes**  
>>>>**Axis ranges**  
>>>>>**Max**: "100"
>>  
>>>**Legend**  
>>>>**Use legend for chart colors**: tag (appears as a white tick in a green field)  
>>>>>**Select a legend**: tag (appears as a white tick in a green field)  
>>>>>**Legend**: "Stockout count"  

![](image-106.png)

### District level

#### Statistics

>**32 MSR - Stock receipt - District - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock receipt - Pivot table"  
>**Description**: "MSR DV 32 - Monthly Stock Reporting / Stock receipt / Last 12 months / Health facility / By item / Pivot table  
This report provides the monthly stock receipts by health facility in a district as reported at the end of every month."  
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
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Filter**: "Relative periods"  
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stock receipt"  
>>
>>**Options**  
>>>**Data**  
>>>>**Totals**  
>>>>>**Column sub-totals**: tag (appears as a white tick in a green field)  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  

![](image-61.png)

>**33 MSR - Stock distribution - District - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock distribution - District - Pivot table"  
>**Description**: "MSR DV 33 - Monthly Stock Reporting / Stock distribution / Last 12 months / District / By item / Pivot table  
This report provides the monthly stock distributions by health facility in a district as reported at the end of every month."  
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
>>
>>**Options**  
>>>**Data**  
>>>>**Totals**  
>>>>>**Column sub-totals**: tag (appears as a white tick in a green field)  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  

![](image-57.png)

>**34 MSR - Stock redistribution - District - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock redistribution - District - Pivot table"  
>**Description**: "MSR DV 34 - Monthly Stock Reporting / Stock redistribution / Last 12 months / District / By item / Pivot table.    
This report provides the monthly stock redistributions by health facility in a district as reported at the end of every month."  
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
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Filter**: "Relative periods"  
>>>>**Selected Periods**: "Last 12 months"  
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stock redistribution"  
>>
>>**Options**  
>>>**Data**  
>>>>**Totals**  
>>>>>**Column sub-totals**: tag (appears as a white tick in a green field)  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  

![](image-62.png)

>**35 MSR - Stock discard - District - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "35 MSR - Stock discard - District - Pivot table"  
>**Description**: "MSR DV 35 - Monthly Stock Reporting / Stock discard / Last 12 months / District / By item / Pivot table  
This report provides the monthly stock discards by health facility in a district as reported at the end of every month."  
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
>>>**Organisation unit**: "User organisation unit"  
>>>
>>**Filter**: "Relative periods"  
>>>>**Selected Periods**: "Last 12 months"  
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stock discard"  
>>
>>**Options**  
>>>**Data**  
>>>>**Totals**  
>>>>>**Column sub-totals**: tag (appears as a white tick in a green field)  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  

![](image-56.png)

>**36 MSR - Stock on hand - District - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock on hand - District - Pivot table"  
>**Description**: "MSR DV 36 - Monthly Stock Reporting / Stock on hand / Last 12 months / District / By item / Pivot table  
This report provides the monthly stock on hand by health facility in a district as reported at the end of every month.  
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
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Filter**: "Relative periods"  
>>>>**Selected Periods**: "Last 12 months"  
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stock on hand"  
>>
>>**Options**  
>>>**Data**  
>>>>**Totals**  
>>>>>**Column sub-totals**: tag (appears as a white tick in a green field)  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  

![](image-59.png)

>**37 MSR - Stock correction - District - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock correction - District - Pivot table"  
>**Description**: "MSR DV 37 - Monthly Stock Reporting / Stock correction / Last 12 months / District / By item / Pivot table
This report provides the monthly stock corrections by health facility in a district as reported at the end of every month."  
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
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Filter**: "Relative periods"  
>>>>**Selected Periods**: "Last 12 months"  
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stock correction"  
>>
>>**Options**  
>>>**Data**  
>>>>**Totals**  
>>>>>**Column sub-totals**: tag (appears as a white tick in a green field)  
>>>>>**Row totals**: tag (appears as a white tick in a green  

![](image-55.png)

>**38 MSR - Stock report complete - Last 3 months - District - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock report complete - Last 3 months - District - Pivot table"  
>**Description**: "MSR DV 38 - Monthly Stock Reporting / Stock report complete / Last 3 month / District / By item / Pivot table
This report provides an overview of all stock data by health facility in a district from the last 3 months."  
>>**Columns**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last month"  
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stock distribution"  
>>
>>**Rows**  
>>>**Data**  
>>>>**Data Type**: "Data elements"  
>>>>**Data element group**: select "[Stock item list] - MSR  
>>>>**Disaggregation**: "Totals only"  
>>>>**Selected items**: select all (->>)  
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Options**  
>>>**Data**  
>>>>**Totals**  
>>>>>**Column sub-totals**: tag (appears as a white tick in a green field)  

![](image-63.png)

#### Indicators

>**39 MSR - Coefficient of Variation x 10 - District - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Coefficient of Variation x 10 - District - Pivot table"  
>**Description**: "MSR DV 10 - Monthly Stock Reporting / Stock distribution / Coefficient of Variation x 10 / Last 12 months / District / By item / Pivot table
This report provides the coefficient of variation (standard deviation of stock distribution divided by the average stock distribution) which is based on the previous six months for each of the twelve month as a Pivot table for each item and by health facilities in a district. Since decimals cannot be displayed in this report, the result of the actual calculation is multiplied by 10 and rounded to the next integer."  
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
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Filter**: "Relative periods"  
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Coefficient of variation"  
>>
>>**Options**  
>>>**Data**  
>>>>**Totals**  
>>>>>**Column sub-totals**: tag (appears as a white tick in a green field)  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  
>>>
>>>**Legend**  
>>>>**Use legend for chart colors**: tag (appears as a white tick in a green field)  
>>>>>**Legend type**  
>>>>>>**Select a legend**: tag (appears as a white tick in a green field)  
>>>>>>**Legend**: "Coefficient of variation"  
>>>>>**Show legend key** tag (appears as a white tick in a green field)  

![](image-64.png)

>**40 MSR - Coefficient of Variation x 10 - District - Stacked bar chart**  
>
>**Visualization type**: select "Stacked bar"  
>**Name \(*)**: "MSR - Coefficient of Variation x 10 - District - Stacked bar chart"  
>**Description**: "MSR DV 40 - Monthly Stock Reporting / Stock distribution / Coefficient of Variation x 10 / Last month / District / Across items / Stacked bar chart
This report provides the coefficient of variation (standard deviation of stock distribution divided by the average stock distribution) which is based on the previous six months as a group of column charts for the last month and by health facilities in a district. Since decimals cannot be displayed in this report the result of the actual calculation is multiplied by 10 and rounded to the next integer."  
>>**Series**  
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Category**  
>>>**Data**  
>>>>**Data Type**: "Data elements"  
>>>>**Data element group**: select "[Stock item list] - MSR  
>>>>**Disaggregation**: "Totals only"  
>>>>**Selected items**: select all (->>)  
>>
>>**Filter**: "Relative periods"  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 months"  
>>>
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Coefficient of variation"  
>>>
>>>**Legend**  
>>>>**Use legend for chart colors**: tag (appears as a white tick in a green field)  
>>>>>**Legend type**  
>>>>>>**Select a legend**: tag (appears as a white tick in a green field)  
>>>>>>**Legend**: "Coefficient of variation"  
>>>>>>**Show legend key** tag (appears as a white tick in a green field)  

![](image-65.png)

>**41 MSR - Coefficient of Variation x 10 - Distric - Bar chart**  
>
>**Visualization type**: select "Bar"  
>**Name \(*)**: "MSR - Coefficient of Variation x 10 - Column chart"  
>**Description** "MSR DV 41 - Monthly Stock Reporting / Stock distribution / Coefficient of Variation x 10 / Last month / District / By item / Column chart
This report provides the coefficient of variation (standard deviation of stock distribution divided by the average stock distribution) which is based on the previous six months as a group of column charts for each of the twelve months by healt facility in the district. Since decimals cannot be displayed in this report the result of the actual calculation is multiplied by 10 and rounded to the next integer."  
>>**Series**  
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Coefficient of variation"  
>>
>>**Category**  
>>>**Data**  
>>>>**Data Type**: "Data elements"  
>>>>**Data element group**: select "[Stock item list] - MSR  
>>>>**Disaggregation**: "Totals only"  
>>>>**Selected items**: select all (->>)  
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Filter**: "Relative periods"  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last months"  
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
>>>>>>**Value**: "5"  
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

![](image-66.png)

>**42 MSR - Coefficient of Variation x 10 distribution - District - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "42 MSR - Coefficient of Variation x 10 distribution - District - Pivot table"  
>**Description**: "MSR DV 13 - Monthly Stock Reporting / Coefficient of Variation x 10 distribution / Last 12 months / Health facility / By item / Pivot table
This report provides the coefficient of variation (standard deviation of stock distribution divided by average stock distribution) by health facilities in the district over the last 12 months with a colour legend."  
>>**Columns**  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Indicator group**: "Coefficient of variation"  
>>>>**Selected items**: select the following items in the following order:  
>>>>- Low variability  
>>>>- Medium variability  
>>>>- High variability  
>>**Rows**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 months"  
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Options**  
>>>**Data**  
>>>>**Totals**  
>>>>>**Column sub-totals**: tag (appears as a white tick in a green field)  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  

![](image-67.png)

>**43 MSR - Coefficient of Variation x 10 distribution - Last 12 months - District - Stacked column chart**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "43 MSR - Coefficient of Variation x 10 distribution - Last 12 months - District - Stacked column chart"  
>**Description**: "MSR DV 14 - Monthly Stock Reporting / Coefficient of Variation x 10 distribution / Last 12 months / District / By item / Stacked column chart
This report provides the number of items which fall into the respective coefficient of variation (standard deviation of stock distribution divided by average stock distribution) ranges (low, medium and high) across all items at a health facility for all health facilities in a district over the last 12 months."  
>>**Series**  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Indicator group**: "Coefficient of variation"  
>>>>**Selected items**: select the following items in the following order:  
>>>>- Low variability  
>>>>- Medium variability  
>>>>- High variability  
>>
>>**Category**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 months"  
>>>**Organisation unit**: "User organisation unit"  

![](image-69.png)

>**44 MSR - MSR - Coefficient of Variation x 10 distribution - Last month - District - Column chart**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Coefficient of Variation x 10 distribution - Last month - District - Column chart"  
>**Description**: "MSR DV 15 - Monthly Stock Reporting / Coefficient of Variation x 10 distribution / Last month / Health facility / By item / Column chart
This report provides the number of items which fall into the respective coefficient of variation (standard deviation of stock distribution divided by average stock distribution) ranges (low, medium and high) across all items at a health facility for the last month by health facilities in the district."  
>>**Series**  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Indicator group**: "Coefficient of variation"  
>>>>**Selected items**: select the following items in the following order:  
>>>>- Low variability  
>>>>- Medium variability  
>>>>- High variability  
>>
>>**Category**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last month"  
>>>**Organisation unit**: "User organisation unit"  

![](image-70.png)

>**45 MSR - Stock availability - District - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock availability - District - Pivot table"  
>**Description**: "MSR DV 45 - Monthly Stock Reporting / Stock availability / Last 12 months / District / By item / Pivot table
This report provides the stock availability across all stock items for all health facilities in a district over the last 12 months with a colour legend."  
>>**Columns**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 months"  
>>
>>**Rows**  
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Filter**  
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

![](image-71.png)

>**46 MSR - Stock availability - District - Column chart - Last 12 months**  
>
>**Visualization type**: select "Bar"  
>**Name \(*)**: "MSR - Stock availability - District - Column chart - Last 12 months"  
>**Description**: "MSR DV 46 - Monthly Stock Reporting / Stock availability / Last 12 months / District / Column chart
This report displays the stock availability (number of items with non-zero stock on hand divided by the total number of stock items) as percentage for the past 12 months for all health facilities in a district as column charts with a legend."  
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

![](image-72.png)

>**47 MSR - Stock availability - District - Column chart - Last month**  
>
>**Visualization type**: select "Single value"  
>**Name \(*)**: "MSR - Stock availability - District - Column chart - Last month"  
>**Description**: "MSR DV 47 - Monthly Stock Reporting / Stock availability / Last month / Health facility / Column chart
This report displays the stock availability (number of items with non-zero stock on hand divided by the total number of stock items) as percentage for the last month for all health facilities in a district as a Column chart with a legend."  
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
>>>>>
>>>>>**Legend type**  
>>>>>>**Select a legend**: tag (appears as a white tick in a green field)  
>>>>>>**Legend**: "Stock availability / %"  
>>>>>>**Show legend key** tag (appears as a white tick in a green field)  

![](image-74.png)

>**xx MSR - Stockout percentage - District - Column chart**  
>
>**Visualization type**: select "Column"  
>**Name \(*)**: "MSR - Stockout percentage - District - Column chart"  
>**Description**: "MSR DV xx - Monthly Stock Reporting / Stockout percentage / Last 12 months / Health facility / Column chart
This report displays a bar chart with the percentage of items with a stockout for the past 12 months."  
>>**Series**  
>>>>**Data Type**: "Indicators"  
>>>>**Selected items**: "Stockout percentage"
>>
>>**Category**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 month"  
>>>**Organisation unit**: "User organisation unit"  

![](image-108.png)

>**xx MSR - Stock availability and stockout percentage - District - Stacked column chart**  
>
>**Visualization type**: select "Stacked column"  
>**Name \(*)**: "MSR - Stock availability and stockout percentage - District - Stacked column chart"  
>**Description**: "MSR DV xx - Monthly Stock Reporting / Stock availability and stockout percentage / Last 12 months / District  / Stacked column chart
This report displays the stock availability (number of items with non-zero stock on hand divided by the total number of stock items) as percentage for the past 12 months for all health facilities in a district as column charts with a legend."  
>>**Series**  
>>>>**Data Type**: "Indicators"  
>>>>**Indicator group**: "Stockout count"  
>>>>**Selected items**:
>>>>>- "Stock availability / %"  
>>>>>- "Stockout percentage"  
>>
>>**Category**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 month"  
>>>**Organisation unit**: "User organisation unit"  

![](image-109.png)

>**48 MSR - Stockouts - District - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stockouts - District - Pivot table"  
>**Description**: "MSR DV 48 - Monthly Stock Reporting / Stockout by item / Last 12 months / District / By item / Pivot table
This report displays a Pivot table with all items and indicating for each item whether it was out of stock for all health facilities in a district for the last 12 months".  
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
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Filter**: "Relative periods"  
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stockout Yes/No"  

![alt text](image-75.png)

>**49 MSR - Stockout count - District - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stockout count - District - Pivot table"  
>**Description**: "MSR DV 49 - Monthly Stock Reporting / Stockout count / Last 12 months / District / Pivot table
This report displays the number of stockouts for all items across a health facility for each of the past 12 months for all health facilities in a district as a Pivot table."  
>>**Columns**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 months"  
>>
>>**Rows**  
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Filter**  
>>>**Data**  
>>>>**Data Type**: "Data elements"  
>>>>**Data element group**: select "[Stock item list] - MSR  
>>>>**Disaggregation**: "Totals only"  
>>>>**Selected items**: select all (->>)  
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stockout Yes/No"  
>>
>>**Options**  
>>>**Legend**  
>>>>**Use legend for chart colors**: tag (appears as a white tick in a green field)  
>>>>>**Legend style**  
>>>>>>**Legend changes background color**: tag (appears as a white tick in a green field)   
>>>>>
>>>>>**Legend type**  
>>>>>>**Select a legend**: tag (appears as a white tick in a green field)  
>>>>>>**Legend**: "Stockout count"  

![alt text](image-79.png)

>**50 MSR - Stockout count - District - Column chart**  
>
>**Visualization type**: select "Column"  
>**Name \(*)**: "MSR - Stockout count - District - Column chart"  
>**Description**: "MSR DV 50 - Monthly Stock Reporting / Stockout count / Last 12 months / District / Stacked column chart
This report displays the number of stockouts for each of the past 12 months for all health facilities in a district as a column chart."     
>>**Series**  
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stockout Yes/No"  
>>
>>**Category**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 months"  
>>>**Organisation unit**: "User organisation unit"  
>>
>>>**Filter**  
>>>>**Data Type**: "Data elements"  
>>>>**Data element group**: select "[Stock item list] - MSR  
>>>>**Disaggregation**: "Totals only"  
>>>>**Selected items**: select all (->>)  

![](image-77.png)

>**51 MSR - Stockout count - District - Single value chart**  
>
>**Visualization type**: select "Single value"  
>**Name \(*)**: "MSR - Stockout count - District - Single value chart"  
>**Description**: "MSR DV 51 - Monthly Stock Reporting / Stockout count / Last month / District / Single value chart
This report displays the total number of stockouts in all health facilities of a district during the last month as a single value chart."  
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
>>
>>**Options**  
>>>**Legend**  
>>>>**Use legend for chart colors**: tag (appears as a white tick in a green field)  
>>>>>**Legend style**  
>>>>>>**Legend changes background color**: tag (appears as a white tick in a green field)  
>>>>> 
>>>>>**Legend type**  
>>>>>>**Select a legend**: tag (appears as a white tick in a green field)  
>>>>>>**Legend**: "Stockout count"  

![](image-78.png)

>**52 MSR - Stockout length - District - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stockout length - District - Pivot table"  
>**Descriptions**: "MSR DV 24 - Monthly Stock Reporting / Stockout length / Last 12 months / District / Pivot table 
This report displays a Pivot table by item with a "1" indicating a stockout (and "0" indicating stock was available) with a total for the past 12 months which represents the number of months during which a stockout occurred for all health facilities in the district."  
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
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Options**  
>>>**Data**  
>>>>**Totals**  
>>>>>**Column totals**: tag (appears as a white tick in a green field)  
>>>>>**Column sub-totals**: tag (appears as a white tick in a green field)  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  
>>>
>>>**Legend**  
>>>>**Use legend for chart colors**: tag (appears as a white tick in a green field)  
>>>>>**Legend style**  
>>>>>>**Legend changes background color**: tag (appears as a white tick in a green field)  
>>>>>
>>>>>**Legend type**  
>>>>>>**Select a legend**: tag (appears as a white tick in a green field)  
>>>>>>**Legend**: "Stockout count"  

![](image-82.png)

>**53 MSR - Stockout length - District - Stacked bar chart**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stockout length - District - Bar chart"  
>**Description**: "MSR DV 53 - Monthly Stock Reporting / Stockout length / Last 12 months / District / Stacked bar chart
This report displays a stacked bar chart with the number of stockouts for each item by health facilities in the district during the past 12 months."  
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
>>
>>**Options**  
>>>**Data**  
>>>>**Hide empty categories**: tag (appears as a white tick in a green field)  
>>>>>**Dropdown menu**: select "All"  

![](image-134.png)

>**54 MSR - Stock coverage time - District - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock coverage time - District - Pivot table"  
>**Description**: "MSR DV 54 - Monthly Stock Reporting / Stock coverage time / absolute / Last 12 months / District / Pivot table
This report displays a Pivot table by item with the coverage time (stock on hand divided by stock distributed during the last month) for the past 12 months for each health facility in a distrct. A blank field is shown, if either the stock on hand or the stock distribution for a month is zero."  
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
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Filter**  
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stockout coverage"  
>>
>>**Options**  
>>>**Legend**  
>>>>**Use legend for chart colors**: tag (appears as a white tick in a green field)  
>>>>>**Legend style**  
>>>>>>**Legend changes background color**: tag (appears as a white tick in a green field)   
>>>>>
>>>>>**Legend type**  
>>>>>>**Select a legend**: tag (appears as a white tick in a green field)  
>>>>>>**Legend**: "Stock coverage time"  
>>>>>>**Show legend key** tag (appears as a white tick in a green field)  

![](image-84.png)

>**55 MSR - Stock coverage time distribution - District - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock coverage time distribution - District - Pivot table"  
>**Description**: "MSR DV 55 - Monthly Stock Reporting / Stock coverage time / distribution / Last 12 months / District / Column chart
This report displays a Pivot table  with the number of items for which the coverage time fell into the respective coverage time bins (stockout, 1 to 12 months, 1-2 and 2-3 years or greater than or equal to 3 years) for all health facilities in a district for each of the past 12 months."  
>>**Columns**  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Indicator group**: select "Stock coverage time"  
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
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Options**  
>>>**Data**  
>>>>**Totals**  
>>>>>**Columns totals**: tag (appears as a white tick in a green field)  
>>>>>**Columns sub-totals**: tag (appears as a white tick in a green field)  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  

![alt text](image-52.png)

>**56 MSR - Stock coverage time distribution - Last 12 months - District - Stacked column chart**  
>
>**Visualization type**: select "Stacked column"  
>**Name \(*)**: "MSR - Stock coverage time distribution - Last 12 months - District - Stacked column chart"  
>**Description**: "MSR DV 56 - Monthly Stock Reporting / Stock coverage time / distribution / Last 12 months / District / Stacked column chart
For each of the 12 past months, this report displays a stacked column chart with the number of items for each stock coverage time bin (in months and years) separately for each health facility in the district."  
>>**Series**  
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Category**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 month"  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Indicator group**: select "Stock coverage time"  
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

![](image-85.png)

>>**57 MSR - Stock coverage time distribution - Last month - District - Stacked column chart**  
>
>**Visualization type**: select "Stacked column"  
>**Name \(*)**: "MSR - Stock coverage time distribution - Last month - District - Stacked column chart"  
>**Description**: "MSR DV 29 - Monthly Stock Reporting / Stock coverage time / distribution / Last month / District / Stacked column chart
For the last month, this report displays a stacked column chart with the number of items for each stock coverage time bin (in months and years) separately for each health facility in the district.  
>>**Series**  
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Category**  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Indicator group**: select "Stock coverage time"  
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
>>**Filter**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last month"  

![](image-88.png)

>>**xx MSR - Stock coverage time ranges - District  - Stacked column chart- Last month**  
>
>**Visualization type**: select "Stacked column"  
>**Name \(*)**: "MSR - Stock coverage time distribution - Last month - District - Stacked column chart"  
>**Description**: "MSR DV xx - Monthly Stock Reporting / Stock coverage time / Ranges / District / Stacked column chart / Last month
For the last month, this report displays a stacked column chart with the number of items for each coverage range (stockout, understock, appropriate stock, overstock and excessive stock) for each health facility in the district."  
>>**Series**  
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Category**  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Indicator group**: select "Stock coverage time"  
>>>>**Selected items**: select the following indicators in the following order:  
>>>>- "Stockout count"  
>>>>- "Understock (0-3 months)"  
>>>>- "Appropriate stock (3-6 months)"  
>>>>- "Overstock (6-12 months)"  
>>>>- "Excessive stock (> 12 months)"  
>>
>>**Filter**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last month"  

![](image-110.png)

>>**xx MSR - Stock coverage time ranges - District  - Stacked column chart - Last 12 months**  
>
>**Visualization type**: select "Stacked column"  
>**Name \(*)**: "MSR - Stock coverage time distribution - Last month - District - Stacked column chart"  
>**Description**: "MSR DV xx - Monthly Stock Reporting / Stock coverage time / Ranges / District / Stacked column chart / Last month
For the 12 last months, this report displays a stacked column chart with the number of items for each coverage range (stockout, understock, appropriate stock, overstock and excessive stock) for each health facility in the district."  
>>**Series**  
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Category**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 months"  
>>>
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Indicator group**: select "Stock coverage time"  
>>>>**Selected items**: select the following indicators in the following order:  
>>>>- "Stockout count"  
>>>>- "Understock (0-3 months)"  
>>>>- "Appropriate stock (3-6 months)"  
>>>>- "Overstock (6-12 months)"  
>>>>- "Excessive stock (> 12 months)"  

![](image-111.png)

>**58 MSR - Stock discrepancy - District - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock discrepancy - District - Pivot table"  
>**Description**: ">MSR DV 58 - Monthly Stock Reporting / Stock discrepancy / list / Last 12 months / District / Pivot table
This report displays a list with the positive and negative stock discrepancy of the past 12 months by item for all health facilities in a district.  
+ Stock on hand from the previous month (final stock on hand)  
+ Stock receipt  
- Stock distributed  
- Stock redistributed  
- Stock discard  
- Stock correction  
- Stock on hand"  
>>  
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
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Filter**  
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stock discrepancy count"  
>>  
>>**Options**  
>>>**Data**  
>>>>**Totals**  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  

![alt text](image-54.png)

>**59 MSR - Stock discrepancy count - District - Stacked column chart**  
>
>**Visualization type**: select "Column"  
>**Name \(*)**: "MSR - Stock discrepancy count - District - Stacked column chart"  
>**Visualization type**: "MSR DV 31 - Monthly Stock Reporting / Stock discrepancy / count / Last 12 months / District / Stacked column chart
This report displays the number of stock discrepancies for the past 12 months separately for each health facility in a district."  
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

![](image-87.png)

>**xx MSR - Stock discrepancy count - Percentage - District - Column chart**  
>
>**Visualization type**: select "Column"  
>**Name \(*)**: "MSR - Stock discrepancy count - Percentage - Column chart"  
>**Visualization type**: "MSR DV xx - Monthly Stock Reporting / Stock discrepancy / Percentage / Last 12 months / District / Health facility / Column chart
This report displays the percentage of all items with a stock discrepancies for the past 12 months by health facilities in the district."  
>>
>>**Series**  
>>>**Organisation unit**: "User organisation unit"  
>>  
>>**Category**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 month"  
>>
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Indicator group**: select "Stockout discrepancy"  
>>>>**Selected items**: "Stock discrepancy percentage"

![](image-112.png)

### Province level

#### Statistics

>**60 MSR - Stock receipt - Province - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock receipt - Province - Pivot table"  
>**Description**: "MSR DV 60 - Monthly Stock Reporting / Stock receipt / Last 12 months / Province / By item / Pivot table
This report provides the monthly stock receipts by district in a province as reported at the end of every month."  
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
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Filter**: "Relative periods"  
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stock receipt"  
>>
>>**Options**  
>>>**Data**  
>>>>**Totals**  
>>>>>**Column sub-totals**: tag (appears as a white tick in a green field)  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  

![](image-115.png)

>**61 MSR - Stock distribution - Province - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock distribution - Province - Pivot table"  
>**Description**: "MSR DV 61 - Monthly Stock Reporting / Stock distribution / Last 12 months / Province / By item / Pivot table  
This report provides the monthly stock distributions by district in a province as reported at the end of every month."  
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
>>>**Organisation unit**: "User organisation unit" (Level set to "District")  
>>>>**Selected Periods**: "Last 12 months"    
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stock distribution"  
>>
>>**Options**  
>>>**Data**  
>>>>**Totals**  
>>>>>**Column sub-totals**: tag (appears as a white tick in a green field)  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  

![](image-114.png)

>**62 MSR - Stock redistribution - Province - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock redistribution - Province - Pivot table"  
>**Description**: "MSR DV 62 - Monthly Stock Reporting / Stock redistribution / Last 12 months / Province / By item / Pivot table.    
This report provides the monthly stock redistributions by district facility in a province as reported at the end of every month."  
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
>>>**Organisation unit**: "User organisation unit" (Level set to "District")  
>>
>>**Filter**: "Relative periods"  
>>>>**Selected Periods**: "Last 12 months"  
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stock redistribution"  
>>
>>**Options**  
>>>**Data**  
>>>>**Totals**  
>>>>>**Column sub-totals**: tag (appears as a white tick in a green field)  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  

![](image-116.png)

>**63 MSR - Stock discard - Province - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock discard - Province - Pivot table"  
>**Description**: "MSR DV 63 - Monthly Stock Reporting / Stock discard / Last 12 months / Province / By item / Pivot table  
This report provides the monthly stock discards by districts in a province as reported at the end of every month."  
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
>>>**Organisation unit**: "User organisation unit" (Level set to "District")  
>>>
>>**Filter**: "Relative periods"  
>>>>**Selected Periods**: "Last 12 months"  
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stock discard"  
>>
>>**Options**  
>>>**Data**  
>>>>**Totals**  
>>>>>**Column sub-totals**: tag (appears as a white tick in a green field)  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  

![](image-117.png)

>**64 MSR - Stock on hand - Province - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock on hand - Province - Pivot table"  
>**Description**: "MSR DV 64 - Monthly Stock Reporting / Stock on hand / Last 12 months / Province / By item / Pivot table  
This report provides the monthly stock on hand by district in a province as reported at the end of every month."  
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
>>>**Organisation unit**: "User organisation unit" (Level set to "District")  
>>
>>**Filter**: "Relative periods"  
>>>>**Selected Periods**: "Last 12 months"  
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stock on hand"  
>>
>>**Options**  
>>>**Data**  
>>>>**Totals**  
>>>>>**Column sub-totals**: tag (appears as a white tick in a green field)  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  

![](image-118.png)

>**65 MSR - Stock correction - Province - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock correction - Province - Pivot table"  
>**Description**: "MSR DV 65 - Monthly Stock Reporting / Stock correction / Last 12 months / Province / By item / Pivot table
This report provides the monthly stock corrections by district in a province as reported at the end of every month."  
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
>>>**Organisation unit**: "User organisation unit" (Level set to "District")  
>>
>>**Filter**: "Relative periods"  
>>>>**Selected Periods**: "Last 12 months"  
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stock correction"  
>>
>>**Options**  
>>>**Data**  
>>>>**Totals**  
>>>>>**Column sub-totals**: tag (appears as a white tick in a green field)  
>>>>>**Row totals**: tag (appears as a white tick in a green  

![](image-119.png)

>**66 MSR - Stock report complete - Last 3 months - Province - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock report complete - Last 3 months - Province - Pivot table"  
>**Description**: "MSR DV 66 - Monthly Stock Reporting / Stock report complete / Last 3 months / Province / By item / Pivot table
This report provides an overview of all stock data by district in a province from the last 3 months."  
>>**Columns**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last month"  
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stock distribution"  
>>
>>**Rows**  
>>>**Data**  
>>>>**Data Type**: "Data elements"  
>>>>**Data element group**: select "[Stock item list] - MSR  
>>>>**Disaggregation**: "Totals only"  
>>>>**Selected items**: select all (->>)  
>>>**Organisation unit**: "User organisation unit"   (Level set to "District")  
>>
>>**Options**  
>>>**Data**  
>>>>**Totals**  
>>>>>**Column sub-totals**: tag (appears as a white tick in a green field)  

![](image-120.png)

#### Indicators

>**7x MSR - Coefficient of Variation x 10 - Province - Stacked bar chart**  
>
>**Visualization type**: select "Stacked bar"  
>**Name \(*)**: "MSR - Coefficient of Variation x 10 - Province - Stacked bar chart"  
>**Description**: "MSR DV xx - Monthly Stock Reporting / Stock distribution / Coefficient of Variation x 10 / Last month / Province / By item / Stacked bar chart
This report provides the coefficient of variation (standard deviation of stock distribution divided by the average stock distribution) which is based on the previous six months as a group of column charts for the last month and by health facilities in a province. Since decimals cannot be displayed in this report the result of the actual calculation is multiplied by 10 and rounded to the next integer."  
>>**Series**  
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Category**  
>>>**Data**  
>>>>**Data Type**: "Data elements"  
>>>>**Data element group**: select "[Stock item list] - MSR  
>>>>**Disaggregation**: "Totals only"  
>>>>**Selected items**: select all (->>)  
>>
>>**Filter**: "Relative periods"  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last month"  
>>>
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Coefficient of variation"  
>>>
>>>**Legend**  
>>>>**Use legend for chart colors**: tag (appears as a white tick in a green field)  
>>>>>**Legend type**  
>>>>>>**Select a legend**: tag (appears as a white tick in a green field)  
>>>>>>**Legend**: "Coefficient of variation"  
>>>>>>**Show legend key** tag (appears as a white tick in a green field)  

![](image-121.png)

>**7x MSR - Coefficient of Variation x 10 distribution - Province - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "42 MSR - Coefficient of Variation x 10 distribution - District - Pivot table"  
>**Description**: "MSR DV 13 - Monthly Stock Reporting / Coefficient of Variation x 10 distribution / Last 12 months / Health facility / By item / Pivot table
This report provides the coefficient of variation (standard deviation of stock distribution divided by average stock distribution) by health facilities in the district over the last 12 months with a colour legend."  
>>**Columns**  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Indicator group**: "Coefficient of variation"  
>>>>**Selected items**: select the following items in the following order:  
>>>>- Low variability  
>>>>- Medium variability  
>>>>- High variability  
>>**Rows**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 months"  
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Options**  
>>>**Data**  
>>>>**Totals**  
>>>>>**Column sub-totals**: tag (appears as a white tick in a green field)  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  

![](image-67.png)

>**7x MSR - Coefficient of Variation x 10 distribution - Last 12 months - Province - Stacked column chart**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "43 MSR - Coefficient of Variation x 10 distribution - Last 12 months - District - Stacked column chart"  
>**Description**: "MSR DV 14 - Monthly Stock Reporting / Coefficient of Variation x 10 distribution / Last 12 months / District / By item / Stacked column chart
This report provides the number of items which fall into the respective coefficient of variation (standard deviation of stock distribution divided by average stock distribution) ranges (low, medium and high) across all items at a health facility for all health facilities in a district over the last 12 months."  
>>**Series**  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Indicator group**: "Coefficient of variation"  
>>>>**Selected items**: select the following items in the following order:  
>>>>- Low variability  
>>>>- Medium variability  
>>>>- High variability  
>>
>>**Category**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 months"  
>>>**Organisation unit**: "User organisation unit"  

![](image-69.png)

>**7x MSR - MSR - Coefficient of Variation x 10 distribution - Province - Column chart - Last month**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Coefficient of Variation x 10 distribution - Last month - District - Column chart"  
>**Description**: "MSR DV 15 - Monthly Stock Reporting / Coefficient of Variation x 10 distribution / Last month / Health facility / By item / Column chart
This report provides the number of items which fall into the respective coefficient of variation (standard deviation of stock distribution divided by average stock distribution) ranges (low, medium and high) across all items at a health facility for the last month by health facilities in the district."  
>>**Series**  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Indicator group**: "Coefficient of variation"  
>>>>**Selected items**: select the following items in the following order:  
>>>>- Low variability  
>>>>- Medium variability  
>>>>- High variability  
>>
>>**Category**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last month"  
>>>**Organisation unit**: "User organisation unit"  

![](image-70.png)

>**7x MSR - Stock availability - Province - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock availability - Province - Pivot table"  
>**Description**: "MSR DV xx - Monthly Stock Reporting / Stock availability / Last 12 months / Province / By item / Pivot table
This report provides the stock availability across all stock items for all health facilities in a province over the last 12 months with a colour legend."
>>  
>>**Columns**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 months"  
>>
>>**Rows**  
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Filter**  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Selected items**: select "Stock availability / %"  
>>
>>**Options**  
>>>**Legend**  
>>>>**Use legend for chart colors**: tag (appears as a white tick in a green field)  
>>>>>**Legend type**  
>>>>>>**Select a legend**: tag (appears as a white tick in a green field)  
>>>>>>**Legend**: "Stock availability / %"  
>>>>>
>>>>>**Show legend key** tag (appears as a white tick in a green field)  

![](image-122.png)

>**7x MSR - Stock availability - Province - Column chart**  
>
>**Visualization type**: select "Column"  
>**Name \(*)**: "MSR - Stock availability - District - Bar chart"  
>**Description**: "MSR DV xx - Monthly Stock Reporting / Stock availability / Last 12 months / Province / Across items / Column chart
This report provides the stock availability across all stock items for all health facilities in a province for the last month with a colour legend." 
>> 
>>**Series**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last month"  
>>
>>**Category**  
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Filter**  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Selected items**: select "Stock availability / %"  
>>
>>**Options**  
>>>**Legend**  
>>>>**Use legend for chart colors**: tag (appears as a white tick in a green field)  
>>>>>**Legend type**  
>>>>>>**Select a legend**: tag (appears as a white tick in a green field)  
>>>>>>**Legend**: "Stock availability / %"  
>>>>>>**Show legend key** tag (appears as a white tick in a green field)  

![](image-125.png)

>**7x MSR - Stockout percentage - Province - Column chart**  
>
>**Visualization type**: select "Column"  
>**Name \(*)**: "MSR DV xx - Monthly Stock Reporting / Stockout percentage / Last month / Province / Column chart
This report displays a column chart with the percentage of items with a stockout for the last month across health facilities in a province."
>>  
>>**Series**  
>>>>**Data Type**: "Indicators"  
>>>>**Selected items**: "Stockout percentage"
>>
>>**Category**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 month"  
>>>**Organisation unit**: "User organisation unit"  

![](image-126.png)

>*7x MSR - Stock availability and stockout percentage - Province - Stacked column chart**  
>
>**Visualization type**: select "Stacked column"  
>**Name \(*)**: "MSR - Stock availability and stockout percentage - District - Stacked column chart"  
>**Description**: "MSR DV xx - Monthly Stock Reporting / Stock availability and stockout percentage / Last 12 months / Province  / Stacked column chart
This report displays the stock availability (number of items with non-zero stock on hand divided by the total number of stock items) as percentage for the past 12 months for all health facilities in a province as stacked column chart with a legend."  
>>**Series**  
>>>>**Data Type**: "Indicators"  
>>>>**Indicator group**: "Stockout count"  
>>>>**Selected items**:
>>>>>- "Stock availability / %"  
>>>>>- "Stockout percentage"  
>>
>>**Category**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 month"  
>>>**Organisation unit**: "User organisation unit"  

![](image-124.png)

>**7x MSR - Stockouts - Province - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stockouts - Province - Pivot table"  
>**Description**: "MSR DV xx - Monthly Stock Reporting / Stockout by item / Last 12 months / Province / By item / Pivot table
This report displays a Pivot table with all items and indicating for each item whether it was out of stock for each of the health facilities in a province for the last 12 months".
>>  
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
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Filter**: "Relative periods"  
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stockout Yes/No"  
>>
>>**Options**  
>>>**Legend**  
>>>>**Use legend for chart colors**: tag (appears as a white tick in a green field)  
>>>>>**Legend style**  
>>>>>>**Legend changes background color**: tag (appears as a white tick in a green field)  
>>>>>
>>>>>**Legend type**  
>>>>>>**Select a legend**: tag (appears as a white tick in a green field)  
>>>>>>**Legend**: "Stockout count"  

![](image-128.png)

>**7x MSR - Stockout count - Province - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stockout count - District - Pivot table"  
>**Description**: "MSR DV 49 - Monthly Stock Reporting / Stockout count / Last 12 months / District / Pivot table
This report displays the number of stockouts for all items across a health facility for each of the past 12 months for all health facilities in a district as a Pivot table."  
>>**Columns**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 months"  
>>
>>**Rows**  
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Filter**  
>>>**Data**  
>>>>**Data Type**: "Data elements"  
>>>>**Data element group**: select "[Stock item list] - MSR  
>>>>**Disaggregation**: "Totals only"  
>>>>**Selected items**: select all (->>)  
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stockout Yes/No"  
>>
>>**Options**  
>>>**Legend**  
>>>>**Use legend for chart colors**: tag (appears as a white tick in a green field)  
>>>>>**Legend style**  
>>>>>>**Legend changes background color**: tag (appears as a white tick in a green field)  
>>>>>
>>>>>**Legend type**  
>>>>>>**Select a legend**: tag (appears as a white tick in a green field)  
>>>>>>**Legend**: "Stockout count"  

![](image-129.png)

>**7x MSR - Stockout count - Province - Stacked column chart**  
>
>**Visualization type**: select "Stacked column"  
>**Name \(*)**: "MSR - Stockout count - Province - Stacked column chart"  
>**Description**: "MSR DV xx - Monthly Stock Reporting / Stockout count / Last 12 months / Province / Stacked column chart
This report displays the number of stockouts for each of the past 12 months for each facility in a province as a Stacked column chart."  
>>
>>**Series** 
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Category**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 months"  
>>
>>>**Filter**  
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stockout Yes/No"
>>>
>>>**Data**
>>>>**Data Type**: "Data elements"  
>>>>**Data element group**: select "[Stock item list] - MSR  
>>>>**Disaggregation**: "Totals only"  
>>>>**Selected items**: select all (->>)  

![](image-132.png)

>**7x MSR - Stockout count - Province - Column chart**  
>
>**Visualization type**: select "Column chart"  
>**Name \(*)**: "MSR - Stockout count - Province - Column chart"  
>**Description**: "MSR DV xx - Monthly Stock Reporting / Stockout count / Last month / Province / Column chart
This report displays the number of stockouts for all items across districts in a province for the last month as a Column chart."  
>>**Series**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last month"  
>>
>>**Category**  
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stockout Yes/No"
>>
>>**Filter**  
>>>**Organisation unit**: "User organisation unit"  
>>>**Data**  
>>>>**Data Type**: "Data elements"  
>>>>**Data element group**: select "[Stock item list] - MSR  
>>>>**Disaggregation**: "Totals only"  
>>>>**Selected items**: select all (->>)  
>>
>>**Options**  
>>>**Legend**  
>>>>**Use legend for chart colors**: tag (appears as a white tick in a green field)  
>>>>>**Legend style**  
>>>>>>**Legend changes background color**: tag (appears as a white tick in a green field)   
>>>>>
>>>>>**Legend type**  
>>>>>>**Select a legend**: tag (appears as a white tick in a green field)  
>>>>>>**Legend**: "Stockout count"  

![](image-133.png)

>**7x MSR - Stockout length - Province - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stockout length - District - Pivot table"  
>**Descriptions**: "MSR DV xx - Monthly Stock Reporting / Stockout length / Last 12 months / Province / Pivot table 
This report displays a Pivot table with a count of the number of months (during the past 12 months) during which and item was out of stock at each of the health facilities in a province."  
>>**Columns**  
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stockout Yes/No"  
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Rows**  
>>>**Data**  
>>>>**Data Type**: "Data elements"  
>>>>**Data element group**: select "[Stock item list] - MSR  
>>>>**Disaggregation**: "Totals only"  
>>>>**Selected items**: select all (->>)  
>>
>>**Filter**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 month"  
>>
>>**Options**  
>>>**Data**  
>>>>**Totals**  
>>>>>**Column totals**: tag (appears as a white tick in a green field)  
>>>>>**Column sub-totals**: tag (appears as a white tick in a green field)  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  
>>>**Legend**  
>>>>**Use legend for chart colors**: tag (appears as a white tick in a green field)  
>>>>>**Legend style**  
>>>>>>**Legend changes background color**: tag (appears as a white tick in a green field)  
>>>>>
>>>>>**Legend type**  
>>>>>>**Select a legend**: tag (appears as a white tick in a green field)  
>>>>>>**Legend**: "Stockout count"  

![](image-135.png)

>**7x MSR - Stockout length - Province - Stacked bar chart**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stockout length - District - Bar chart"  
>**Description**: "MSR DV 53 - Monthly Stock Reporting / Stockout length / Last 12 months / District / Stacked bar chart
This report displays a stacked bar chart with the number of stockouts for each item by health facilities in the district during the past 12 months."  
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

![](image-83.png)

xxxxxx

>**7x MSR - Stock coverage time - Province - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock coverage time - District - Pivot table"  
>**Description**: "MSR DV 54 - Monthly Stock Reporting / Stock coverage time / absolute / Last 12 months / District / Pivot table
This report displays a Pivot table by item with the coverage time (stock on hand divided by stock distributed during the last month) for the past 12 months for each health facility in a distrct. A blank field is shown, if either the stock on hand or the stock distribution for a month is zero."  
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
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Filter**  
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stockout coverage"  

![](image-84.png)

>**7x MSR - Stock coverage time distribution - Province - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock coverage time distribution - District - Pivot table"  
>**Description**: "MSR DV 55 - Monthly Stock Reporting / Stock coverage time / distribution / Last 12 months / District / Column chart
This report displays a Pivot table  with the number of items for which the coverage time fell into the respective coverage time bins (stockout, 1 to 12 months, 1-2 and 2-3 years or greater than or equal to 3 years) for all health facilities in a district for each of the past 12 months."  
>>**Columns**  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Indicator group**: select "Stock coverage time"  
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
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Options**  
>>>**Data**  
>>>>**Totals**  
>>>>>**Columns totals**: tag (appears as a white tick in a green field)  
>>>>>**Columns sub-totals**: tag (appears as a white tick in a green field)  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  

![alt text](image-52.png)

>**7x MSR - Stock coverage time distribution - Province - Stacked column chart - Last 12 months**  
>
>**Visualization type**: select "Stacked column"  
>**Name \(*)**: "MSR - Stock coverage time distribution - Last 12 months - District - Stacked column chart"  
>**Description**: "MSR DV 56 - Monthly Stock Reporting / Stock coverage time / distribution / Last 12 months / District / Stacked column chart
For each of the 12 past months, this report displays a stacked column chart with the number of items for each stock coverage time bin (in months and years) separately for each health facility in the district."  
>>**Series**  
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Category**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last 12 month"  
>>>**Data**  
>>>>**Data Type**: "Indicators"  
>>>>**Indicator group**: select "Stock coverage time"  
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

![](image-85.png)

>>**7x MSR - Stock coverage time distribution - Province - Stacked column chart - Last month**  
>
>**Visualization type**: select "Stacked column"  
>**Name \(*)**: "MSR - Stock coverage time distribution - Last month - District - Stacked column chart"  
>**Description**: "MSR DV 29 - Monthly Stock Reporting / Stock coverage time / distribution / Last month / District / Stacked column chart
For the last month, this report displays a stacked column chart with the number of items for each stock coverage time bin (in months and years) separately for each health facility in the district.  
>>**Series**  
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Category**  
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
>>**Filter**  
>>>**Period**: "Relative periods"  
>>>>**Period type**: "Months"  
>>>>**Selected Periods**: "Last month"  

![](image-88.png)

>**7x MSR - Stock discrepancy - Province - Pivot table**  
>
>**Visualization type**: select "Pivot table"  
>**Name \(*)**: "MSR - Stock discrepancy - District - Pivot table"  
>**Description**: ">MSR DV 58 - Monthly Stock Reporting / Stock discrepancy / list / Last 12 months / District / Pivot table
This report displays a list with the positive and negative stock discrepancy of the past 12 months by item for all health facilities in a district.  
+ Stock on hand from the previous month (final stock on hand)  
+ Stock receipt  
- Stock distributed  
- Stock redistributed  
- Stock discard  
- Stock correction  
- Stock on hand"  
>>  
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
>>>**Organisation unit**: "User organisation unit"  
>>
>>**Filter**  
>>>**YOUR DIMENIONS**  
>>>>**Name**: "Monthly stock report"  
>>>>**Selected Items**: "Stock discrepancy count"  
>>  
>>**Options**  
>>>**Data**  
>>>>**Totals**  
>>>>>**Row totals**: tag (appears as a white tick in a green field)  

![alt text](image-54.png)

>**7x MSR - Stock discrepancy count - Province - Stacked column chart**  
>
>**Visualization type**: select "Column"  
>**Name \(*)**: "MSR - Stock discrepancy count - District - Stacked column chart"  
>**Visualization type**: "MSR DV 31 - Monthly Stock Reporting / Stock discrepancy / count / Last 12 months / District / Stacked column chart
This report displays the number of stock discrepancies for the past 12 months separately for each health facility in a district."  
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

![](image-87.png)

## Map App - Analytics

>**1 Health facility**  
>>>- 1 MSR - Health facility  
>
>**2 District level**  
>>**2.1 Statistics**  
>>>- 2 MSR - Health facilities - District  
>
>>**2.2 Indicators**  
>>>- 3 MSR - Stock availability- District  
>>>- 4 MSR - Stock discrepancy count - District  
>>>- 5 MSR - Stockout count - District  
>
>**3 Province level**  
>>**3.1 Statistics**  
>>>- 6 MSR - Health facilities - Province: ok  
>
>>**3.2 Indicators**  
>>>- 7 MSR - Stock availability- Province: ok  
>>>- 8 MSR - Stock discrepancy count - Province: ok  
>>>- 9 MSR - Stockout count - Province: ok
>
>**4 Country**  
>>**4.1 Statistics**  
>>>- 10 MSR - Health facilities - Country  
>
>>**4.2 Indicators**  
>>>- 11 MSR - Stock availability- Country  
>>>- 12 MSR - Stock discrepancy count - Country  
>>>- 13 MSR - Stockout count - Country

### Health facility level

#### Statistics

>**1 MSR - Health facilities - District**  
>
>**Name \(*)**: "MSR - Health facilities - District"  
>**Decription**: "This map displays the location of all health facilities in a district together with the administrative district boundary on a map."  
>
>**Add layer**  
>>**1 Facilities**  
>>>**Organisation Units**  
>>>>**Selection**: "User organisation unit"  
>>>>**Level**: "Facility"  
>>>**Style**  
>>>>**Labels**  
>>>>>**Size**: "15"  
>>>>>**Colour**: select black  
>>>>**Point color**: select preferred colour  
>>>>**Point radius**: "10"  
>>
>>**2 Organisation units**  
>>>**Organisation Units**  
>>>>**Selection**: "User organisation unit"  
>>>>**Level**: "District"  
>>>**Style**  
>>>>**Labels**: tag (appears as a white tick in a green square)  
>>>>>**Size**: "20"  
>>>>>**Colour**: select red  
>>>>**Boundary colour**: select preferred colour  
>
>**2 MSR - Health facility**  
>
>**Name \(*)**: "MSR - Health facility"  
>**Decription**: "This map displays the location of a health facility together with the administrative district boundary on a map."  
>
>**Add layer**  
>>**1 Facilities**  
>>>**Organisation Units**  
>>>>**Selection**: "User organisation unit"  
>>>>**Level**: "Facility" 
>>> 
>>>**Style**  
>>>>**Labels**  
>>>>>**Size**: "15"  
>>>>>**Colour**: select black  
>>>>**Point color**: select preferred colour  
>>>>**Point radius**: "10"  
>>
>>**2 Organisation units**  
>>>**Organisation Units**  
>>>>**Selection**: "User organisation unit"  
>>>>**Level**: "District"  
>>>
>>>**Style**  
>>>>**Labels**: tag (appears as a white tick in a green square)  
>>>>>**Size**: "20"  
>>>>>**Colour**: select red  
>>>>**Boundary colour**: select preferred colour  
>
>**3 MSR - Stock availability - District**  
>
>**Name \(*)**: "MSR - Health facility"  
>**Decription**: "This map displays the stock availability for all health facilities in a district with the administrative district boundary as a timeline for the past 12 months on a map."  
>
>**Add layer**  
>>**1 Stock availability / %**  
>>>**Data**  
>>>>**Item type**: "Indicator"  
>>>>**Indicator group**: "Stock availability / %"  
>>>>**Indicator**: "Stock availability / %"  
>>>>**Aggregation type**: "By data element"  
>>>
>>>**Period**  
>>>>**Period type**: "Relative"  
>>>>**Period**: "Last 12 months"  
>>>>**Display periods**: "Timeline"  
>>>**Organisation Units**  
>>>>**Selection**: "User organisation unit"  
>>>
>>>**Style**  
>>>>**Bubble map**  
>>>>>**High radius**: "15"  
>>>>>**Colour**: select black  
>>>>**Automatic color legend**: tag  
>>>>**Classification**: "Equal intervals"  
>>>>**Classes**: "5"  
>>
>>**2 Organisation units**  
>>>**Organisation Units**  
>>>>**Selection**: "User organisation unit"  
>>>>**Level**: "District"  
>>>
>>>**Style**  
>>>>**Labels**: tag (appears as a white tick in a green square)  
>>>>>**Size**: "20"  
>>>>>**Colour**: select red  
>>>>**Boundary colour**: select preferred colour  
>
>**4 MSR - Stock discrepancy count - District**  
>
>**Name \(*)**: "MSR - Stock discrepancy count - District"  
>**Decription**: "This map displays the stock discrepancy count for all health facilities in a district with the administrative district boundary as a timeline for the past 12 months on a map."  
>
>**Add layer**  
>>**1 Stock discrepancy count**  
>>>**Data**  
>>>>**Item type**: "Indicator"  
>>>>**Indicator group**: "Stock discrepancy count"  
>>>>**Indicator**: "Stock discrepancy count"  
>>>>**Aggregation type**: "By data element"  
>>> 
>>>**Period**  
>>>>**Period type**: "Relative"  
>>>>**Period**: "Last 12 months"  
>>>>**Display periods**: "Timeline"  
>>>
>>>**Organisation Units**  
>>>>**Selection**: "User organisation unit"  
>>>
>>>**Style**  
>>>>**Bubble map**  
>>>>>**High radius**: "15"  
>>>>>**Colour**: select black  
>>>>
>>>>**Automatic color legend**: tag  
>>>>**Classification**: "Equal intervals"  
>>>>**Classes**: "5"  
>>
>>**2 Organisation units**  
>>>**Organisation Units**  
>>>>**Selection**: "User organisation unit"  
>>>>**Level**: "District"  
>>>
>>>**Style**  
>>>>**Labels**: tag (appears as a white tick in a green square)  
>>>>>**Size**: "20"  
>>>>>**Colour**: select red  
>>>>**Boundary colour**: select preferred colour  
>
>**5 MSR - Stockout count - District**  
>
>**Name \(*)**: "MSR - Stockout count - District"  
>**Decription**: "This map displays the stockout count for all health facilities in a district with the administrative district boundary on a map as a timeline for the past 12 months."  
>
>**Add layer**  
>>**1 Stockout count**  
>>>**Data**  
>>>>**Item type**: "Indicator"  
>>>>**Indicator group**: "Stockout count"  
>>>>**Indicator**: "Stockout count"  
>>>>**Aggregation type**: "By data element"  
>>> 
>>>**Period**  
>>>>**Period type**: "Relative"  
>>>>**Period**: "Last 12 months"  
>>>>**Display periods**: "Timeline"  
>>>
>>>**Organisation Units**  
>>>>**Selection**: "User organisation unit"  
>>>
>>>**Style**  
>>>>**Bubble map**  
>>>>>**High radius**: "15"  
>>>>>**Colour**: select black  
>>>>
>>>>**Automatic color legend**: tag  
>>>>**Classification**: "Equal intervals"  
>>>>**Classes**: "5"  
>>
>>**2 Organisation units**  
>>>**Organisation Units**  
>>>>**Selection**: "User organisation unit"  
>>>>**Level**: "District"  
>>>
>>>**Style**  
>>>>**Labels**: tag (appears as a white tick in a green square)  
>>>>>**Size**: "20"  
>>>>>**Colour**: select red  
>>>>**Boundary colour**: select preferred colour  

## Dashboard App - Analytics

>**1 Health facility level**  
>>- 1 MSR - Visualization library - Health facility level  
>>- 2 MSR - Health facility level - Analytics  
>
>**2 District level**  
>>- 3 MSR - Visualization library - District level  
>>- 4 MSR - District level - Analytics  
>
>**3 Regional level**  
>>- 5 MSR - Visualization library - Province level  
>>- Selection  
>
>**4 National level**  
>>- Library  
>>- Selection  
>
>**5 Thematic dashboards**  
>>- Essential LMIS KPIs  
>>- Xx

### Health facility level

>**1 MSR - Visualization library - Health facility level**  
>
>**Dashboard title**: "MSR - Visualization library - Health facility level"  
>**Dashboard description**: "Library of all available LMIS visualizations for the health facility level in the order of their documentation. These are intended for immediate use or adapting to national policies and requirements."  
>**Search for visualizations, reports and more**  
>>- MSR - Stock receipt - Pivot table  
>>- MSR - Stock distribution - Pivot table  
>>- MSR - Stock redistribution - Pivot table  
>>- MSR - Stock discard - Pivot table  
>>- MSR - Stock on hand - Pivot table  
>>- MSR - Stock correction - Pivot table  
>>- MSR - Stock report complete - Last 3 months - Pivot table  
>>- MSR - Stock report complete - Last 12 months - Pivot table  
>>- MSR - Stock report complete - Column chart  
>>- MSR - Coefficient of Variation x 10 - Pivot table  
>>- MSR - Coefficient of Variation x 10 - Stacked bar chart  
>>- MSR - Coefficient of Variation x 10 - Column chart  
>>- MSR - Stock availability - Pivot table  
>>- MSR - Stock availability - Bar chart  
>>- MSR - Stock availability - Single value chart  
>>- MSR - Stock availability - Gauge chart  
>>- xx MSR - Stockout percentage - Bar chart
>>- xx MSR - Stock availability and stockout percentage - Bar chart
>>- MSR - Stockouts - Stacked column chart  
>>- MSR - Stockout count - Pivot table  
>>- MSR - Stockout count - Column chart  
>>- MSR - Stockout count - Single value chart  
>>- MSR - Stockout length - Pivot table  
>>- MSR - Stockout length - Bar chart  
>>- MSR - Stock coverage time - Pivot table  
>>- MSR - Stock coverage time distribution - Pivot table  
>>- MSR - Stock coverage time distribution - Last 12 months - Column chart  
>>- MSR - Stock coverage time distribution - Last month - Column chart  
>>>- xx MSR - Stock coverage time ranges - Last month
>>>- xx MSR - Stock coverage time ranges - Last 12 months
>>- MSR - Stock discrepancy - Pivot table  
>>- MSR - Stock discrepancy count - Column chart  
>>>- xx MSR - Stock discrepancy count - Perecentage - Column chart  
>
>**2 MSR - Health facility level - Analytics**  
>
>**Dashboard title**: "MSR - Monthly Stock Reporting - Health facility level"  
>**Dashboard description**: "This dashboard presents a selection of the DHIS2-LMIS Visualization library - MSR - Health facility level and is intended as a suggestion for customizing dashboards to national policies and requirements."  
>**Search for visualizations, reports and more**  
>>- MSR - Stock availability - Single value chart  
>>- MSR - Stock availability - Bar chart  
>>- MSR - Stockout count - Single value chart  
>>- MSR - Health facility  
>>- MSR - Stockouts - Stacked column chart  
>>- MSR - Stockout length - Bar chart  
>>- MSR - Stock coverage time distribution - Last month - Column chart  
>>- MSR - Coefficient of Variation x 10 - Bar chart  
>>- MSR - Stock report complete - Last 3 months - Pivot table  
>>- MSR - Stock discrepancy count - Column chart  

![](image-89.png)

### District level

>**3 MSR - Visualization library - District level**  
>
>**Dashboard title**: "MSR - Visualization library - District level"  
>**Dashboard description**: "Library of all available LMIS visualizations for the district in the order of their documentation. These are intended for immediate use or adapting to national policies and requirements."  
>**Search for visualizations, reports and more**  
>>>- MSR - Stock receipt - District - Pivot table  
>>>- MSR - Stock distribution - District - Pivot table  
>>>- MSR - Stock redistribution - District - Pivot table  
>>>- MSR - Stock discard - District - Pivot table  
>>>- MSR - Stock on hand - District - Pivot table  
>>>- MSR - Stock correction - District - Pivot table  
>>>- MSR - Stock report complete - Last 3 months - District - Pivot table  
>>>- MSR - Coefficient of Variation x 10 - District - Pivot table  
>>>- MSR - Coefficient of Variation x 10 - District - Stacked bar chart  
>>>- MSR - Coefficient of Variation x 10 - District - Column chart  
>>>- MSR - Coefficient of Variation x 10 distribution - District - Pivot table  
>>>- MSR - Coefficient of Variation x 10 distribution - District - Stacked Column chart- Last 12 months  
>>>- MSR - Coefficient of Variation x 10 distribution - District - Column chart  - Last month  
>>>- MSR - Stock availability - District - Pivot table  
>>>- MSR - Stock availability - District - Column chart  
>>>- MSR - Stock availability - District - Column chart  
>>>- **xx** MSR - Stockout percentage - District - Column chart
>>>- **xx** MSR - Stock availability and stockout percentage - District - Stacked column chart
>>>- MSR - Stockouts - District - Pivot table  
>>>- MSR - Stockout count - District - Pivot table  
>>>- MSR - Stockout count - District - Column chart  
>>>- MSR - Stockout count - District - Single value chart  
>>>- MSR - Stockout length - District - Pivot table  
>>>- MSR - Stockout length - District - Stacked bar chart  
>>>- MSR - Stock coverage time - District - Pivot table  
>>>- MSR - Stock coverage time distribution - District - Pivot table  
>>>- MSR - Stock coverage time distribution - District - Stacked column chart- Last 12 months   
>>>- MSR - Stock coverage time distribution - District - Stacked column chart - Last month  
>>>- **xx** MSR - Stock coverage time ranges - District - Last month
>>>- **xx** MSR - Stock coverage time ranges - District - Last 12 months
>>>- MSR - Stock discrepancy - District - Pivot table  
>>>- MSR - Stock discrepancy count - District - Stacked column chart  
>>>- **xx** MSR - Stock discrepancy count - Percentage - District - Column chart  
>>>- MSR - Health facilies - District - Map  
>>>- MSR - Stock availability - District - Map  
>>>- MSR - Stock discrepancy count - District - Map  
>>>- MSR - Stockout count - District - Map  
>
>**4 MSR - District level - Analytics**  
>
>**Dashboard title**: "MSR - District level - Analytics"  
>**Dashboard description**: "This dashboard presents a selection of the MSR - Visualization library - District level and is intended as a suggestion for customizing dashboards to national policies and requirements."  
>**Search for visualizations, reports and more**  
>>>- MSR - Stockout count - District - Single value chart  
>>>- MSR - Stock availability - District - Column chart  
>>>- MSR - Stock coverage time distribution - Last month - District - Stacked column chart  
>>>- MSR - Health facilities - District  
>>>- MSR - Stock availability- District  
>>>- MSR - Stock discrepancy count - District  
>>>- MSR - Stockout count - District  
>>>- MSR - Stock availability - District - Bar chart  
>>>- MSR - Stockout count - District - Column chart  
>>>- MSR - Stockout length - District - Stacked bar chart  
>>>- MSR - Stock coverage time distribution - Last 12 months - District - Stacked column chart  
>>>- MSR - Coefficient of Variation x 10 - District - Stacked bar chart  
>>>- MSR - Coefficient of Variation x 10 distribution - Last month - District - Column chart  
>>>- MSR - Coefficient of Variation x 10 - District - Stacked bar chart  
>>>- MSR - Stock report complete - Last 3 months - District - Pivot table  

![](image-90.png)
![](image-91.png)

### Province level

>**5 MSR - Visualization library - Province level**  
>
>**Dashboard title**: "MSR - Visualization library - Province level"  
>**Dashboard description**: "Library of all available LMIS visualizations for the province in the order of their documentation. These are intended for immediate use or adapting to national policies and requirements."  
>**Search for visualizations, reports and more**  
>>>- MSR - Stock receipt - Province - Pivot table  
>>>- MSR - Stock distribution - Province - Pivot table  
>>>- MSR - Stock redistribution - Province - Pivot table  
>>>- MSR - Stock discard - Province - Pivot table  
>>>- MSR - Stock on hand - Province - Pivot table  
>>>- MSR - Stock correction - Province - Pivot table  
>>>- MSR - Stock report complete - Last 3 months - Province - Pivot table  

