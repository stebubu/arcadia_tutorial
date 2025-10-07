# aut lab3 heatstress draft2

### Introduction and Objectives of the Climate Risk Assessment

#### Regional context

The Innovation Lab 3 is located in [Lower Austria](https://en.wikipedia.org/wiki/Lower_Austria), with a focus on the urban area of [**Amstetten**](https://en.wikipedia.org/wiki/Amstetten,_Lower_Austria). The region combines medium-sized urban centres, densely built residential zones, and surrounding rural areas. Rising temperatures, limited vegetation in central districts, and a high proportion of sealed surfaces contribute to an intensification of **urban heat stress**.

This hazard is further amplified by the **urban heat island effect**, where built-up zones record significantly higher air and surface temperatures compared to adjacent rural surroundings. Vulnerable groups—such as the elderly, children, and people with pre-existing health conditions—are particularly at risk.

Urban heat stress represents a **priority climate risk** for Amstetten and similar Austrian towns, with direct impacts on **public health, liveability, and energy demand for cooling**.

**Climate Projections** from public datasets indicate that the **frequency, duration, and intensity of heatwaves** will increase under future climate scenarios, posing long-term adaptation challenges.

Nature-Based Solutions (NbS) such as **expansion of tree canopy, creation of public green spaces, and installation of green roofs** (Figure 2) are identified as the most relevant adaptation strategies to mitigate urban heat in this regional context.

The Climate Risk Assessment in this tutorial focuses on testing the effectiveness of these NbS to reduce thermal stress and to provide evidence for integration into **urban planning and adaptation strategies**.

Figure 1 - physical map of Lower Austria. Source: https://maps-austria.com/lower-austria-map (top), location of city of Amstetten (bottom)

Figure 2 – example of NbS in urban areas following the sponge-city principle. © P. Hirner, NiG.

{% hint style="warning" %}
This tutorial is intended as a general workflow example and does not replace software-specific documentation (e.g., GIS, heatwave modelling tools user/technical manuals). Users should already be familiar with the relevant geospatial data formats, data pre-processing techniques, and modelling concepts, as well as with the specific input/output requirements and run functionalities of the modelling software before attempting to replicate this workflow.
{% endhint %}

#### Scope of the tutorial

This tutorial outlines a **replicable Climate Risk Assessment (CRA) workflow** for urban heat stress in Amstetten.

The methodology combines **climate datasets, socio-economic data, and high-resolution geospatial information** with the **PALM-4U urban climate model** to identify hotspots of heat exposure and test the cooling potential of NbS interventions.

The workflow is designed to be **transferable to other regions**, even outside Austria, by suggesting **open and European-wide datasets** (e.g. Copernicus, EURO-CORDEX) when national or local data are unavailable. It does not require advanced programming and, at the current stage, the CRA relies on existing datasets and modelling tools.

The aim is to support **urban planning, public health strategies, and climate adaptation policies**, providing evidence-based insights for municipalities and regional authorities. The outputs allow for **prioritisation of greening measures**, **evaluation of vulnerable districts**, and **long-term integration of NbS** into adaptation strategies.

#### CRA objectives

The Climate Risk Assessment (CRA) in Amstetten aims to:

* **Identify and quantify high-risk heat exposure zones**, especially in urban areas with limited vegetation and high sealing.
* **Evaluate the effectiveness of NbS interventions** (tree canopy management, public green spaces, green roofs) in reducing thermal stress.
* **Provide technical evidence (spatial risk assessment) to be integrated into urban planning processes**, enabling proactive and spatially differentiated decision-making.
* **Provide evidence base for investment in green infrastructure**, public awareness, and long-term climate resilience.
* **Acknowledge limitations** related to microclimatic variability, climate projection uncertainties, and NbS performance under extreme heat scenarios.

#### Intended users

The CRA in Lab 3 is designed for stakeholders involved in **urban planning, environmental health, and climate adaptation policy**.

Intended users include:

* **City administrations and municipal planning departments** – to integrate heat risk maps and NbS scenarios into local development frameworks.
* **Public health authorities** – to identify vulnerable groups and prepare targeted protection measures during heatwaves.
* **Municipal environmental departments and regional authorities** – to prioritise NbS interventions and guide climate adaptation strategies.

By providing spatially explicit evidence, the CRA enables these actors to **prioritize interventions, develop adaptation strategies, and embed NbS** into decision-making processes for stronger long-term urban resilience.

### Hazard – Urban heat stress

#### Description and context

The city of **Amstetten** faces a growing risk of **urban heat stress**, intensified by the **urban heat island (UHI) effect**. Dense built-up areas with sealed surfaces and limited vegetation retain heat, resulting in significantly higher air and surface temperatures compared to surrounding rural zones.

This condition threatens **public health, comfort, and liveability**, especially for vulnerable groups such as elderly citizens, children, and people with pre-existing medical conditions. Climate projections from **EURO-CORDEX** and **ÖKS15** datasets indicate a steady rise in the **frequency, duration, and intensity of heatwaves** in the coming decades.

To address these challenges, the CRA supports both the identification and quantification of high-risk heat exposure zones and provides an evidence base for evaluating the effectiveness of **Nature-Based Solutions (NbS)**, including:

* management and expansion of urban **tree canopy**,
* creation of **public green spaces**,
* deployment of **green roofs**.

The assessment focuses on quantifying the **cooling potential** of these NbS interventions and on identifying areas of **highest vulnerability** within Amstetten.

| **Dimension**            | **Indicator(s)**                        | **Unit**        | **Purpose**                                      |
| ------------------------ | --------------------------------------- | --------------- | ------------------------------------------------ |
| Heatwave characteristics | Number of heat-days and tropical-nights | Days per season | Quantify hazard severity and temporal evolution  |
| UHI extent & intensity   | Maps of near surface air temperature    | °C, km²         | Delineate urban heat island extent and intensity |

Table 1 – key indicators tracked — Urban heat stress Hazard.

#### Data sources and tools

The CRA combines datasets on **climate hazards, exposure, and vulnerability** under both current and future conditions. Required inputs include **climate projections, high-resolution geospatial data, building geometries, land cover, urban tree inventories, and socio-economic indicators**. These datasets provide the basis for heat stress simulations and for the derivation of spatially explicit risk indicators.

In relation to **topography**, urban climate models benefit from **high-resolution terrain and surface data** to represent accurately both ground morphology and above-ground structures such as buildings and vegetation. While **LiDAR-based products** are preferable, at present a **national DTM at 10 × 10 m resolution** has been identified as the available baseline source for Amstetten, to be complemented where possible by higher-resolution datasets.

| Data type                                        | Source                                                                                                                                                                                                                           | Role in workflow                                                                                  | Open/EU alternative                                                                                                           |
| ------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| Climate projections (precipitation, temperature) | [https://data.hub.geosphere.at/group/oks15](https://data.hub.geosphere.at/group/oks15) **ÖKS15** (Austrian scenarios, 1 km)                                                                                                      | Input for modelling future urban heat exposure under different climate scenarios                  | Copernicus **EURO-CORDEX** (12.5 km /0.11°); ERA5-Land hourly data from 1950 to present                                       |
| Topography                                       | [https://www.data.gv.at/katalog/en/dataset/b5de6975-417b-4320-afdb-eb2a9e2a1dbf#additional-info](https://www.data.gv.at/katalog/en/dataset/b5de6975-417b-4320-afdb-eb2a9e2a1dbf#additional-info) **National DEM Austria** (10 m) | Base terrain morphology for heat modelling. LiDAR datasets are generally preferable for high res. | No open alternative general DTM available at the resolution required; explore national/regional geoportals for LiDAR datasets |
| Building geometries with height                  | Local datasets / project partners                                                                                                                                                                                                | Representation of urban form (building footprints, heights)                                       | OpenStreetMap building layer ([https://osmbuildings.org/](https://osmbuildings.org/)); Copernicus **Urban Atlas**             |
| Land cover / surface sealing                     | Local datasets / project partners                                                                                                                                                                                                | Input for surface characteristics in urban climate simulations                                    | Copernicus **Urban Atlas**; **CLCplus Backbone**                                                                              |
| Urban tree inventory                             | Local datasets / project partners                                                                                                                                                                                                | Input for NbS scenarios (tree canopy, crown diameter, height)                                     | Copernicus HRL **Tree Cover and Forests** (raster 10m)                                                                        |
| Socio-economic and demographic data              | [https://wegcshiny.uni-graz.at/alm/DISCC-AT/](https://wegcshiny.uni-graz.at/alm/DISCC-AT/) Statistik Austria, DISCC-AT platform                                                                                                  | Exposure and vulnerability assessment (population density, age structure, income)                 | WorldPop Hub ([https://dx.doi.org/10.5258/SOTON/WP00646](https://dx.doi.org/10.5258/SOTON/WP00646)) (raster 100m)             |

Table 2 – used data, and alternative datasets to replicate the assessment outside the study area, when available

{% hint style="info" %}
Urban climate modelling at this scale generally benefits from high-resolution topographic data, typically derived from LiDAR surveys. Such datasets allow the extraction of critical information (e.g., building heights from digital surface models, DSM), which can then be assigned to building footprints and other model elements.
{% endhint %}

Figure 3 - Administrative boundaries of the city of Amstetten overlaid on the available national DTM at 10 × 10 m resolution. This terrain model provides the base layer for urban climate simulations.

Figure 8 – example of above: Wind speed and global radiation from epw-file. Below: Air temperature from ground station data compared with those simulated in the grid of the model including the station (source \[1]).

The Lab uses the **PALM-4U urban climate model** to simulate microclimatic conditions (air temperature, surface temperature, wind, radiation) at building level. It is applied to Amstetten for baseline and NbS scenarios (tree canopy, green spaces, green roofs).

**GIS platforms** (QGIS, ArcGIS) are used for data preparation, spatial integration, and visualization.

Another open alternative has been provided to foster replicability.

| Tool                                                                                                                                                                                                | Type                | Role                                                                                              |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------- | ------------------------------------------------------------------------------------------------- |
| [https://palm.muk.uni-hannover.de/trac/wiki/palm4u](https://palm.muk.uni-hannover.de/trac/wiki/palm4u) PALM-4U                                                                                      | Urban climate model | Simulation of urban microclimate (air/surface temperature, wind, radiation); NbS scenario testing |
| [https://umep-docs.readthedocs.io/projects/tutorial/en/latest/Tutorials/UWGSpatial.html](https://umep-docs.readthedocs.io/projects/tutorial/en/latest/Tutorials/UWGSpatial.html) UMEP (QGIS plugin) | Open                | Urban climate modelling, including UHI mapping and scenario analysis; NbS scenario testing        |
| [https://qgis.org/](https://qgis.org/) QGIS                                                                                                                                                         | Open-source GIS     | Spatial data preparation, integration of geospatial layers, mapping and visualisation             |

Table 3 – used tools and role in the workflow; all tools are free to use.

{% hint style="info" %}
PALM-4U is the core model for high-resolution urban climate simulations, but it runs only on Linux/Unix systems and typically requires HPC environments. To improve replicability on Windows systems, the open-source UMEP plugin for QGIS has been included as an alternative tool for UHI mapping and NbS scenario analysis.
{% endhint %}

#### Methodology

{% hint style="warning" %}
The urban climate simulations in Lab 3 are intended to be run with the PALM-4U model. Due to the high computational cost and complexity, simulations are executed on high-performance computing (HPC) systems. Each run—whether baseline or NbS scenario—is resource-intensive, and results are treated as static datasets for downstream risk analysis.

At the current stage, the detailed execution workflow for PALM-4U in Amstetten is still under development; comprehensive documentation on data preparation, model setup, and post-processing will be released during Lab 3.

For tutorial purposes, an alternative workflow based on UMEP (QGIS plugin) is presented. This workflow uses the same data types required by PALM-4U, ensuring consistency in data acquisition and preparation while enabling replicability on standard desktop environments (Windows/Linux).
{% endhint %}

{% stepper %}
{% step %}
### Step 1 — Data acquisition and preparation

Collect and prepare spatial and environmental datasets required as inputs to the modelling tool (UMEP in QGIS). Harmonise layers in coordinate system, resolution and coverage, and pre-process through the plugin’s utilities.

* Convert climate projections (e.g., ÖKS15, EURO-CORDEX) into formats compatible with the modelling suite, typically EPW weather files for UMEP.
* EPW files should be adapted with local meteorological data where available.
* Prepare topographic base (national DTM 10 × 10 m), and where possible include LiDAR-derived DSMs/DTMs to derive building heights.
* Reformat building geometries, land cover, surface sealing, and tree inventory into the input structure expected by UMEP:
  * attribute building footprints with height,
  * reclassify land cover into impervious vs vegetated surfaces,
  * prepare tree datasets as grids of canopy cover and crown size.
* Project, clip to study area, and harmonize resolution for all layers.
* Prepare socio-economic layers (population density, age distribution, income) for later combination with hazard indicators.
{% endstep %}

{% step %}
### Step 2 — Analysis and mapping

Configure the modelling environment in UMEP to simulate near-surface air temperature and related thermal indicators.

* Use the input grids (buildings, land cover, vegetation) with the EPW weather file to produce spatial simulations of urban heat.
* Generate thematic layers that visualize spatial distribution of heat exposure and its drivers (vegetation cover, building density, sealing, population).
* Identify priority zones where NbS can deliver the greatest cooling benefits.
{% endstep %}

{% step %}
### Step 3 — Baseline urban climate modelling

Develop a baseline urban climate model representing current conditions during extreme heat events.

* Import pre-processed land cover, vegetation, and morphology grids into the modelling framework.
* Integrate meteorological time series representative of identified heatwave periods.
* Parameterize urban form (building heights, materials, vegetation characteristics).
* Optionally cross-check outputs with satellite-derived LST maps and observed temperature anomalies.

The baseline results provide a quantitative reference for evaluating the potential effects of NbS scenarios.
{% endstep %}

{% step %}
### Step 4 — NbS scenario testing

Run alternative simulations to test Nature-Based Solutions (increase tree canopy, create public green spaces, implement green roofs).

* Modify spatial input layers to represent each intervention while keeping meteorological forcing constant.
* Compare air temperature, surface temperature, and thermal comfort outputs against the baseline.
* Quantify cooling effects and map changes in hotspot intensity and extent.
* Overlay results with socio-economic layers to identify where benefits coincide with vulnerable populations.

These comparisons provide an evidence base for local adaptation planning and prioritisation of green interventions.
{% endstep %}
{% endstepper %}

#### Meteorological inputs

Meteorological input requirements and formatting vary depending on the modelling code used. For UHI simulations with UMEP, required variables include air temperature, dew point or relative humidity, surface pressure, wind speed and direction, shortwave radiation (global, diffuse and direct), longwave radiation, precipitation, and cloud cover. UMEP relies on the **EPW format (EnergyPlus Weather)**.

EPW files are “typical meteorological dataset with a typical year” and can be downloaded from several sources (e.g., EnergyPlus, EPWmap) or generated from reanalysis datasets such as **ERA5(-Land)**. Users are encouraged to download the file closest to their location and **adapt it with local meteorological data** so the weather inputs reflect actual conditions of the study area.

Free tools are available to inspect and modify EPW files, such as [Elements](https://bigladdersoftware.com/projects/elements/). Consult the official **UMEP documentation and tutorial examples** to adjust EPW variables for modelling requirements.

Figure 5 – example of EPW files as “typical meteorological dataset with a typical year” downloaded near Amstetten and opened for modification.

Figure 9 – example of temperature difference in mean ground temperature \[°C] for an urban area simulated with UMEP.

References

* https://umep-docs.readthedocs.io/projects/tutorial/en/latest/Tutorials/UWGSpatial.html#executing-the-model
