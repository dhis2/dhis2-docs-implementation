# Metadata Management - Detailed Description of Items to Review

## Dashboards

### Dashboards should have content

All dashboards should have content on them. Dashboards without any content do not serve any purpose, and may have been created by accident or as part of a training exercise.

#### Recommendation

Dashboards without content that have not been modified in the last 14 days can be removed.

#### Diagnosing if the problem exists

Dashboards that do not have any content can be identified via the SQL View "X" or within the R-Markdown report. This will identify both the number of dashboards that do not have content as well as provide you with a list of dashboard items to review.

---

### Dashboards should be viewed routinely

All dashboards should be reviewed routinely. Dashboards that are no longer viewed routinely are not being used and serve no purpose within the system. The definition of "routine" may vary between implementations and therefore you can assess this over both the last 12 months as well as a pre-defined period of your choosing.

#### Recommendation

Dashboards that are not viewed routinely can be removed.

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

You can retrieve this detail via the SQL View "X" or within the R-Markdown report. This will identify both the number of data elements that are not used in any saved analysis items and provide you with a list of these saved items to review.

---