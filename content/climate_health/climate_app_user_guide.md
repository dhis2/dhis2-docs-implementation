# DHIS2 Climate App User Guide


## Background and context { #climateapp_background }

The purpose of this document is to complement the existing guide provided within the [Climate App](https://apps.dhis2.org/app/effb986c-a3c7-485e-a2f6-5e54ff9df7c3), offering users a clear, step-by-step reference on how to install the app and use it within their DHIS2 instance. Most of the content in this guide builds upon the instructions available directly in the app after installation, while providing additional context and explanations to make the process easier to follow prior to installation.

This pilot app is part of the ongoing [“DHIS2 for Climate” project](https://dhis2.org/climate). It receives frequent updates, so please ensure you are using the latest version available on the [DHIS2 App Hub.](https://apps.dhis2.org/app/effb986c-a3c7-485e-a2f6-5e54ff9df7c3) The app is developed by the University of Oslo, though it is not a DHIS2 core application. However, useful components from this app may be incorporated into the DHIS2 core in the future based on user feedback.

The app allows users to explore and import various weather and climate parameters—such as temperature, precipitation, humidity, and heat stress—directly into DHIS2. See *Table 1* for the full list of supported parameters. The primary data source is ERA5-Land, widely recognized as one of the most accurate and complete global climate datasets. These datasets are produced by combining weather observations with [advanced climate reanalysis models](https://www.youtube.com/watch?v=FAGobvUGl24).

Other supported data sources include:

* ERA5-Land – [Copernicus Climate Data Store](https://cds.climate.copernicus.eu/datasets/reanalysis-era5-land)
* CHIRPS –[ Climate Hazards Center](https://www.chc.ucsb.edu/data/chirps)
* ERA5-HEAT – [Copernicus Climate Data Store](https://cds.climate.copernicus.eu/datasets/derived-utci-historical)
* NASA LP DAAC – [Land Processes Distributed Active Archive Center](https://www.earthdata.nasa.gov/data/catalog)


## Key features of the app { #climateapp_features }

**Explore data:** Use this feature to view weather and climate data for your organization units without importing it into the system. No metadata configuration is required, but your organization units must have coordinates and a valid Google Earth Engine (GEE) key. See the section on Installation *Prerequisites* for more details.

**Setup guide:** Before importing climate data, you must configure your DHIS2 instance. See the section on *Metadata Configuration for Climate Data Import* for setup instructions.

**Import data:** Once metadata configuration is complete, you can import climate data into DHIS2. This allows you to combine climate and health data across all DHIS2 analytics applications. After importing, remember to generate the analytics tables in the Data Administration app.


## How the data is calculated

All climate data are computed for your organization units using Google Earth Engine (GEE). Please consider the spatial resolution of the selected dataset.


* For **health facilities,** the data value corresponds to the exact location of the facility.
* For **districts/provinces,** all values are aggregated within the district/province.
* If two organization units are located within the same grid cell (at the dataset’s resolution), they will share the same data value.

See *Table 1* for detailed descriptions of the available parameters.


## **Installation prerequisites**

1. Ensure your DHIS2 instance is running on version 2.37 or higher, as the app is only compatible with these versions.
2. Verify that your DHIS2 instance is connected to Google Earth Engine (GEE), which is free to use for governments and non-profit organizations. If you do not already have access, please request it by sending an email to [maps@dhis2.org,](mailto:maps@dhis2.org),  specifying the name of your organisation. Alternatively, you may set up a Google Cloud project [independently](#install_google_service_account_configuration).
3. Confirm that your DHIS2 organisation units are configured with **geographic coordinates** at all administrative levels where you intend to access climate data.


## **Exploring climate data using the app**


### Data availability

The **Explore data** window allows you to select an organisation unit and a specific climatic parameter such as temperature, precipitation, humidity, climate change (temperature anomaly), vegetation, land cover, or elevation. Details of these parameters are provided in *Table 1*.

Callout: All climate data visualized in the Explore data window are dynamically computed “on the fly” by Google Earth Engine, meaning the data do not need to be imported into DHIS2 as data values to be analyzed.

Some climatic parameters share common aggregation periods, while others do not. For example:

* Temperature can be viewed **daily or monthly.**
* Vegetation index is displayed by default in **16-day** intervals but can also be viewed weekly or monthly.
* Land cover and elevation are aggregated **annually**.

For parameters available in daily or monthly formats, you can define both **start** and **end** **periods** to limit the time range of your analysis. *(Note: this option is not available for land cover or elevation data.)*

The app includes two **30-year reference periods**; 1961–1990 and 1991–2020 that allow you to compare current monthly values with long-term climate normals for temperature, precipitation, and humidity.

Additional filters are available for some parameters:


* **Land cover** includes 20 classification types.
* **Vegetation index** includes two selectable types, depending on your analysis needs.

*Table 1: Summary of parameters in the climate app*


<table>
  <tr>
   <td><strong>Parameter</strong>
   </td>
   <td><strong>Elements</strong>
   </td>
   <td><strong>Period of aggregation</strong>
   </td>
   <td><strong>Source</strong>
   </td>
   <td><strong>Reference periods</strong>
   </td>
   <td><strong>Data resolution</strong>
   </td>
  </tr>
  <tr>
   <td>Temperature
   </td>
   <td>
<ul>

<li>Min temperature</li>

<li>Mean temperature</li>

<li>Max temperature</li>

<li>Normal temperature</li>
</ul>
   </td>
   <td>Daily or Monthly
   </td>
   <td>ERA5 Land
   </td>
   <td>1961–1990 and 1991–2020
   </td>
   <td>9X9 km (0.1°)
   </td>
  </tr>
  <tr>
   <td>Precipitation
   </td>
   <td>
<ul>

<li>Precipitation</li>

<li>Normal precipitation</li>
</ul>
   </td>
   <td>Daily or Monthly
   </td>
   <td>ERA5 Land & CHIRPS
   </td>
   <td>1961–1990 and 1991–2020
   </td>
   <td>9X9 km (0.1°)
   </td>
  </tr>
  <tr>
   <td>Humidity
   </td>
   <td>
<ul>

<li>Relative humidity</li>

<li>Dewpoint temperature</li>

<li>Air temperature</li>

<li>Normal relative humidity</li>
</ul>
   </td>
   <td>Daily or Monthly
   </td>
   <td>ERA5 Land
   </td>
   <td>1961–1990 and 1991–2020
   </td>
   <td>9X9 km (0.1°)
   </td>
  </tr>
  <tr>
   <td>Heat
   </td>
   <td>
<ul>

<li> Universal Thermal Climate Index (UTCI)</li>
</ul>
   </td>
   <td>Daily or Monthly
   </td>
   <td>ERA5-HEAT
   </td>
   <td>N/A
   </td>
   <td>31X31 km (0.25°)
   </td>
  </tr>
  <tr>
   <td>Climate Change
   </td>
   <td>Temperature anomaly
   </td>
   <td>Months of the year
   </td>
   <td>ERA5 Land
   </td>
   <td>1961–1990 and 1991–2020
   </td>
   <td>9X9 km (0.1°)
   </td>
  </tr>
  <tr>
   <td>Vegetation
   </td>
   <td>
<ul>

<li>Landsat Normalized Difference Vegetation Index (NDVI)</li>

<li>Enhanced vegetation index (EVI)</li>
</ul>
   </td>
   <td>16-day (default); Weekly; Monthly
   </td>
   <td>NASA
   </td>
   <td>N/A
   </td>
   <td>250X250m
   </td>
  </tr>
  <tr>
   <td>Elevation
   </td>
   <td>Elevation distribution
   </td>
   <td>One-off annual
   </td>
   <td>NASA
   </td>
   <td>N/A
   </td>
   <td>30m
   </td>
  </tr>
  <tr>
   <td>Land Cover
   </td>
   <td>
<ul>

<li>Barren or sparsely vegetated, </li>

<li>Closed shrublands,</li>

<li>Cropland/natural vegetation mosaic, </li>

<li>Croplands, </li>

<li>Deciduous broadleaf forest, Deciduous needleleaf forest,</li>

<li>Evergreen broadleaf forest,</li>

<li>Evergreen needleleaf forest,</li>

<li>Grasslands, </li>

<li>Mixed forest, </li>

<li>Open shrublands, </li>

<li>Permanent wetlands,</li>

<li>Savannas, </li>

<li>Snow and ice,</li>

<li>Urban and built,</li>

<li>Water</li>

<li>Woody savannas</li>
</ul>
   </td>
   <td>Annual (2002-2024)
   </td>
   <td>NASA
   </td>
   <td>N/A
   </td>
   <td>500m
   </td>
  </tr>
</table>



### Using the Climate App for data exploration

The “Explore data” section provides dynamic visualizations for all the above climatic parameters. Simply select an organisation unit at the left side of the screen. By default, the first page to show up will be the “10 days forecast” tab. Tabs for further parameters can be selected at the Navbar at top. You may click the arrows at left and right to find more.

This image shows the Explore data window in the DHIS2 Demo instance.

![Fig 1: Explore data](resources/images/climate_app_explore_info.png)

The explorable features are identified by the Letter callout boxes, and described below.

A) The Organisation Unit context. This is selected in the Organisation Unit hierarchy tree at right. When the geography for an Organisation Unit is a point, a “pin” icon appears next to the organisation unit name, while for polygons this icon is a “grid”. Users only have access to their “data view” organisation units.

B) After you select a climatic parameter, you can further select at top left of the visualization name whether to display daily or monthly aggregations.

C) Scrolling over the visualisation will show you the data series values at that time period in a callout box. Here we see temperature values (mean, range, and climatic normal) for February 2025.

D) You may change the start and end periods for the visualization. Click the Update button to view.

E) You may further select between the two 30-year reference periods

F) The resolution of the climate data is described as well as important contextual details on the calculation.

G) In the menu at top right of the visualisation, you can view full screen, print the chart, or  download the chart in various formats (PNG, JPEG, PDF, SVG)

H) At the bottom right you can view the linked data source and attribution.

This presentation from the 2025 DHIS2 Annual Conference (starting 10:00) has details on the available datasets to explore through the Climate App as of July 2025.

![](https://www.youtube.com/embed/L7h_mGOjaeE?si=XSgM030IiqswxYTy&amp;start=603)

## **Metadata configuration for climate data import** { #climateapp_config }

Before you can import data, you need to make some configurations in the Maintenance app. For detailed instructions on how to configure DHIS2, choose which data you would like to import below.

**1. Create the data elements**

Create DHIS2 data elements only for the parameters you plan to import. It is recommended to include the **data source** in the name to help distinguish it from other sources. For example, *precipitation data* may be available from both **ERA5-Land** and **CHIRPS**.

If you use the same **codes** specified on table 1, the corresponding data elements will be automatically preselected in the import interface.

When **daily data** is imported, it can be aggregated into other period types within DHIS2. However, it is **not recommended to aggregate across organisation unit levels**, particularly from facility level to higher administrative levels, as this may distort spatial accuracy.

For each data element, set the following key configurations (see *Table 2* for reference):



* **zeroIsSignificant = true: **data element is able to store zero value when imported
* **domainType = AGGREGATE**: data element belongs to the aggregate DHIS2 domain
* **aggregationLevel = all:** to ensure that the data element aggregates climate for each level separately.

*Table 2: Datasets metadata configurations*


<table>
  <tr>
   <td><strong>id</strong>
   </td>
   <td><strong>code</strong>
   </td>
   <td><strong>name</strong>
   </td>
   <td><strong>Short Name</strong>
   </td>
   <td><strong>Aggregation Type</strong>
   </td>
   <td><strong>description</strong>
   </td>
  </tr>
  <tr>
   <td>DZte8CXJ6zJ
   </td>
   <td>CHIRPS_PRECIPITATION
   </td>
   <td>CCH - Precipitation (CHIRPS)
   </td>
   <td>Precipitation CHIRPS
   </td>
   <td>SUM
   </td>
   <td>Total precipitation in mm
   </td>
  </tr>
  <tr>
   <td>X0Tq9B9meJU
   </td>
   <td>ERA5_HEAT_UTCI
   </td>
   <td>CCH - Heat stress (ERA5-HEAT)
   </td>
   <td>Heat stress
   </td>
   <td>AVERAGE
   </td>
   <td>Average felt temperature in °C. Data source: ERA5-Heat / Copernicus Climate Change Service
   </td>
  </tr>
  <tr>
   <td>BmszSzqKgFb
   </td>
   <td>ERA5_HEAT_UTCI_MAX
   </td>
   <td>CCH - Max heat stress (ERA5-HEAT)
   </td>
   <td>Max heat stress
   </td>
   <td>MAX
   </td>
   <td>Same as above
   </td>
  </tr>
  <tr>
   <td>N5ENtQKKQcj
   </td>
   <td>ERA5_HEAT_UTCI_MIN
   </td>
   <td>CCH - Min heat stress (ERA5-HEAT)
   </td>
   <td>Min heat stress
   </td>
   <td>MIN
   </td>
   <td>Same as above
   </td>
  </tr>
  <tr>
   <td>CLbMVtinuoV
   </td>
   <td>ERA5_LAND_DEWPOINT_TEMPERATURE
   </td>
   <td>CCH - Dewpoint temperature (ERA5-Land)
   </td>
   <td>Dewpoint temperature
   </td>
   <td>AVERAGE
   </td>
   <td>Temperature in °C at 2m above the surface to which the air would have to be cooled for saturation to occur.
   </td>
  </tr>
  <tr>
   <td>RMaMv7SrUYd
   </td>
   <td>ERA5_LAND_PRECIPITATION
   </td>
   <td>CCH - Precipitation (ERA5-Land)
   </td>
   <td>Precipitation
   </td>
   <td>SUM
   </td>
   <td>Total precipitation in mm
   </td>
  </tr>
  <tr>
   <td>hsQg4SfG5pO
   </td>
   <td>ERA5_LAND_RELATIVE_HUMIDITY
   </td>
   <td>CCH - Relative humidity (ERA5-Land)
   </td>
   <td>Relative humidity
   </td>
   <td>AVERAGE
   </td>
   <td>Percentage of water vapor in the air compared to the total amount of vapor that can exist in the air at its current temperature. Calculated using air temperature and dewpoint temperature at 2m above surface.
   </td>
  </tr>
  <tr>
   <td>Pjd8Rn6mTb0
   </td>
   <td>ERA5_LAND_TEMPERATURE
   </td>
   <td>CCH - Air temperature (ERA5-Land)
   </td>
   <td>Air temperature
   </td>
   <td>AVERAGE
   </td>
   <td>Average air temperature in °C at 2m above the surface
   </td>
  </tr>
  <tr>
   <td>BDIuhHdQEDI
   </td>
   <td>ERA5_LAND_TEMPERATURE_MAX
   </td>
   <td>CCH - Max air temperature (ERA5-Land)
   </td>
   <td>Max air temperature
   </td>
   <td>AVERAGE
   </td>
   <td>Maximum air temperature in °C. at 2m above the surface
   </td>
  </tr>
  <tr>
   <td>QZilZRiGNvB
   </td>
   <td>ERA5_LAND_TEMPERATURE_MIN
   </td>
   <td>CCH - Min air temperature (ERA5-Land)
   </td>
   <td>Min air temperature
   </td>
   <td>AVERAGE
   </td>
   <td>Minimum air temperature in  °C. at 2m above the surface
   </td>
  </tr>
  <tr>
   <td>dl1JTXinsIM
   </td>
   <td>MODIS_EVI
   </td>
   <td>CCH - Enhanced vegetation index (MODIS)
   </td>
   <td>EVI
   </td>
   <td>AVERAGE
   </td>
   <td>Enhanced vegetation index (EVI) differs from NDVI by reducing the influence of atmospheric conditions and canopy background noise. EVI values range from -1 to 1, with higher values indicating denser vegetation. Data originates from MODIS (NASA).
   </td>
  </tr>
  <tr>
   <td>BC3vgSOKONN
   </td>
   <td>MODIS_NDVI
   </td>
   <td>CCH - Normalized difference vegetation index (MODIS)
   </td>
   <td>NDVI
   </td>
   <td>AVERAGE
   </td>
   <td>Landsat Normalized Difference Vegetation Index (NDVI) is used to quantify vegetation greenness and is useful in understanding vegetation density and assessing changes in plant health. NDVI values range from -1 to 1, with higher values indicating denser vegetation. Data originates from MODIS (NASA).
   </td>
  </tr>
  <tr>
   <td>iwwgPNFBtlH
   </td>
   <td>MODIS_LANDCOVER_1
   </td>
   <td>CCH - Evergreen Needleleaf forest (MODIS)
   </td>
   <td>Evergreen Needleleaf forest
   </td>
   <td>AVERAGE
   </td>
   <td>Percentage of area with this land cover type.Data source: NASA LP DAAC at the USGS EROS Center
   </td>
  </tr>
  <tr>
   <td>uXW9TzHcDCA
   </td>
   <td>MODIS_LANDCOVER_10
   </td>
   <td>CCH - Grasslands (MODIS)
   </td>
   <td>Grasslands
   </td>
   <td>AVERAGE
   </td>
   <td>Same as above
   </td>
  </tr>
  <tr>
   <td>evTogVMkoV6
   </td>
   <td>MODIS_LANDCOVER_11
   </td>
   <td>CCH - Permanent wetlands (MODIS)
   </td>
   <td>Permanent wetlands
   </td>
   <td>AVERAGE
   </td>
   <td>Same as above
   </td>
  </tr>
  <tr>
   <td>CJlLGqQvopa
   </td>
   <td>MODIS_LANDCOVER_12
   </td>
   <td>CCH - Croplands (MODIS)
   </td>
   <td>Croplands
   </td>
   <td>AVERAGE
   </td>
   <td>Same as above
   </td>
  </tr>
  <tr>
   <td>qKotwyKfjau
   </td>
   <td>MODIS_LANDCOVER_13
   </td>
   <td>CCH - Urban and built-up (MODIS)
   </td>
   <td>Urban and built-up
   </td>
   <td>AVERAGE
   </td>
   <td>Same as above
   </td>
  </tr>
  <tr>
   <td>QpLuERXDjNK
   </td>
   <td>MODIS_LANDCOVER_14
   </td>
   <td>CCH - Cropland/Natural vegetation mosaic (MODIS)
   </td>
   <td>Cropland/Natural vegetation mosaic
   </td>
   <td>AVERAGE
   </td>
   <td>Same as above
   </td>
  </tr>
  <tr>
   <td>sU8FbQJFtbH
   </td>
   <td>MODIS_LANDCOVER_15
   </td>
   <td>CCH - Snow and ice (MODIS)
   </td>
   <td>Snow and ice
   </td>
   <td>AVERAGE
   </td>
   <td>Same as above
   </td>
  </tr>
  <tr>
   <td>ET9dc084XVm
   </td>
   <td>MODIS_LANDCOVER_16
   </td>
   <td>CCH - Barren or sparsely vegetated (MODIS)
   </td>
   <td>Barren or sparsely vegetated
   </td>
   <td>AVERAGE
   </td>
   <td>Same as above
   </td>
  </tr>
  <tr>
   <td>eOQR9EGNHDn
   </td>
   <td>MODIS_LANDCOVER_17
   </td>
   <td>CCH - Water (MODIS)
   </td>
   <td>Water
   </td>
   <td>AVERAGE
   </td>
   <td>Same as above
   </td>
  </tr>
  <tr>
   <td>RLAWu61P9V1
   </td>
   <td>MODIS_LANDCOVER_2
   </td>
   <td>CCH - Evergreen Broadleaf forest (MODIS)
   </td>
   <td>Evergreen Broadleaf forest
   </td>
   <td>AVERAGE
   </td>
   <td>Same as above
   </td>
  </tr>
  <tr>
   <td>bt7b1kiFU0T
   </td>
   <td>MODIS_LANDCOVER_3
   </td>
   <td>CCH - Deciduous Needleleaf forest (MODIS)
   </td>
   <td>Deciduous Needleleaf forest
   </td>
   <td>AVERAGE
   </td>
   <td>Same as above
   </td>
  </tr>
  <tr>
   <td>NNYm1uG1CSS
   </td>
   <td>MODIS_LANDCOVER_4
   </td>
   <td>CCH - Deciduous Broadleaf forest (MODIS)
   </td>
   <td>Deciduous Broadleaf forest
   </td>
   <td>AVERAGE
   </td>
   <td>Same as above
   </td>
  </tr>
  <tr>
   <td>nLORr2NrETU
   </td>
   <td>MODIS_LANDCOVER_5
   </td>
   <td>CCH - Mixed forest (MODIS)
   </td>
   <td>Mixed forest
   </td>
   <td>AVERAGE
   </td>
   <td>Same as above
   </td>
  </tr>
  <tr>
   <td>Yh8EXp49asL
   </td>
   <td>MODIS_LANDCOVER_6
   </td>
   <td>CCH - Closed shrublands (MODIS)
   </td>
   <td>Closed shrublands
   </td>
   <td>AVERAGE
   </td>
   <td>Same as above
   </td>
  </tr>
  <tr>
   <td>SJYCTc90cTb
   </td>
   <td>MODIS_LANDCOVER_7
   </td>
   <td>CCH - Open shrublands (MODIS)
   </td>
   <td>Open shrublands
   </td>
   <td>AVERAGE
   </td>
   <td>Same as above
   </td>
  </tr>
  <tr>
   <td>hEOiu9kECX6
   </td>
   <td>MODIS_LANDCOVER_8
   </td>
   <td>CCH - Woody savannas (MODIS)
   </td>
   <td>Woody savannas
   </td>
   <td>AVERAGE
   </td>
   <td>Same as above
   </td>
  </tr>
  <tr>
   <td>l9g7AmOAw4V
   </td>
   <td>MODIS_LANDCOVER_9
   </td>
   <td>CCH - Savannas (MODIS)
   </td>
   <td>Savannas
   </td>
   <td>AVERAGE
   </td>
   <td>Same as above
   </td>
  </tr>
  <tr>
   <td>n33IIowe04z
   </td>
   <td>SRTM_ELEVATION_MAX
   </td>
   <td>CCH - Max elevation (SRTM)
   </td>
   <td>Max elevation
   </td>
   <td>FIRST_AVERAGE_ORG_UNIT
   </td>
   <td>Max elevation in meters above sea level. Data source: NASA / USGS / JPL-Caltech
   </td>
  </tr>
  <tr>
   <td>pse3lCkdHHF
   </td>
   <td>SRTM_ELEVATION_MEAN
   </td>
   <td>CCH - Mean elevation (SRTM)
   </td>
   <td>Mean elevation
   </td>
   <td>FIRST_AVERAGE_ORG_UNIT
   </td>
   <td>Mean elevation in meters above sea level. Data source: NASA / USGS / JPL-Caltech
   </td>
  </tr>
  <tr>
   <td>lfRpta1LI1u
   </td>
   <td>SRTM_ELEVATION_MIN
   </td>
   <td>CCH - Min elevation (SRTM)
   </td>
   <td>Min elevation
   </td>
   <td>FIRST_AVERAGE_ORG_UNIT
   </td>
   <td>Min elevation in meters above sea level. Data source: NASA / USGS / JPL-Caltech
   </td>
  </tr>
</table>


**2. Assign to a data set**

If you are importing daily data, assign the data elements to a daily data set (e.g., *Weather and Climate*). For weekly or monthly data, assign them to a weekly or monthly data set (e.g., *Vegetation Index*).

Assigning data elements to an appropriate data set helps maintain metadata quality and ensures data integrity, consistency, approvals, and protection. The specific configuration of each data set will depend on the available users and user groups in your system.

Decisions about which organisation units can collect the daily climate data will vary depending on local context. Since data can be provided for any administrative unit with defined geographic boundaries, this choice is left to system administrators. In most cases, the best option is to include all organisation units in your DHIS2 system.

Refer to *Table 3* for detailed metadata configuration guidance.

Table 3: Datasets metadata configurations


<table>
  <tr>
   <td><strong>id</strong>
   </td>
   <td><strong>code</strong>
   </td>
   <td><strong>name</strong>
   </td>
   <td><strong>shortName</strong>
   </td>
   <td><strong>description</strong>
   </td>
   <td><strong>Period Type</strong>
   </td>
  </tr>
  <tr>
   <td>mck6wRvBafz
   </td>
   <td>CCH_DAILY
   </td>
   <td>CCH - Climate/Weather (Daily)
   </td>
   <td>Climate/Weather (Daily)
   </td>
   <td>This will take on all data elements for climate data that can be imported on a daily time period
   </td>
   <td>Daily
   </td>
  </tr>
  <tr>
   <td>gKA14xjAFiw
   </td>
   <td>CCH_WEEKLY
   </td>
   <td>CCH - Environment (Weekly)
   </td>
   <td>Environment (Weekly)
   </td>
   <td>This will take on all data elements for vegetation index that is imported on a weekly time period
   </td>
   <td>Weekly
   </td>
  </tr>
  <tr>
   <td>seNaPr5spPO
   </td>
   <td>CCH_ANNUAL
   </td>
   <td>CCH - Landcover and Elevation (Annual)
   </td>
   <td>Landcover and Elevation (Annual)
   </td>
   <td>This will take on all data elements for landcover and Elevation that is imported on an annual time period
   </td>
   <td>Yearly
   </td>
  </tr>
</table>


**3. Assign to a data element group**

To be able to select the data elements in all the DHIS2 analytics apps you also need to assign them to a data element group. For example for the Climate/Weather group.


<table>
  <tr>
   <td><strong>id</strong>
   </td>
   <td><strong>code</strong>
   </td>
   <td><strong>name</strong>
   </td>
   <td><strong>shortName</strong>
   </td>
   <td><strong>description</strong>
   </td>
  </tr>
  <tr>
   <td>U4ClQbCq7Fv
   </td>
   <td>CCH_DAILY
   </td>
   <td>CCH - Climate/Weather (Daily)
   </td>
   <td>Climate/Weather (Daily)
   </td>
   <td>This will take on all data elements for climate data that can be imported on a daily time period
   </td>
  </tr>
  <tr>
   <td>YUbFn4nqNJM
   </td>
   <td>CCH_WEEKLY
   </td>
   <td>CCH - Environment (Weekly)
   </td>
   <td>Environment (Weekly)
   </td>
   <td>This will take on all data elements for vegetation index that is imported on a weekly time period
   </td>
  </tr>
  <tr>
   <td>u9w6yiCGxHa
   </td>
   <td>CCH_ANNUAL
   </td>
   <td>CCH - Landcover and Elevation (Annual)
   </td>
   <td>Landcover and Elevation (Annual)
   </td>
   <td>This will take on all data elements for landcover and Elevation that is imported on an annual time period
   </td>
  </tr>
</table>



## Import weather and climate data { #climateapp_import }

Before importing weather or climate data, you need to first create the corresponding data elements in DHIS2. Refer to the previous section for detailed instructions. You can import data in batches, and it is recommended to start with a few organisation units to ensure that everything functions as expected before performing larger imports.


### **Steps to import data**


1. **Data:** Select the climate or weather variable you would like to import.
2. **Period:** Choose the start and end dates for your import. The system will import **daily data** for the selected period, which can later be aggregated into **weekly** or **monthly** periods within DHIS2. If your DHIS2 instance uses a timezone different from UTC, the system will automatically calculate daily values based on your configured timezone.
3. **Parent organisation unit:** Select the parent organisation unit for which data should be imported. The system will import data for all organisation units that fall under this parent.
4. **Organisation unit level:** Select the organisation unit level for import. The system will import data for all units at this level under the selected parent. If the parent organisation unit is already at that level, data will be imported only for that single unit.
5. **Data element:** Select the DHIS2 data element where the imported data will be stored. Refer to the previous section for details on how to configure data elements correctly.
6. **Import summary:** After the import, an import summary will be displayed showing:
    1. The number of data values successfully imported or updated.
    2. Any data values that failed to import, along with the reason for each failure


## Settings

In the Settings section, you can adjust system-wide settings for the Climate App, which will apply to all Climate App users on your DHIS2 instance.


* *Default start page for users* - this sets the landing page for all users of the Climate App, so you can skip the Home page and go straight to Explore Data.
* *Time zone where your org units are located* - used for displaying 10-day weather forecasts with the correct time zone of the org unit locations. This overrides the time zone of the user’s web browser.

**Chart settings**

All charts under the Explore Data section display data for a single organisation unit at a time. Y-axis ranges are set automatically by the data displayed. The Chart settings allow you to set y-axis ranges for various data series displayed in these charts. This would help compare data across organisation units, for example, downloading climate charts at different organisation units to present together.

The list of ranges here are included. This list may change over time as more climate parameters are added to the Climate App.

* Max and min temperature
* Max change in temperature
* Max monthly and daily temperature
* Heat stress upper and lower categories
