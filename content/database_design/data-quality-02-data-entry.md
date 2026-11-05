# Data entry for aggregate data

As much as possible, data quality issues should be detected and addressed as early as possible. By the time data is entered into DHIS2, it will often have been recorded first on patient cards or registers, then manually tallied into tally sheets, before the data is aggregated into weekly, monthly, or quarterly values and recorded in aggregate facility reporting forms. Finally, data from these aggregate forms is entered into DHIS2. The design and quality of all these different tools, and the training provided and time allocated to staff to correctly perform these data collection activities, are critical for the quality of the data.


## Design of data entry

Design of the data collection forms is an often overlooked element of good data quality. Design of paper-based data collection tools and forms is beyond the scope of this document, but well-designed paper-based forms that are easy for data collection staff to fill out are an important factor in improving data quality. Forms that are extremely complex can be difficult to fill out on paper, which can lead to transcription errors on the original paper form. These errors can then carry over into the digital form (that is, DHIS2) when electronic data entry takes place.

[Data entry forms](https://docs.dhis2.org/en/use/user-guides/dhis-core-version-master/configuring-the-system/metadata-metadata-management-app.html#mm_manage_data_set) in DHIS2 can either be auto-generated (default or section forms) or have a custom design (custom forms). DHIS2 implementers can use HTML and JavaScript to create complex custom forms that closely mimic the layout and design of a paper form. DHIS2 generates section forms automatically. They consist of sections of data that share a common type of disaggregation. Section forms are generally easier to maintain and work well on mobile devices such as Android. Use section forms when possible. However, section forms might not match the design of paper forms. This can make data entry harder and make mistakes in the transcription process more likely.

Custom forms are sometimes necessary to make a data entry form that is easy to transfer from paper to digital. However, custom forms are sensitive to changes in the underlying metadata (for example, data elements and category dimensions). This can lead to data being entered into the incorrect data element/category option combination without the data entry user noticing it. Complicated custom forms can also need extra work to make “tabbing” between cells work correctly, which is important for efficient data entry without errors.

More generally, data entry forms that are overwhelmingly big (such as tables with 100+ rows x 10+ columns, not uncommon for recording morbidity data) come with the risk that the data entry user loses track of which row and column (for example, disease and age/sex disaggregation) they are entering data into.

This guide does not cover all aspects of creating data entry forms. Consider these items in your design before you configure any data set in DHIS2, because this can help prevent some data quality issues before they arise:



* What are the data elements on the form?
* Which period is the form going to be collected?
* Are there any disaggregations associated with the data elements that need to be made?
* Which organisation units should be reporting on the form routinely?
* Are there any items that can be automated, for example indicators or calculated totals?
* Are there any items you should collect using other means (population data, cumulative totals, and so on)?
* Design your dimensions with data use in mind, not data collection. 
    * This means that the disaggregation of data values at the time of collection should be easily aggregated up along the various dimensions, that is, they add up to a meaningful total.
* Reuse dimensions as much as possible, because this increases the ability to compare disaggregated data (for example, age groups, fixed/outreach, sex, and so on).

Configure data elements with the appropriate value types, so that only the right type of data values can be saved. For example, configure data elements for service delivery usage, cases/deaths, number of tests, and so on as zero or positive integers, to prevent negative numbers or decimals.


## Validation rules

[Validation rules](https://docs.dhis2.org/en/use/user-guides/dhis-core-version-master/configuring-the-system/metadata-maintenance-app.html#about_validation_rule) are a critical way to make sure that related data values follow defined patterns. For example, there cannot be more people who test positive for malaria than people who were tested for malaria. Similarly, if any people have tested positive for malaria, there should be at least as many people who were tested.

In DHIS2, validation rules consist of two values (a left side and a right side) that are compared using a mathematical operator (less than, greater than, and so on) to produce a logical true or false result. Validation rules compare values that are in DHIS2, at the level of capture and periodicity that the validation rule defines. Using the malaria example in the previous paragraph, a validation rule in DHIS2 can look like this:

![A validation rule with positive malaria cases as the left side, less than or equal to as the operator, and malaria tests performed as the right side.](resources/images/dq_image3.png)

If this data is collected monthly at the facility level, then it can be compared at least every month at the facility level, and additionally can be run at higher levels and lower frequencies if needed (for example, at district level for a year). 

Validation rules do not run when you work offline in the web-based Data entry app. They do work offline in the DHIS2 Android app on a mobile device.


### Configuring validation rules

This section shows how to create the validation rule from the previous example in DHIS2. Malaria testing can use different methods, so this example rule is only for rapid diagnostic tests (RDT).

![A validation rule with positive malaria cases as the left side, less than or equal to as the operator, and malaria tests performed as the right side.](resources/images/dq_image3.png)

You create validation rules in the **Maintenance** app, in the **Validation** section:

1. Add a **Name** (required, unique). Make it descriptive, for example “MAL - Positive (RDT) &lt;= Tested (RDT)”.

2. Add an **Instruction**. This field is not required, but users see it both in validation analysis and when they review validation rules during data entry, so you should always add one. You can also add a short name, code, and description.

![The validation rule form with the name, code, and instruction fields filled in for the RDT example.](resources/images/dq_image63.png)

3. Choose an **Importance** (**High**, **Medium**, or **Low**). The importance is a description that DHIS2 shows to users. It does not affect priority or whether the rule runs.

4. Choose a **Period type**. You cannot choose a period type more frequent than the frequency of data entry: if data is collected monthly, the period cannot be weekly.

5. Create the left side of the expression:
    1. If you want to compare data relative to the period, choose **Sliding window**. For more information, see [About validation rules](https://docs.dhis2.org/en/use/user-guides/dhis-core-version-master/configuring-the-system/metadata-maintenance-app.html#about_validation_rule).
    2. Choose a **Missing value strategy**. It sets how DHIS2 evaluates the rule if data is missing:

| Option                         	| Description                                                                                                                                                                                                                                         	|
|--------------------------------	|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| Never skip                     	| The validation rule will never be skipped in case of missing data, and all missing operands will be treated effectively as a zero. This is the default option. Always select this option if you use the Exclusive pair or Compulsory pair operator. 	|
| Skip if all values are missing 	| The validation rule will be skipped only if all of the operands which compose it are missing                                                                                                                                                        	|
| Skip if any value is missing   	| The validation rule will be skipped if any of the values which compose the expression are missing.                                                                                                                                                  	|

   3. Enter a **Description**. Build the expression by double-clicking data items in the right pane and combining them with the mathematical operators below the left pane. Then click **Save**.

![The left side expression editor with the description Positive (RDT) and the disaggregated RDT positive malaria cases data elements added to the expression.](resources/images/dq_image69.png)

> **Note**
>
> Use the disaggregated data elements instead of the total data element, as shown in the previous figure (that is, all the positive malaria cases by age and sex). If you choose the total data element, the details are empty when you look at them in validation rule analysis, and you cannot drill down to find where the problem comes from.

6. Choose an **Operator**: **Compulsory pair**, **Equal to**, **Exclusive pair**, **Greater than**, **Greater than or equal to**, **Less than**, **Less than or equal to**, or **Not equal to** (**Less than or equal to** in this example).

    1. The *Compulsory pair* operator requires that data values are entered for both the left and right sides, or for neither side. That is, if one field is filled, the other fields must also be filled.
    2. The *Exclusive pair* operator requires that if any value exists on the left side, there should be no values on the right side (or the reverse), for a given period, organisation unit, and attribute option combo.

7. Create the right side in the same way as the left side. The completed rule shows the descriptions of both sides and the operator:

![The completed rule with Positive (RDT) as the left side, Less than or equal to as the operator, and Tested (RDT) as the right side.](resources/images/dq_image90.png)

8. Optionally, choose which **Organisation unit levels** DHIS2 evaluates the rule for (empty means all levels, which is the most common option). Also choose whether to **Skip this rule during form validation** (normally not, so that users can review the rule during data entry). Click **Save**.


#### Creating validation rule groups

After you create validation rules, group them. Groups of similar validation rules help in particular when you review the rules together in bulk analysis.

In the **Maintenance** app, go to **Validation** > **Validation rule group**. Add a new group with a name, code, and description. Move the related validation rules from the left pane to the right pane, then click **Save**.

![The validation rule group form with malaria validation rules moved to the selected list on the right.](resources/images/dq_image48.png)

The best way to define groups depends on how data elements and data sets are structured in a particular implementation. Examples are:

* A group with all validation rules linked to data elements in one specific data set (for example, a monthly data set for malaria reporting).
* A group with all validation rules linked to data elements in one particular section of a data set (for example, a malaria section of an integrated HMIS data set).
* A group with all validation rules linked to data elements across several related data sets (for example, across separate malaria testing and malaria treatment data sets).

#### Review validation rule violations in the data entry app

You can also run validation rules in the Data entry app. Click **Run validation** at any time, or click **Mark complete** if you want to complete the data set.

![The bottom bar of the Data entry app with the Run validation and Mark complete buttons highlighted.](resources/images/dq_image29.png)


The results show in the **Validation** panel on the right side of the app. The panel shows the number of High, Medium, and Low priority violations, and lists the violations in a color that matches their priority. The new app shows the violations slightly differently from the previous Data entry app. It shows the instruction, then the left side and its value, the operator, and the right side and its value.

![The Validation panel in the Data entry app with an alert summary and one medium priority violation.](resources/images/dq_image68.png)

Review the values for each of these rules, and decide if you can correct them before you continue with other work in DHIS2.

Ideally, create validation rules before you train staff on data entry for a program. You can then include validation violations and how to correct them in the training. During training, make sure that all data sets pass validation, where possible, before submission.


#### Review validation rule violations in data entry (DHIS2 v41 and earlier)

After you create the validation rules you need, use them to check your data routinely. You can review validation rules both in data entry and through [validation rule analysis](data-quality-03-analysis.md) in the Data Quality app. When you review validation rules, DHIS2 shows only the rules that are violated, not the rules that pass.

To check the data in the Data entry app, scroll to the top or bottom of the data set and click **Run validation**. (Validation rules also run when you click **Complete** at the bottom of the data entry screen.)

![The Data entry app with the Run validation button highlighted.](resources/images/dq_image15.png)

This runs all validation rules that use data elements in the data set you chose.

A pop-up window shows the validation rules that are violated.

![The Validation Result window listing violated rules with their left side, operator, and right side values.](resources/images/dq_image75.png)

The window shows several violations, including the rule created in the previous section. Review each of these rules to make sure that the data values in this data set are entered correctly before you finish data entry. If possible, correct wrong values to reduce errors at the source of collection.

In the example, there is an obvious error that you should change to the correct value:

![The Positive (RDT) value 2 highlighted in the data entry form, where Tested (RDT) is 4.](resources/images/dq_image18.png)

![The Positive (RDT) value 200 highlighted in the data entry form, where Tested (RDT) is 4.](resources/images/dq_image7.png)

If you correct all the errors that validation found for this data set, period, and organisation unit, and then run validation again, DHIS2 shows a message that validation passed.

![The Validation Result window with the message that the data entry screen passed validation.](resources/images/dq_image59.png)


### Validation rule notifications

Validation rule notifications let you create messages that DHIS2 sends when a validation rule is violated. A notification consists of the validation rules that trigger it, the recipients, and the message about the violation. DHIS2 can send notifications to recipients in three ways: email, SMS, and the DHIS2 internal messaging service. For more information, see the documentation on configuring [email](https://docs.dhis2.org/en/use/user-guides/dhis-core-version-master/configuring-the-system/system-settings.html?h=system+settings+master+use#system_email_settings) and [SMS](https://docs.dhis2.org/en/use/user-guides/dhis-core-version-master/maintaining-the-system/configure-sms.html). The following image shows an example of a validation rule notification sent by email.

![An email from DHIS2 that reports one medium priority validation violation for Positive (RDT) and Tested (RDT).](resources/images/dq_image4.png)

When you create and use validation rule notifications, take care that recipients do not ignore the messages. Keep the number of notifications low, so that users do not receive too many messages. Experience shows that when users receive too many messages, they tend to ignore them, and real problems are not fixed. In general, create notifications only for priority areas of correction, and send them only to the users who need to see them. You can find other violations through routine data quality review procedures.

Validation rule notifications use user groups to define the recipients. To learn how to create a user group in DHIS2, see the [documentation on user groups](https://docs.dhis2.org/en/use/user-guides/dhis-core-version-master/configuring-the-system/users-roles-and-groups.html#mgt_usergroup).

#### Configuring validation notifications

In the **Maintenance** app, go to **Validation** > **Validation Notification** and add a new notification. Fill in the key fields:

1. **Name** (and optionally a code).

2. **Validation rules**: the rules that trigger this notification. To make messages easier to understand, it is generally best to use only one validation rule per notification. If the recipients have access to several organisation units, there can be several violations in a given period, and the message identifies each violation.

3. **User groups**: the groups that receive the notification. The user groups must exist (see the [documentation on user groups](https://docs.dhis2.org/en/use/user-guides/dhis-core-version-master/configuring-the-system/users-roles-and-groups.html#mgt_usergroup)). Users must have the relevant contact information filled in, for example an email address for email notifications. Target only the users who need to receive and act on the information.

4. **Notification strategy**: how DHIS2 sends notifications when it detects several violations (over several organisation units, periods, or both):
    1. **Collective summary**: DHIS2 summarizes all detected violations in one email, SMS, or DHIS2 message.
    2. **Single notification**: one message per violation. Use this option sparingly, for high priority violations.

5. **Message template**: what the message looks like. It consists of plain text and template variables that DHIS2 replaces with values.

![An example notification email with numbered markers on the subject and on each value that replaces a template variable.](resources/images/dq_image11.png)

The following example of an output message shows how template variables and plain text appear in a notification when DHIS2 sends it.

![The Message template section with the subject template, the message template, and the list of template variables.](resources/images/dq_image6.png)

1. This is the subject template in the message. Each violation shows the subject before the contents of the message template.
2. The template itself has a mix of free text and variables. The first variable is the left side description. In the message, DHIS2 replaces it with Positive (RDT).
3. This is the left side value. In the actual message, DHIS2 replaces it with the value stored in DHIS2.
4. This is the operator for the validation rule.
5. This is the right side description, replaced with Tested (RDT) in the message.
6. This is the right side value, taken from DHIS2.
7. This is the organisation unit.
8. This is the period.

You can use several different variables to create the message and give the correct details to the person who reviews the notification.

To create the template, enter free text and choose the variables you need from the **Template variables** list on the right side of the screen.


When you have filled in these fields, click **Save**.


### Recommendation on validation rules configuration

Validation rules help prevent data entry errors. But if they are not configured in an appropriate way, they can also be a source of error by nudging users to “fix” mistakes.

In some cases, you might want to create validation rules for checks that are _most often_ real data quality problems, but that DHIS2 can flag falsely. An example of this is the comparison between women making their first (ANC1) and fourth antenatal care visit (ANC4). Across the whole population, the number of ANC1 visits should be greater than or equal to the number of ANC4 visits. Every woman making a fourth visit has also made the first visit, but inevitably some women do not come to their fourth appointment. So ANC4 should always be less than or equal to ANC1. However, this is _not appropriate as a validation rule_, because ANC visits are spread over several months, and women can make different visits in different health facilities. For example, a health facility can have 100 ANC 1 visits and 74 ANC 4 visits in a year (ANC 1 ≥ ANC 4), but in one month there could be 9 women making their 4th visit and only 8 making their first visit (ANC 1 &lt; ANC 4). This is not a data quality problem, but a validation rule comparing ANC1 and ANC4 would record it as one.

Do _not_ create validation rules in these cases. The validation rule warning can confuse the data entry user, and in the worst case they might edit the data to meet the validation rule criteria. If you _do_ create this type of validation rule, it show have low priority and the message to users should clearly say that they should examine the warning, but that it might not be an actual data quality problem in all cases.

Many of the aggregate metadata packages in the [health data toolkits](https://dhis2.org/metadata-downloads/) include examples validation rules for different health programs.


## Min-max values

The min-max functionality in DHIS2 is a set of features that lets you check for outliers in the data _during data entry_. The min-max value is based on setting minimum and maximum accepted values for a combination of data element, category option combination, and organisation unit. During data entry, DHIS2 highlights values outside these minimum and maximum thresholds in the data entry screen. As with validation rules, if a data value is outside the boundaries that the min-max values define, DHIS2 still lets you save the value. However, DHIS2 highlights the value in the data entry screen and shows a dialog that the user must acknowledge.

The min-max functionality has two main advantages:

* It lets you detect and flag data quality issues at the point of data entry, so that the person entering data can check the data right away and correct typos and so on.

* Min-max values can be set for any numeric data element that has a minimum of historical data, even when there is no logical relationships that lets you create validation rules.

For data sets disaggregated with an attribute category combination, the min-max values apply to all attribute option combinations.


### Configuring min/max values

You can set min-max values manually in the data entry app, or use methods that calculate minimum and maximum values from historical data with statistical methods. This guide does not recommend using the built-in DHIS2 tool to generate min-max values. For the reasons, see [Limitations with min/max values](#limitations-with-minmax-values).


You can currently view and _edit_ the min-max values in the data entry apps. You can list values that *violate* the min-max thresholds in bulk with the Data Quality app, as described in [Review min-max values in the Data Quality app](#review-min-max-values-in-the-data-quality-app).

#### Viewing and configuring min/max values in the data entry app

In the Data entry app, to see min-max values, choose an input field (that is, a cell for data entry) and click **View details** in the toolbar at the bottom of the app.

![The toolbar at the bottom of the Data entry app with the View details button highlighted.](resources/images/dq_image104.png)

A details panel opens on the right side of the screen, with a separate section for min-max limits. All users can see the min-max values that are set, and users with the appropriate permissions can also edit or delete them.

![The Min and max limits section of the details panel, with the Edit limits and Delete limits buttons.](resources/images/dq_image20.png)


#### Viewing and configuring min/max values in the data entry app (DHIS2 v41 and earlier)

In the Data entry app, double-click an input field (that is, a cell for data entry) to open a pop-up window with information about that data element and category option combination.

![The data value pop-up window in the Data entry app, with the min-max limits section and a data element history chart that shows the max value.](resources/images/dq_image86.png)

The **Min-max limits** section in the top right corner of the window shows the min-max limits that are set. Users with the appropriate permissions can remove limits or save new ones. These values then apply to that combination of data element, category option combination, and organisation unit. If a maximum value is set, the **Data element history** graph also shows it.


#### Built-in generator

DHIS2 can generate and remove min-max values in bulk for one or more data sets and a selection of organisation units. This function is in the Data Administration app. To generate or remove min-max values in bulk:


1. Open the **Data Administration** app.
2. Choose the **Min-Max Value Generation** section.
3. Choose one or more data sets for which you want to generate min-max values. DHIS2 generates or removes min-max values for all data elements with category option combinations in that data set.
4. Choose the organisation unit boundary to generate values for. DHIS2 generates or removes min-max values for all organisation units below the chosen organisation unit, including the chosen organisation unit itself.
5. Click **Generate min-max values** or **Remove min-max values**.

DHIS2 generates min-max values only for combinations of data element, category option combination, and organisation unit that already have data. This does not depend on how the data set is assigned.

![The Min-Max Value Generation section of the Data Administration app, with numbered markers on the section, the data sets, the organisation unit tree, and the generate and remove buttons.](resources/images/dq_image34.png)

DHIS2 generates min-max values by calculating the mean of all existing data values for a given combination of data element, category option combination, and organisation unit. It then calculates lower and upper bounds a certain number of standard deviations from this mean. The number of standard deviations comes from a system setting called **Data analysis std dev factor**. The default value is 2 standard deviations. You can change it in the System Settings app, in the **General** section.

![The General section of the System Settings app with the Data analysis std dev factor setting set to 2.](resources/images/dq_image97.png)


##### Limitations with min/max values

As a general rule, do not use the Min-Max value generation tool with its current functionality. It has several major limitations that cause it to generate min-max values that are too restrictive. As a result, DHIS2 flags too many values as possibly wrong in the data entry app. This is a nuisance to data entry staff, and it can lead them to incorrectly edit values so that they are within the limits.

In _some_ cases this function can work well enough to use. This requires enough historical data for the statistical analysis, data that is reasonably normally distributed (that is, not seasonal and not changing over time), and no facilities that always report very low numbers. In reality, there are very few cases where this is true. In practice, one or more of these requirements are most often _not_ met:



* Some small health facilities consistently report very low numbers every month. In a hypothetical example, a health facility reports values of 2 or 3 every second month in one year. The thresholds at 2 standard deviations above and below the mean are 1.5 and 3.5. In other words, if the facility reports 1 or 4 in a month, the value is outside the threshold.

* Data is very often _not_ normally distributed. The typical example is data associated with rainy seasons, such as malaria. However, even data that is not typically considered seasonal has some months in the year with higher or lower numbers, for example reproductive health (and as a consequence immunizations, PMTCT, and so on).

* DHIS2 generates min-max values for all combinations of data element, category option combination, and organisation unit that have any value. For example, even if a health facility recently started reporting in DHIS2 and data exists for only a couple of months, DHIS2 generates min-max values, but from a very limited basis.

* The built-in min-max generation can use only the _mean_ of the existing data, so it is sensitive to any existing outliers.


#### Custom generation of min-max values

The [DHIS2 API](https://docs.dhis2.org/en/develop/using-the-api/dhis-core-version-master/maintenance.html#webapi_min_max_data_elements) lets you save and remove min-max values. You can therefore generate the min-max values outside DHIS2 with other tools, and then import them through the API. A limitation of this approach is that the API lets you POST or DELETE only _individual_ values (for one combination of data element, category option combination, and organisation unit). However, min-max values do not need to be updated often (unlike analytics, for example), so you can work around this limitation.


#### Generating min-max values with the DQ Workbench

The recommended way to generate min-max values is the [Data Quality Workbench](https://github.com/dhis2/tool-dq-workbench). This server-side tool has several data quality monitoring functions, and it can generate and routinely update min-max values through the DHIS2 API. It is designed to address the main shortcomings of the built-in min-max generation functionality:

* It lets you set different parameters according to the median values that organisation units report. For example, min-max for small facilities can be based on the previous highest values rather than standard deviations, while larger facilities can have a stricter statistical threshold.

* It lets you set a minimum completeness of historical data for a combination of data element and organisation unit before it generates min-max values for it, so that ranges are not based on sparse data.

* It supports several statistical methods that suit health data better than the built-in mean ± SD approach: previous maximum, z-score, median absolute deviation (MAD), interquartile range (IQR), and Box-Cox transformation (which normalizes the data before setting thresholds, to work better with data that is not normally distributed).

The [GitHub repository](https://github.com/dhis2/tool-dq-workbench) has detailed documentation on installation (Windows installer or Docker) and configuration. As with any bulk generation of min-max values, review the generated ranges in a test environment before you apply them to a production system.

#### Review min/max values in data entry

Users do not need to do anything to review min-max values in the Data entry app. When someone enters a number outside the min-max limits, a pop-up window with a warning message appears right away, and DHIS2 highlights the cell in dark orange.

![A warning pop-up in the Data entry app saying that the value of BCG doses given is greater than the maximum value of 50.](resources/images/dq_image91.png)
![The BCG doses given cell with the value 60 highlighted in dark orange.](resources/images/dq_image101.png)


When you mark the data set as complete or click **Run validation**, DHIS2 also lists the min-max violations, in a similar way to validation rule violations.

![The Validation Result window listing BCG doses given as an outlier with the value 60, a min of 5, and a max of 50.](resources/images/dq_image51.png)

#### Review min-max values in the Data Quality app

You can review min-max values in bulk with **Outlier detection** in the Data Quality app. **Min-max values** is one of the options in the **Algorithm** menu.

![The Outlier Detection page of the Data Quality app with Min-max values chosen as the algorithm.](resources/images/dq_image110.png)


To analyze values outside the min-max thresholds:

1. Choose one or more data sets to analyze.
2. Choose one or more organisation units.
3. Set the start and end date.
4. Choose **Min-max values** as the **Algorithm**.
5. Click **Start**.

The result is a list that shows the data element, period, and organisation unit where a value outside the min and max thresholds was reported.

![The Outlier Detection results table with data element, period, organisation unit, value, deviation, min, max, and follow-up columns.](resources/images/dq_image87.png)

The **Value** column is the reported data value. **Deviation** is how far the number is above the max threshold or below the min threshold, and the **Min** and **Max** columns show the min-max thresholds for the data element and organisation unit. The table is sorted by deviation, because the violations with the highest deviation have the biggest impact on the overall data. **Follow-up** lets you mark data values for follow-up, so that you can review them later with the [Follow-up analysis](https://docs.dhis2.org/en/use/user-guides/dhis-core-version-master/collecting-data/data-quality.html?h=follow-up+anal+master+use#about-follow-up-analysis) function.
