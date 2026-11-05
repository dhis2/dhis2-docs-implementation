# Data quality

Good data quality is a prerequisite for using health data for decision making, and DHIS2 has a wide range of functionality for preventing, detecting, and assessing data quality issues. This chapter covers both the principles behind data quality work in DHIS2 and the practical configuration and implementation of data quality functionality. The guidance assumes DHIS2 version 2.41 or later.

The functionality can be thought of in four complementary roles: *preventing* errors from entering the system (well-designed data collection tools, validation rules, and min-max thresholds at data entry), *identifying* issues in data already reported (completeness, consistency, and outlier analysis), *monitoring* data quality over time (dashboards with configured metrics, and stored counts of outliers and validation rule violations), and *fixing* issues in a controlled way (SOPs and supervision).

The chapter is organized as follows:

* [Principles](data-quality-01-principles.md): the overall approach to data quality in DHIS2, following the WHO Data Quality Assurance (DQA) framework, including the review frequencies (routine, discrete, periodic) and the four measures of data quality (completeness/timeliness, internal consistency, external consistency, and consistency of denominators).
* [Data entry](data-quality-02-data-entry.md): detecting and preventing errors as early as possible through the design of data entry forms, validation rules and validation notifications, and min-max values.
* [Analysis](data-quality-03-analysis.md): assessing the quality of data already in DHIS2, including completeness and timeliness of data sets and data elements, facilities consistently reporting, consistency between related variables (scatter plots, validation rule analysis), and consistency over time (year-over-year charts, outlier metrics, outlier tables, and outlier analysis). This section also introduces the *configured data quality metrics* and the **DQ Metrics Configuration Tool** used to configure them, and describes how to transition away from the WHO Data Quality Tool which is no longer maintained.
* [Denominators](data-quality-05-denominators.md): assessing the quality of the population estimates used as denominators in coverage indicators.
* [Implementation](data-quality-04-implementation.md): making data quality functionality actually used, through data quality dashboards for different user groups, validation notifications, minimum implementation standards, standard operating procedures (SOPs), and the required scheduling and server configuration.
* [Supervision](data-quality-07-supervision-web.md): user guides for the Supervision App ([web](data-quality-07-supervision-web.md) and [Android](data-quality-06-supervision-android.md)), supporting planning, execution, and follow-up of data quality supervision visits.

If you are looking for something specific:

| I want to... | Go to |
|---|---|
| Prevent impossible values from being entered | [Data entry](data-quality-02-data-entry.md): validation rules, min-max values |
| See how complete reporting is | [Analysis](data-quality-03-analysis.md): data set and data element completeness |
| Find suspicious values in reported data | [Analysis](data-quality-03-analysis.md): outlier tables, outlier analysis, configured outlier metrics |
| Configure data quality indicators for dashboards | [Analysis](data-quality-03-analysis.md): configured data quality metrics |
| Check whether population denominators are plausible | [Denominators](data-quality-05-denominators.md) |
| Plan a data quality implementation or SOPs | [Implementation](data-quality-04-implementation.md) |
| Digitalize supervision visits | [Supervision](data-quality-07-supervision-web.md) |
