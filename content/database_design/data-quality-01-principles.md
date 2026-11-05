# Data quality principles

The DHIS2 approach for data quality follows what is outlined within the [WHO Data Quality Assurance (DQA) guidelines](https://www.who.int/data/data-collection-tools/health-service-data/data-quality-assurance-dqa). For the best results when you implement DHIS2 data quality features, review these guidelines as a reference to this toolkit. The DQA guidelines identify several frequencies for the review of data: 

_Routine review_

These should be regular reviews of data quality (for example weekly or monthly, depending on the frequency of data collection). They are built into a system of checks of the HMIS or other program reporting systems, as part of a feedback cycle that identifies errors in near real-time so that they can be corrected as they occur. This routine examination of data can be more holistic and either cross-cutting or program-specific. Different users of data can conduct it (for example national HMIS managers, program managers, district information officers, health facility staff).

_Discrete assessments_

These are needed to look at the quality of health facility data being used both to measure the performance of the health sector and also for policy and planning purposes. These assessments should be done before a planning cycle, such as before an annual health sector review (periodicity is country-specific, but likely most comparable to an annual cycle).

_Periodic review_

These should focus on a single disease or program area and should be timed to meet the planning needs of the specific program (for example before program reviews).

DHIS2 can support these different frequencies of data quality review. This toolkit focuses on measures involved in the routine review of data quality, because general observations indicate that this can be challenging to implement in practice. These routine practices can be built on and used for the purposes of discrete and periodic review as needed.


## Measuring data quality

A typical review of data quality assesses four measures of data quality:

1. Completeness and timeliness
2. Internal consistency
3. External consistency
4. Consistency of denominator data

### Completeness and timeliness

Completeness is measured either by reviewing reporting rates for an entire reporting form/data set or by reviewing the completeness of specific data elements within reporting forms. 

*Data set completeness: reporting rates*

In DHIS2, reporting rate completeness = Received reports/expected reports x 100%

* Received reports: the number of data sets for a given period and organisation unit which the data entry clerk has marked as complete, using the **complete** button in the data entry app

* Expected reports: the number of organisation units a data set is assigned to based on the reporting period the data set should be reported on. For a monthly data set assigned to 100 facilities, DHIS2 expects 100 reports in a month.

*Data set timeliness*

Reporting timeliness:  Received reports on time/expected reports x 100%


* Received reports on time: the number of data sets for a given period and organisation unit which have been marked as complete _within a deadline set for that particular data set_.

“On time” depends on the configuration within a country or organization, and is often based on procedures that have been locally defined. For example, in a monthly reporting form, “on time” could be defined as 15 days after the end of the previous reporting month. In that case, data for May that is submitted by 15 June is timely.

*Data element completeness*

The goal of a data element reporting rate is to assess the reporting consistency of a single variable. This is applicable to aggregate data elements only.

Data element completeness = Number of received values / Number of expected values x 100%

The [analysis section](data-quality-03-analysis.md) describes completeness and timeliness measures in DHIS2 in more detail.

### Internal consistency

Internal consistency is meant to compare internal data sources to determine if there are significant variations based on either statistical rules or logical comparisons. DHIS2 supports the review of internal consistency through several measures, including:


* Consistency between related variables
* Consistency over time
* Outlier analysis
* Validation rules
* Min-max analysis


### External consistency

External consistency is meant to compare your data with data from other sources. For example, you could compare data in a routine health information system with data collected from a survey. If this external data is imported into DHIS2, you can review external consistency with several comparative measures: the Data Visualizer app, the Data Quality Annual Report app, and validation rules.


### Consistency of denominator data

This measure reviews the denominators that are used to calculate coverage. This can involve aspects of both internal and external consistency. For example, comparing related census population estimates such as estimated pregnant women, estimated live births, and estimates of &lt;1 year would be an internal comparison. Comparing these census measures with UN population estimates would be an example of external consistency.
