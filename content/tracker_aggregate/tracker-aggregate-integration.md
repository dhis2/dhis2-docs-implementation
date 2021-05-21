# Integrating tracker and aggregate data
This guide presents different approaches for combining data collected through tracker programmes with aggregate data, so that it can be analysed and used together. Tracker and aggregate data are collected and stored separately in DHIS2, but there are many cases where combining the two types of data is useful: 

* Data collected through tracker programmes and aggregate data sets may be complimentary. For example, if tracker is used as an electronic immunisation registry, calculating immunisation coverages requires the service data collected through tracker to be combined with population estimates typically available as aggregate (yearly) data.
* In many cases, tracker implementations are done in a phased approach, where it is first implemented in certain types of health facilities or by geographical region. Consequently, the same data may be collected through tracker in some locations and as aggregate data in other locations, and getting a complete overview of the data requires the tracker and aggregate data to be combined.
* Data collected through tracker may partially overlap with established aggregate reports. For example, a monthly report on malaria-related activities [(example)]() may include information both on malaria cases, as well as preventive activities such as bed-net distribution. If tracker is introduced for malaria case registration, the monthly malaria report can be partially completed based on tracker data.
* When tracker is introduced for in an area (immunisation, HIV etc) where aggregate data has previously been collected, ensuring that data is comparable over time necessitates combining aggregate and tracker data.
* Certain data quality checks in DHIS2 is only available for aggregate data. Applying these checks on tracker data thus requires that it is first aggregated and stored as aggregate data elements.
 
There are several ways in which this can be achieved, with different advantages and disadvantages, and which are suitable for different purposes. In the [next section](alternative-approaches) three overall approaches to combining tracker and aggregate data, followed by a section on [choosing an approach](#choosing-an-approach) that outlines considerations and examples of when each of the approaches may be appropriate. Finally, for each approach, a how-to guide is outlining how to use the approach.

## Alternative approaches
There are three main ways in which tracker and aggregate data can be combined in DHIS2 by:

- showing data side by side in the same chart, table or dashboard
- combining data through aggregate indicators
- saving aggregates calculated from tracker data as aggregate data values

This section gives a summary of the three approaches, with the advantages and disadvantages of each.

### Showing tracker and aggregate data side by side
Aggregate and tracker data can be shown and analysed together by including it within the same Data Visualizer charts or tables. Furthermore, visualisations of tracker-based data can be created in the Event Report and Event Visualizer apps, and combined with visualisations of aggregate data on Dashboards.

{Example screenshot}

* Brief summary on how this is done

> **Advantages:**
>
> * easy to set up
> * works well for presenting and analysing complimentary data
> * detailed data can be included (e.g. anonymous line lists)
>
> **Disadvantages:**
>
> * limited dimensionality in analysis of tracker data, i.e. for showing age/sex disaggregations
> * not truly integrated/comparable with aggregated data, for example displayed
> * requires the tracker and aggregate data to be in the same DHIS2 instance


### Combining data through aggregate indicators
Aggregate indicators can be based on both aggregate and tracker data, separately or combined in a single aggregate indicator. Tracker data elements, tracked entity attributes and program indicators can all be included in the calculation of aggregate indicators.

This approach can be useful in several scenarios: 

* The same data is collected through aggregate data set and tracker programmes in different health facilities, i.e. some collect aggregate data and others collect individual-level data through tracker.
* The same data is available as aggregate data values and tracker data values for different periods, for example if data currently collected through tracker was in previous years collected as aggregate data.
* When indicators are needed based on a combination of data, i.e. service data collected through tracker combined with denominators available as aggregate data. 

{Example screenshot}

* Brief summary on how this is done

> **Advantages:**
>
> * relatively easy to set up
> * can potentially hide some of the complexity of integrated aggregate and tracker data to end users
> 
> **Disadvantages:**
>
> * tracker data cannot be analysed with disaggregations such as age/sex as separate data dimensions
> * difficult to manage in cases where there may be overlapping data
> * requires the tracker and aggregate data to be in the same DHIS2 instance

### Saving aggregates of tracker data as aggregate data
Tracker data can be aggregated to, for example, weekly or monthly values, and these values can be saved as aggregate data element values in DHIS2. This corresponds to what is often done manually in health facilities when registers are tallied every month to produce monthly reports. Program indicators can be defined that produce aggregate numbers based on tracker data, corresponding to aggregate data elements. The program indicator value should represent the same value as the aggregate (e.g. *number of new and relapsed TB cases notified* or *number of BCG doses given to children under 1*. The data transfer can be done on an ad-hoc basis as needed, or as part of a routine process where data is (automatically) transferred at fixed intervals (show in the figure below).

![Example: Information flow between a DHIS2 instance with tracker programmes, and a DHIS2 HMIS instance with aggregate data.](resources/images/image8.jpg)

![Example: Aggregate data set (in the data entry app) which has been automatically filled by the data pushed from tracker program indicators.](resources/images/image5.png)

There are multiple ways in which actual transfer of data from program indicators to aggregate data elements can be done. This includes: 

* manually or via a script querying the [DHIS2 API]() to export the program indicator values, and subsequently importing them into DHIS2 using either the [Import/export app]() or the API
* automating the export and import of data from the API using a script
* using one of several applications developed by the DHIS2 community and available on the [DHIS2 App Hub](apps.dhis2.org) to export and import the data
* setting up [Predictors](), which can be scheduled to transfer the program indicator values into aggregate data elements routinely

This approach is described in further details below, with examples and pointers to different tools which can be used to facilitate the process.

> **Advantages:**
>
> * data can be analysed with all the dimensionality as aggregate data (see example screenshot below)
> * can still be combined with detailed tracker data (i.e. the first approach)
> * ensures that there is no overlap
> * works when tracker and aggregate data are collected in separate DHIS2 instances
>
> **Disadvantages:**
>
> * more complicated to set up
> * requires external tools/scripts to move data via api, or predictors
> * if data is moved between two DHIS2 instances, organisation units must also be harmonised and kept in sync across the instances
> * may require more ongoing maintenance

![Example: TB Case Surveillance to aggregate quarterly TB report for TB notifications. Program indicator data values from tracker data (data elements/disaggregation can be produced, but not pivoted by dimensions as gender, age group)](resources/images/image4.png)

![Example: Aggregate dashboard output (with ability to pivot male/female as a data dimension)](resources/images/image1.png)


## Choosing an approach
Each of the three approaches have advantages and disadvantages, as outlined above. For a single implementation, several of them are likely needed. For example, it may be useful to present certain tracker data with frequent updates (i.e. daily numbers children immunised), while at the same time transferring aggregate program indicator values into aggregate data element values every month so that the data can be compared with facilities not yet using tracker, or with additional dimensionality (such as age/sex disaggregations) that cannot easily be done directly with aggregate data.

The first two approaches are both relatively straightforward to implement, using the standard applications built into DHIS2. While configuring aggregate indicators (the second approach) must be done by a systems administrator with access to configure such indicators, any user with access to the DHIS2 analysis apps can make use of these approaches. However, a major limitation is that they require the tracker and the aggregate data to be in the same instance of DHIS2. 

For countries implementing DHIS2 tracker for individual-level data collection, a separate dedicated DHIS2 instance is recommended for tracker deployment. Many countries have a mature, stable HMIS used primarily for capturing aggregate data across health programs in an integrated environment. By maintaining separate tracker and aggregate DHIS2 instances, performance can be better managed by system admins and data governance principles can be applied to ensure personally identifiable data captured by Tracker can be protected according to national policies and governance frameworks.

TODO - rewrite/merge paragraph(s) above/below

There is a clear benefit in being able to leverage individual data
collection through DHIS2 tracker to automatically 'report' aggregated data to the routine HMIS (e.g. to aggregate datasets, often monthly/weekly/quarterly reports from facility level). Capturing individual level data through DHIS2 tracker can improve the quality of the data reported into the routine aggregate HMIS, while also enabling ad hoc analysis of the tracker data in the Tracker Instance as required.

3. Parallel and hybrid reporting flows
	a. Phased scale up of tracker: some facilities/districts adopting tracker sooner while others may retain the paper based aggregate reporting
	b. Parallel reporting: some countries necessitate a period of parallel reporting of paper-based and tracker data collection for a pilot period

It may in some cases be desirable or necessary to import aggregate data values into a DHIS2 tracker instance, such as data used as denominators in indicators (e.g. population estimates). However, a more common approach is to produce aggregate data values based on tracker data, and move this to the DHIS2 instance used for aggregate data (e.g. the HMIS), which is the third approach outlined here. There are several ways, technically, to do this. In the how-to section below, the focus is on the steps needed to set up an automated migration of tracker data into an aggregate system. Compared to the other approaches, this approach is more complicated and requires scripts or tools outside of DHIS2. 

The rest of this guide is focused on this topic. The next section outlines some key management and implementation considerations related to the migration of tracker and aggregate date. 

## Implementation considerations

* Governance of the data
	* Frequency of data transfer
		* How often to do the aggregation, for example daily, or on day of HMIS reporting deadline etc. How often the aggregate data is used for analysis and decision making should also be considered.
		* How many months back in time to update aggregate data for, for example last month, last 3 months, current and last month etc.
	* Data quality 
		* validation
		* Discrepancies
		* ; How can values for 'late reporting' be updated in the aggregate dataset; managing discrepancies between tracker and aggregate data set based on the timing of data submission
	* Completeness and timeliness
	* Governance principles and national HMIS policies for locking datasets, timely reporting
	* If not well communicated, the 'source of truth' can be obscured
* Access to data - different for tracker and aggregate
* Ensuring users understanding of data when being combined/merged

* If metadata in the tracker instance or in the aggregate HMIS instance are altered, the mapping of program indicators to aggregate data elements may need to be updated

## How-to: saving aggregated tracker data as aggregate data values
This section describes the recommended approach for saving tracker data as aggregate data element values. While requiring an external tool or script as part of transferring the data, it leverages the existing functionality of DHIS2 as far as possible so that the script can be as simple as possible. What is outlined here is also the approach taken in the [WHO configuration packages](dhis2.org/who) for DHIS2, which includes mapping of variables between tracker programmes and aggregate data sets where relevant. This is described [below](#dhis2-digital-data-packages-and-linking-tracker-and-aggregate-data).

The approach described here is recommended as a long-term, automated solution for saving tracker data as aggregate data values. Technically, there are several other ways in which this can be done, including using predictors, exporting the data and transforming it using other software (for example excel), or through custom DHIS2 apps (including some that are available in the [DHIS2 App Hub](apps.dhis2.org). These tools and methods can also be relevant in certain cases. For example if there is only a need to do ad-hoc transfers of data from time to time, or during early stages of tracker implementations when data is transferred primarily for testing and the configuration is still undergoing changes.  The final part of this how-to guide provides some pointers to [alternative methods and tools](#alternative-methods-and-tools). 

### Assumptions and key steps
When tracker data and aggregate data are managed in separate DHIS2 instances, which is generally recommended, migrating data between the two instances requires the organisation units to be the same, or at least have a shared set of identifiers. Because organisation units are often re-used when new DHIS2 instances are set up, this may not be a problem initially. However, keeping organisation units synchronised across two or more DHIS2 instances over time requires careful management, whether changes are handled manually or through an automated process. Forthcoming implementation guidance will discuss this issue in further detail. For the purpose of this guide, a prerequisite is that organisations are harmonised and have a shared set of identifiers across the two instances. In cases where tracker data is migrated to aggregate data values within the same DHIS2 instances, synchronising organisation units is not an issue.

Conceptually, the steps involved in migrating aggregates of tracker data to aggregate data values involves:

1. Establish a mapping between program indicators and the corresponding  data elements and category option combinations, using codes.
2. Export program indicator values as an aggregate *data value set*
3. Import the *data value set* as aggregate data element values

The following sections explains (1) how to establish a mapping between program indicators and data elements, (2) the DHIS2 APIs relevant for importing/exporting data values, and (3) considerations when automating the import and export process.

### Mapping program indicators with aggregate data elements
To produce aggregate data values from tracker data, program indicators must be defined for each data point. Each of these data values corresponds to a data element and if applicable a category option combination. A mapping using an identifier is thus needed to specify which program indicator relates to which specific data element (with category option combination). While not discussed in detail here, the mapping can also include attribute option combinations.

For example, {Covax example}...

![TODO - make proper illustration.](resources/images/draft_tracker_agg_mapping.jpg)

It is recommended to use *codes* as identifier for this mapping, and this is what is presented here.

#### Coding data elements
Because the data element and category option combination codes will be added as attributes to the program indicators, it is often easiest to first create and/or add a code to the data elements and category option combinations. This should be done in the DHIS2 instance in which aggregate data values will be saved. If the data elements and category option combinations already have codes, these can be used.

{Screenshot of data element with code - covax}
{Screenshot of coc with code - covax}

While not strictly necessary, it may be advisable to add the data elements to a data set if they are not already. This data set (or sets) define the period type of the data to be transferred (e.g. weekly, monthly), and when imported the aggregated tracker data will be validated against this period type. Similarly, if the data set is assigned to the organisation units expected to receive data, a validation warning can be displayed if importing data for other organisation units. Furthermore, such assigned may be the basis of subsequent calculation of data completeness.

**TODO**: verify that the above on validation is correct and/or if any API parameters are needed to enable them.


#### Coding program indicators
Program indicators have a fixed attribute used specifically for specifying the category option combination (and attribute option combination) identifier that is used when the program indicator value is exported as a data values set.

![TODO - update with screenshot with "blank" fields](resources/images/image6.png)

However, there is by default no such field for which to specify the identifier (i.e. code) of the data element. In principle, the code of the program indicator itself *could* be used, but this will fail in the common scenario that multiple program indicators are linked to the same data element (but different category option combinations). Instead, it is recommended to create an [attribute](https://docs.dhis2.org/en/use/user-guides/dhis-core-version-master/configuring-the-system/metadata.html#about_attribute) that is assigned to program indicators.

The custom attribute should be of the type `Text`. It should *not* be mandatory, since not all program indicators will be linked to aggregate data elements. It should *not* be unique, since multiple program indicators may point to the same data element code. And it should be applied to "Program indicator" only, since it is not relevant elsewhere. Other properties like name, description and code can be defined according to the [metadata naming conventions]() of that particular instance. The screenshot below shows how the custom attribute included in the WHO metadata packages is configured. If this custom attribute has already been imported into the DHIS2 instance in question, it can be re-used.

**Note:** as described below under [known issues](#known-issues), a bug prevents this field to be displayed when editing program indicators in the Maintenance app in some versions of DHIS2.

![Example showing how a custom attribute for linking program indicators and aggregate data elements can be defined.](resources/images/custom_attribute_definition.png)

Once the custom attribute is assigned to program indicators, the custom attribute will appear as a new field/attribute when adding or editing program indicators in the Maintenance app. Every program indicator for which data is to be transferred to aggregate data elements needs to be created and/or modified to include the code of the corresponding data element and category option combination code.

![TODO: update with COVAX exampe](resources/images/image6.png)

### DHIS2 Web API for export and import of dataValueSets
Once the mapping between program indicators and the corresponding data elements and category option combinations has been done, aggregated program indicator data can be exported as dataValueSets and subsequently imported as aggregate data values. As noted in the introduction, we assume for the purpose of this guide that organisation units are identical or have a common identifier in the DHIS2 instance where data is to be imported and exported

#### Export
To export data from the DHIS2 Web API `/api/analytics/dataValueSet` endpoint, which is described in further detail in the [developer documentation](https://docs.dhis2.org/en/develop/using-the-api/dhis-core-version-master/analytics.html#webapi_analytics_data_value_set_format). The endpoint can return data in `JSON` or `XML` representation. It requires three parameters to be specified:

* Data (dx) - which are the program indicators for which data is to be exported.
* Period (pe) - the period for which to export data for, which should match the period type of the aggregate data elements to which data should be migrated.
* Organisation unit (ou) - the organisation units for which to import data.

The format of the these parameters are described in detail in the [developer documentation](https://docs.dhis2.org/en/develop/using-the-api/dhis-core-version-master/analytics.html#webapi_analytics_dimensions_and_items).

In addition to specifying the data, period and organisation units dimensions of the query, it is also necessary to specify that the custom attributes holding the data element codes should be used as identifier for the data values in the data value set being exported. This is done by setting the optional 'outputDataElementIdScheme' parameter to point to the UID of the custom attribute, for example `

**TODO**: check use of "outputDataElementIdScheme" vs "outputIdScheme". Does outputDataElementIdScheme apply to PIs?

A complete example of an API call, using the program indicators including in the COVAX...:

**TODO:**
```
/api/analytics/dataValueSet.json?dimension=dx:Uvn6LCg7dVU;OdiHJayrsKo&dimension=pe:LAST_MONTH
&dimension=ou:lc3eMKXaEfw&outputIdScheme=ATTRIBUTE:vudyDP7jUy5
```

This query will return a file (in JSON format in this example) with aggregate data values.

As specified in documentation on the `/analytics/dataValueSet` API endpoint, when using attribute-based identifier schemes for export (as is this guide) there is a risk of producing duplicate data values. This can happen if multiple program indicators have been assigned the same combination of data element and category option combination codes. The boolean query parameter `duplicatesOnly` can be used for debugging purposes to return only duplicates data values, and this check is recommended after any changes to the mapping between program indicators and aggregate data elements.

**TODO**: update example query
```
/api/analytics/dataValueSet.json?dimension=dx:Uvn6LCg7dVU;OdiHJayrsKo
 &dimension=pe:LAST_MONTH&dimension=ou:lc3eMKXaEfw&duplicatesOnly=true
```

#### Import
When a file with aggregated data values has been exported from the '/api/analytics/dataValueSet' endpoint with the appropriate parameters as described above, it can be imported directly into the DHIS2 instance to which data is to be migrated. For testing purposes, the data file can be imported using the [Import/Export app](https://docs.dhis2.org/en/use/user-guides/dhis-core-version-master/maintaining-the-system/importexport-app.html), or via the DHIS2 Web API. Here, we show how to use the API.

The API endpoint for importing data value sets is '/api/dataValueSets', described in further detail in the [developer documentation](https://docs.dhis2.org/en/develop/using-the-api/dhis-core-version-master/data.html#webapi_data_values). Of particular relevance is the different [import parameters](https://docs.dhis2.org/en/develop/using-the-api/dhis-core-version-master/data.html#webapi_data_values_import_parameters), which must be adapted for our purposes as described here:

* `dataElementIdScheme` and `categoryOptionComboIdScheme` must be set to `code`, since we use codes to map values from Program indicators to aggregate data elements and category option combinations.
*  `orgUnitIdScheme` must be set to whatever is appropriate for each particular case.
* `dryRun` makes it possible to get an import summary without actually importing data, and can be useful for testing.
* `importStrategy` should in most cases be set to `CREATE_AND_UPDATE`, which means that new data values will be imported and existing ones updated. In some cases, it *may* be relevant to set this to only `CREATE` or `UPDATE`, for example if a decision is made not to update existing data after a certain time period. This is discussed in further detail [below](#implementation-considerations)

This is an example of how to specify the appropriate parameters when importing data using the API:

```
/api/dataValueSets/dataElementIdScheme=CODE&categoryOptionComboIdScheme=CODE&importStrategy=CREATE_AND_UPDATE&dryRun=false
```

### Writing scripts to automate data migration
A template script for automating routine migration of data from tracker to aggregate, within the same or between separate DHIS2 instances, will be made available in the near future. Whether adapting this template, or developing custom tools or script to perform the migration, there are certain recommendations that should be followed. 

* Separate the script performing the export and import from the configuration of what data to migrate. This allows more easily modifying the configuration without danger of introducing errors in the logic of the script, and makes it easy to have multiple configurations (i.e. one for each tracker programme). 
* The script should produce a log with key events and information, such as when the script has been triggered, a summary of the import results (on success), or details of the error (in case of failure).
* A system should be in place to notify the persons responsible for the data migration in case of errors, for example through an email server configured on the server, or using the messaging functionality of DHIS2 itself (accessible through the Web API).

### Known issues
- There is a bug in 2.33.3/2.33.4 that prevents us from creating this custom attribute; not exposed in the UI ([Jira 8755](https://jira.dhis2.org/browse/DHIS2-8755)): for now must insert the attribute via the API.

- There is a bug ([Jira 8868](https://jira.dhis2.org/browse/DHIS2-8868)) that causes metadata-dependency-export tool to fail when custom attribute assigned to program indicator

- Decide on use of codes or UIDs for linking PIs to data elements and categoryoptioncombos. The example script uses codes for data elements, uids for categoryoptioncombos.

- Improving the script so that it will at a minimum notify administrators if there is an error and/or sending a DHIS2 message with the import summary.

*There could also be other and more advanced scripts out in the community that can be considered.*

### Alternative methods and tools


## DHIS2 Digital Data Packages and linking tracker and aggregate data
DHIS2 digital data packages have been developed to support both
aggregate reporting & analysis, as well as tracker data capture and facility-level analysis.

Aggregate digital data packages (inclusive of standard aggregate dashboards) are available for health programmes such as TB, HIV, malaria, RMNCAH and disease surveillance. Aggregate packages include:

1. Data set, data elements and category option sets ('target' for sending tracker data)
2. Metadata codes that are ADX compliant and enable the mapping of data values from tracker to the aggregate 'target'

In addition, tracker packages are being developed for a growing number of use cases such as immunisation eRegistries and case-based surveillance for TB, HIV and integrated disease reporting. Where tracker data packages are designed to capture data that can be aggregated and submitted to the corresponding aggregate dataset, we have included the following in the tracker digital data packages:

1. Program indicators configured to produce data values corresponding to the data elements and disaggregations included in the aggregate digital data package data
2. Custom attribute for 'Aggregate data element code'
3. Attributes per program indicator populated with the data element codes and category option combination code from the aggregate digital data package

### Summary
1. Define a list of the variables for which data is to be generated and transferred.
2. Ensure that the aggregate data elements to which data will be associated exist and have a code.
3. Ensure that the category option combinations assigned to these data elements have a code.
4. Create a custom attribute assigned to program indicators.
5. Ensure that the program indicators producing the aggregate data values exists, and assign them with the code of the corresponding data element and category option combination.
6. Export program indicators values as a data value set using the 'api/...' Web API endpoint in the DHIS2 instance hosting the tracker data.
7. Import the data value set to the 'api/...' Web API endpoint in the DHIS2 instance that will hold the aggregate data.
