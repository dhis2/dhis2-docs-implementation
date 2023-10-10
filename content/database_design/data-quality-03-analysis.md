# Assessing data quality

DHIS2 has a wide range of functions for assessing data quality, available across different apps and functions, and this section gives and overview of this functionality. It is structured according to the type of data quality metric:


* Completeness and timeliness of data
* Consistency of data across related variables
* Consistency of data over time

## Completeness and timeliness

_Completeness_ of reporting gives an indication of how much of the expected data has actually been reported. In DHIS2, most of the completeness checks are based on assessing the _data set_ completeness, i.e. how many data sets (forms) have been submitted by organisation unit and period. The timeliness calculation is based on a system setting called Days after period end to qualify for timely data submission. 

The built-in functionality for completeness and timeliness in DHIS2, e.g. what is built into the Data Visualizer, Reports and Maps application, refers to _data set _reporting rates. However, we can also configure DHIS2 to assess the proportion of facilities that are _consistently reporting_, as well as the completeness of individual data elements.


### Data set completeness and timeliness

The completeness reports will also show which organisation units in an area are reporting on time, and the percentage of timely reporting facilities in a given area. 

Data set completeness and timeliness can be reviewed in the reports app as well as  core visualization apps (Data visualizer and Maps). The core visualization apps allow for you to review completeness and timeliness in more significant detail across multiple org units and periods; however the reports app has a simplified user experience that has been validated by its widely observed use in comparison to other apps within DHIS2. 


#### Using Data Visualizer

In data visualizer, you will be able to review dataset completeness and timeliness measures similar to the reports app; however you are now free to select multiple data sets, periods and organisation units at the same time. You can also add completeness and timeliness measures to charts and tables that include other data, such as health service delivery data, to verify that the data you are reviewing is representative of the situation within the country you are working with. This gives you much more flexibility when compared to the reports app; however the additional options can make it less accessible compared to the reports app. Ideally, these visualizations are pre-made and placed on a dashboard for users to review routinely; however it is useful for a subset of users to know how to create outputs using these metrics within the data visualizer.

Within data visualizer, select your “Data” input, along with “Data Set” as the data type. This will allow you to search or add filters for the data set and metric type that you want to add to your visualization.

![](resources/images/dq_image94.png)

Here is an example of a chart comparing BCG doses given with the reporting rate of the immunization data set

![](resources/images/dq_image52.png)

We can quickly note that several of the districts have reporting rates &lt; 80%, and therefore the data being displayed may not be fully representative of the situation in the country. It may be important to verify this through a more detailed analysis reviewing the facilities affecting this value and/or using data element completeness [LINK]

We can go through some examples of tables and charts you could potentially create when reviewing completeness and timeliness within the data visualizer app

**Example 1** : Pivot Table comparing completeness and timeliness over several datasets, periods and organisation units

Select Pivot table as the output type

![](resources/images/dq_image115.png)


* Select data and modify the data type to Data Sets
* Select the metrics you want to add to your table

![](resources/images/dq_image14.png)

Either hide or update the data selector and proceed to modify your periods and organisation units

![](resources/images/dq_image62.png)

![](resources/images/dq_image76.png)

After all of your selections are made modify your layout and update your table

![](resources/images/dq_image107.png)

You should now be able to see the table with your inputs selected. 

![](resources/images/dq_image57.png)


**Example 2** : Line chart comparing completeness and timeliness over several periods

Select line as the output type

![](resources/images/dq_image19.png)

* Select data and modify the data type to Data Sets
* Select the metrics you want to add to your chart. Only one is selected here but you can use as many as necessary.

![](resources/images/dq_image84.png)

* Either hide or update the data selector and proceed to modify your periods and organisation units.

![](resources/images/dq_image62.png)
![](resources/images/dq_image76.png)

* Modify the layout of your chart and update when ready

![](resources/images/dq_image1.png)

**Example 3** : A 2-axes chart comparing service data with dataset completeness

Select column as the output type

![](resources/images/dq_image35.png)

* Select data and modify the data type to Data Sets. Select the metric(s) you want to add to your chart

![](resources/images/dq_image84.png)

* Change the data type. Data elements are used in this example, but you are able to combine the completeness and timeliness metric with any of the existing DHIS2 data types in data visualizer

![](resources/images/dq_image114.png)


* Either hide or update the data selector and proceed to modify your periods and organisation units.

![](resources/images/dq_image40.png)
![](resources/images/dq_image76.png)

* Modify the layout of your chart and update when ready

![](resources/images/dq_image17.png)

* To move one of the items to the 2nd axes, select Options, then Series. Modify the data items to appear on the axes you want using the correct visualization type and update your chart

![](resources/images/dq_image82.png)

![](resources/images/dq_image36.png)


* Additional options, such as ordering the chart items and adding chart titles can then be added to the chart using the options button within the visualizer app

![](resources/images/dq_image27.png)
![](resources/images/dq_image109.png)
![](resources/images/dq_image52.png)

#### Using the reports app

In order to review completeness and timeliness within the reports app, navigate to apps -> Reports

![](resources/images/dq_image67.png)

From here, select “Get Report” under the Reporting Rate Summary heading

![](resources/images/dq_image42.png)

Start by selecting your inputs:

1. Which organisation units you want to review. You select the parent organsation unit, and all of the children within that parent will be selected (along with the overall result for the organisation unit selected). 

2. Select the data set you want to review completeness and timeliness information.

3. Selecting the reporting period, followed by the period itself/

![](resources/images/dq_image96.png)

If you select Show more options, you can use an organisation unit group set to select organisation unit groups to further filter your report; however this is optional.

![](resources/images/dq_image111.png)

After you have selected all of your inputs, select “Get report” to produce the report.

![](resources/images/dq_image13.png)

This will produce a report with the following columns

1. Name: The name of the organisation unit

2. [Dataset name] - Actual reports: This is the number of reports within the period you selected that were marked as complete

3. [Dataset name] - Expected reports: This is the number of expected reports within the period you selected. This is automatically calculated based on the time dimension and the assignment of the data set to orgunits.

4. [Dataset name] - Reporting rate: This is the reporting rate: actual reports reports/expected reports x 100%

5. [Dataset name] - Actual reports on time: This is the number of reports within the period you selected that were marked as complete **_within the timeframe that is defined as “on time” for the selected dataset_**

6. [Dataset name] - Reporting rate on time : This rate = actual reports reports on time /expected reports x 100%

#### Configuring Data Set Completeness

Data Set completeness is based on the organisation unit assignment of your dataset. This determines the value for your expected reports based on the periodicity of the dataset. This is configured within the maintenance app

Navigate to maintenance -> data set -> and select or create the intended data set. Within this data set scroll to the very bottom to find the organisation unit assignment


![](resources/images/dq_image99.png)

You can assign your dataset to organisation units by selecting them individually or using levels or groups. 

The important factor to consider here is to make sure that the dataset **_IS NOT_** assigned to any organisation units that are not expected to report on the dataset. This is because the number of expected reports will be consistently incorrect. For example, in the above screenshot this dataset is assigned to 185 organisation units. Let us say that this dataset is reported on monthly. Each month, 185 submissions will be expected. If only 160 organisation units report on this data set, your completenesss will never exceed 160/185 x 100% = 86% in any given month. This is because those additional 25 organisation units will never fill in the data set as they are not meant to. This is a key consideration when assigning your dataset to organisation units correctly. 


#### Configuring Data Set Timeliness

Timeliness is also configured within the maintenance app when creating or editing a dataset, using the field “days after period to qualify for a timely submission.”

![](resources/images/dq_image43.png)

In the above example, the data set is collected monthly and the timeliness is set to 15. This 
means that the data set must be completed within 15 days after the end of the previous month in order to qualify as a timely submission.


### Data element completeness

Data set completeness and timeliness are useful measures to monitor the overall reporting performance of the system. However, there are several conditions that needs to be met for the data set completeness to give a representative indication of completeness of the data within the data set:


* Users must remember to mark the data set as complete when data has been entered

* User must actually enter data in the form before marking it as complete

* Assignment of data set to orgunits (facilities) must be correct 

Often, one or more of these conditions are _not_ met, which means that it is necessary to also do additional analysis of the reporting completeness. In this section we show 



* how to analyse the proportion of facilities that _consistently report_ data element values over a time period, and

* how to analyse completeness of an individual data element

Common for the approaches outlined is that they require us to configure additional metadata for each variable we want to assess. In practice, this means that they can only be implemented for a limited set of data elements. The implementation section[LINK] below discusses this further.


#### Orgunits consistently reporting

Assessing the proportion of facilities that _consistently report_ over a time period is a completeness metric that adds another dimension to our understanding of data completeness compared to the data set completeness. In cases where a subset of facilities only report intermittently, it is useful to know what percentage of health facility that _consistently report_ over a certain time period, such as one year. For example, if in one month a dispensary reports and a district hospital does not, and the next month it is opposite, the completeness numbers will remain constant but the data on service delivery is likely quite different within that district.

We defined facilities consistently reporting as: 100 X (Facilities reporting every period within a time period)/(Facilities reporting in any period within a time period)

This check could in principle be done based both on the overall data set reporting, or based on a data element within the data set. In the example provided here, we show how to do the latter, since assessing this at the data set level could be achieved by looking at the annual data set reporting rate for individual facilities.


#### Configuring reporting consistency

We will show how to make an indicator for _percentage of orgunits (facilities) consistently reporting_ for one particular data element. It is not possible to calculate this as an indicator directly, so we will use predictors.

This means that we will configure:

Data elements:

* Facilities reporting in all periods within the time period
* Facilities reporting in any period within the time period

Predictors:

* Facilities reporting in all periods within the time period
* Facilities reporting in any period within the time period

Indicator:

* Facilities consistently reporting the data element in the time period (%), for example “ANC 1 - facilities consistently reporting last 12 months (%)

In addition, visualisations should be made and shared with users, and we suggest organising the metadata in groups, and potentially also a data set for the data elements. Whether these groups should be in dedicated Data quality groups or part of existing groups for each health programme (or both) depends on the configuration standards and SoPs in a particular implementation; for clarity, the [demo instance](demos.dhis2.org/hmis) where an example of this configuration can be reviewed uses dedicated groups.

In the following, we will use ANC 1 (i.e. pregnant women making their first antenatal care visit) as an example.


#### Creating data elements

Data elements are needed to hold the aggregate data values generated by the two predictors doing the actual calculations for this indicator. The data elements should be named according to local naming convention, be in the aggregate domain, and (in most cases) have value type Positive or zero integer. 

![](resources/images/dq_image43.png)

For ANC 1, we could create these two data elements:

* DQ - ANC 1 orgunits reported in all the last 12 Months
* DQ - ANC 1 orgunits reported in any of the last 12 months


#### Creating predictors

Next, we must set up two predictors to calculate the data values for our two data elements. Documentation on predictors is available here [LINK]

1. Provide name (required), short name, code and description to the predictor

   ![](resources/images/dq_image95.png)

2. Specify the output data element; this should refer to the data elements we created in the previous step

   ![](resources/images/dq_image72.png)

3. Specify the period type of the predictor; this should match the period type of the data element we are assessing. In this example, we are assessing ANC 1, which we assume is collected monthly.

    ![](resources/images/dq_image70.png)

4. Specify the organisation unit level. For this data quality indicator, this should be the level at which data is collected, typically the facility level.  \
We also need to make a selection in the “Organisation units providing data”, which should be “At selected level(s) only”, since we are calculating the consistently of reporting only based on the level we have selected as the data collection level.

    ![](resources/images/dq_image23.png)

5. Next, we must specify the Generator. This is where we define the actual expression for calculating the consistency of reporting.

    ![](resources/images/dq_image49.png)

    1. To calculate the predictor for “number of orgunits reported in _all_ the last 12 Months”, we use the formula “if( sum( if(isNotNull([data element]), 1, 0)) == 12, 1, 0)”
        1. **if**(**isNotNull(**[data element]**), 1, 0)**, and produces a 1 if a value exists, and 0 otherwise
        2. **sum**( if(isNotNull([data element]), 1, 0)** )** adds up the number of periods in which the if(isNotNull()) statement returns 1. So it adds 1 for each period in which a value has been reported.
        3. **if**(sum(if(isNotNull([data element]), 1, 0))** == 12, 1, 0) **checks whether the number of periods that has been added up by sum() equals the number of periods we as assessing. If we are assessing a monthly data set for a 1-year period, we comper this to 12. If the number of periods with a value  matches 12, the predictor produces a 1. This indicates that the organisation unit has reported in all the previous 12 months.

    
        ![](resources/images/dq_image80.png)


    2. To calculate the predictor for “number of orgunits reported in _any _of the last 12 Months”, we use the formula “if(isNotNull([data element]),1,0)”
        4. **if**(**isNotNull(**[data element]**), 1, 0)**, and produces a 1 if a value exists in any of the periods, and 0 otherwise. 1 indicates that the organisation unit has reported in _at least one _of the previous 12 months.

       ![](resources/images/dq_image45.png)


6. Finally, we need to specify the sample and skip counts. Sample skip test should not be set. Sequential sample count should be set to the number of periods we want to calculate the consistency of reporting for. For monthly data that we want to assess for one year, we should set the Sequential sample count to 12. This means that the 12 months preceding the period which we are generating the predictor for will be checked.  \
Annual sample count and sequential sample count should both be 0. 

   ![](resources/images/dq_image77.png)

#### Creating the indicator

When the two data elements and two predictors have been defined, we can define the indicator that produces the actual data quality metric we are interested in: the percentage of facilities that have consistently reported a given data element in the last year. 


1. The indicator name, shortName, code and description should be specified according to local naming and coding conventions.

![](resources/images/dq_image53.png)


2. The indicator should** not** be annualized, and the indicator type should be Percentage (factor = 100)

3. The numerator expression should be Facilities that have reported in all the previous 12 months (assuming the data is monthly)

4. The denominator expression should be Facilities that have reported in any of the previous 12 months (assuming the data is monthly)

![](resources/images/dq_image28.png)
![](resources/images/dq_image54.png)

After predictors have been generated and aggregate analytics have been run (see below [LINK]), the indicator is available for use in the Data visualizer and Maps applications..

#### Calculating data element completeness

In some DHIS2 implementations it has been observed that reporting is inconsistent for all data elements in a data set. DHIS2 by default only assesses the reporting rates of data sets and not of the individual data elements in that data set. The goal of a data element reporting rate is to assess the reporting consistency of a single value. This is for aggregate data elements only.

A reporting rate is: 100 x (Number of received values / Number of expected values)

To calculate the reporting rate for a data element we have to define an indicator with the numerator (number of received values) and the denominator (number of expected values), and with a factor of 100 (percentage indicator type). While the numerator is always the count of data values, there are various options for defining the denominator, and which one of these is appropriate must be decided based on the local situation.

How data element completeness is configured in DHIS2 also depends on the DHIS2 version: some ways of defining the numerator and denominator requires that predictors are used as an intermediate step in the calculation, in particular in 2.37 and below. Note that predictors will need to be scheduled to run on the server, see the final section[LINK] for guidance on instructions.

#### Configuring the numerator - values received

We first review how to define the _numerator_ of our data element completeness indicator. As explained above, this will always be the count of data values that has been reported for a certain data element. There are nonetheless a few things that must be considered.

**Zero value storage**

For several reasons [link], it is generally recommended to _not_ store zero values being reported for data elements unless there is a clear reason for it (for example the “aggregation type” being of a type where zeros are relevant, such as average). This has implications when reviewing data element completeness, since for data elements where zero values are not entered and stored we cannot differentiate between facilities that have 0 to report and facilities that have not reported. One option is to enable zero values storage for the specific data elements where you want to define data element completeness indicators. However, this is difficult to implement in practice since data entry users must then know for what specific data input fields a 0 is expected. A more practical option is to focus configuration of data element completeness on data elements where all or almost all facilities are expected to have a value > 0 to report, and being explicit in descriptions of the indicator and visualizations that reaching 100% data element completeness is not necessarily expected.

**Disaggregations**

How to take into consideration any disaggregations that might be applied to the data element is critical, because it affects how to configure the indicator expressions and also whether use of predictors are needed or not. For example, if a data element for a child vaccination such as BCG that is disaggregated by &lt; 1 year and 1+ year, should the data element completeness be based on:

* One specific category option combination. For example, “reported” means having reported for “BCG doses &lt; 1 year”.

* Both category option combinations. For example, “reported” means having reported for “BCG doses &lt; 1 year” or “BCG doses &lt; 1 year”.

* Either of category option combination. For example, “reported” means having reported for “BCG doses &lt; 1 year” or “BCG doses &lt; 1 year”

The decision on this depends on the specific data element and disaggregation. For child vaccinations, the target age group for vaccinations is &lt; 1 year, and it might be common that there is no data to report in the 1+ year age group. Thus it would make sense to define the completeness for &lt; 1 year specifically. On the other hand, if “Confirmed malaria cases” is disaggregated into &lt; 5 years and 5+ years, facilities can be expected to have a values for each age group and it would make sense to consider both values to be expected; in this case, the denominator must be adjusted accordingly.

The same consideration applies when data sets are disaggregated with an attribute option combination[LINK], though this is less common.

The following table outlines the alternative approaches for configuring the numerator, considering whether the data element is disaggregated, how to evaluate completeness of disaggregations when applicable, and whether they can be configured directly in indicators or first using predictors.

|                                                                                                                        	| 2.38 and above                                                                           	| 2.37 and below 	|
|------------------------------------------------------------------------------------------------------------------------	|------------------------------------------------------------------------------------------	|----------------	|
| Data element with no disaggregation                                                                                    	| Indicator (with subExpression)                                                           	| Predictor      	|
| Data element with disaggregation - analysis of one category option combo                                               	| Indicator (with subExpression)                                                           	| Predictor      	|
| Data element with disaggregations - counting each category option combo with a value as “reported”                     	| Indicator (with subExpression); multiply denominator with number of categoryOptionCombos 	| Predictor      	|
| Data element with disaggregation - all category option combos must have value for data element to be “reported”        	| Predictor                                                                                	| Predictor      	|
| Data element with disaggregation - if any category option combos has a value the data element is considered “reported” 	| Predictor                                                                                	| Predictor      	|





We explain first how to configure the options that can be done with indicators directly, and then we show the configuration with predictors, 


#### Numerator configuration with indicator and subExpressions

As explained above, the numerator should be the count of values for a data element (with or without disaggregation). From version 2.38, this can be done directly in an aggregate indicator using a subExpression with a isNotNull conditional statement in the expression. This will return a 1 value for any time there is a number (including zero) entered for this data element. An example is given below.

![](resources/images/dq_image39.png)

* **if(isNotNull(**[data element id]**), 1, 0) **will return 1 for every value for that data element, 0 otherwise.
    * If the data element has no disaggregation, it will return 1 or 0 depending on whether data has been reported.

    * If the _id_ specified inside isNotNull() includes a specific category option combination (for example isNotNull(#{TWWbtMMWD51.JKuWbG5bWAu})), it will return 1 or 0 depending on whether data has been reported for that specific data element + category option combination

    * If the data element is disaggregated, but no category option combination is specified, it will return 1 _for each data value across category option combination_. So if a data element has a &lt; 1 year, 1+ year disaggregation and a facility has reported a value for both, the expression will return 2. In this case, the denominator must be adjusted accordingly.

* **subExpression** if(isNotNull([data element id])** ) **ensures that the if(isNotNull()) statement is executed at the level of data collection, before the expression is aggregated over time and up the organization unit hierarchy.

To summarise, what should be used as a expression for the numerator is: 

|                                                                                                    	| Method                                  	| Expression with example data element                             	|
|----------------------------------------------------------------------------------------------------	|-----------------------------------------	|------------------------------------------------------------------	|
| Data element with no disaggregation                                                                	| Indicator                               	| subExpression( if( isNotNull(#{TWWbtMMWD51}), 1, 0))             	|
| Data element with disaggregation - analysis of one category option combo                           	| Indicator                               	| subExpression( if( isNotNull(#{TWWbtMMWD51.JKuWbG5bWAu}), 1, 0)) 	|
| Data element with disaggregations - counting each category option combo with a value as “reported” 	| Indicator; denominator must be adjusted 	| subExpression( if( isNotNull(#{TWWbtMMWD51}), 1, 0))             	|


#### Numerator configuration - with predictor

Versions 2.37 and below does not support subExpressions in indicators. For this you have to make a predictor that uses isNotNull() conditional statements in the generator. 

As explained above, whether the data element is disaggregated or not, and how to account for the disaggregation in terms of completeness dictates exactly how the Generator expression should be defined. The following table shows each of the alternative approaches and the corresponding generator expression to use:


|                                                                                                                        	| Generator expression with sample data element                                                        	|
|------------------------------------------------------------------------------------------------------------------------	|------------------------------------------------------------------------------------------------------	|
| Data element with no disaggregation                                                                                    	| if( isNotNull(#{OWk2WulfJYQ}), 1, 0)                                                                 	|
| Data element with disaggregation - analysis of one category option combo                                               	| if( isNotNull(#{TWWbtMMWD51.JKuWbG5bWAu}), 1, 0)                                                     	|
| Data element with disaggregations - counting each category option combo with a value as “reported”                     	| if( isNotNull(#{TWWbtMMWD51.JKuWbG5bWAu}), 1, 0) +  if( isNotNull(#{TWWbtMMWD51.UIQxmxgioxH}), 1, 0) 	|
| Data element with disaggregation - all category option combos must have value for data element to be “reported”        	| if(  isNotNull(#{TWWbtMMWD51.JKuWbG5bWAu}) &&  isNotNull(#{TWWbtMMWD51.UIQxmxgioxH}),  1, 0)         	|
| Data element with disaggregation - if any category option combos has a value the data element is considered “reported” 	| if( isNotNull(#{OWk2WulfJYQ}), 1, 0)                                                                 	|


When you have decided on what appropriate approach, follow these steps to make the predictor:


5. Make your output data element.

6. Assign the output data element to your predictor.

7. Set the period type (typically monthly).

8. Assign the org unit level for the analysis (typically facility level).

9. Configure the generator as below.

10. Set the sequential sample count to 0

11. Set the annual sample count to 0

12. Leave the sequential skip count blank

13. Define the Generator, using one of the expressions outlined above.

![](resources/images/dq_image8.png)


14. Create a predictor group and add this predictor to that group.


#### Configuring the denominator - expected values

While the numerator for a data element completeness indicator is always the count of data values received (with some variations in how disaggregations are managed), there are several ways to define the “expected reports received” denominator. These options include:


1. Count of orgunits to which the data set(s) the data element is part of is assigned

2. Count of orgunits for which the data set(s) the data element is part of has been marked as completed (reported)

3. Count of reported values of another data element that is part of the same data set

4. Count of orgunits that have previously reported on the data element itself

![](resources/images/dq_image38.png)

Which of these options are appropriate depends several contextual factors, such as how correct and updated the assignment of  data set is, and whether the purpose is to look at the overall completeness of the data element (how much of the true figure do I capture) or the completeness within a data set (how completely are facility staff and data entry clerks filling in the reporting form). Each option is outlined below, with instructions for configuration both in 2.38 and above, and 2.37 and below.


##### Option 1 - Count of orgunits to which the data set(s) the data element is part of is assigned

The first option is to use the assignment of the data set that the data element is part of as the basis for calculating completeness. This measure is quite similar to how the data set completeness (reporting rates) described above [LINK] works. This option is relatively straightforward to configure, since the “expected reports” of a data set is available directly to use in indicator expressions. The main limitation of using the data set expected reports as the denominator for data element completeness is that it assumes that data set assignment is correct and kept up to date.

To use this as a denominator, simply choose the _expected reports_ variable that is available when configuring the indicator denominator:


![](resources/images/dq_image93.png)

The denominator expression is R{[data set id].EXPECTED_REPORTS}, for example R{tQc4Gv2Jwco.EXPECTED_REPORTS}

Special care needs to be taken in cases where the same data element is reported in multiple data sets. If the data sets are not used in the same organization units, adding up the expected reports for each data set will give a correct denominator. However, if there is a risk that the same organization units will have two data sets assigned with the data element included, this option will not provide a reliable denominator.


##### Option 2 - Count of orgunits for which the data set(s) has been received

Option 2 is similar to option 1, but instead of using the actual reports as denominator rather than expected reports. Choosing actual reports will give an indicator that assesses the completeness of the data element among the organization units that reported, i.e. a measure of how often a particular data element is filled in the data sets that are submitted. 

![](resources/images/dq_image103.png)

![](resources/images/dq_image71.png)


Again, special care needs to be taken in cases where the same data element is reported in multiple data sets. If the data sets are not used in the same organization units, adding up the expected reports for each data set will give a correct denominator. However, if there is a risk that the same organization units will have two data sets assigned with the data element included, this option will not provide a reliable denominator.


##### Option 3 - Count of reported values of another data element

This option is based on using the number of reported values for another data element as the expected values in the completeness calculation. This other data element can be chosen based on different criteria, described below. Note that when looking at data element completeness based on other data elements, the results should be analyzed together with the overall data set completeness.

_Based on data element in the same data set_

This option is similar to the above, but using a data element reported in the same data set or data set section as the data element you are calculating the reporting rate for (numerator) - without necessarily being logically related. With this approach, you should choose a data element that is always (or often) reported on in the data set. For example, in a data set with maternal health data, more health facilities will likely report on a data element for “Antenatal care first visits” than for “Assisted delivery”, and “Antenatal care first visits” would therefore be a better estimation of the number of expected reports.

_Based on core indicator_

If the data element you want to get a reporting rate for is used in a key performance indicator calculation with routinely reported data in the denominator, using the count of values reported for the denominator to calculate completeness is recommended. This option is not viable if the data element is not used in an indicator calculations, or if the denominator is based on a population estimate or other value that is not reported with the same periodicity as the numerator. 

As an example, consider the indicator Suspected cases tested for Malaria (%):

100 x (Malaria tested cases / Suspected cases)

In this case, it can be useful to look at the completeness of Malaria cases tested with the count of Suspected cases as denominator. 

The advantage of this option is that it gives a good indication of the completeness/consistency of data used to calculate a particular core indicator. 

_Based on related data element_

This option is similar to the above, but using a data element that is closely related to the data element in the numerator to calculate the denominator. For example, if you are looking at a reporting rate for inpatient malaria cases under 5 years (numerator), then you might consider using the count of inpatient malaria cases 5 years and above, inpatient malaria deaths, outpatient malaria cases or similar as denominator.

**Configuration**

Please refer to the section on how to configure the numerator[LINK] if using a related data element as denominator. The exact same considerations and configuration steps apply.


##### Option 4 - Count of orgunits that have previously reported on the data element itself

The final option is to use the count of facilities that have reported on the data element previously, within a given time frame, as denominator. This is similar to the denominator used for the indicator on “facilities consistently reporting” [LINK]. This can be a good estimation of the number of expected reports, in particular in cases where data set assignment is not accurate: if a facilities has reported on a particular data element previously, it typically means the the facility is providing whatever service/diagnostic the data element represents and one can expect it should report on it routinely. However, the results should still be analyzed together with the overall data set completeness since it will not include facilities that are _supposed_ to report, but have not done so in the given time period.

To calculate the count of times an orgunit has reported on the data element you are assessing in any of the previous last 12 months, we must use a predictor and extra data element. This is the same calculation as for the denominator described above in the section on Orgunits consistently reporting[LINK]. In summary, a predictor with a generator 

**if**(**isNotNull(**[data element]**), 1, 0) **

and sequential sample count set to the number of previous periods you want to assess will produce the count to use as denominator.

#### Ad-hoc analysis of completeness for multiple data elements

The approaches outlined above for calculating data element completeness gives many alternatives in terms of how exactly to define the numerator and denominator, and allows us to produce indicators that can be used in charts, maps and tables on a dashboard. However, because they require us to add at least one new metadata object for every variable we want to assess, they are best suited to be configured for a subset of key data elements.

To get a better understanding of data element completeness of a large number of data elements within a data set, we can relatively easily produce this in the data visualizer app as a Pivot table or chart by following these steps:


1. Open Data visualizer, and choose Pivot table as the chart type
2. As Data dimension, choose:
    1. The expected or actual reports for a particular data set
    2. All or some data elements within the same data set, using the “Details only” option for disaggregation
3. Modify the layout, placing Periods as columns (e.g. for last 12 months) and Data on Rows \


![](resources/images/dq_image56.png)


4. Open Option and
    3. Enable Row totals
    4. In the Advanced section, change the Aggregation type to “Count”

5. Update the visualization, and optionally sort the total column from high to low (note: the total for “expected reports” will show NaN, but remain at the top)

![](resources/images/dq_image113.png)


The table produced is now showing on the top row the data element completeness “denominator”, i.e. the expected reports based on the data set (actual reports can also be used). In the other rows, the data element completeness “numerator” for each data element (with disaggregation) is shown. This table allows you to quickly review the completeness of a large number of data elements within a data set.

Following the same approach (using aggregation type “Count”), if looking at a single period a bar chart sorted from High to low will give a quick overview of data element completeness.

![](resources/images/dq_image50.png)

## Consistency of related data

### Scatter plots in data visualizer

![](resources/images/dq_image25.png)

This is a scatterplot in which an outlier analysis or two related variables at the facility level is being performed. The two variables on this chart are related to one another - ANC 1 and ANC 4 - and this is why you can see many of the values so closely clustered together in green colour.

Outlier analyses within data visualizer using scatterplots allows you to identify if related values fit into an expected model or deviate in some way. Red values on the chart do not fit the expected model, and the farther these red values are from the outlier lines, the more likely there is an underlying issue causing these values to not fit the expected model correctly.

These scatterplots can use several methods to identify these outliers, and each of these methods have different levels of sensitivity (ie. each one will detect more or less outliers based on their calculation). The different methods currently available are 

* Interquartile range
* Z-score
* Modified z-score

Z-score has been included as it is a well understood method; however it is the least sensitive of the 3 methods.

#### Create a scatter plot

Scatter plots can be created in the data visualizer app. 

Start the process by selecting the scatter plot from the visualization selector in data visualizer.

![](resources/images/dq_image26.png)

Review the layout after selecting this chart type. Certain items are locked which differentiates it from a number of charts. You must select data items for both the vertical (Y) and horizontal (X) axes of the chart. The points will also always be org units. As discussed, you should select related data items for this type of chart. If you select unrelated data items, your output is unlikely to be useful.

Select your vertical and horizontal data. We will select ANC 1 and ANC 4 as they are related (you will typically see less ANC4 than ANC1 within an identified period for example).

![](resources/images/dq_image74.png)
![](resources/images/dq_image100.png)


Select your org unit (in this case all facilities)

![](resources/images/dq_image31.png)

Select your period

![](resources/images/dq_image83.png)

Update your chart.

![](resources/images/dq_image5.png)

You will now see the scatterplot between these two related items. We can see how they are clustered closely in the bottom left corner of the chart as this is where the majority of values lie. We have not yet added our outlier information to this chart; we can do this as a next step.


#### Add outlier details

To add in the outlier details select the chart options and the “outliers” section

![](resources/images/dq_image9.png)

Enable both the outlier analysis as well as the extreme lines.

For the outlier analysis, we will use the method of interquartile range. This is a method of outlier detection that can be applied to scatterplot data. Here is a reference if you need more info : [https://medium.com/analytics-vidhya/outliers-in-data-and-ways-to-detect-them-1c3a5f2c6b1e](https://medium.com/analytics-vidhya/outliers-in-data-and-ways-to-detect-them-1c3a5f2c6b1e)

You do not need to completely understand this method of outlier detection; just note that all 3 methods will determine outliers by seeing if they fit a model as described by the different methods selected.

You can also select the “Extreme lines” option. This will help you to identify the most extreme outlier values that are potential sources of error

![](resources/images/dq_image41.png)

After selecting these options, update your chart.

![](resources/images/dq_image25.png)

Let us review how we can interpret our output. First, let us zoom in on our cluster of values to review them more closely. We can do this by dragging our mouse cursor over the area we want to zoom into.

![](resources/images/dq_image33.png)

We can reset the zoom if needed by selecting “reset zoom” after we have zoomed in

Review one of the outlier values highlighted in red

![](resources/images/dq_image112.png)

The model for this data is very narrow (ie, most values are closely clustered together); however we see some values that are quite far outside of the outlier boundaries. Neither of these values on its own may be considered an outlier (there are other ANC 1 values that are higher, and other ANC 4 values that are higher); however, this value pairing we have highlighted on the above chart lies outside of the range of 1% of the total y values (which represents ANC 1). This is because a typical ANC 4 value in this range has a much lower ANC 1 value in comparison when reviewing the majority of the other data values.

When reviewing this type of chart, you therefore must review the relationship between the two items being compared and also compare the values to the cluster that falls within the boundaries of the outlier model. In this case, either ANC 1 or ANC 4 values could be incorrect (if we decrease the ANC 1 values OR increase the ANC 4 values, this facility will likely fit in the model accordingly); or this could just be an anomaly having a different ratio between ANC 1 and ANC 4 higher than the interquartile range threshold of 1.5 that has been defined (ie. these values are correct and do not need to be modified). It is more likely that the ANC 1 value is the problem however, as the majority of ANC 4 values in this range have a lower ANC 1 value. As it is such a high outlier as compared to the rest of the data however (given its distance from the outlier boundary and that is outside the 1% y-value line) it does warrant investigation to determine if these values are correct within this facility.

### Validation rule analysis

Validation rules are integrated into the data entry apps of DHIS2, and can be reviewed there during data entry[LINK to above section]. Validation rule violations can also be viewed in the Validation rule analysis section of the Data quality app. This is useful as it allows you to review validation rule violations in bulk; rather than reviewing them for a specific organisation unit, period and dataset you can review them for many organisation units over any specified period of time. This also makes it possible for users who do not do data entry, or even have access to the data entry app, to analyse and monitor validation rule violations.

When reviewing validation rules using this method, it is best to divide your validation rules into validation rule groups. The configuration of these groups is shown in the section https://docs.google.com/document/d/1CkL9Cb6rU5m1XIYDJQfKU-f73Ze8HKKyb0xCknbJ3Ik/edit#heading=h.3ll3cq25tjxs

In order to run validation rule analysis, go to the data quality app and select “Run validation”

Apps -> Data Quality

![](resources/images/dq_image22.png)

Select Run validation under the “Validation Rule Analysis” heading

![](resources/images/dq_image24.png)

From here, you will need to select your inputs. This includes the following:

* The organisation unit
* The start and end date. This defines the period that you are reviewing. 
    * For the period, the start and end dates should fully cover the period you want to review. If you want to review monthly data, this means your start date will the 1st of the month, while your end date should be the 1st of the next month. For example, in this screenshot, data from June 2023 - August 2023 is being reviewed. 
* The validation rule group. This should contain the validation rules you want to review
* Send notifications: this will send out any validation notifications based on the validation violations that are found
* Persist new results

![](resources/images/dq_image88.png)

Once you have selected the inputs select “Validate.” It may take a little while to run the validation analysis depending on the amount of data you have selected to review. If you are planning to review large amounts of data at once (for example many org units across many periods including many validation rules), the validation rule analysis will take longer to run in comparison to running it for a smaller amount of data. 

If there are no violations of the validation rules, you'll see a message saying “Validation passed successfully.” If there are validation violations, they will be presented in a list like the following:

![](resources/images/dq_image66.png)


To review the validation details, select the info button under the details column. 

![](resources/images/dq_image61.png)

This will open up a pop-window with more information on the violation

![](resources/images/dq_image85.png)

We can see how validation rule analysis can be useful in reviewing the violations for multiple org units/time periods at once, as we can also see all the component parts of the violation. This can allow us to identify exactly which value is incorrect and requires further follow-up.

The validation details show a the name and description of the violation along with all of the data elements that are part of the validation rule along with their values.

You are also able to download these validation rule violations. This may be helpful if you want to refer to this list and follow-up on values to fix them over time. Do this by selecting one of the file types in the top right corner after running validation analysis.

![](resources/images/dq_image58.png)



## Consistency over time

[section coming later]


### Year-over-year charts

![](resources/images/dq_image12.png)


This is a year-over-year (line) chart. A year-over-year (line) chart is used to evaluate consistency over time of a single data type (data element, indicator, etc.). In this example, we are displaying data for ANC 1 visits for all 12 months within a year for 2023, 2022 and 2021. This chart allows us to easily identify obvious outliers as we are able to see increases or decreases (if they exist) quite easily when compared to current and previous data. As an example, you can see obvious outliers in January 2023, May 2022 and September 2023 by reviewing each of the lines on this chart and comparing them to their own historical trends. The next step would be taking this chart and drilling down into the hierarchy for these specific periods in order to find the source of these outliers. These charts could be placed on a dashboard for key variables within your workflow to allow for staff to review these on a routine basis based on how frequently the data is collected. 

In order to create this visualization, you will use data visualizer

![](resources/images/dq_image78.png)


Select year-over-year (line) to start creating this chart

![](resources/images/dq_image19.png)

#### The interface - Period selection and filter

After we select this chart type, we can see that both the category and the series are automatically populated with period types. The period selection on the left menu where other dimensions are selected is also greyed out. Organisation units and data are automatically placed in the filter. For this reason, this chart type works best when only one data item is selected for comparison. Multiple organisation units can be used in the filter however depending on what you want displayed (it will filter the data belonging to these organisation units).

![](resources/images/dq_image64.png)

#### The interface - Category

In this example, the category determines the periods that will be displayed along the x-axis and group the data together. So with “months per year” selected, all the months within a year from January - December will be displayed. If we were to select “Quarters per year” it would instead display the 4 quarters of a year along the x-axis.

![](resources/images/dq_image73.png)


You will notice that the selections in the categories are all relative periods, you can not select for example specific months in the category in this chart type.

![](resources/images/dq_image16.png)

#### The interface - Series

The series determines which years you will be displaying data for. If I have this year and last year selected, it will display these years respectively based on the current date. I can also specify years rather than a relative period, for example 2021, 2022 and 2023.

![](resources/images/dq_image47.png)

With these two options selected I am now creating a chart which will display data from January - December (due to the category selection) along the x-axis. And with 2021, 2022 and 2023 selected as my series, data values from these 3 years will be displayed by month on the year over year chart.

#### The interface - Data

When selecting data, it is best to only select one data item. These could be supplemented by choosing groups or disaggregations to further filter the data by, however as the data selection is automatically added to the filter and can not be moved, adding in more than one data item will have no effect on the chart.

![](resources/images/dq_image74.png)

**Update and review the chart**

We can now update our chart. In this case we are using the default country organisation unit, however we could also change this if necessary.

We can see how the chart has been generated based on our category and series period selection as well as the selection of our data item (in this case ANC 1st visit).

The series has determined which years we are displaying data for, while the category determines how to group the data along the x-axis.

![](resources/images/dq_image12.png)


## WHO Data Quality Tool

The WHO Data Quality Tool is an application available in the [DHIS2 App Hub](https://apps.dhis2.org/), supporting a range of data quality analysis functionality based on the WHO Data Quality Review framework. At the time it was released around 2016, much of the data quality analysis functionality was not available in the core DHIS2 applications. Over the years, this has changed and most of the analysis can now be done in DHIS2 core. In the coming 1-2 years, the WHO Data Quality app will no longer be updated for new DHIS2 versions. A new and modernized application is being developed to fill remaining functionality gaps, primarily related to automatic generation of annual data quality reports.

The below table gives an overview of what functionality is available in the WHO Data Quality Tool and what is available in DHIS2 core (as of 2.38).

| Analysis functionality                             	| WHO Data Quality Tool                   	| DHIS2 core apps 	|
|----------------------------------------------------	|-----------------------------------------	|-----------------	|
| Completeness and timeliness of data sets           	| Supported                               	| Supported       	|
| Completeness and timeliness of data elements       	| Limited support (in annual report only) 	| Supported       	|
| Validation rule analysis                           	| Not supported                           	| Supported       	|
| Min-Max outlier analysis                           	| Not supported                           	| Supported       	|
| Consistency of related data using scatterplots     	| Supported                               	| Supported       	|
| Analysis of negative dropout rates                 	| Supported                               	| Supported       	|
| Year-over-year charts                              	| Supported                               	| Supported       	|
| Outlier analysis (time series)                     	| Supported                               	| Supported       	|
| Consistency over time using scatterplots           	| Supported                               	| Not supported   	|
| Automatic generation of annual data quality report 	| Supported                               	| Not supported   	|

A dedicated [user manual](https://docs.dhis2.org/en/use/optional-apps/who-data-quality-tool/installation-and-configuration.html#how-to-configure-the-dhis2-based-who-data-quality-tool) is available for the WHO Data Quality Tool, and its functionality is therefore not discussed in this guide.

