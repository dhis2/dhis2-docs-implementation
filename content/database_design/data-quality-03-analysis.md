# Assessing data quality

DHIS2 has a wide range of functions for assessing data quality, available across different apps and functions, and this section gives and overview of this functionality. It is structured according to three types of data quality metrics:

* Completeness and timeliness of data
* Consistency of data across related variables
* Consistency of data over time

## Completeness and timeliness

***Completeness*** of reporting gives an indication of how much of the expected data has actually been reported. In DHIS2, most of the completeness checks are based on assessing the _data set_ completeness, i.e. how many data sets (forms) have been submitted by organisation unit and period. The timeliness calculation is based on a system setting called "Days after period end to qualify for timely data submission." 

The built-in functionality for completeness and timeliness in DHIS2, e.g. what is built into the Data Visualizer, Reports and Maps application, refers to *data set reporting rates*. However, we can also configure DHIS2 to assess the proportion of facilities that are _consistently reporting_, as well as the *completeness of individual data elements*.

### Data set completeness and timeliness

The completeness reports will also show which organisation units in an area are reporting on time, and the percentage of timely reporting facilities in a given area. 

Data set completeness and timeliness can be reviewed in the reports app as well as  core visualization apps (Data visualizer and Maps). The core visualization apps allow for you to review completeness and timeliness in more significant detail across multiple org units and periods; however the reports app has a simplified user experience that has been validated by its widely observed use in comparison to other apps within DHIS2. 

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

#### Using Data Visualizer

In data visualizer, you will be able to review dataset completeness and timeliness measures similar to the reports app; however you are now free to select multiple data sets, periods and organisation units at the same time. You can also add completeness and timeliness measures to charts and tables that include other data, such as health service delivery data, to verify that the data you are reviewing is representative of the situation within the country you are working with. This gives you much more flexibility when compared to the reports app; however the additional options can make it less accessible compared to the reports app. Ideally, these visualizations are pre-made and placed on a dashboard for users to review routinely; however it is useful for a subset of users to know how to create outputs using these metrics within the data visualizer.

Within data visualizer, select your “Data” input, along with “Data Set” as the data type. This will allow you to search or add filters for the data set and metric type that you want to add to your visualization.

![](resources/images/dq_image94.png)

Here is an example of a chart comparing BCG doses given with the reporting rate of the immunization data set

![](resources/images/dq_image52.png)

We can quickly note that several of the districts have reporting rates &lt; 80%, and therefore the data being displayed may not be fully representative of the situation in the country. It may be important to verify this through a more detailed analysis reviewing the facilities affecting this value and/or using data element completeness.

We can go through some examples of tables and charts you could potentially create when reviewing completeness and timeliness within the data visualizer app

##### Example 1 : Pivot Table comparing completeness and timeliness over several datasets, periods and organisation units

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


##### Example 2 : Line chart comparing completeness and timeliness over several periods

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

##### Example 3 : A 2-axes chart comparing service data with dataset completeness

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

* How to analyse the proportion of facilities that _consistently report_ data element values over a time period, and

* How to analyse completeness of an individual data element

Common for the approaches outlined is that they require us to configure additional metadata for each variable we want to assess. In practice, this means that they can only be implemented for a limited set of data elements. The implementation section discusses this further.

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

Next, we must set up two predictors to calculate the data values for our two data elements. Documentation on predictors is available [here](#manage-predictors)

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

After predictors have been generated and aggregate analytics have been run ([see below](#scheduling), the indicator is available for use in the Data visualizer and Maps applications..

#### Calculating data element completeness

In some DHIS2 implementations it has been observed that reporting is inconsistent for all data elements in a data set. DHIS2 by default only assesses the reporting rates of data sets and not of the individual data elements in that data set. The goal of a data element reporting rate is to assess the reporting consistency of a single value. This is for aggregate data elements only.

A reporting rate is: 100 x (Number of received values / Number of expected values)

To calculate the reporting rate for a data element we have to define an indicator with the numerator (number of received values) and the denominator (number of expected values), and with a factor of 100 (percentage indicator type). While the numerator is always the count of data values, there are various options for defining the denominator, and which one of these is appropriate must be decided based on the local situation.

How data element completeness is configured in DHIS2 also depends on the DHIS2 version: some ways of defining the numerator and denominator requires that predictors are used as an intermediate step in the calculation, in particular in 2.37 and below. Note that predictors will need to be scheduled to run on the server, see the [final section](#scheduling) for guidance on instructions.

#### Configuring the numerator - values received

We first review how to define the _numerator_ of our data element completeness indicator. As explained above, this will always be the count of data values that has been reported for a certain data element. There are nonetheless a few things that must be considered.

**Zero value storage**

For several reasons, it is generally recommended to _not_ store zero values being reported for data elements unless there is a clear reason for it (for example the “aggregation type” being of a type where zeros are relevant, such as average). This has implications when reviewing data element completeness, since for data elements where zero values are not entered and stored we cannot differentiate between facilities that have 0 to report and facilities that have not reported. One option is to enable zero values storage for the specific data elements where you want to define data element completeness indicators. However, this is difficult to implement in practice since data entry users must then know for what specific data input fields a 0 is expected. A more practical option is to focus configuration of data element completeness on data elements where all or almost all facilities are expected to have a value > 0 to report, and being explicit in descriptions of the indicator and visualizations that reaching 100% data element completeness is not necessarily expected.

**Disaggregations**

How to take into consideration any disaggregations that might be applied to the data element is critical, because it affects how to configure the indicator expressions and also whether use of predictors are needed or not. For example, if a data element for a child vaccination such as BCG that is disaggregated by &lt; 1 year and 1+ year, should the data element completeness be based on:

* One specific category option combination. For example, “reported” means having reported for “BCG doses &lt; 1 year”.

* Both category option combinations. For example, “reported” means having reported for “BCG doses &lt; 1 year” or “BCG doses &lt; 1 year”.

* Either of category option combination. For example, “reported” means having reported for “BCG doses &lt; 1 year” or “BCG doses &lt; 1 year”

The decision on this depends on the specific data element and disaggregation. For child vaccinations, the target age group for vaccinations is &lt; 1 year, and it might be common that there is no data to report in the 1+ year age group. Thus it would make sense to define the completeness for &lt; 1 year specifically. On the other hand, if “Confirmed malaria cases” is disaggregated into &lt; 5 years and 5+ years, facilities can be expected to have a values for each age group and it would make sense to consider both values to be expected; in this case, the denominator must be adjusted accordingly.

The same consideration applies when data sets are disaggregated with an [attribute option combination](#about-additional-data-dimensions), though this is less common.

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

The first option is to use the assignment of the data set that the data element is part of as the basis for calculating completeness. This measure is quite similar to how the data set completeness (reporting rates) [described above works](#configuring-data-set-completeness). This option is relatively straightforward to configure, since the “expected reports” of a data set is available directly to use in indicator expressions. The main limitation of using the data set expected reports as the denominator for data element completeness is that it assumes that data set assignment is correct and kept up to date.

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

The final option is to use the count of facilities that have reported on the data element previously, within a given time frame, as denominator. This is similar to the denominator used for the indicator on [“facilities consistently reporting.”](#orgunits-consistently-reporting) This can be a good estimation of the number of expected reports, in particular in cases where data set assignment is not accurate: if a facilities has reported on a particular data element previously, it typically means the the facility is providing whatever service/diagnostic the data element represents and one can expect it should report on it routinely. However, the results should still be analyzed together with the overall data set completeness since it will not include facilities that are _supposed_ to report, but have not done so in the given time period.

To calculate the count of times an orgunit has reported on the data element you are assessing in any of the previous last 12 months, we must use a predictor and extra data element. This is the same calculation as for the denominator described above in the section on [Orgunits consistently reporting](#orgunits-consistently-reporting). In summary, a predictor with a generator 

**if**(**isNotNull(**[data element]**), 1, 0) **

and sequential sample count set to the number of previous periods you want to assess will produce the count to use as denominator.

#### Ad-hoc analysis of completeness for multiple data elements

The approaches outlined above for calculating data element completeness gives many alternatives in terms of how exactly to define the numerator and denominator, and allows us to produce indicators that can be used in charts, maps and tables on a dashboard. However, because they require us to add at least one new metadata object for every variable we want to assess, they are best suited to be configured for a subset of key data elements.

To get a better understanding of data element completeness of a large number of data elements within a data set, we can relatively easily produce this in the data visualizer app as a Pivot table or chart by following these steps:


1. Open Data visualizer, and choose Pivot table as the chart type
2. As Data dimension, choose:
    1. The expected or actual reports for a particular data set
    2. All or some data elements within the same data set, using the “Details only” option for disaggregation
3. Modify the layout, placing Periods as columns (e.g. for last 12 months) and Data as the Rows


![](resources/images/dq_image56.png)


4. Open the Options menu and
   1. Enable Row totals
   2. In the Advanced section, change the Aggregation type to “Count”

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

When reviewing validation rules using this method, it is best to divide your validation rules into validation rule groups. The configuration of these groups is shown in the section on validation rule groups. 

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

### Statistical outliers in time series

"Extreme outliers" are values which are highly suspicious and which need to be double checked for accuracy. These are different from the values normally reported by a health facility. If extreme outliers are found to be incorrect, then they should be edited following local procedures outlining how data values should be edited. In this section, we show how outliers *in the time dimension* can be identified in DHIS2 using [predictors](#manage_predictor), and with the [outlier analysis](#outlier_detection) function. We specify *over time* to differentiate this from the outliers described in the section on [scatter plots](#scatter-plots-in-data-visualizer), which identify organization units that are outliers for a single period.

The two functions presented for identifying outliers each have some advantages. The *DHIS2 Data Quality app* permits doing analysis in bulk (i.e. for large numbers of variables at the same time) without any prior configuration. It lets the users choose different statistical methods for the outlier calculation, and run it on any data set and period combination. It is thus both flexible and powerful, but requires users to open the app, choose the appropriate parameters, and wait for the analysis to finish. By using *predictors* to calculate outliers thresholds and related data elements and indicators, we can create notifications, view these values on the dashboard, or use it in combination with other DHIS2 functionality such as validation rules. This results in a greater flexibility in how to make the results of the outlier analysis available to users in different ways, but requires configuration of multiple metadata objects for *each* variable we want to assess. The two methods should therefore be considered complementary.

#### Outlier analysis with predictors and indicators


> **Note**
>
> In a live implementation, predictors can be resource intensive and specific care needs to be taken to stress test the DHIS2 system in order to ensure it is able to generate predictors on an ongoing, regularly scheduled basis as new data is added prior to live implementation. In addition, even after the Predictor has generated new data, the data will not be visible until Analytics has been updated; this is another step which may require significant time depending on the size of the system. As a result, considerable patience and several prolonged pauses in the workflow are likely to be required the first time guidance is followed. ***It is important to replicate and test predictors on development systems first, so they can be thoroughly tested*** ***without affecting a production system.***

[Predictors](#manage-predictors) provides generic functionality in DHIS2, which we will here show how to apply for the purpose of outlier detection and analysis. While the initial process of creating predictors can be time consuming, once you have successfully configured one data element/indicator and confirmed that the resulting outputs are correct, the configuration process for each subsequent data element or indicator should take less time.

Configuring predictors for outlier detection requires two sets of predictors:

-   one predictor to calculate the *outlier threshold*. This is defined from analyzing previously reported data, and defining thresholds over which values are considered outliers (for a combination of data element and organization unit).

-   one or more predictors that use the outlier threshold in further calculations, such as counting how many facilities have reported outliers, assigning only outlier or non-outlier values to separate data elements for analysis etc.

Since predictors produce data values that need to be stored before they're used in further calculations, each new predictor needs to be associated with a data element. These data elements could be organized in one or more new data sets.

There are several alternatives in terms of what predictors/data elements and indicators that can be configure for each of the variables you would like to analyze/monitor:

-   Outlier threshold (predictor/data element)

-   Count of values that *are* outliers (predictor/data element)

-   Count of values that are *not* outliers (predictor/data element)

-   Values that are outliers (%) (indicator)

-   Values that *are* outliers (predictor/data element)

-   Values that are *not* outliers (predictor data element)

-   Data values excluding outliers (indicator)

These are further defined and explained below. First, it is important to understand how the data flow is for these metadata objects, outlined in this figure

![](resources/images/dq_outlier_image11.png)

Predictors must be scheduled to run by the system, just like the *analytics* process. Scheduling is therefore critical for this to work. For the indicators to be available to end users, we first need to run the first set of predictors (calculating thresholds), then the second set of predictors, and finally the normal analytics process for the data sets and indicators to be available in Data visualizer and other analysis tools. This is discussed further [here](#scheduling).

##### Predictor for outlier threshold

We first configure the predictor and data element that calculates the outlier threshold for a particular variable, either a data element (default/total) or one particular disaggregation (category option combination). In the following example we'll use *Malaria confirmed cases* as an example.

**Configuration steps**

1.  Create a data element to store the outlier threshold value:

    -   Name: "DQ - Malaria confirmed cases outlier threshold (mean + 3 SD)"

    -   Description: "Auto-generated from predictor. Outlier threshold for the Malaria confirmed cases data element (total for all disaggregations), based on the average + 3 standard deviations over the previous 12 months. This can be used for identifying potential outliers."

    -   Type: Aggregate

    -   Value type: Positive or zero integer

2.  Create a new predictor with basic properties:

    -   Name: "DQ - Malaria confirmed cases outlier threshold (mean + 3 SD)"

    -   Description: "Generates the outlier threshold for malaria confirmed cases, defined as mean + 3 standard deviations, not including the values for last month."

3.  Set the Output data element to point to the data element created in step 1.

4.  Set Period type to match the data collection frequency of the data element we are assessing. For our Malaria confirmed cases example this is collected Monthly.

5.  Set Organisation units levels to the level at which the data is collected, which in most cases will be Facility.

![](resources/images/dq_outlier_image10.png)

6.  Configure the *Generator*, which is the expression that defines the actual calculation performed by the predictor.

    -   Set Missing value strategy to Skip if all values are missing.

    -   The expression in this case should be:

*avg({data_element_uid}) + (3 \* stddevPop({data_element_uid}))*

*avg()* gives us the average/mean for the data element in the periods we are assessing (defined in the next step. *stddevPop()* gives us the population-based standard deviation for the data element in the periods we're assessing, and we multiply this with 3 since we want the thresholds to be 3 standard deviations above the average. We use 3 here because it's often used as the definition of extreme outliers, but other values can be used.

![](resources/images/dq_outlier_image9.png)

7.  Finally, set the Sequential sample count. This defines how many previous periods of data should be included in the calculation. In this case, the data is monthly (defined in step 4), and we want to use 1 year of previous data to calculate the threshold and therefore set this to 12. Annual sample count and sequential skip count should be 0 (the default)

![](resources/images/dq_outlier_image3.png)

##### Predictors for outlier metrics

When the outlier threshold is defined and stored as a data element value, we can create additional predictors to do more specific calculations. These are configured in the same way, except the actual Generator expression. We outline the general steps to create the predictors once, whilst the actual expression for each of the specific predictors are provided in table below.

We will review how to create four different predictors/data elements using the outlier threshold:

  ---------------------------------------------------------------------------------------
  Data element excluding outliers   Data element values that are not outliers.
  --------------------------------- -----------------------------------------------------
  Data element outliers             Data element values that *are* outliers.

  Data element non-outlier count    Count of data element values that are not outliers.

  Data element outlier count        Count of data element values that are outliers.
  ---------------------------------------------------------------------------------------

The following example (with ANC 1st visit as the data element we are assessing) shows for an time series what output the different predictors are expected to produce

| | **Jan** | **Feb** | **Mar** | **Apr** | **May** | **Jun** | **Jul** |
| :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | 
| ANC 1 | 165 | 196 | 214 | 204 | 219 | 4243 | 195 | 
| ANC 1 outlier threshold | 253 | 265 | 253 | 244 | 242 | 246 | 4716 | 
| ANC 1 excl outliers | 165 | 196 | 214 | 204 | 219 | | 195 | 
| ANC 1 outliers | | | | | | 4243 | | 
| ANC 1 non-outlier count | 1 | 1 | 1 | 1 | 1 | | 1 | 
| ANC 1 outlier count | | | | | | 1 | | 

To configure these predictors, follow these general steps after first creating data elements to which the values can be assigned:

1.  Create a new predictor

2.  Set the Output data element to point to the data element that has been created

3.  Set Period type to match the data collection frequency of the data element we are assessing.

4.  Set Organisation units levels to the level at which the data is collected, in most cases Facility.

5.  Configure the *Generator*, using the appropriate expression from the table below

6.  Set the Sequential sample count to **1**, the annual sample count to 0, and sequential skip count to 0.

This table provides the expressions that should be used in Generator of the different predictors:

  
| Predictor | Expression | Example | Explanation |
| :-- | :-- | :-- | :-- | 
| Data element excluding outliers | if( {DE} <= {DE threshold}, {DE}, 0) | if(#{KV1LlPytf4f}<=#{dx8Y0ZrHji7}, #{KV1LlPytf4f}, 0) | If the data element value is below the threshold, use the data element value, else return 0. | 
| Data element outliers | if( {DE} > {DE threshold}, {DE}, 0) | if(#{KV1LlPytf4f} > #{dx8Y0ZrHji7}, #{KV1LlPytf4f}, 0) | If the data element value is above the threshold, use the data element value, else return 0. | 
| Data element non-outlier count | if( {DE} <= {DE threshold}, 1, 0) | if(#{KV1LlPytf4f}<=#{dx8Y0ZrHji7}, 1, 0) | If the data element value is below the threshold, return 1, else return 0. | 
| Data element outlier count | if( {DE} > {DE threshold}, 1, 0) | if(#{KV1LlPytf4f}>#{dx8Y0ZrHji7}, 1, 0) | If the data element value is above the threshold, return 1, else return 0. | 
 
  
The data elements populated by these predictors can be used in visualizations and on dashboards directly, e.g. showing the reported values against the threshold, having a simple counter of the number of outliers that were flagged in the previous month, or producing tables that highlight the specific outlier values by facility.

![](resources/images/dq_outlier_image4.png)

##### Indicators for outlier analysis

When predictors and data elements have been configured for these core data quality measure as explained above, we can define two indicators:

**Percentage of values that are outlier values** for a particular data element:

Numerator: count of outlier values

Denominator: count of outlier values + count of non-outlier values

Factor: 100

Purpose: metric of the data quality, and can be used to look at geographical comparisons or changes over time

**Value excluding outliers as a percentage of the overall value** for a particular data element:

Numerator: the values for the data element that are not outliers

Denominator: all values for the data element

Factor: 100

Purpose: metric for the *significance* the outlier values has on the overall value for a data element, and can be used both for time trends and geographical comparisons. Also gives an indication of how significantly outliers affect the overall data which is an important consideration when analyzing data.

Configuration of these indicators are straightforward once the underlying predictors/data elements are available (options a and b below refers to each of the above indicators)

1.  Create a new indicator with an appropriate name and description. Description is important here since these indicators might be new to most users.

2.  Set the indicator type to be Percentage (exact name can vary, but the factor of the indicator type should be 100)

3.  Configure the numerator

    a.  Count of outliers (example: Malaria confirmed cases outlier count)

    b.  Values excluding outliers (example: Malaria confirmed cases excluding outliers)

4.  Configure the denominator

    a.  Count of outlier values + count of non-outlier values (example: Malaria confirmed cases outlier count + Malaria confirmed cases non-outlier count)

    b.  Data element values (example: Malaria confirmed cases)

5.  Save the indicator and assign it to appropriate groups

These indicators can now be used in visualizations and dashboards, allowing users to easily monitor trends in outliers, make geographical comparisons, and monitor the overall impact of outliers on the data element in question.

#### DHIS2 Outlier analysis

It is not realistic to configure a set of predictors, data elements and indicators for every data element. Outlier analysis in the Data Quality makes it possible to run outlier analysis on whole data sets, and is therefore a useful complement to the predictor-based outlier checks.

To run outlier analysis, open the Data Quality app, and click Analyze under Outlier detection.

![](resources/images/dq_outlier_image6.png)

Start by selecting the key parameters for the analysis:

-   Data set - choose one or more data sets to include in the analysis

-   Organization units - choose one or more organization units to include; all orgunits below the selected units will be included.

-   Start and end dates - periods within this date range will be included. Note that these are the periods we are analyzing for outliers. Data from *all* periods for a particular organization unit and data element is included when the average/median and standard deviation is calculated, unless otherwise specified (see advanced options below).

![](resources/images/dq_outlier_image5.png)

Next, specify the statistical methods and parameters to use for the analysis.

-   Algorithm:

    -   Z-score - detection of outliers based on standard deviations from the mean. More information [[about z-score]{.ul}](https://en.wikipedia.org/wiki/Standard_score).

    -   Modified z-score - detection of outliers based on standard deviations from the median.

    -   Min-max - based on min-max values, discussed [here](#review-min-max-values-in-the-data-quality-app)

-   Threshold - the number of standard deviations from the mean/median a value must be before it is considered an outlier. The default is 3, which is often used as a default definition of an "extreme" outlier.

-   Max results - the maximum number of outliers that will be included in the results table.

![](resources/images/dq_outlier_image2.png)

Optionally, change the advanced options:

-   Data start and end date - allows you to limit what data is used as the basis for calculating the mean/median and standard deviations, overriding the default options which is to include all data. Note that a certain number of periods are needed for the statistical calculations to be meaningful.

-   Sort by - specified how the results are sorted, with two options

    -   Absolute deviation from median/mean (default) - this sorts the resulting table of outliers according to the absolute deviation of the outlier from the median/mean. In general, this means that the outliers with the biggest significance/impact on the result is shown first.

    -   Z-score/modified z-score - this sorts the resulting table according to the z-score, i.e. "how extreme" the outlier is. This means that a relatively small value (i.e. from a small facility) could be displayed before a much larger number (i.e. from a big facility), if the smaller value is further from the mean/median.

![](resources/images/dq_outlier_image8.png)

Finally, click Start to run the analysis. Depending on the parameters selected and size of the database, this may take some time. The resulting table lists all the outliers that have been detected (up to the maximum allowed results), with information on:

-   Data element

-   Period

-   Organization unit

-   Value - the value that has been identified as an outlier

-   Z-score - the z-score of the outlier

-   Deviation - the deviation of the outlier, i.e. the difference between the mean/median and the actual value

-   Std Dev - the value of one standard deviation.

-   Median/mean - median/mean value, depending on the method used

-   Min and Max - min and max value for the data element, based on the specified number of standard deviations set in the parameters section.

-   Follow-up - check-box that allows values to be marked for follow-up, which means they can be listed using the "Follow-up analysis" function of the Data Quality app.

![](resources/images/dq_outlier_image1.png)

#### Outlier Tables

The outlier table is a new feature available from DHIS2 version 41 and is meant, in part, to replicate and expand upon the outlier table functionality that was previously available within the WHO data quality tool. 

Similar to the outlier table in the WHO data quality tool, the outlier table displays data and analyzes them for outliers using either the standard z-score or modified z-score (modified z-score is used by default).

The outlier table is accessible as a visualization type within the data visualizer application. 

Making an outlier table is very easy:

1. Select the outlier table visualization type from the visualization selector in the data visualizer app
2. The outlier table has 3 fixed dimensions in which you must select inputs for:
   1. Data
   2. Period
   3. Organisation Units
3. Select the inputs for these items and select "Update" 

Select the outlier table visualization type from the visualization selector in the data visualizer app

![](resources/images/dq_select_outliertable.png)

Select the inputs for the data, period and organisations units and "Update" the table. These 3 inputs are locked, meaning that all 3 are needed and inputs ***must*** be selected for them. Note that you are able to select multiple data items to use on this table.

![](resources/images/dq_outlier_lockedlayout.png)

After updating you should see a table like the following:

![](resources/images/dq_outliertable_output.png)


A review of the items available on this table is located here:

1. Data : This column shows the data items you have selected. You can select as many data items as needed.
2. Category option combination : This is the specific disaggregation, if any, that the value is representing. In our example, the ANC 4th or more visits is disaggregated into Fixed and Outreach (see dataset below). In the outlier table, we have identified outliers that are coming from the ANC 4th or more visits ***Fixed*** value.

![](resources/images/dq_outlier_catcombo.png)

3. Period : This is the period in which the outlier value has been found. 
4. Organisation unit : This is the organisation unit where the outlier has been found. Note that it shows the source organisation unit. When you select an org unit in your hierarchy, it will therefore look for outliers in all of the children of the organisation unit.
5. Value : This is the value that is recorded in DHIS2
6. Median : The median is the middle value for the period selected within the data element, category option combination, period and organisation unit combination. When a recorded value is significantly higher then the median, the data is not following an expected pattern.
7. Modified z-score : The modified z score is a standardized score that measures outlier strength or how much a particular score differs from the typical score. Using standard deviation units, it approximates the difference of the score from the median. We can define the cut off used to identify outliers using the modified z-score. The higher this value, the more deviation a recorded value has from the median.
8. Median absolute deviation : This is the average distance that the data values are from the median. The purpose is to provide a numerical description of how spread out the values of the set are. If we take our example in the first row, the median absolute deviation is only 2.5 with a median of 9. The recorded value is 854, deviating by a value of 845 from the median. 
9. Min : The minimum value threshold that has been set for the data element, disaggregation and organisation unit combination. This is not limited to a particular period.
10. Max : The maximum value threshold that has been set for the data element, disaggregation and organisation unit combination. This is not limited to a particular period.

***Modifying the outlier table***

You are able to modify the outlier table by using the table options. There are 3 items you can alter:

1. Data
2. Style
3. Outliers

![](resources/images/dq_outlier_options.png)

1. Data : From the data tab you can skip rounding and also select the maximum number of results you want to display. You can display up to 500 outliers in the table.

![](resources/images/dq_outlier_data.png)

2. Style : From the style tab yoiu can modify the display density, font size, digit group seperator and choose to display the organisation unit hierarchy in the organisation unit column

![](resources/images/dq_outlier_style.png)

3. Outliers : In the outliers tab you can select your outlier detection method and set your threshold factor. *By default, the modified z-score and a threshold factor of 3 are set to detect outliers.* The z-score/standard score method uses the mean rather then the median to detect outliers, which may be less sensitive to detection.

![](resources/images/dq_outlier_outliers.png)

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
| Automatic generation of annual data quality report 	| Supported                               	| Not supported (NB: this is supported in the [data quality annual report app](https://apps.dhis2.org/app/73f87a14-d71c-40b8-8363-0d956745ba06))  	|

A dedicated [user manual](https://docs.dhis2.org/en/use/optional-apps/who-data-quality-tool/installation-and-configuration.html#how-to-configure-the-dhis2-based-who-data-quality-tool) along with a [training package](https://www.who.int/publications/i/item/9789240036475) is available for the WHO Data Quality Tool, and its functionality is therefore not discussed in this guide.

