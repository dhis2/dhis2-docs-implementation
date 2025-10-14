# Climate data in malaria program planning: key considerations

*Attribution: the guidance below was written to support a Climate & Health early warning component to the Mozambique Ministry of Health’s national DHIS2-based [malaria information system](https://hispafrica.org/climate-health/), developed in collaboration with Clinton Health Access Initiative (CHAI) and Saudigitus (HISP Mozambique).*

This document is intended to provide guidance for public health professionals, particularly those working for or with malaria control programs, using climate and weather data to inform programmatic decisions for malaria control and elimination. The steps below are key considerations that these professionals should take into account; and while specific in this context for malaria these steps and considerations are relevant for professionals working on all climate-sensitive diseases.

## 1. Develop policy-relevant question(s)

This is the most important step. If questions and the subsequent work are not linked to a specific policy-relevant concerns, such as particular health outcomes, or formulated in a way that the results will improve decision-making for malaria control/elimination, the work will simply be an academic exercise. Consider the question, “so what?”; if this can’t be easily answered following the analysis then it shouldn’t be done, or the question should be re-formulated. For example, simply wanting to look at the relationship between temperature or precipitation and malaria cases by itself will not result in improved programmatic decision-making. Instead, consider using the relationship between climate and malaria to identify areas where certain interventions will likely be more or less effective. Some key examples include:

a.  Incorporation of climate data into sub-national tailoring and risk maps for intervention targeting

b.  Average seasonality duration for SMC targeting

c.  Seasonality onset and duration for IRS timing

d.  Early warning systems, or EWS (only if tied to a specific response plan so the predictions are used for programmatic decisions)

e.  Ideal location and types of responses during emergencies

## 2. What data do you need?

This will largely depend on what question(s) you are asking. There are many sources of weather and climate data and different indicators that can be used; deciding which to use can be overwhelming. Annex 1 outlines some common data sources and indicators, though a more comprehensive source for climate data is [here](https://climatedataguide.ucar.edu/climate-data). While this document isn’t intended to be a complete guide on climate and health data and data sources, there are important points to understand prior to using climate data for decision making.

a.  Data use trainings. Having a more in depth understanding of climate data and data sources can be valuable both for routine analyses and more complex analyses that countries might want to conduct. Google Earth Engine has many guides and tutorials for using data available on their platform [here](https://developers.google.com/earth-engine/guides). Additionally, through its [ARSET](https://appliedsciences.nasa.gov/what-we-do/capacity-building/arset) program, NASA conducts free trainings on the use of remote sensing data for health applications; the program is highly recommended. Many of these trainings are archived as well.

b.  Know the strengths and weaknesses of the data and data sources you intend to use. Most researchers and professionals choose between satellite-derived data vs station data for climate and weather indicators: station data are generally considered to be more accurate and the gold standard, although availability, spatial and temporal coverage, and variety of indicators is often significantly limited in Africa. Satellite-derived data is generally not as accurate as station data, but it is free and available for the entire world often at resolutions of 1km or better going back to as far as 1901. Additionally, while remote sensing data are available for all geographic regions, the resolution of these data varies considerably, and is never going to be as accurate for a specific location as station data. Remote sensing data have limitations and uncertainties that are not always inherently obvious. Both can also be subject to gaps in time series and missing data that can have significant implications if not addressed or filled. How important these limitations are and the impact they have is dependent on the specific data being used, and what they are being used for.

c.  Know your options. There is a wide range of indicators developed from satellite data, which increases the number of potential questions that can be answered with these data but also increases the complexity of choosing which indicators to use. For example, temperature estimates from satellite-derived data are often available as a maximum, minimum, or difference between these two. It is also generally available at the hourly, daily, weekly, monthly, or annual levels, meaning that researchers must also consider whether they want to use a daily, weekly, monthly average; a daily, weekly, monthly maximum; and/or daily, weekly, or monthly minimum (or the difference between these); the answer often depends on the scale of the health data. Finally, absolute values of indicators, for example temperature and precipitation, can be uninformative due to inter- and intra-country variation. If used, these absolute values should therefore be used in conjunction with historical averages and deviations from these averages.

d.  Pay attention to data size and data management requirements. Climate and weather data, especially satellite-derived data come in large files that require consistent and strong internet bandwidth to download. Storage of these files may require local servers and/or access to cloud-based storage systems for consistent use in the analyses described in this document.

e.  Given this complexity, it is recommended that researchers first do a literature search for climate factors associated with malaria in country and use this as a basis to decide which data are appropriate for their given questions, as ultimately what data and data sources you will need will be entirely dependent on the questions(s) you are asking. It also is beneficial to talk with a meteorologist about the planned analyses so they can advise on appropriate data and data sources.

## 3. Disease data and data quality issues

This document assumes that researchers and professionals have at least a foundational knowledge of disease data and how different types and sources of data can influence data quality. There are however additional considerations about disease data and their relationship to climate and weather data that should be taken into account:

a.  Temporal and spatial resolution, as with climate and weather data, varies from source to source. These resolutions should be matched between disease and climate/weather data whenever possible. For example if only monthly disease incidence is available then weekly climate/weather data should be aggregated or averaged at the monthly level to match the incidence data. Similarly, if routine programmatic decisions are made at the district/state level, then both disease and climate/weather data should be aggregated or averaged at this level as well.
b.  Climate-sensitive diseases such as malaria are influenced by many factors in addition to climate and weather, and these other factors should also be taken into account whenever possible when doing the analyses discussed in this document. These other factors should be noted when conducting literature searches described in Step 2, but often include factors such as timing and coverage of interventions, land use and land change, and demographic data.
c.  Additionally care should be taken to ensure the proper disease case data is used; at times incidence data or numbers of new infections is most appropriate to compare with climate and health data (as is the case with *P. viva*, or with populations under the age of 5 in more endemic settings) while other times prevalence data may be more appropriate. Ultimately this will depend on the questions being asked.

## 4. Background and standardized/routine analyses

Although the specific analyses needed will depend on which questions are being answered, there are some initial steps that should be completed to make analyses easier and more impactful. Using the outputs from the work described in Step 2 above, consider the following activities/analyses:

a.  List key indicators; both those pre-calculated and those that must be calculated from others:
    1.  Temperature, both absolute values and anomalies (deviation from 20 year mean)
        i.  Daily/weekly/monthly minimum
        ii. Daily/weekly/monthly maximum
        iii. Daily/weekly/monthly diurnal temp range
    2.  Precipitation
        i.  Can be daily/weekly/monthly average, or total
        ii. Consider identifying biologically significant thresholds, based on historical averages or literature findings
        iii. Days above/below certain precipitation totals in a week or month
    3.  Humidity
        i.  Specific, relative
    4.  Soil moisture content
        i.  Skin reservoir content
        ii. Surface runoff
        iii. Standardized precipitation-evapotranspiration index
    5.  Severe climate events such as extreme precipitation events, floods, droughts, cyclones, etc.
    6.  El Niño and La Niña events, both frequency and impact.
b.  Decide on what visuals and outputs from the above variables and analyses you will need to answer your question(s). If the country uses DHIS2 and CHAP, then several visuals will be automatically produced. Some additional examples include:
    1.  Onset, duration, and intensity of rainy season (and how to calculate them)
    2.  Weekly/monthly temperature, precipitation, humidity, soil moisture (etc.) anomaly maps for risk stratification
    3.  Severe climate events such as extreme precipitation events, floods, droughts, cyclones, etc
c.  Create a climatology profile for the country (if this hasn’t already been done; check [here](https://climateknowledgeportal.worldbank.org/), for example), using the indicators identified above. Consider also engaging with meteorology department to ensure local station data are included in climatology profiles where possible, as well as compared with satellite-derived estimates of key indicators. These climatology profiles should have the following:
    1.  Historical (\~20 year) averages
    2.  Current situation
    3.  Extreme weather and climate events over the past 5 or 10 years that impacted health
    4.  Recent (last \~5 years) trends
    5.  Predicted future changes
        i.  Short term (weeks to months; for example [NASA Earth Exchange Daily Downscaled Climate Projections](https://www.nccs.nasa.gov/services/data-collections/land-based-products/nex-gddp-cmip6))
        ii. Long term (years to decades; IPCC forecasts for example, though should be used with caution given uncertainty of projections)

## 5. Establish communities of practice (CoPs)

CoPs elevate climate data use cases for health among key agencies and stakeholders. These are important for developing a comprehensive understanding of climate and health analyses in the country, which can result in adoption of new ideas and approaches, improved efficiencies in existing work, as well as preventing duplication of work. It can furthermore promote collaborations between sectors that might otherwise not interact such as agriculture/food security and health departments. These CoPs should include:

a.  Research agencies

b.  Departments of meteorology and environment

c.  Disease departments that focus on climate-sensitive diseases

d.  Emergency operation departments

e.  Partners working in the above areas

f.  Stakeholders from affected communities

## 6. Ensure linkage with action

Follow through with sufficient support so products and outputs of analyses are actually used to aid decision-making. Linking back to Step 1, this is one of the most critical steps for ensuring data are translated into action and the analyses aren’t just an academic exercise. The more well-designed the initial question, the easier it will be to ensure outputs are linked to action. It is additionally important to ensure there is a framework in place to implement the results of the analyses, both in terms of resources (financial and otherwise), as well as governance for roles and responsibilities for action. For example:

a.  Including EWS into broader EPR landscape

b.  Routine analysis of IRS timing based on seasonality calculations

c.  Use of key indicators/anomalies for risk stratification/sub-national tailoring for intervention targeting

## 7. Develop an M&E plan

M&E plan would support all climate data and analyses used for decision making. This is important to further improve the accuracy of analyses, as indicators from satellite-derived estimates can vary in accuracy from country to country, which in turn can impact the effectiveness of analyses they are used for. Properly developed M&E plans can also ensure outputs of climate and health analyses lead to the desired actions, and that these actions have the desired impact.

a.  For most analyses, M&E will focus on the implementation and impact of the results that utilize the climate-health outputs. For example, evaluating the effectiveness of early warning systems would likely be primarily based on the impact of mitigation and response measures implemented based on alerts from the system, rather than the accuracy of the predictions themselves (more information/guidance to come soon).

b.  Available data from climate and weather stations provide an opportunity to evaluate the accuracy of indicators derived from remote sensing/satellite data, because station data are generally considered the gold standard. This also would be a great opportunity to work with meteorology departments to evaluate and improve the quantity and quality of country station data by comparing with satellite-derived estimates

## 8. Engage with national health observatories

If one does not yet exist, consider establishment of a national health observatory. In their ideal form, health observatories or similar agencies have a mandate from the government to access all data relevant to climate-sensitive diseases, thus making all the above steps easier (although this is more relevant from a disease-agnostic perspective than from a malaria-specific focus). These observatories can also serve as sources of expertise on proper data sources and analyses, thereby eliminating the need to establish and/or maintain all the knowledge and expertise required to perform these analyses within one disease department.

## 9. Governance

This is an often overlooked but important component that should always be considered for long-term sustainability. While more relevant for disease-agnostic work, having the governance in place for work on climate and health can be key to establishing health observatories, creating data interoperability and quality standards, promoting cross-sectoral collaborations, and ensuring roles/responsibilities, standard operating procedures, and funding are in place for actions based on climate and health analyses.

## Annex 1. List of climate data sources

**Key data sources**

+--------------------------------------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+----------------------------+----------------------------------------+-------------------------------------------------------------+-----------------------------------------------------------------------------------------+
| **Name**                                   | **Link**                                                                       | **Type of data**                                                                                                                      | **Software language used** | **Downloadable data format**           | **Benefits**                                                | **Drawbacks**                                                                           |
+--------------------------------------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+----------------------------+----------------------------------------+-------------------------------------------------------------+-----------------------------------------------------------------------------------------+
| Google Earth Engine (GEE)                  | [data catalog](https://developers.google.com/earth-engine/datasets)            | Various, from current/historical individual weather variables to land cover, imagery, to climate projections                          | Javascript, Python, REST   | Various                                | Access to almost any indicator from multiple sources/models | Must know one of the software languages                                                 |
|                                            |                                                                                |                                                                                                                                       |                            |                                        |                                                             |                                                                                         |
|                                            | [Earth Engine](https://earthengine.google.com/)                                |                                                                                                                                       |                            |                                        |                                                             |                                                                                         |
+--------------------------------------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+----------------------------+----------------------------------------+-------------------------------------------------------------+-----------------------------------------------------------------------------------------+
| Climate Data Store (CDS)                   | [Home](https://cds.climate.copernicus.eu/cdsapp#!/home)                        | Various; ERA5 products specifically                                                                                                   | Python                     | netCDF                                 | API much easier to use/edit than GEE                        | Large download file size                                                                |
|                                            |                                                                                |                                                                                                                                       |                            |                                        |                                                             |                                                                                         |
|                                            | [Datasets](https://cds.climate.copernicus.eu/cdsapp#!/search?type=dataset)     |                                                                                                                                       |                            |                                        |                                                             |                                                                                         |
+--------------------------------------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+----------------------------+----------------------------------------+-------------------------------------------------------------+-----------------------------------------------------------------------------------------+
| Climate Hazards Center/CHIRPS              | [Data](https://data.chc.ucsb.edu/products/CHIRPS-2.0/)                         | Precipitation                                                                                                                         | None                       | .tif, .png (in compressed format)      | No special software needed                                  | Each time point must be downloaded separately; can be confusing to navigate the website |
+--------------------------------------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+----------------------------+----------------------------------------+-------------------------------------------------------------+-----------------------------------------------------------------------------------------+
| Climate Research Unit (CRU)                | [Datasets](https://crudata.uea.ac.uk/cru/data/hrg/#current)                    | Temp, others                                                                                                                          | None                       | .nc, .dat, .stn (in compressed format) | No special software needed                                  | Each time point must be downloaded separately; can be confusing to navigate the website |
+--------------------------------------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+----------------------------+----------------------------------------+-------------------------------------------------------------+-----------------------------------------------------------------------------------------+
| NASA GISS station temperature data         | [Datasets](https://data.giss.nasa.gov/gistemp/station_data_v4_globe/)          | Surface temperature (monthly mean)                                                                                                    | None                       | .txt or .csv                           | Actual station data                                         | Lots of missing data; poor coverage for some countries                                  |
+--------------------------------------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+----------------------------+----------------------------------------+-------------------------------------------------------------+-----------------------------------------------------------------------------------------+
| World Bank Climate Change Knowledge Portal | [Knowledge portal](https://climateknowledgeportal.worldbank.org/download-data) | Various projected indicators under different future SSP scenarios from CMIP models; also some historical data (CRU, ERA5 for example) | None                       | Excel, others?                         | Many options, also good source of projected future data     | Download options not very customizable                                                  |
+--------------------------------------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+----------------------------+----------------------------------------+-------------------------------------------------------------+-----------------------------------------------------------------------------------------+

**Key indicators and best sources**

|                       |                                                 |                                                                                                           |
|-----------------------|-------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| **Indicator**         | **Source(s)**                                   | **Options**                                                                                               |
| Temperature           | ERA5, CRU (CDS, GEE, CRU)                       | Daily/weekly/monthly mean; daily/weekly/monthly min and max; daily/weekly/monthly mean diurnal temp range |
| Precipitation         | CHIRPS, ERA5 (Climate Hazards Center, CDS, GEE) | Daily/weekly/monthly mean; Daily/weekly/monthly sum; days above 10/50/200mm                               |
| Humidity              | ERA5, others (CDS, GEE)                         | Relative, specific                                                                                        |
| Soil moisture content | ERA5, others (CDS, GEE)                         | Also surface runoff, skin reservoir content measure propensity for standing water                         |
