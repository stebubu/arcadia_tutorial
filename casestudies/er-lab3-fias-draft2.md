# er lab3 fias draft2

### Introduction and Objectives of the Climate Risk Assessment

#### Regional context

The Innovation Lab 3 is located in the upper Bidente–Ronco basin, in the municipalities of [Galeata](https://maps.app.goo.gl/1z1h3h64Sf2cemWr7)–[Santa Sofia](https://maps.app.goo.gl/AaxfgSnbjj6mExaB7) (Forlì–Cesena Province, Emilia-Romagna, Italy). This area represents a mixed forest–agricultural landscape in the Apennine foothills, characterized by steep slopes, permeable soils, and high rainfall variability.

Heavy precipitation events often generate flash runoffs and landslides, while prolonged summer dry spells cause water scarcity and stress for crops and ecosystems. These combined hazards directly affect water availability, soil stability, and agricultural productivity. The regional context is also shaped by the role of the Canale Emiliano Romagnolo (CER) and the associated land reclamation consortia, which are key actors in irrigation management and climate adaptation strategies. Within this setting, Forested Infiltration Areas (FIAs) are tested as a Nature-Based Solution to enhance infiltration, reduce runoff peaks, improve water quality, and support sustainable irrigation demand in forest nurseries and surrounding agricultural lands.

#### Scope of the tutorial

This tutorial describes a replicable Climate Risk Assessment (CRA) workflow designed for a mixed forest–agricultural landscape in Emilia-Romagna. The assessment focuses on Forested Infiltration Areas (FIAs) as a Nature-Based Solution to address flash runoff, erosion, and water scarcity. Two complementary workflows are presented:

* a catchment-scale workflow, aimed at quantifying how land-use changes and infiltration areas influence runoff, water harvesting and water quality.
* a site-scale workflow, focused on the water demand and irrigation management of a single forest nursery (NEOS), assessing how improved infiltration capacity supports sustainable operations.

Both workflows integrate geospatial datasets, environmental monitoring, and climate information, and are structured so that methods can be transferred and adapted to other regions. The approach supports the integration of NbS into adaptation planning, providing indicators for land-use strategies, water management, and regional policy development.

{% hint style="info" %}
This tutorial is intended as a general workflow example and does not replace software-specific documentation (e.g., GIS, hydrological, hydraulic models’ user/technical manuals). Users are expected to be familiar with geospatial data formats, pre-processing techniques, and the basic concepts of hydrological and environmental modelling. Inputs, outputs, and methodological details may need to be adapted depending on data availability, local conditions, and the specific software selected for the analysis, before attempting to replicate this workflow.
{% endhint %}

#### CRA objectives

The Climate Risk Assessment in Innovation Lab 3 aims to:

* Establish the baseline — Define the current hydrology and water-quality status of the Galeata–Santa Sofia sub-catchment.
* Quantify FIA effects at sub-catchment/micro-catchment scale — Measure changes in infiltration rate, catchment water-harvesting potential, and runoff peaks, under current conditions and, where available, projected climate.
* Evaluate pollutant retention and erosion control — Track Nitrogen, Phosphorus, and Suspended Solids (SS) to assess water-quality improvement and sediment trapping.
* Assess site-scale irrigation implications — Quantify nursery water demand and examine whether increased water-harvesting potential can meet the optimized demand at the nursery, noting that catchment and site workflows are run independently.
* Support planning and policy — Deliver decision-ready indicators for Water Protection Plans (PTAs) and Rural Development Programs (RDPs) and future design guidelines for FIAs.

#### Intended users

The outputs are designed for regional policymakers and planners, land-reclamation consortia and environmental organisations that need quantitative, model-based evidence to:

* Support the draft or update Water-Protection Plans (PTA) and Rural-Development Program (PSR) measures,
* develop best practices for Forested Infiltration Areas and other NbS,
* guide day-to-day decisions on irrigation scheduling and soil-erosion control within the study catchment or in the specific area (e.g. nursery area in this case).

***

### Catchment-Scale Hazard: Runoff, Erosion & Water Quality

#### Description and context

The study area is the Galeata–Santa Sofia sub-catchment in the upper Bidente–Ronco basin, Emilia-Romagna. It is a mixed forest–rural–agricultural landscape affected by flash runoff from heavy rainfall and by summer water scarcity. These hazards impact water availability, soil stability, and crop productivity.

This workflow establishes the baseline hydrology and water-quality status, then tests Forested Infiltration Areas (FIAs) as a Nature-Based Solution at hillslope and riparian locations. The analysis quantifies changes in infiltration rate, catchment water-harvesting potential, and runoff peaks, and tracks Nitrogen, Phosphorus, and Suspended Solids (SS) to evaluate pollutant retention and sediment trapping. Climate-change scenarios can be included where compatible datasets are available.

The assessment uses regional datasets for elevation, soils, land use, and daily meteorology, complemented by open European alternatives when replication outside the region is needed. Outputs are geospatial layers and tables suitable for supporting land planning measures. Proposed set of indicators aims to isolate the FIA signal on catchment hydrology and water quality: changes in runoff peaks/base-flow, added infiltration and water-harvesting, and sediment/nutrient concentrations deliver decision-ready evidence for regional planning measures.

| Dimension           | Indicator(s)                                            |              Unit | Purpose                                                   |
| ------------------- | ------------------------------------------------------- | ----------------: | --------------------------------------------------------- |
| Hydrologic response | Runoff peak at catchment outlet; Base-flow              |            m³ s⁻¹ | Detect peak attenuation and base-flow change due to FIAs. |
| Water storage       | Infiltration rate; Catchment water-harvesting potential | m d⁻¹; m³ month⁻¹ | Quantify added soil-water and storage from FIAs.          |
| Water quality       | Nitrogen; Phosphorus;                                   |            mg L⁻¹ | Evaluate pollutant-filtering effectiveness.               |
| Erosion             | Suspended Solids (SS) concentration                     |            mg L⁻¹ | Assess sediment trapping by forest cover.                 |

_Table 1 – Key indicators tracked — Catchment-scale hazard: runoff, erosion & water quality_

Figure – Example of the study area and the sub-basin in red where SWAT+ will be applied

#### Data sources and tools

Catchment-scale analysis uses regional elevation, soils, land-use, and daily meteorology to delineate sub-basins, parameterize hydrological response units, and force baseline vs FIA scenarios. Open European datasets are listed to enable replication beyond Emilia-Romagna.

| Data type                                   | Source                                                                                                                                                                                                                                 | Role in workflow                                                          | Open/EU alternative                                                                                                                                                                                                                                                                                                                         |
| ------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Digital Terrain Model (DTM) 5 m             | Emilia-Romagna Geoportal ([open- WCS service](https://geoportale.regione.emilia-romagna.it/servizi/servizi-ogc/wcs))                                                                                                                   | Delineates watershed & sub-basins; slope & flow-direction grids for SWAT+ | Copernicus DEM - Global and European Digital Elevation Model ([open – raster 30m, 10m for selected users](https://dataspace.copernicus.eu/explore-data/data-collections/copernicus-contributing-missions/collections-description/COP-DEM))                                                                                                  |
| Soil map 1:50 000 or higher scale           | Emilia-Romagna regional soil map ([open , shapefile](https://datacatalog.regione.emilia-romagna.it/catalogCTA/dataset/r_emiro_2016-01-28t184735))                                                                                      | Supplies texture, OC, Ksat for each HRU; controls infiltration & erosion  | [European Soil Database v2.0 (vector and attribute data)](https://esdac.jrc.ec.europa.eu/content/european-soil-database-v20-vector-and-attribute-data)                                                                                                                                                                                      |
| Land-cover 2023                             | ([open AGREA shapefile](https://geoportale.regione.emilia-romagna.it/download/dati-e-prodotti-cartografici-preconfezionati/pianificazione-e-catasto/uso-del-suolo/2020-coperture-vettoriali-uso-del-suolo-di-dettaglio-edizione-2023)) | Re-mapped to HRUs to parameterize vegetation and management               | [CORINE Land Cover 2018 (vector/raster 100 m), Europe, 6-yearly](https://land.copernicus.eu/en/products/corine-land-cover/clc2018)                                                                                                                                                                                                          |
| Daily meteorology (P, T, RH, SR, wind, PET) | ARPAE DEXT3R ([open- gauges time series](https://simc.arpae.it/dext3r/))                                                                                                                                                               | Atmospheric forcing baseline and FIA scenarios                            | Daily gridded observational dataset for precipitation, temperature, E-OBS ([open , gridded](https://surfobs.climate.copernicus.eu/dataaccess/access_eobs.php)), ERA5-Land post-processed daily statistics from 1950 to present ([open, raster](https://cds.climate.copernicus.eu/datasets/derived-era5-land-daily-statistics?tab=overview)) |

_Table 3 – Used data and open alternatives_

{% hint style="info" %}
Bias-corrected climate-projection datasets may be incorporated, with particular focus on hydrogeological modelling. Examples: [Copernicus temperature and precipitation climate impact indicators from 1970 to 2100 derived from European climate projections](https://cds.climate.copernicus.eu/datasets/sis-hydrology-meteorology-derived-projections?tab=overview).
{% endhint %}

Tools: QGIS (desktop GIS), QSWAT+ (QGIS plugin included in SWAT+ installer), and SWAT+ Editor/runner.

| Tool                                                 | Type                     | Role in this workflow                                                                                               |
| ---------------------------------------------------- | ------------------------ | ------------------------------------------------------------------------------------------------------------------- |
| [QGIS](https://qgis.org/download/)                   | Desktop GIS              | Data prep, watershed delineation, HRU definition, mapping, results viewing.                                         |
| QSWAT+ (QGIS plugin included in SWAT+ installer)     | SWAT+ pre/post-processor | Build sub-basins, LSUs, HRUs; export to SWAT+; visualize outputs and compare scenarios.                             |
| [SWAT+ Editor](https://swat.tamu.edu/software/plus/) | Model editor/runner      | Import project DB, set weather data and print options, run SWAT+, write outputs to SQLite for QSWAT+ visualization. |

_Table 2 – Tools and role in the workflow_

{% hint style="info" %}
This tutorial targets QSWAT+ within QGIS. The SWAT+ toolchain can be used without the GIS interface by working directly with the SWAT+ Editor and its runners. Consult the official [SWAT+ software page](https://swat.tamu.edu/software/plus/) for alternative installers and workflows, and keep project databases and input folders consistent with this tutorial.
{% endhint %}

#### Methodology

{% stepper %}
{% step %}
### Step 1 — Data acquisition and preparation

* Assemble regional inputs and prepare a coherent catchment dataset before any model run.
* Acquire base geospatial layers (e.g., 5 m DTM, regional soil map, 2023 land-use shapefile) and clip them to a single area-of-interest mask.
* Reproject to a common CRS, align resolution and extent, and fix No Data or geometry issues.
* Build a land-use and soil crosswalk so classes/attributes match the model parameters; derive slope where needed for HRU structuring.
* Prepare meteorological inputs as station-based daily time series in the model’s required text format. For each gauge provide ID, name, latitude, longitude, elevation, and a file with daily values (include documented variables, units, and missing-value code).
* During runs, associate each sub-basin with the nearest available precipitation and temperature stations.
* Read the model documentation to confirm exact fields and layouts and keep the simulation period consistent with available observations.
{% endstep %}

{% step %}
### Step 2 — Model setup and run

* Load pre-processed geospatial layers and station-based meteorological series into the modelling environment.
* Define the study area (Galeata–Santa Sofia) and time window for the baseline.
* Initialize the model with catchment topology, soil–land-use attributes, and daily climate forcing. Configure warm-up and daily time step.
* Run the baseline simulation to produce decision-ready outputs for the indicators in Table 1: runoff peak and base-flow, infiltration/storage proxies, and water-quality/erosion indicators.
* Outputs are saved as tables and can be linked to sub-basin/HRU layers for GIS inspection.
* Baseline processing sequence: DEM topographic processing → delineate watershed/sub-basins/channels → assign attributes by intersecting land use, soils, slope → create HRUs → run daily water-balance and water-quality simulation.
{% endstep %}

{% step %}
### Step 3 — Analysis and interpretation

* Extract outlet runoff peak and base-flow, compute infiltration/storage proxies, and read water-quality and erosion metrics (N, P, SS) at sub-basin and HRU level.
* Inspect results as tables and geospatial layers in GIS to map HRU/sub-basin patterns, plot time series, and export summaries for reporting.
* Identify runoff hot spots, sediment sources, and reaches with elevated nutrients; relate these to soils, land use, slope, and drainage.
* Key standard outputs: a static HRU map (shapefile with aggregated metrics) and an outlet flow time series (SWATGraph). If gauges exist, compare simulated and observed discharge and iteratively refine baseline setup before proceeding to FIA testing.
{% endstep %}

{% step %}
### Step 4 — FIAs testing

* Duplicate the calibrated baseline, keep forcing, spatial setup, warm-up, and print options identical.
* Introduce Forested Infiltration Areas by converting only the selected hillslope and riparian polygons to forest where Lab 3 plans FIAs. Do not change soil or climate inputs.
* Re-run the same period so changes reflect the FIA signal on key indicators (runoff peak, base-flow, infiltration/storage proxies, N, P, SS).
* Compare baseline and FIA scenarios by exporting static HRU/sub-basin layers, plotting outlet hydrographs, mapping deltas in GIS, and overlaying hydrographs to show peak attenuation and base-flow shifts.
* Optionally, introduce climate change effects in weather forcings to test combined scenarios with/without FIAs.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Note: Full HRU vs Actual HRU

* Full HRU: all unique combinations of land use, soil type, and slope are represented, even if they cover a very small area — maximum spatial detail, higher computational effort.
* Actual HRU: only HRUs above user-defined thresholds are kept; smaller ones are merged into larger units — reduced complexity at the cost of some spatial detail.
{% endhint %}

***

### Nursery-Scale Hazard: Irrigation Water Demand & Drought Resilience

#### Description and context

The nursery in the Galeata–Santa Sofia area is analysed to quantify nursery plants’ water requirements and support drought-resilient irrigation scheduling. The assessment uses a field-scale decision-support tool (IRRIFRAME; open alternative AquaCrop) that ingests site-specific inputs—soil analyses, continuous soil-moisture readings, coefficients (Kc) for nursery plants, local meteorology, and recorded irrigation events—and returns tabular demand estimates. Compatible climate projections may be explored for future demand. This nursery workflow is methodologically independent from the catchment analysis and informs operational water management and planning.

Key indicators tracked at nursery scale:

| Dimension                          | Indicator(s)                                  |              Unit | Purpose                                                          |
| ---------------------------------- | --------------------------------------------- | ----------------: | ---------------------------------------------------------------- |
| Irrigation demand                  | Crop water need (ETc for nursery plants)      | mm d⁻¹; mm/season | Computed from daily ETo and Kc by growth stage.                  |
| Irrigation scheduling & efficiency | Irrigation advice (next date and event depth) |    date; mm/event | Event timing and depth from soil–plant water balance thresholds. |

_Table – Key indicators tracked — Nursery scale: water demand._

#### Data sources and tools

A field-scale irrigation-balance model needs site-specific inputs to compute ETc and irrigation advice: recent soil analyses, soil-moisture observations, crop coefficients (Kc) by growth stage, daily meteorology, and irrigation logs.

| Data type                           | Source                                                                                                                                                   | Role in workflow                                                                                                     | Open / EU alternative                                                                                                                                         |
| ----------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Soil analyses                       | Nursery lab tests (2024 season); regional repo ([open repo](https://datacatalog.regione.emilia-romagna.it/catalogCTA/dataset/r_emiro_2023-08-02t140310)) | Main soil properties like field capacity, wilting point, and soil parameters for the soil–plant water balance        | European Soil Database & soil properties ([open. Raster-vector](https://esdac.jrc.ec.europa.eu/resource-type/european-soil-database-soil-properties))         |
| Soil-moisture readings              | On-site sensors                                                                                                                                          | Trigger thresholds and validation of advice                                                                          | Soil moisture gridded data from 1978 to present ([open, coarse 0.25°x0.25°](https://cds.climate.copernicus.eu/datasets/satellite-soil-moisture?tab=overview)) |
| Nursery plants Kc and crop info     | Nursery records (species, stage)                                                                                                                         | Compute ETc from ETo×Kc; scheduling by stage                                                                         | FAO-56 Kc tables; Chapagain and Hoekstra (2004)                                                                                                               |
| Local meteorology (P, T, ET0) Daily | ARPAE DEXT3R station series                                                                                                                              | Drives ETo/ETc and advice. (ETo may be computed with Hargreaves if only precipitation and temperature are available) | ERA5-Land hourly data from 1950 to present                                                                                                                    |
| Irrigation cycles logs              | Nursery records                                                                                                                                          | Compare applied vs recommended; fine-tune scheduling                                                                 | —                                                                                                                                                             |

_Table – Used data and open alternatives for nursery-scale workflow_

{% hint style="info" %}
Bias-corrected climate-projection datasets may be incorporated for future demand testing (e.g., Copernicus climate indicators).
{% endhint %}

Tools: IRRIFRAME (proprietary cloud DSS used in ER) and AquaCrop (FAO open alternative).

| Tool                                              | Type                  | Role in this workflow                                                                                                                                                                                                                       |
| ------------------------------------------------- | --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [IRRIFRAME](https://www.consorziocer.it/irrinet/) | Proprietary Cloud DSS | Produces nursery-plant water requirement and operational irrigation advice from soil analyses, optional soil-moisture readings, Kc, local daily ETo/meteorology, and applied-irrigation logs; returns next irrigation date and event depth. |
| [AquaCrop](https://www.fao.org/aquacrop/en/)      | Open alternative      | Runs soil–crop–climate water balance to estimate ETc and event depths, enabling comparable irrigation scheduling at nursery scale.                                                                                                          |

_Table – Tools and role in the nursery workflow_

#### Methodology

{% stepper %}
{% step %}
### Step 1 — Data acquisition and preparation

* Assemble local inputs as clean, time-consistent series and tables: current-season soil analyses, soil-moisture observations, nursery-plant Kc by growth stage, daily ETo/precipitation/air temperature, and irrigation logs.
* Keep phenology calendars and Kc tables aligned with species and stages.
* Ensure soil parameters (field capacity, wilting point, texture) are available to drive the soil–plant balance.
* Use the irrigation log to check applied events versus model thresholds.
{% endstep %}

{% step %}
### Step 2 — Model setup and run

* The model reads ETo, precipitation, air temperature, and Kc; computes ETc = Kc × ETo; updates soil water storage (inputs, evapotranspiration, percolation); and checks depletion against operational thresholds.
* When thresholds are exceeded, it outputs an irrigation advice (next date and event depth) in tabular form.
* Inputs: site/season data, daily meteorology, soil parameters, Kc by growth stage, and optional soil-moisture observations. Follow the official documentation for exact formats.
* AquaCrop is the open alternative and provides daily ET, Kc (Tr), and net irrigation requirement (Inet) from which ETc and event depths can be derived.
{% endstep %}

{% step %}
### Step 3 — Analysis and interpretation

* Use graphical outputs to derive ETc (crop water need) and the irrigation advice (next date and event depth).
* Use a spreadsheet or similar tool to plot daily ETc with precipitation and temperature, then overlay advised vs applied events from the nursery log to quantify compliance, stress days, and potential savings.
* Aggregate to weekly or seasonal totals to size demand and optimize cycles. Outputs are CSV-like tables suitable for operational scheduling and resource-allocation planning.
{% endstep %}

{% step %}
### Step 4 — FIAs testing (nursery-scale)

* Create a scenario that mimics the hydrologic effect of FIAs at plot scale without changing crop demand logic.
* Keep site, season, meteorology, and Kc identical to the baseline. Represent the FIA as an infiltration-enhancing configuration: increase rain storage and infiltration at the soil surface and reduce direct runoff so a larger share of rainfall becomes effective rainfall.
* In IRRIFRAME, adjust the soil surface layer settings that govern infiltration rate, runoff, and effective rainfall. In AquaCrop, adjust field/soil settings that control surface storage and runoff (e.g., CN logic) so more water infiltrates.
* Re-run the model and compare Inet/ET and irrigation events between baseline and FIA scenarios. Fewer or smaller advised events indicate FIA benefit (differences arise from enhanced effective rainfall and soil storage, not from crop changes).
* Document the delta in seasonal irrigation requirement and event count for reporting.
{% endstep %}
{% endstepper %}

#### Reference formulas / definitions

* ETc (crop evapotranspiration): water use of the crop under standard conditions. Units: mm d⁻¹ or mm per period. Computation: ETc = Kc × ETo; with water-stress adjustment the actual ET is ETa = Kc × Ks × ETo. Used to size irrigation depth once effective rainfall and soil storage are considered.

***

If you want, I can:

* extract the image filenames and convert them into GitBook-embedded image blocks,
* create a downloadable checklist for data preparation,
* or produce a condensed one-page flowchart summarizing both workflows. Which would you prefer?
