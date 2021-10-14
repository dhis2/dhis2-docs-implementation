# Extended Metadata Assessment - Detailed Description of Items to Review

## Dashboards

### Dashboards should have content

All dashboards should have content on them. Dashboards without any content do not serve any purpose, and may have been created by accident or as part of a training exercise.

#### Recommendation

Dashboards without content that have not been modified in the last 14 days can be removed.

#### Diagnosing if the problem exists

Dashboards that do not have any content can be identified via the SQL View "X" or within the R-Markdown report. This will identify both the number of dashboards that do not have content as well as provide you with a list of dashboard items to review.

---

### Dashboards should be viewed routinely

All dashboards should be reviewed routinely. Dashboards that are no longer viewed routinely are not being used, or potentially being used incorrectly. The definition of "routine" may vary between implementations and therefore you can assess this over both the last 12 months as well as a pre-defined period of your choosing.

#### Recommendation

Dashboards that are not viewed routinely and are no longer needed can be removed.

Dashboards that should be reviewed routinely and are not point to a broader data use issue that will not be addressed by technical means. Such dashboards may need to be kept while a process for reviewing them more frequently becomes more well defined.

#### Diagnosing if the problem exists

Dashboards that are not viewed routinely can be identified via the SQL View "X" or within the R-Markdown report. This will identify both the number of dashboards that are not viewed routinely as well as provide you with a list of dashboard items to review and is separated into the following categorizations:

- Dashboards that have been viewed 1 time or less since the year you select
- Dashboards that have not been opened in the last 12 months
- Dashboards that are publicly viewable
- Public dashboards that have been viewed 1 time or less since the year you select
- Public dashboards that have not been opened in the last 12 months

---

### Dashboards should be shared (when appropriate)

Dashboards should be shared so they can be used appropriately throughout the system. In cases where individual, private dashboards are made, these should serve a very specific purpose unique to the user that created it.

#### Recommendation

- The number of private dashboards should be less then the number of shared dashboards
- Private dashboards that are no longer in use can be deleted
- Private dashboards in which more users need access to them should have the correct sharing settings applied to them

#### Diagnosing in the problem exists

Dashboards that are note shared can be identified via the SQL View "X" or within the R-Markdown report. This will identify both the number of dashboards that are not shared as well as provide you with a list of dashboard items to review.

---

## Data Elements

### Data elements should be in a data element group

All data elements should be in a data element group. This allows users to find the data elements more easily in analysis apps and also contributes to having more complete data element group sets. Maintenance operations can also be made more efficient by applying bulk settings (ex. sharing) to all data elements within a data element group.

#### Recommendation

Data elements that are not in a data element group should be added to a relevant data element group. If the data elements are not needed, they should be deleted.

#### Diagnosing if the problem exists

Data elements that are not in a data element group can be found by running the data integrity check. You can also identify them via the SQL View "X" or within the R-Markdown report. This will identify both the number of data elements that are not within a group as well as provide you with a list of data elements items to review.

---

### Data elements should have data values

All data elements in a production database should have data values associated with them. If there are data elements that have been in the system for some time and do not have any data values associated with them, they are serving no purpose in the system. They may have been created during training or a development period.

#### Recommendation

Data elements that do not have any data values should be deleted. Data elements that should have recent data values but do not should be reviewed to determine if the program intends to keep reporting on them; if not these should be removed from the dataset or program they are associated with.

#### Diagnosing if the problem exists

We can review if data elements have any data values using different sets of criteria. This will allow you to determine in more detail if data elements need to be deleted or can be kept. The criteria we are currently summarizing for **AGGREGATE** data elements includes:

- "Abandoned" data elements. These are data elements that have not been updated in at least 100 days and do not have any data values associated with them.
- Data elements that have not been recently updated with data values (we defined this as data elements with no new values in the last 3 periods based on the data set period type associated with those data elements)
- Data elements with no values at all

You can retrieve this detail via the SQL View "X" or within the R-Markdown report. This will identify both the number of data elements that do not have values and provide you with a list of data elements items to review.

---

### Data elements should be used for analysis

All data elements that are captured in DHIS2 should be used to produce some type of analysis output (charts, maps, tables). This can be by using them directly in an output, or by having them contribute to an indicator calculation that is used an output. 

#### Recommendation

Data elements that are not routinely being reviewed in analysis, either directly or indirectly through indicators, should be reviewed to determine if they still need to be collected. If these are meant to be used in routine review, then associated outputs should be created using them. If these data elements are not going to be used for any type of information review, consideration should be made to either archive them or delete them.

#### Diagnosing if the problem exists

To review if data elements are being used in analysis outputs, we can review saved charts, maps and tables to determine if the data element is either directly or indirectly being used in these saved items.

You can retrieve this detail via the SQL View "X" or within the R-Markdown report. This will identify both the number of data elements that are not used in any saved analysis items and provide you with a list of these data elements to review.

---

## Data sets

### Data sets should have data

All **active** datasets should have data values associated with them. Active data sets are data sets which should be currently used (this is defined as within the last 3 reporting periods) to collect data.

#### Recommendation

- If a data set is not being updated with new data or no new data values are being entered within the last 3 periods (relative to the period type assigned to the dataset ex. monthly will be the last 3 months, quarterly the last 3 quarters) against the dataset **but** there are data values from previous periods the data set should be archived (ie. assign it a prefix)
- If a data set has no new or previous data values within the last 3 periods (relative to the period type assigned to the dataset) and will not be used to collect data, the data set should be removed.

#### Diagnosing if the problem exists

You can retrieve this detail via the SQL View "X" or within the R-Markdown report. This will identify both the number of data sets that do not have data within the last 3 reporting periods and provide you with a list of these data sets to review.

---

### Data sets should be assigned to organisation units

All **active** datasets should be assigned to an organisation unit. Active data sets are data sets which should be currently used (within the last 3 reporting periods) to collect data.

#### Recommendation

- Data sets that have not been recently updated (within the last 100 days) and are not assigned to any organisation units that **should be** active should be assigned to organisation units as appropriate
- Data sets that have not been recently updated (within the last 100 days) and **should not be** active should be marked as archived (ie. assign it a prefix)
- Data sets that have not been recently updated (within the last 100 days) and **do not have any data** should be deleted if they are not going be used. You can determine if a data set has data by reviewing the section ["Data sets should have data."](#data-sets-should-have-data)

#### Diagnosing if the problem exists

You can retrieve this detail via the SQL View "X" or within the R-Markdown report. This will identify both the number of data sets that that are not assigned to any organisation units and provide you with a list of these data sets to review.

---

## Indicators

### Indicators should be in an indicator group

All indicators should be in an indicator group. This allows users to find the indicators more easily in analysis apps and also contributes to having more complete indicators group sets. Maintenance operations can also be made more efficient by applying bulk settings (ex. sharing, filtering) to all indicators within an indicator group.

#### Recommendation

Indicators that are not in a indicator group should be added to a relevant indicator group. If the indicators are not needed, they should be deleted.

#### Diagnosing if the problem exists

Indicators that are not in an indicator group can be found by running the data integrity check. 

You can retrieve this detail via the SQL View "X" or within the R-Markdown report. This will identify both the number of indicators not within an indicator group and provide you with a list of these indicators to review.

---

### Indicators should be used in analysis outputs

All indicators that are calculated should be used to produce some type of analysis output (charts, maps, tables). This can be by using them directly in an output or providing direct feedback in a dataset.

#### Recommendation

Indicators that are not routinely being reviewed in analysis, either in an output or data set, should be reviewed to determine if they still need to be calculated. If these are meant to be used for routine review, then associated outputs should be created using them. If these indicators are not going to be used for any type of information review, consideration should be made to either archive them or delete them.

#### Diagnosing if the problem exists

To review if indicators are being used in analysis outputs, we can review saved charts, maps and tables to determine if the indicator is being used in saved output or within a data set.

You can retrieve this detail via the SQL View "X" or within the R-Markdown report. This will identify both the number of indicators that are not used in any saved analysis items and provide you with a list of these indicators to review.

---

## Indicators should be shared with a user group(s)

Depending on the system configuration, indicators may need correct sharing settings applied to them such that each indicator has the correct sharing settings applied to the indicator.

- In implementations where all indicators are public, then this principle can largely be ignored.
- In implementations where indicators have some sharing settings applied (or are meant to have some sharing settings applied), these should be applied uniformly so indicators can be accessed by the correct user group.

### Recommendation

If an indicator is not shared correctly, share it with the appropriate user group(s).

### Diagnosing if the problem exists

You can retrieve this detail via the SQL View "X" or within the R-Markdown report. This will identify both the number of indicators that are not shared and provide you with a list of these indicators to review.

---

## Organisation Units

### Organisation units at the lowest level of the hierarchy should have data sets assigned to them

Organisation units at the lowest level are often considered reporting units and should have data sets assigned to them.

#### Recommendation

#### Diagnosing if the problem exists

You can retrieve this detail via the the R-Markdown report within the section "Organisation Units." This will identify both the number of indicators that are not used in any saved analysis items and provide you with a list of these indicators to review.

---

### Organisation units should belong to all compulsory organisation unit group sets

#### Recommendation

#### Diagnosing if the problem exists

---

### Organisation units with data sets assigned to them should have completed data sets

#### Recommendation

#### Diagnosing if the problem exists

### Organisation units with data sets assigned to them should have data within those data sets

#### Recommendation

#### Diagnosing if the problem exists

---

### Organisation unit hierarchies should only have 1 ROOT level

#### Recommendation

#### Diagnosing if the problem exists


### Organisation units should be unique

#### Recommendation

### Diagnosing if the problem exists

---

## Charts, Tables, Maps

### Charts should be viewed routinely

The definition of "routine" may vary between implementations and therefore you can assess this over both the last 12 months as well as any pre-defined period of your choosing.

#### Recommendation

If a chart has been viewed 1 time or less within your definition of routine, it should be deleted.

#### Diagnosing if the problem exists

---

### Tables should be viewed routinely

The definition of "routine" may vary between implementations and therefore you can assess this over both the last 12 months as well as any pre-defined period of your choosing.

#### Recommendation

If a table has been viewed 1 time or less within your definition of routine, it should be deleted.

#### Diagnosing if the problem exists

---

### Maps should be viewed routinely

The definition of "routine" may vary between implementations and therefore you can assess this over both the last 12 months as well as any pre-defined period of your choosing.

#### Recommendation

If a map has been viewed 1 time or less within your definition of routine, it should be deleted.

#### Diagnosing if the problem exists

---

### Map points should be within the boundaries of their parent organisation unit boundaries

#### Recommendation

#### Diagnosing if the problem exists

---

## Users

### Users should log in routinely

All users should log in routinely. The definition of "routine" may vary between implementations and therefore you can assess this over both the last 12 months as well as a pre-defined period of your choosing.

#### Recommendation

- Users that have not logged in for the period defined as routine can likely be disabled.
- Users that have never logged in can likely be deleted.
- For users in which an invitation was sent but never activated their account two courses of action can be taken:
  - Delete the invitation
  - Resend the invitation for the user to activate their account

#### Diagnosing if the problem exists

---

### Users should be part of a user group

If there are any sharing settings applied, all users should be part of a user group.

#### Recommendation

If a user is not part of any user group(s) (or a user group(s) that gives them access to something they need), they should be added to the required user group(s).

#### Diagnosing if the problem exists