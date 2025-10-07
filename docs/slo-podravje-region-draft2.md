## Introduction and Objectives of the Climate Risk Assessment

### Regional context.

The [Podravje
Region](https://en.wikipedia.org/wiki/Podravje_Statistical_Region),
located in northeastern Slovenia, covers a diverse mix of urban, rural,
and riverine landscapes, with key urban centres such as
[Maribor](https://en.wikipedia.org/wiki/Maribor) (the country’s second
largest city) and Ptuj (one of Slovenia’s oldest towns). The region is
dominated by the [Drava River](https://en.wikipedia.org/wiki/Drava)
basin and its tributaries, with fertile agricultural lowlands and a
dense network of settlements. This geographic setting, coupled with
changing climatic patterns, exposes the area to multiple climate-related
hazards. Riverine and pluvial flooding and urban heatwaves are
identified as priority risks in this tutorial. Drought and biodiversity
loss also affect the region but are not addressed in detail in this
first release.

### Scope of the tutorial.

This tutorial describes a replicable Climate Risk Assessment (CRA)
workflow for the two main hazards — floods (both fluvial and pluvial)
and urban heatwaves — in the Podravje Innovation Lab. The approach does
not require coding and relies on a combination of national datasets,
proprietary and open-source tools, and publicly available European
datasets to ensure transferability to other regions. The workflow
supports integration of Nature-Based Solutions (NbS) and Blue-Green
Infrastructure (BGI) into local and regional adaptation strategies,
enabling assessment under current and projected climate scenarios.

  - #### Disclaimer

> This tutorial is intended as a general workflow example and does not
> replace software-specific documentation (e.g., GIS, hydrological,
> hydraulic, or urban climate modelling tools user/technical manuals).
> Users should already be familiar with the relevant geospatial data
> formats, data pre-processing techniques, and modelling concepts
> applicable to their hazard of interest (e.g., floods, UHIs, droughts,
> etc.), as well as with the specific input/output requirements and run
> functionalities of the modelling software before attempting to
> replicate this workflow

### CRA objectives.

The Podravje CRA aims to:

**Understand vulnerabilities** — Identify communities, ecosystems, and
infrastructure most exposed to floods and heatwaves.

**Characterize hazards** — Analyze current and future climate conditions
using observed data, climate projections, and socio-economic scenarios.

**Assess impacts** — Quantify exposure and potential consequences across
key sectors such as agriculture, infrastructure, water resources,
health, and biodiversity.

**Prioritize adaptation measures** — Identify where NbS and BGI can
deliver the highest resilience gains and co-benefits.

**Support planning and policy** — Provide evidence for land-use
planning, emergency preparedness, and regional development strategies.

**Enable monitoring** — Define baseline indicators and monitoring
frameworks to track hazard trends and adaptation effectiveness over
time.

### Intended users.

For both hazards, the Climate Risk Assessment is intended for r**egional
and municipal authorities** who need to integrate hazard and exposure
data into spatial and emergency planning, civil protection **agencies**
responsible for preparedness and response to extreme events, and
**environmental NGOs and research institutions** engaged in monitoring,
restoration, and public outreach. **Policy-makers** and **land
managers** also use the results to design adaptive regulations and
direct investments where resilience measures can provide the greatest
benefits.

In the Podravje context, this means that flood hazard outputs support
zoning, infrastructure planning, and the identification of priority
areas for floodplain restoration, while heatwave assessments guide urban
greening strategies, cooling infrastructure placement, and health risk
reduction measures in vulnerable districts.

## Flood Hazard – Podravje Region

### Description and context

The Podravje Region is exposed to two main types of flooding: **fluvial
flooding** from the Drava River and its tributaries, and **pluvial
flooding** resulting from intense rainfall events. Both hazards affect
urban areas such as Maribor and Ptuj, as well as surrounding
agricultural lowlands. Historic events have caused significant damage to
farmland, settlements, transport infrastructure, and cultural heritage.

Climate projections indicate an increased frequency of extreme
precipitation, which will likely amplify both flood extent and depth in
the future. The regional adaptation strategy promotes **Nature-Based
Solutions (NbS)** and **Blue-Green Infrastructure (BGI)**, for example
Restoration of wetlands and riparian zones along the Drava River to
reduce flood risk and enhance biodiversity.

| **Dimension**         | **Indicator(s)**                                                           | **Unit**        | **Purpose**                                                          |
| --------------------- | -------------------------------------------------------------------------- | --------------- | -------------------------------------------------------------------- |
| Flood extent & depth  | Flooded area and maximum water depth by return period (10, 100, 200 years) | km², m          | Identify hazard zones, quantify severity, and guide design standards |
| Frequency & intensity | Return period statistics and climate-adjusted scenarios                    | Years, % change | Evaluate changing hazard probability under climate change            |

Table 1 – key indicators tracked-Flood Hazard

![Slika, ki vsebuje besede zemljevid, besedilo, atlas Vsebina,
ustvarjena z umetno inteligenco, morda ni
pravilna.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/SLO-Podravje%20Region_draft2_media/media/image1.png)

Figure 1 – example of flood risk map for Flood map Slovenia – river
Drava in its downstream in Slovenia.

### Data sources and tools

Flood risk assessment in Podravje relies on an integrated set of
**hydrological**, **topographic**, and **land use** datasets.

Hydrological data form the backbone of the workflow. The Slovenian
Environment Agency (ARSO) provides estimation of a peak discharge at
selected stations for specific return periods (e.g. 10, 100, 500 years)
o be used directly in hydraulic models

Historical flood event records may also be consulted to validate hazard
maps and identify vulnerable locations.

High-resolution **LiDAR-based Digital Terrain Models (1 m)** provide the
topographic base for hydraulic simulations and floodplain delineation,
while land use and cover maps from the Slovenski INSPIRE system define
runoff characteristics and support exposure analysis.

For regional transferability or gap-filling, **Copernicus DEM** (10–30
m), **Copernicus Climate Data Store** hydrology-related impact
indicators, and harmonized land cover datasets (CLCplus Backbone, Urban
Atlas) may be explored.

<table>
<thead>
<tr class="header">
<th><strong>Data type</strong></th>
<th><strong>Source</strong></th>
<th><strong>Role in workflow</strong></th>
<th><strong>Open/EU alternative</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Annual max river discharge values</td>
<td><a href="https://vode.arso.gov.si/hidarhiv/pov_arhiv_tab.php">ARSO gauging stations</a></td>
<td>Input to flood frequency analysis (if official extreme flood statistics are not available)</td>
<td>None (site-specific)</td>
</tr>
<tr class="even">
<td>Historical flood event data and flood statistics</td>
<td><a href="https://www.arso.gov.si/vode/podatki/">ARSO publications</a></td>
<td>Input for flood hazard maps</td>
<td>Copernicus <a href="https://cds.climate.copernicus.eu/datasets/sis-hydrology-variables-derived-projections?tab=overview">Hydrology-related climate impact indicators from 1970 to 2100 derived from bias adjusted European climate projections</a> (daily values only)</td>
</tr>
<tr class="odd">
<td>Digital Terrain Model (1 m LiDAR)</td>
<td><a href="https://gis.arso.gov.si/evode/profile.aspx?id=atlas_voda_Lidar@Arso">ARSO Geoportal</a></td>
<td>Hydraulic model topography; floodplain delineation</td>
<td><a href="https://dataspace.copernicus.eu/explore-data/data-collections/copernicus-contributing-missions/collections-description/COP-DEM">Copernicus DEM</a> (10–30 m)</td>
</tr>
<tr class="even">
<td>Land use / land cover</td>
<td><a href="https://eprostor.gov.si/imps/srv/eng/catalog.search#/metadata/49c8dd3a-e5db-4ed1-8bf1-e1b7def60dd0">Slovenski INSPIRE,</a></td>
<td>Exposed assets overlay</td>
<td><p><strong>Copernicus</strong> <a href="https://land.copernicus.eu/en/products/urban-atlas"><strong>Urban Atlas</strong></a></p>
<p><a href="https://land.copernicus.eu/en/products/clc-backbone"><strong>CLCplus Backbone</strong></a></p></td>
</tr>
<tr class="odd">
<td><strong>Building Footprints</strong></td>
<td><a href="https://eprostor.gov.si/imps/srv/eng/catalog.search#/metadata/9a8fd241-9162-407c-94e7-c98e05766881">Slovenski INSPIRE</a></td>
<td>Exposed assets overlay, DTM correction to consider building presence</td>
<td><p><strong>OpenStreetMap building layer (<a href="https://osmbuildings.org/">vector, global)</a></strong></p>
<p><strong>Copernicus</strong> <strong><a href="https://land.copernicus.eu/en/products/urban-atlas">Urban Atlas</a> (harmonised land use and land cover maps as well as information on <a href="https://land.copernicus.eu/en/products/urban-atlas?tab=building_height">building block heights</a></strong></p></td>
</tr>
</tbody>
</table>

Table 3 – used data, an alternative dataset to replicate the assessment
outside the study area, when available

  - #### Climate change effects in hydrological extremes

> *Although the current workflow does not incorporate official climate
> projections, a first approximation of future flood hazards, if not
> available from local studies, may be derived using open datasets from
> the Copernicus Climate Data Store. These include bias-adjusted impact
> indicators such as daily river discharge extremes under different
> climate scenarios (e.g. RCP 8.5).*
> 
> *A practical example of this approach has been implemented*
> *[here](https://www.euspa.europa.eu/newsroom-events/success-stories/copernicus-hydropower-flood-assessments)
> for a hydropower site in Switzerland, where Copernicus climate
> projections, coupled with limited gauging station statistics for basic
> downscaling, were used to estimate future 100-year flood discharges
> and run simplified hydraulic simulations to assess potential
> downstream impacts. The methodology explores how to use Copernicus
> datasets to create a preliminary “climate-adjusted” flood map.*

**The following tools**, both proprietary and open-source, can be used
in the Podravje flood hazard workflow to acquire, process, and model
hydrological and spatial data, to generate decision-ready outputs and
replicate the assessment in other regions:

| **Tool**                                                                                                                     | **Type**    | **Role**                                                                         |
| ---------------------------------------------------------------------------------------------------------------------------- | ----------- | -------------------------------------------------------------------------------- |
| [HEC-RAS](https://www.hec.usace.army.mil/software/hec-ras/download.aspx)                                                     | Open        | Hydraulic modelling of riverine and pluvial floods                               |
| [ArcGIS Pro Flood Simulation](https://pro.arcgis.com/en/pro-app/latest/help/mapping/simulation/simulation-in-arcgis-pro.htm) | Proprietary | GIS based flood modeling tool                                                    |
| [SaferPlaces](https://saferplaces.co/)                                                                                       | Proprietary | Cloud-based hazard modelling for fluvial, pluvial and coastal flooding scenarios |
| [QGIS](https://qgis.org/)                                                                                                    | Open        | Spatial analysis, mapping, and hazard–exposure overlay                           |
| [ArcGIS Pro](https://www.esri.com/en-us/arcgis/products/arcgis-pro/overview)                                                 | Proprietary | Spatial analysis, mapping, and hazard–exposure overlay                           |

Table 2 – used tools and role in the Flood Hazard workflow, when
available a free similar alternative to proprietary solutions is
provided.

### Methodology

#### Step 1 - Data acquisition and preparation

Download local hydrological time series of maximum peak flood or
directly official floods statistics for target stations. Thes will be
used for local flood model input (“design events”)

Using GIS tools prepare terrain from high resolution LiDAR DTM (e.g.
mosaic tiles in the area of interest, enforce structures such as
buildings). Please note that Lidar datasets have no information on
underwater topography (Figure 2), this may be derived from local
bathymetric surveys or, in the worst case, estimated.

Harmonize land use/cover for roughness and exposure in GIS. Depending on
the flood modeling tool you are using, this layer may serve as a basemap
to assign surface roughness values as well

Gather boundary conditions for upstream inflows (peak flow for assigned
return time of interest), tributaries if present and downstream
conditions (e.g. energy slope)

](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/SLO-Podravje%20Region_draft2_media/media/image2.png)![Immagine
che contiene schizzo, bianco e nero Il contenuto generato dall'IA
potrebbe non essere
corretto.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/SLO-Podravje%20Region_draft2_media/media/image3.png)

Figure 2 – example of Lidar DTM from ARSO geoportal compared to
satellite map, obstacles such as buildings and trees are filtered from
the terrain surface. Underwater topography is not represented.

#### Step 2 - Model setup and run

Define the hydraulic domain and scheme (1D/2D/coupled) with a stable
mesh; assign Manning’s n from land-use classes. Configure steady or
unsteady simulations depending on the hydrological input available and
your time computation resources constraint. Depending on the model
complexity and data volume, this may involve use of local hardware, for
smaller-scale or less complex simulation or Cloud-Based Platform, for
large-scale, data-intensive simulations requiring significant
computational power.

Import topography (DTM) and modify it to consider underwater topography,
presence of structures such as levees of relevant hydraulic structures
(such as weirs or bridges) m please refer to the flood modeling tool
manual for details.

](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/SLO-Podravje%20Region_draft2_media/media/image4.png)![Immagine
che contiene mappa, dipinto, Policromia, arte Il contenuto generato
dall'IA potrebbe non essere
corretto.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/SLO-Podravje%20Region_draft2_media/media/image5.png)

Figure 3 – example of DTM imported in a flood Modeling tools (lefts) and
roughness coefficient assigned over an imported land use map (right),
generic urban area.

If you have reference maps (e.g. Figure 1) or observed stages
corresponding to observed flows you may first calibrate your model to
reproduce such event, then run design events (e.g., 10, 100, 500-year)
to produce maximum water surface, depth, and velocity raster.

  - #### Note: river modeling 

> **Where no detailed modeling of the river is possible** nor of
> interest (e.g. for lack of river cross sections or presence of stable
> embankments) an alternative approach is estimating **flood volume
> outside of the river** (e.g. a fraction of the expected event volume
> in the river) and simulating a flood domain outside of the river , as
> in the example of Figure 7

](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/SLO-Podravje%20Region_draft2_media/media/image6.png)![Immagine
che contiene schermata, blu, Parallelo, linea Il contenuto generato
dall'IA potrebbe non essere
corretto.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/SLO-Podravje%20Region_draft2_media/media/image7.png)

Figure 4 – example of flood maps for a generic lowland area, derived by
2d Modeling of estimated flood volumes outside of the river , courtesy
of
[SaferPlaces](https://saferplaces.co/rimini-and-climate-change-the-added-value-of-the-sea-park-parco-del-mare/)
platform.

Optionally, derive **climate-adjusted variants** by scaling design flows
with CDS indicators consistent with local gauges (see note in the Data
sources and tools section)

#### Step 3 - Analysis and interpretation

Post-process water depth raster maps, eventually velocity maps may be
loaded into GIS environment to plot extent and to classify hazard (e.g.
water depth ranges)

Overlay hazard with buildings, infrastructure, land use or other
relevant exposure layers (e.g. population) to quantifying potential
losses and social impacts, including affected populations and critical
infrastructure.

#### Step 4 - NbS testing for fluvial mitigation

Screen reaches for floodplain reconnection, riparian and wetland
restoration, levee flood protection areas

Implement simple what-if runs or scenario including presence of Nbs
modification in the flood model (step 2,) to compare baseline vs NbS
options

Eventually, I use GIS to derive performance indicators and statistics
such as peak stage reduction, flooded area change, and number of exposed
assets.

## Heatwave Hazard – Podravje Region

### Description and context

The Podravje Region experiences increasingly frequent and intense
**heatwaves**, with the highest impacts concentrated in urban areas such
as Maribor and Ptuj. The [**Urban Heat Island
(UHI)**](https://land.copernicus.eu/en/feature-articles/urban-heat-islands-measured-mapped-and-managed)
effect amplifies thermal stress in dense built-up districts, where
impervious surfaces and limited vegetation lead to higher air and
surface temperatures compared to surrounding rural areas.

These conditions pose health risks, especially for vulnerable
populations (elderly, children, people with pre-existing health
conditions), reduce thermal comfort, and exacerbate energy demand for
cooling. Climate projections indicate a further increase in the
frequency, intensity, and duration of heatwave events in the coming
decades.

Historical climate data already show clear warming trends in Slovenia.
The comparison of average July temperatures between the periods
1971–2000 and 1981–2010 reveals a consistent increase across the
country, while the deviation map highlights areas with the most
pronounced anomalies. These patterns underline the growing relevance of
heatwave and UHI assessments in the Podravje Region (Figure 2,Figure 3).

> ![Slika, ki vsebuje besede besedilo, grafični prikaz, vrstica, diagram
> Vsebina, ustvarjena z umetno inteligenco, morda ni
> pravilna.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/SLO-Podravje%20Region_draft2_media/media/image8.png)

Figure 5 - Deviation of average temperature in Slovenia.

> ![Slika, ki vsebuje besede besedilo, zemljevid, atlas, posnetek
> zaslona Vsebina, ustvarjena z umetno inteligenco, morda ni
> pravilna.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/SLO-Podravje%20Region_draft2_media/media/image9.png)
> 
> ![Slika, ki vsebuje besede besedilo, zemljevid Vsebina, ustvarjena z
> umetno inteligenco, morda ni
> pravilna.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/SLO-Podravje%20Region_draft2_media/media/image10.png)

Figure 6 -Comparison of average temperature in July (left period
1971-2000, right: period 1981-2010)

Adaptation strategies for the heatwave hazard focus on **Nature-Based
Solutions (NbS)** and **Blue-Green Infrastructure (BGI)** to mitigate
the UHI effect, including expansion of urban tree canopy, creation of
green corridors, installation of green roofs and walls, and integration
of water features for evaporative cooling.

| **Dimension**            | **Indicator(s)**                               | **Unit** | **Purpose**                                 |
| ------------------------ | ---------------------------------------------- | -------- | ------------------------------------------- |
| UHI extent & intensity   | Temperature anomaly vs rural baseline          | °C, km²  | Identify and map urban heat hotspots        |
| Heatwave characteristics | Duration, frequency, maximum daily temperature | Days, °C | Quantify hazard severity and monitor trends |

Table 4 – key indicators tracked-UHI Hazard

### Data sources and tools

Assessment of heatwave risk and UHI patterns in Podravje requires a
combination of meteorological, remote sensing, and land use datasets.

**Meteorological data** from ARSO provide daily maximum and mean air
temperatures, as well as humidity, wind speed, and solar radiation,
enabling the identification of extreme heat events and the calculation
of relevant indices.

**Remote sensing data**, such as Landsat and Sentinel-3 imagery, supply
Land Surface Temperature (LST) maps to detect and quantify UHI
intensity.

**Land use and morphology datasets**, including building footprints and
heights (Slovenski INSPIRE, Urban Atlas), are used to analyze the
spatial configuration of heat hotspots.  
For future climate projections, bias-adjusted datasets from the
**Copernicus Climate Data Store** offer temperature scenarios aligned
with regional climate models.

Following table illustrates example datasets:

<table>
<thead>
<tr class="header">
<th><strong>Data type</strong></th>
<th><strong>Source</strong></th>
<th><strong>Role in workflow</strong></th>
<th><strong>Open/EU alternative</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Digital Terrain Model (1 m LiDAR )</td>
<td><a href="https://gis.arso.gov.si/evode/profile.aspx?id=atlas_voda_Lidar@Arso">ARSO Geoportal</a></td>
<td>Base terrain morphology for heat modeling</td>
<td>No open alternative general DTM available at the resolution required for such analysis, explore your national- regional geoportals for lidar datasets</td>
</tr>
<tr class="even">
<td>Digital Surface Model (DSM</td>
<td>Derived from original LiDAR LAS files available on the <a href="ARSO%20Geoportal">ARSO Geoportal</a></td>
<td>Required for representing building and vegetation heights in heat modelling.</td>
<td></td>
</tr>
<tr class="odd">
<td>hourly temperature &amp; climate variables</td>
<td>ARSO meteorological network</td>
<td>Provide Meteo input to heat stress an analysis, see note on the meteorological inputs</td>
<td><p>Copernicus <a href="https://cds.climate.copernicus.eu/datasets/reanalysis-era5-land?tab=download"><strong>ERA5-Land hourly data from 1950 to present</strong></a></p>
<p><a href="https://cds.climate.copernicus.eu/datasets/sis-heat-and-cold-spells?tab=overview">Heat waves and cold spells in Europe derived from climate projections</a></p></td>
</tr>
<tr class="even">
<td>Land Surface Temperature (LST)</td>
<td></td>
<td>Map UHI presence via Satellite-Based Thermal Imaging</td>
<td><a href="https://rslab.gr/Landsat_LST.html">Landsat8</a> derived land surface temperature maps</td>
</tr>
<tr class="odd">
<td>Land use / land cover</td>
<td><a href="https://eprostor.gov.si/imps/srv/eng/catalog.search#/metadata/49c8dd3a-e5db-4ed1-8bf1-e1b7def60dd0">Slovenski INSPIRE,</a></td>
<td>UHI drivers and green areas</td>
<td><p><strong>Copernicus</strong> <a href="https://land.copernicus.eu/en/products/urban-atlas"><strong>Urban Atlas</strong></a></p>
<p><a href="https://land.copernicus.eu/en/products/clc-backbone"><strong>CLCplus Backbone</strong></a></p></td>
</tr>
<tr class="even">
<td><strong>Building Footprints</strong></td>
<td><a href="https://eprostor.gov.si/imps/srv/eng/catalog.search#/metadata/9a8fd241-9162-407c-94e7-c98e05766881"><strong>Slovenski INSPIRE metapodatkovni sistem</strong></a></td>
<td><p><strong>local topography modification in detailed modeling</strong></p>
<p><strong>building height shall be estimated</strong></p></td>
<td><p><strong>OpenStreetMap building layer (<a href="https://osmbuildings.org/">vector, global)</a></strong></p>
<p><strong>Copernicus</strong> <strong><a href="https://land.copernicus.eu/en/products/urban-atlas">Urban Atlas</a> (harmonised land use and land cover maps as well as information on <a href="https://land.copernicus.eu/en/products/urban-atlas?tab=building_height">building block heights</a> and street trees for</strong></p></td>
</tr>
<tr class="odd">
<td>Population</td>
<td>@</td>
<td>Overlay to heat stress, to detect where UHI exacerbate public health risks</td>
<td> <a href="https://dx.doi.org/10.5258/SOTON/WP00646">World pop Hub</a></td>
</tr>
<tr class="even">
<td>Vegetation</td>
<td><p>@</p>
<p>Height to be assigned to vegetation based on DSM-DTM difference</p></td>
<td>Map vegetation to estimate vegetation height above ground when no DSM is available</td>
<td><strong>Copernicus High Resolution Layer <a href="https://land.copernicus.eu/en/products/high-resolution-layer-forests-and-tree-cover">Tree Cover and Forests</a> (raster 10m)</strong></td>
</tr>
</tbody>
</table>

Table 3 – used data, an alternative dataset to replicate the assessment
outside the study area, when available

  - ##### meteorological inputs  
    *Meteorological input requirements and formatting vary depending on the modelling code used. For UHI simulations with UMEP (Table 2), the required variables include air temperature, dew point or relative humidity, surface pressure, wind speed and direction, shortwave radiation (global, diffuse and direct), longwave radiation, precipitation, and cloud cover. UMEP relies on the **EPW format (EnergyPlus Weather)**. EPW files are “typical meteorological dataset with a typical year” and be downloaded from several sources (e.g. EnergyPlus , EPWmap ) or generated from reanalysis datasets such as **ERA5(-Land)**. Users are encouraged to download the file closest to their location and **adapt it with local meteorological data**, so that the weather inputs reflect the actual conditions of the study area.*

> *Free tools are available to inspect and modify EPW files, such as
> [Elements](https://bigladdersoftware.com/projects/elements/). We
> recommend changing the epw file after reading the official **UMEP
> documentation and tutorial examples** (Table 2) to adjust the
> variables, ensuring that the file accurately represents both the local
> climate data and the modelling requirements.*

The following tools, combining GIS platforms, remote sensing processors,
and urban climate modelling software, can be used in the Podravje
heatwave workflow to process temperature and land cover data, map UHI
patterns, and test the effectiveness of mitigation strategies under
current and projected climate scenarios.

<table>
<thead>
<tr class="header">
<th><strong>Tool</strong></th>
<th><strong>Type</strong></th>
<th><strong>Role</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="https://qgis.org/">QGIS</a></td>
<td>Open</td>
<td>Spatial analysis and mapping of UHI hotspots; integration of temperature, land cover, vegetation, and demographic data</td>
</tr>
<tr class="even">
<td><a href="https://www.esri.com/en-us/arcgis/products/arcgis-pro/overview">ArcGIS Pro</a></td>
<td>Proprietary</td>
<td>Advanced spatial analysis, 3D visualization, and map production for UHI and heat stress assessments</td>
</tr>
<tr class="odd">
<td><a href="https://umep-docs.readthedocs.io/projects/tutorial/en/latest/Tutorials/UWGSpatial.html">UMEP</a> (QGIS plugin)<br />
<a href="https://umep-docs.readthedocs.io/projects/tutorial/en/latest/Tutorials/TARGETTutorial.html">Tutorials</a> a are available</td>
<td>Open</td>
<td>Urban climate modelling, including UHI mapping and scenario analysis using Urban Weather Generator (UWG)</td>
</tr>
<tr class="even">
<td><a href="https://envi-met.com/">ENVI-met</a></td>
<td>Proprietary</td>
<td>3D microclimate modelling to simulate temperature distribution, vegetation effects, and NbS cooling potential</td>
</tr>
</tbody>
</table>

Table 2 – used tools and role in the UHI workflow, when available a free
similar alternative to proprietary solutions is provided.

### Methodology – Step-by-step

#### Step 1 – Data acquisition and preparation

Obtain historical temperature and humidity series from **ARSO** to
define baseline climatic conditions and detect past extreme heat events.
Complement these with **land use and land cover** layers from Slovenski
INSPIRE or Copernicus Urban Atlas, including vegetation cover, building
footprints, and building heights derived from **DSM generated from LiDAR
LAS** files. Add **population datasets** (e.g., WorldPop) to assess
exposure and identify vulnerable communities. All datasets should be
converted into a **GIS-compatible format**.

Retrieve **cloud-free Landsat-derived Land Surface Temperature (LST)**
images for peak summer periods (Figure 7). In GIS, classify LST values
into indicative temperature ranges (e.g., \< 25 °C, 25–35 °C, \> 45 °C)
to produce a first proxy map of UHI zones.

For microclimate modelling, these layers often require reformatting to
match the input structure of the chosen modelling framework (e.g.,
ENVI-met, UMEP). This includes:

  - Classifying land cover into model-compatible categories

  - Generating continuous DTM and DSM surfaces

  - Attributing building polygons with height and material properties

  - Preparing hourly meteorological series in the correct format

These pre-processing operations can be performed manually in GIS or
using dedicated utilities integrated in the modelling framework. For
instance, the **UMEP plugin for QGIS** offers functions to extract urban
form parameters, generate input grids, and prepare weather files for the
Urban Weather Generator, as illustrated in its online
[tutorial](https://umep-docs.readthedocs.io/projects/tutorial/en/latest/Tutorials/UWGSpatial.html).
](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/SLO-Podravje%20Region_draft2_media/media/image11.png)

![Immagine che contiene mappa, testo Il contenuto generato dall'IA
potrebbe non essere
corretto.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/SLO-Podravje%20Region_draft2_media/media/image12.png)

Figure 7- an example of LST \[°C\] Satellite map from Landsat 8 image
for July 2025 loaded and classified in GIS, at the bottom overlay of the
map with over 65 population density map from
[WorlpopoHUB](https://hub.worldpop.org/).

#### Step 2 – Analysis and mapping

Using the prepared datasets, map near surface air temperature and
eventually valuate anomalies between urban cores and their surrounding
rural areas(Figure 7, Figure 8) to map the intensity and extent of UHI
zones.

In GIS, you re able overlay these UHI maps with demographic layers to
locate clusters of vulnerable populations.

The outputs of this stage typically include thematic layers visualizing
**spatial patterns of thermal stress** and their **relationship with key
physical drivers** such as vegetation cover, building density, land
cover type, and **population distribution**. These maps form the basis
for identifying priority areas for targeted mitigation measures.

#### Step 3 – Baseline Urban Climate Modelling

Using the datasets prepared in Step 1 and the analytical overlays from
Step 2, develop a baseline urban climate model to represent current
conditions during extreme heat events. The objective is to simulate
microclimatic patterns—such as air temperature distribution, surface
temperature, and thermal comfort indices—across the study area without
any mitigation interventions applied.

This process typically involves:

  - Importing pre-processed land cover, vegetation, and morphology grids
    into the selected modelling framework.

  - Integrating meteorological time series representative of identified
    heatwave periods.

  - Parameterizing urban form (building heights, materials, vegetation
    characteristics) to reflect present-day conditions.

Where available, satellite-derived LST maps and temperature anomaly
layers from Step 2 can be used to cross-check the model outputs,
ensuring that simulated baseline conditions (e.g. Figure 8) are
consistent with observed spatial patterns of heat stress.

These validated baseline results then serve as a quantitative reference
for evaluating the potential effects of Nature-Based Solutions in the
following step.

![Immagine che contiene mappa, testo Il contenuto generato dall'IA
potrebbe non essere
corretto.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/SLO-Podravje%20Region_draft2_media/media/image13.png)

Figure 8 – example of temperature difference in mean ground temperature
\[°C\] for an urban area simulated with UMEP.

#### Step 4 – NbS scenario testing

Repeat the baseline modelling from Step 3, incorporating **Nature-Based
Solutions** identified in regional adaptation strategies, such as
increasing urban tree canopy, creating green corridors, installing green
roofs and walls, or applying reflective surface materials. Configure
each scenario within the chosen modelling framework to quantify cooling
effects under both present-day conditions and **projected future
climates** (e.g., using downscaled scenarios from Copernicus CDS).

Outputs should allow direct comparison with the baseline, evaluating
changes in maximum temperatures, reduction of UHI hotspot extent, and
improvements in thermal comfort indices. If relevant, integrate observed
thermal maps from Step 2 to validate simulated changes and ensure
scenario realism.
