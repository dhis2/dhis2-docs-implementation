# Data Integrity Check

| **Data Elements**                                                                                                                |   |
|------------------------------------------------------------------------------------------------------------------------------|---|
| Data elements should be in a data element group                                                                              |   |
| Data elements should be assigned to a data set                                                                               |   |
| Data elements in a data set should be assigned to either sections or the custom form                                         |   |
| Data elements should belong to one group within a group set                                                                  |   |
| Data elements should be assigned to data sets of only one period type                                                        |   |
| **Indicators**                                                                                                                   |   |
| Indicators should be unique                                                                                                  |   |
| Indicators should be in an indicator group                                                                                   |   |
| Indicators should have a valid numerator                                                                                     |   |
| Indicatrors should have a valid denominator                                                                                  |   |
| Indicators should belong to one group within a group set                                                                     |   |
| **Data Sets**                                                                                                                    |   |
| Data sets should be assigned to organisation units                                                                           |   |
| **Organisation Units**                                                                                                          |   |
| Organisation units should be in at least one organisation unit group                                                         |   |
| Organisation units should belong to all compulsory organisation unit group sets                                              |   |
| Organisation units should belong to only one organisation unit group within a single organisation unit group set             |   |
| Organisation units should belong to at least one organisation unit group set                                                 |   |
| Organisation units should be assigned an organisation unit level                                                             |   |
| Organisation units should be                                                                                                 |   |
| **Validation Rules**                                                                                                           |   |
| Validation rules should be in a validation rule group                                                                        |   |
| Validation rules should have a valid left side expression                                                                    |   |
| Validation rules should have a valid right side expression                                                                   |   |
| **Program Rules**                                                                                                               |   |
| Program rules should have a condition within their expression                                                                |   |
| Program rules should have a priority                                                                                         |   |
| Program rules should have at least one action                                                                                |   |
| Program rule variables with source types of Tracked Entity Attribute should have a tracked entity attribute assigned to them |   |
| Program rule variables with source types of Data Element should have a data element assigned to them                         |   |
| Program rule actions should have a data object assigned to them                                                              |   |
| Program rule actions of either send or schedule message should have a message template assigned to them                      |   |
| Program rules actions that hide a section should have a section ID assigned to them                                          |   |
| Program rules actions that hide a program stage should have a program stage ID assigned to them                              |   |
| **Program Indicators**                                                                                                           |   |
| Program indicators should have a valid indicator expression                                                                  |   |
| Program indicators should have a valid indicator filter expression                                                           |   |