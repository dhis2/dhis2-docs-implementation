# Data Quality Principles

The DHIS2 approach for data quality follows what is outlined within the [WHO Data Quality Assurance (DQA) guidelines](https://www.who.int/data/data-collection-tools/health-service-data/data-quality-assurance-dqa). For the best results in implementing DHIS2 data quality features, it is recommended that you review these guidelines as reference to this toolkit. In the DQA guidelines, several frequencies for the review of data are identified: 

_Routine Review_

These should be regular (e.g. weekly/monthly etc. depending on the frequency of data collection) reviews of data quality built into a system of checks of the HMIS or other program reporting systems as part of a feedback cycle that identifies errors in near real-time so they can be corrected as they occur. This routine examination of data can be more holistic and either cross-cutting or programme-specific, and can be conducted by different users of data (e.g. HMIS managers, program managers, etc.).

_Discrete Assessments_

These are needed to look at the quality of health facility data being used both to measure the performance of the health sector and also for policy and planning purposes. These assessments should be carried out before a planning cycle, such as in advance of an annual health sector review (periodicity is country-specific, but likely most comparable to an annual cycle).

_Periodic Review_

These should focus on a single disease or program area and should be timed to meet the planning needs of the specific program (e.g. prior to program reviews).

DHIS2 is able to support these different frequencies of data quality review. This toolkit will focus on measures involved in the routine review of data quality as general observations indicate this can be challenging to implement in practice. These routine practices can be built on and used for the purposes of discrete and periodic review as needed.


## Measuring data quality

During a typical review of data quality, there are 4 measures of data quality that are typically assessed:



1. Completeness and Timeliness
2. Internal Consistency
3. External Consistency
4. Consistency of denominator data


### Completeness and Timeliness

Completeness is measured either by reviewing reporting rates for an entire reporting form/data set or by reviewing the completeness of specific data elements within reporting forms when additional accuracy is required. 

<span style="text-decoration:underline;">Data set completeness - reporting rates</span>

In DHIS2, reporting rate completeness = Received reports/expected reports x 100%

* Received reports: the number of data sets for a given period and organisation unit which have been marked as complete by the data entry clerk, using the “complete” button in the data entry app

* Expected reports: the number of organisation units a data set is assigned to based on the reporting period the data set should be reported on. For a monthly dataset assigned to 100 facilities we expect 100 reports in a month.

<span style="text-decoration:underline;">Data set timeliness</span>

Reporting timeliness:  Received reports on time/expected reports x 100%


* Received reports on time: the number of data sets for a given period and organisation unit which have been marked as complete _within a deadline specified for that particular data set_.

“On time” is dependent on the configuration within a country or organization, and is often based on procedures that have been locally defined. For example, in a monthly reporting form on time could be defined as 15 days after the end of the previous reporting month. In that case, submitting data by June 15 for May data would be considered timely.

<span style="text-decoration:underline;">Data element completeness</span>

The goal of a data element reporting rate is to assess the reporting consistency of a single variable. This is applicable to aggregate data elements only.

Data element completeness = Number of received values / Number of expected values x 100%

This section[LINK] in this toolkit describes completeness and timeliness measures in DHIS2 in more detail.

### Internal Consistency

Internal consistency is meant to compare internal data sources to determine if there are significant variations based on either statistical rules or logical comparisons. In DHIS2, we can support the review of internal consistency through several measures including:


* Consistency between related variables
* Consistency over time
* Outlier analysis
* Through the use of validation rules
* Min-max analysis

These are described in more detail within this section[LINK]


### External Consistency

External consistency is meant to compare your data with data from other sources. For example, you could compare data in a routine health information system with data collected from a survey. If this external data is imported into DHIS2, several comparative measures can be used to review external consistency via data visualizer, the WHO data quality app and through the use of validation rules.

This is described in more detail within this section[LINK]


### Consistency of denominator data

This measure reviews the denominators that are used to calculate coverage. This can involve aspects of both internal and external consistency. For example, comparing related census population estimates such as estimated pregnant women, estimated live births and estimates of &lt;1 year would be an internal comparison; while comparing these census measures with UN population estimates would be an example of external consistency. 

This is described in more detail within this section[LINK]
