# slo podravje region draft2

### Introduction and Objectives of the Climate Risk Assessment

#### Regional context

The [Podravje Region](https://en.wikipedia.org/wiki/Podravje_Statistical_Region), located in northeastern Slovenia, covers a diverse mix of urban, rural, and riverine landscapes, with key urban centres such as [Maribor](https://en.wikipedia.org/wiki/Maribor) (the country’s second largest city) and Ptuj (one of Slovenia’s oldest towns). The region is dominated by the [Drava River](https://en.wikipedia.org/wiki/Drava) basin and its tributaries, with fertile agricultural lowlands and a dense network of settlements. This geographic setting, coupled with changing climatic patterns, exposes the area to multiple climate-related hazards. Riverine and pluvial flooding and urban heatwaves are identified as priority risks in this tutorial. Drought and biodiversity loss also affect the region but are not addressed in detail in this first release.

#### Scope of the tutorial

This tutorial describes a replicable Climate Risk Assessment (CRA) workflow for the two main hazards — floods (both fluvial and pluvial) and urban heatwaves — in the Podravje Innovation Lab. The approach does not require coding and relies on a combination of national datasets, proprietary and open-source tools, and publicly available European datasets to ensure transferability to other regions. The workflow supports integration of Nature-Based Solutions (NbS) and Blue-Green Infrastructure (BGI) into local and regional adaptation strategies, enabling assessment under current and projected climate scenarios.

{% hint style="info" %}
This tutorial is intended as a general workflow example and does not replace software-specific documentation (e.g., GIS, hydrological, hydraulic, or urban climate modelling tools user/technical manuals). Users should already be familiar with the relevant geospatial data formats, data pre-processing techniques, and modelling concepts applicable to their hazard of interest (e.g., floods, UHIs, droughts, etc.), as well as with the specific input/output requirements and run functionalities of the modelling software before attempting to replicate this workflow.
{% endhint %}

#### CRA objectives

* Understand vulnerabilities — Identify communities, ecosystems, and infrastructure most exposed to floods and heatwaves.
* Characterize hazards — Analyze current and future climate conditions using observed data, climate projections, and socio-economic scenarios.
* Assess impacts — Quantify exposure and potential consequences across key sectors such as agriculture, infrastructure, water resources, health, and biodiversity.
* Prioritize adaptation measures — Identify where NbS and BGI can deliver the highest resilience gains and co-benefits.
* Support planning and policy — Provide evidence for land-use planning, emergency preparedness, and regional development strategies.
* Enable monitoring — Define baseline indicators and monitoring frameworks to track hazard trends and adaptation effectiveness over time.

#### Intended users

For both hazards, the Climate Risk Assessment is intended for regional and municipal authorities who need to integrate hazard and exposure data into spatial and emergency planning, civil protection agencies responsible for preparedness and response to extreme events, and environmental NGOs and research institutions engaged in monitoring, restoration, and public outreach. Policy-makers and land managers also use the results to design adaptive regulations and direct investments where resilience measures can provide the greatest benefits.

In the Podravje context, this means that flood hazard outputs support zoning, infrastructure planning, and the identification of priority areas for floodplain restoration, while heatwave assessments guide urban greening strategies, cooling infrastructure placement, and health risk reduction measures in vulnerable districts.

### Flood Hazard – Podravje Region

#### Description and context

The Podravje Region is exposed to two main types of flooding: fluvial flooding from the Drava River and its tributaries, and pluvial flooding resulting from intense rainfall events. Both hazards affect urban areas such as Maribor and Ptuj, as well as surrounding agricultural lowlands. Historic events have caused significant damage to farmland, settlements, transport infrastructure, and cultural heritage.

Climate projections indicate an increased frequency of extreme precipitation, which will likely amplify both flood extent and depth in the future. The regional adaptation strategy promotes Nature-Based Solutions (NbS) and Blue-Green Infrastructure (BGI), for example restoration of wetlands and riparian zones along the Drava River to reduce flood risk and enhance biodiversity.

| Dimension             | Indicator(s)                                                               | Unit            | Purpose                                                              |
| --------------------- | -------------------------------------------------------------------------- | --------------- | -------------------------------------------------------------------- |
| Flood extent & depth  | Flooded area and maximum water depth by return period (10, 100, 200 years) | km², m          | Identify hazard zones, quantify severity, and guide design standards |
| Frequency & intensity | Return period statistics and climate-adjusted scenarios                    | Years, % change | Evaluate changing hazard probability under climate change            |

Table 1 – key indicators tracked — Flood Hazard

Figure 1 – example of flood risk map for Flood map Slovenia – river Drava in its downstream in Slovenia.

#### Data sources and tools

Flood risk assessment in Podravje relies on an integrated set of hydrological, topographic, and land use datasets.

Hydrological data form the backbone of the workflow. The Slovenian Environment Agency (ARSO) provides estimation of a peak discharge at selected stations for specific return periods (e.g. 10, 100, 500 years) to be used directly in hydraulic models.

Historical flood event records may also be consulted to validate hazard maps and identify vulnerable locations.

High-resolution LiDAR-based Digital Terrain Models (1 m) provide the topographic base for hydraulic simulations and floodplain delineation, while land use and cover maps from the Slovenski INSPIRE system define runoff characteristics and support exposure analysis.

For regional transferability or gap-filling, Copernicus DEM (10–30 m), Copernicus Climate Data Store hydrology-related impact indicators, and harmonized land cover datasets (CLCplus Backbone, Urban Atlas) may be explored.

| Data type                                        | Source                                                                                                                  | Role in workflow                                                                           | Open/EU alternative                                                                                                                                                                                                                                         |
| ------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Annual max river discharge values                | [ARSO gauging stations](https://vode.arso.gov.si/hidarhiv/pov_arhiv_tab.php)                                            | Input to flood frequency analysis (if official extreme flood statistics are not available) | None (site-specific)                                                                                                                                                                                                                                        |
| Historical flood event data and flood statistics | [ARSO publications](https://www.arso.gov.si/vode/podatki/)                                                              | Input for flood hazard maps                                                                | Copernicus [Hydrology-related climate impact indicators from 1970 to 2100 derived from bias adjusted European climate projections](https://cds.climate.copernicus.eu/datasets/sis-hydrology-variables-derived-projections?tab=overview) (daily values only) |
| Digital Terrain Model (1 m LiDAR)                | [ARSO Geoportal](https://gis.arso.gov.si/evode/profile.aspx?id=atlas_voda_Lidar@Arso)                                   | Hydraulic model topography; floodplain delineation                                         | [Copernicus DEM](https://dataspace.copernicus.eu/explore-data/data-collections/copernicus-contributing-missions/collections-description/COP-DEM) (10–30 m)                                                                                                  |
| Land use / land cover                            | [Slovenski INSPIRE](https://eprostor.gov.si/imps/srv/eng/catalog.search#/metadata/49c8dd3a-e5db-4ed1-8bf1-e1b7def60dd0) | Exposed assets overlay                                                                     | Copernicus [Urban Atlas](https://land.copernicus.eu/en/products/urban-atlas), [CLCplus Backbone](https://land.copernicus.eu/en/products/clc-backbone)                                                                                                       |
| Building Footprints                              | [Slovenski INSPIRE](https://eprostor.gov.si/imps/srv/eng/catalog.search#/metadata/9a8fd241-9162-407c-94e7-c98e05766881) | Exposed assets overlay, DTM correction to consider building presence                       | OpenStreetMap building layer ([vector, global](https://osmbuildings.org/)); Copernicus Urban Atlas (with building block heights)                                                                                                                            |

Table 3 – used data, an alternative dataset to replicate the assessment outside the study area, when available

{% hint style="info" %}
Although the current workflow does not incorporate official climate projections, a first approximation of future flood hazards, if not available from local studies, may be derived using open datasets from the Copernicus Climate Data Store. These include bias-adjusted impact indicators such as daily river discharge extremes under different climate scenarios (e.g. RCP 8.5).

A practical example of this approach has been implemented [here](https://www.euspa.europa.eu/newsroom-events/success-stories/copernicus-hydropower-flood-assessments) for a hydropower site in Switzerland, where Copernicus climate projections, coupled with limited gauging station statistics for basic downscaling, were used to estimate future 100-year flood discharges and run simplified hydraulic simulations to assess potential downstream impacts. The methodology explores how to use Copernicus datasets to create a preliminary “climate-adjusted” flood map.
{% endhint %}

The following tools, both proprietary and open-source, can be used in the Podravje flood hazard workflow:

| Tool                                                                                                                         | Type        | Role                                                                             |
| ---------------------------------------------------------------------------------------------------------------------------- | ----------- | -------------------------------------------------------------------------------- |
| [HEC-RAS](https://www.hec.usace.army.mil/software/hec-ras/download.aspx)                                                     | Open        | Hydraulic modelling of riverine and pluvial floods                               |
| [ArcGIS Pro Flood Simulation](https://pro.arcgis.com/en/pro-app/latest/help/mapping/simulation/simulation-in-arcgis-pro.htm) | Proprietary | GIS based flood modeling tool                                                    |
| [SaferPlaces](https://saferplaces.co/)                                                                                       | Proprietary | Cloud-based hazard modelling for fluvial, pluvial and coastal flooding scenarios |
| [QGIS](https://qgis.org/)                                                                                                    | Open        | Spatial analysis, mapping, and hazard–exposure overlay                           |
| [ArcGIS Pro](https://www.esri.com/en-us/arcgis/products/arcgis-pro/overview)                                                 | Proprietary | Spatial analysis, mapping, and hazard–exposure overlay                           |

Table 2 – used tools and role in the Flood Hazard workflow

#### Methodology

{% stepper %}
{% step %}
### Data acquisition and preparation

* Download local hydrological time series of maximum peak flood or official floods statistics for target stations. These will be used for local flood model input (“design events”).
* Using GIS tools prepare terrain from high-resolution LiDAR DTM (e.g., mosaic tiles in the area of interest, enforce structures such as buildings). Note: LiDAR datasets have no information on underwater topography; this may be derived from local bathymetric surveys or estimated where unavailable.
* Harmonize land use/cover for roughness and exposure in GIS. Depending on the flood modeling tool, this layer may serve as a basemap to assign surface roughness values.
* Gather boundary conditions for upstream inflows (peak flow for assigned return time of interest), tributaries if present, and downstream conditions (e.g., energy slope).

Figure 2 – example of Lidar DTM from ARSO geoportal compared to satellite map, obstacles such as buildings and trees are filtered from the terrain surface. Underwater topography is not represented.
{% endstep %}

{% step %}
### Model setup and run

* Define the hydraulic domain and scheme (1D/2D/coupled) with a stable mesh; assign Manning’s n from land-use classes.
* Configure steady or unsteady simulations depending on hydrological input and computational resources. Use local hardware for small/medium simulations or cloud platforms for large-scale, data-intensive runs.
* Import topography (DTM) and modify it to consider underwater topography and relevant structures (levees, weirs, bridges). Refer to the flood modeling tool manual for specifics.
* If reference maps or observed stages are available, calibrate the model to reproduce observed events, then run design events (e.g., 10, 100, 500-year) to produce maximum water surface, depth, and velocity rasters.

Figure 3 – example of DTM imported in a flood Modeling tools (left) and roughness coefficient assigned over an imported land use map (right), generic urban area.
{% endstep %}

{% step %}
### Analysis and interpretation

* Post-process water depth rasters and (optionally) velocity maps in a GIS to plot extent and classify hazard (e.g., water depth ranges).
* Overlay hazard with buildings, infrastructure, land use, or other exposure layers (e.g., population) to quantify potential losses and social impacts, including affected populations and critical infrastructure.
{% endstep %}

{% step %}
### NbS testing for fluvial mitigation

* Screen reaches for floodplain reconnection, riparian and wetland restoration, levee setback or retention areas.
* Implement simple what-if runs to include NbS modifications in the flood model and compare baseline vs NbS options.
* Use GIS to derive performance indicators and statistics such as peak stage reduction, flooded area change, and number of exposed assets.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Where no detailed modeling of the river is possible (e.g., lack of river cross sections or presence of stable embankments), an alternative approach is estimating flood volume outside of the river (e.g., a fraction of the expected event volume in the river) and simulating a flood domain outside of the river, as shown in Figure 4.
{% endhint %}

Figure 4 – example of flood maps for a generic lowland area, derived by 2D modeling of estimated flood volumes outside of the river, courtesy of [SaferPlaces](https://saferplaces.co/rimini-and-climate-change-the-added-value-of-the-sea-park-parco-del-mare/).

Optionally, derive climate-adjusted variants by scaling design flows with CDS indicators consistent with local gauges.

### Heatwave Hazard – Podravje Region

#### Description and context

The Podravje Region experiences increasingly frequent and intense heatwaves, with the highest impacts concentrated in urban areas such as Maribor and Ptuj. The [Urban Heat Island (UHI)](https://land.copernicus.eu/en/feature-articles/urban-heat-islands-measured-mapped-and-managed) effect amplifies thermal stress in dense built-up districts, where impervious surfaces and limited vegetation lead to higher air and surface temperatures compared to surrounding rural areas.

These conditions pose health risks, especially for vulnerable populations (elderly, children, people with pre-existing health conditions), reduce thermal comfort, and exacerbate energy demand for cooling. Climate projections indicate a further increase in the frequency, intensity, and duration of heatwave events in the coming decades.

Historical climate data show warming trends in Slovenia. The comparison of average July temperatures between the periods 1971–2000 and 1981–2010 reveals a consistent increase across the country. These patterns underline the relevance of heatwave and UHI assessments in the Podravje Region.

Figure 5 - Deviation of average temperature in Slovenia.

Figure 6 - Comparison of average temperature in July (left period 1971-2000, right: period 1981-2010)

Adaptation strategies for the heatwave hazard focus on Nature-Based Solutions (NbS) and Blue-Green Infrastructure (BGI) to mitigate the UHI effect, including expansion of urban tree canopy, creation of green corridors, installation of green roofs and walls, and integration of water features for evaporative cooling.

| Dimension                | Indicator(s)                                   | Unit     | Purpose                                     |
| ------------------------ | ---------------------------------------------- | -------- | ------------------------------------------- |
| UHI extent & intensity   | Temperature anomaly vs rural baseline          | °C, km²  | Identify and map urban heat hotspots        |
| Heatwave characteristics | Duration, frequency, maximum daily temperature | Days, °C | Quantify hazard severity and monitor trends |

Table 4 – key indicators tracked — UHI Hazard

#### Data sources and tools

Assessment of heatwave risk and UHI patterns in Podravje requires meteorological, remote sensing, and land use datasets.

* Meteorological data from ARSO provide daily maximum and mean air temperatures, humidity, wind speed, and solar radiation for identifying extreme heat events and calculating indices.
* Remote sensing data (Landsat, Sentinel-3) supply Land Surface Temperature (LST) maps to detect UHI intensity.
* Land use and morphology datasets, including building footprints and heights (Slovenski INSPIRE, Urban Atlas), help analyze spatial configuration of heat hotspots.
* For future projections, bias-adjusted datasets from the Copernicus Climate Data Store offer temperature scenarios aligned with regional models.

Example datasets:

| Data type                              | Source                                                                                                                                        | Role in workflow                                                               | Open/EU alternative                                                                                                                                                                                                                                               |
| -------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Digital Terrain Model (1 m LiDAR)      | [ARSO Geoportal](https://gis.arso.gov.si/evode/profile.aspx?id=atlas_voda_Lidar@Arso)                                                         | Base terrain morphology for heat modeling                                      | No open alternative at required resolution; check national/regional geoportals                                                                                                                                                                                    |
| Digital Surface Model (DSM)            | Derived from LiDAR LAS files (ARSO Geoportal)                                                                                                 | Represent building and vegetation heights                                      | —                                                                                                                                                                                                                                                                 |
| Hourly temperature & climate variables | ARSO meteorological network                                                                                                                   | Meteo input to heat stress analysis                                            | Copernicus [ERA5-Land hourly data](https://cds.climate.copernicus.eu/datasets/reanalysis-era5-land?tab=download); [Heat waves and cold spells derived from climate projections](https://cds.climate.copernicus.eu/datasets/sis-heat-and-cold-spells?tab=overview) |
| Land Surface Temperature (LST)         | Satellite imagery (Landsat, Sentinel)                                                                                                         | Map UHI via thermal imaging                                                    | [Landsat8 LST resources](https://rslab.gr/Landsat_LST.html)                                                                                                                                                                                                       |
| Land use / land cover                  | [Slovenski INSPIRE](https://eprostor.gov.si/imps/srv/eng/catalog.search#/metadata/49c8dd3a-e5db-4ed1-8bf1-e1b7def60dd0)                       | UHI drivers and green areas                                                    | Copernicus [Urban Atlas](https://land.copernicus.eu/en/products/urban-atlas), [CLCplus Backbone](https://land.copernicus.eu/en/products/clc-backbone)                                                                                                             |
| Building Footprints                    | [Slovenski INSPIRE metapodatkovni sistem](https://eprostor.gov.si/imps/srv/eng/catalog.search#/metadata/9a8fd241-9162-407c-94e7-c98e05766881) | Local topography modification in detailed modeling; building height estimation | OpenStreetMap building layer ([vector, global](https://osmbuildings.org/)); Copernicus Urban Atlas (building block heights, street trees)                                                                                                                         |
| Population                             | @                                                                                                                                             | Overlay to heat stress to detect where UHI exacerbate public health risks      | [WorldPop Hub](https://dx.doi.org/10.5258/SOTON/WP00646)                                                                                                                                                                                                          |
| Vegetation                             | @ (height assigned via DSM–DTM difference)                                                                                                    | Map vegetation to estimate vegetation height when no DSM is available          | Copernicus High Resolution Layer [Tree Cover and Forests](https://land.copernicus.eu/en/products/high-resolution-layer-forests-and-tree-cover) (10 m raster)                                                                                                      |

Table 3 – used data, alternative datasets where available

**Meteorological inputs**

Meteorological input requirements and formatting vary by modelling code. For UHI simulations with UMEP, required variables include air temperature, dew point or relative humidity, surface pressure, wind speed and direction, shortwave radiation (global, diffuse and direct), longwave radiation, precipitation, and cloud cover. UMEP relies on the EPW format (EnergyPlus Weather). EPW files can be downloaded from several sources or generated from reanalysis datasets such as ERA5(-Land). Users are encouraged to download the file closest to their location and adapt it with local meteorological data so the weather inputs reflect actual conditions.

Free tools are available to inspect and modify EPW files, such as [Elements](https://bigladdersoftware.com/projects/elements/). Read the official UMEP documentation and tutorials to adjust EPW variables appropriately.

Tools for the UHI workflow:

| Tool                                                                                                         | Type        | Role                                                                                                                   |
| ------------------------------------------------------------------------------------------------------------ | ----------- | ---------------------------------------------------------------------------------------------------------------------- |
| [QGIS](https://qgis.org/)                                                                                    | Open        | Spatial analysis and mapping of UHI hotspots; integration of temperature, land cover, vegetation, and demographic data |
| [ArcGIS Pro](https://www.esri.com/en-us/arcgis/products/arcgis-pro/overview)                                 | Proprietary | Advanced spatial analysis, 3D visualization, and map production                                                        |
| [UMEP](https://umep-docs.readthedocs.io/projects/tutorial/en/latest/Tutorials/UWGSpatial.html) (QGIS plugin) | Open        | Urban climate modelling, UHI mapping and scenario analysis using Urban Weather Generator (UWG)                         |
| [ENVI-met](https://envi-met.com/)                                                                            | Proprietary | 3D microclimate modelling to simulate temperature distribution, vegetation effects, and NbS cooling potential          |

Table 2 – used tools and role in the UHI workflow

#### Methodology – Step-by-step

{% stepper %}
{% step %}
### Data acquisition and preparation

* Obtain historical temperature and humidity series from ARSO to define baseline conditions and detect past extreme heat events.
* Acquire land use and land cover layers (Slovenski INSPIRE or Copernicus Urban Atlas), including vegetation cover, building footprints, and building heights derived from DSM generated from LiDAR LAS files.
* Add population datasets (e.g., WorldPop) to assess exposure and identify vulnerable communities.
* Convert all datasets into GIS-compatible formats.
* Retrieve cloud-free Landsat-derived LST images for peak summer periods. In GIS, classify LST values into temperature ranges (e.g., < 25 °C, 25–35 °C, > 45 °C) to produce a first proxy map of UHI zones.
* Reformat layers to match the chosen modelling framework (e.g., classify land cover, generate DTM/DSM, attribute building polygons with height/materials, prepare hourly meteorological series).

Figure 7 – example of LST \[°C] Satellite map from Landsat 8 image for July 2025 loaded and classified in GIS, with population density overlay.
{% endstep %}

{% step %}
### Analysis and mapping

* Map near-surface air temperature and compute anomalies between urban cores and surrounding rural areas to map UHI intensity and extent.
* Overlay UHI maps with demographic layers to locate clusters of vulnerable populations.
* Produce thematic layers showing spatial patterns of thermal stress and relationships with physical drivers (vegetation cover, building density, land cover, population distribution). These layers identify priority areas for mitigation.
{% endstep %}

{% step %}
### Baseline urban climate modelling

* Import pre-processed land cover, vegetation, and morphology grids into the chosen modelling framework.
* Integrate meteorological time series representative of identified heatwave periods.
* Parameterize urban form (building heights, materials, vegetation characteristics) to reflect present-day conditions.
* Use satellite-derived LST maps and temperature anomaly layers to cross-check model outputs and validate simulated baseline conditions.

Figure 8 – example of temperature difference in mean ground temperature \[°C] for an urban area simulated with UMEP.
{% endstep %}

{% step %}
### NbS scenario testing

* Repeat baseline modelling including Nature-Based Solutions (increase urban tree canopy, create green corridors, install green roofs/walls, apply reflective materials).
* Configure scenarios in the modelling framework to quantify cooling effects under present and projected future climates (e.g., downscaled Copernicus CDS scenarios).
* Compare scenario outputs with baseline to evaluate changes in maximum temperatures, reduction of UHI hotspot extent, and improvements in thermal comfort indices. Integrate observed thermal maps to validate simulated changes where relevant.
{% endstep %}
{% endstepper %}
