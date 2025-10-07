## Introduction and Objectives of the Climate Risk Assessment

### Regional context.

The Innovation Lab 3 is located in the upper Bidente–Ronco basin, in the
municipalities of
[<span class="underline">Galeata</span>](https://maps.app.goo.gl/1z1h3h64Sf2cemWr7)–[<span class="underline">Santa
Sofia</span>](https://maps.app.goo.gl/AaxfgSnbjj6mExaB7) (Forlì–Cesena
Province, Emilia-Romagna, Italy). This area represents a mixed
forest–agricultural landscape in the Apennine foothills, characterized
by steep slopes, permeable soils, and high rainfall variability.

|                                                                                                                                                                                                                                                                                         |                                                                                                                                                                                                                                                                                     |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/ER-Lab3_FIAs_draft2_media/media/image1.jpeg) | ](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/ER-Lab3_FIAs_draft2_media/media/image2.jpeg) |

Figure : Figure of the study area: Castellaro Nursery

**Heavy precipitation events** often generate flash runoffs and
landslides, while prolonged summer dry spells cause water scarcity and
stress for crops and ecosystems. These combined hazards directly affect
water availability, soil stability, and agricultural productivity. The
regional context is also shaped by the role of the **Canale Emiliano
Romagnolo (CER)** and the associated land reclamation consortia, which
are key actors in irrigation management and climate adaptation
strategies. Within this setting, **Forested Infiltration Areas (FIAs)**
are tested as a Nature-Based Solution to enhance infiltration, reduce
runoff peaks, improve water quality, and support sustainable irrigation
demand in forest nurseries and surrounding agricultural lands.

](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/ER-Lab3_FIAs_draft2_media/media/image3.png)

@@@@ \_ Schematic example of the FIAs used in this Lab, source CER

### Scope of the tutorial.

This tutorial describes a replicable Climate Risk Assessment (CRA)
workflow designed for a mixed forest–agricultural landscape in
Emilia-Romagna. The assessment focuses on **Forested Infiltration Areas
(FIAs)** as a Nature-Based Solution to address flash runoff, erosion,
and water scarcity. Two complementary workflows are presented:

  - a **catchment-scale workflow**, aimed at quantifying how land-use
    changes and infiltration areas influence runoff, water harvesting
    and water quality.

  - a **site-scale workflow**, focused on the water demand and
    irrigation management of a single forest nursery (NEOS), assessing
    how improved infiltration capacity supports sustainable operations.

Both workflows integrate geospatial datasets, environmental monitoring,
and climate information, and are structured so that methods can be
transferred and adapted to other regions. The approach supports the
integration of NbS into adaptation planning, providing indicators for
land-use strategies, water management, and regional policy development.

  - #### Disclaimer

> This tutorial is intended as a general workflow example and does not
> replace software-specific documentation (e.g., GIS, hydrological,
> hydraulic models’ user/technical manuals). Users are expected to be
> familiar with geospatial data formats, pre-processing techniques, and
> the basic concepts of hydrological and environmental modelling.
> Inputs, outputs, and methodological details may need to be adapted
> depending on data availability, local conditions, and the specific
> software selected for the analysis, before attempting to replicate
> this workflow

### CRA objectives

The Climate Risk Assessment in Innovation Lab 3 aims to:

  - **Establish the baseline** — Define the current hydrology and
    water-quality status of the Galeata–Santa Sofia sub-catchment.

  - **Quantify FIA effects at sub-catchment/micro-catchment scale** —
    Measure changes in infiltration rate, catchment water-harvesting
    potential, and runoff peaks, under current conditions and, where
    available, projected climate.

  - **Evaluate pollutant retention and erosion control** — Track
    Nitrogen, Phosphorus, and Suspended Solids (SS) to assess
    water-quality improvement and sediment trapping.

  - **Assess site-scale irrigation implications** — Quantify nursery
    water demand and examine whether increased water-harvesting
    potential can meet the optimized demand at the nursery, noting that
    catchment and site workflows are run independently.

  - **Support planning and policy** — Deliver decision-ready indicators
    for Water Protection Plans (PTAs) and Rural Development Programs
    (RDPs) and future design guidelines for FIAs.

### Intended users.

The outputs are designed for **regional policymakers and planners,
land-reclamation consortia and environmental organisations** that need
quantitative, model-based evidence to:

  - Support the draft or update Water-Protection Plans (PTA) and
    Rural-Development Program (PSR) measures,

  - develop best practices for Forested Infiltration Areas and other
    NbS,

  - guide day-to-day decisions on irrigation scheduling and soil-erosion
    control within the study catchment or in the specific area (e.g.
    nursery area in this case)

## Catchment-Scale Hazard: Runoff, Erosion & Water Quality

### Description and context

The study area is the Galeata–Santa Sofia sub-catchment in the upper
Bidente–Ronco basin, Emilia-Romagna. It is a mixed
forest–rural–agricultural landscape affected by flash runoff from
heavy rainfall and by summer water scarcity. These hazards impact water
availability, soil stability, and crop productivity.

This workflow establishes the baseline hydrology and water-quality
status, then tests Forested Infiltration Areas (FIAs) as a Nature-Based
Solution at hillslope and riparian locations. The analysis quantifies
changes in **infiltration rate**, **catchment water-harvesting
potential**, and **runoff peaks**, and tracks **Nitrogen**,
**Phosphorus**, and **Suspended Solids (SS)** to evaluate pollutant
retention and sediment trapping. Climate-change scenarios can be
included where compatible datasets are available.

The assessment uses regional datasets for elevation, soils, land use,
and daily meteorology, complemented by open European alternatives when
replication outside the region is needed. Outputs are geospatial layers
and tables suitable for supporting land planning measures Proposed set
of indicators aims to isolate the FIA signal on catchment hydrology and
water quality: changes in runoff peaks/base-flow, added infiltration and
water-harvesting, and sediment/nutrient concentrations follow the
original scope to deliver decision-ready evidence for regional planning
measures.

|                     |                                                         |                   |                                                           |
| ------------------- | ------------------------------------------------------- | ----------------- | --------------------------------------------------------- |
| **Dimension**       | **Indicator(s)**                                        | **Unit**          | **Purpose**                                               |
| Hydrologic response | Runoff peak at catchment outlet; Base-flow              | m³ s⁻¹;           | Detect peak attenuation and base-flow change due to FIAs. |
| Water storage       | Infiltration rate; Catchment water-harvesting potential | m d⁻¹; m³ month⁻¹ | Quantify added soil-water and storage from FIAs.          |
| Water quality       | Nitrogen; Phosphorus;                                   | mg L⁻¹            | Evaluate pollutant-filtering effectiveness.               |
| Erosion             | Suspended Solids (SS) concentration                     | mg L⁻¹            | Assess sediment trapping by forest cover.                 |

*Table 1 – key indicators tracked- Catchment-Scale Hazard: Runoff,
Erosion & Water Quality*

The figure (Figure 2) shows the study basin with the sub-basin
highlighted in red where the SWAT+ model will be applied. It should be
noted that the basin represented is the one obtained from the first
simulations and is therefore not final. Moreover, the small size of the
identified basin requires further evaluations to determine whether or
not to confirm this preliminary result.

](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/ER-Lab3_FIAs_draft2_media/media/image4.png)

Figure  – Example of the study area and the sub-basin in red where SWAT+
will be applied

### Data sources and tools

Catchment-scale analysis uses regional elevation, soils, land-use, and
daily meteorology to delineate sub-basins, parameterize hydrological
response units, and force baseline vs FIA scenarios. Open European
datasets are listed to enable replication beyond Emilia-Romagna.

|                                             |                                                                                                                                                                                                                                                                       |                                                                           |                                                                                                                                                                                                                                                                                                                                                                                                             |
| ------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Data type**                               | **Source**                                                                                                                                                                                                                                                            | **Role in workflow**                                                      | **Open/EU alternative**                                                                                                                                                                                                                                                                                                                                                                                     |
| Digital Terrain Model (DTM) 5 m             | Emilia-Romagna Geoportal ([<span class="underline">open- WCS service</span>](https://geoportale.regione.emilia-romagna.it/servizi/servizi-ogc/wcs))                                                                                                                   | Delineates watershed & sub-basins; slope & flow-direction grids for SWAT+ | Copernicus DEM - Global and European Digital Elevation Model [<span class="underline">(open – raster 30m, 10m for selected users)</span>](https://dataspace.copernicus.eu/explore-data/data-collections/copernicus-contributing-missions/collections-description/COP-DEM)                                                                                                                                   |
| Soil map 1:50 000 or higher scale           | Emilia-Romagna regional soil map ([<span class="underline">open , shapefile )</span>](https://datacatalog.regione.emilia-romagna.it/catalogCTA/dataset/r_emiro_2016-01-28t184735)                                                                                     | Supplies texture, OC, Ksat for each HRU; controls infiltration & erosion  | [<span class="underline">European Soil Database v2.0 (vector and attribute data)</span>](https://esdac.jrc.ec.europa.eu/content/european-soil-database-v20-vector-and-attribute-data)                                                                                                                                                                                                                       |
| Land-cover 2023                             | ([<span class="underline">open AGREA shapefile</span>](https://geoportale.regione.emilia-romagna.it/download/dati-e-prodotti-cartografici-preconfezionati/pianificazione-e-catasto/uso-del-suolo/2020-coperture-vettoriali-uso-del-suolo-di-dettaglio-edizione-2023)) | Re-mapped to HRUs to parameterize vegetation and management               | [<span class="underline">CORINE Land Cover 2018 (vector/raster 100 m), Europe, 6-yearly</span>](https://land.copernicus.eu/en/products/corine-land-cover/clc2018)                                                                                                                                                                                                                                           |
| Daily meteorology (P, T, RH, SR, wind, PET) | ARPAE DEXT3R [<span class="underline">(open- gauges time series)</span>](https://simc.arpae.it/dext3r/)                                                                                                                                                               | Atmospheric forcing baseline and FIA scenarios                            | Daily gridded observational dataset for precipitation, temperature, E-OBS [<span class="underline">(open , gridded )</span>](https://surfobs.climate.copernicus.eu/dataaccess/access_eobs.php), ERA5-Land post-processed daily statistics from 1950 to present ( [<span class="underline">open, raster</span>](https://cds.climate.copernicus.eu/datasets/derived-era5-land-daily-statistics?tab=overview)) |

*Table 3 – used data, an alternative dataset to replicate the assessment
outside the study area, when available*

  - ##### Climate change effects 

> *Bias-corrected climate-projection datasets may be incorporated, with
> particular focus on hydrogeological modelling.*
> 
> *For example [<span class="underline">Copernicus Temperature and
> precipitation climate impact indicators from 1970 to 2100 derived from
> European climate
> projections</span>](https://cds.climate.copernicus.eu/datasets/sis-hydrology-meteorology-derived-projections?tab=overview);
> [<span class="underline">Climate and energy indicators for Europe from
> 2005 to 2100 derived from climate projections</span>](about:blank).*

As tools you need a GIS platform, likely QGIS 3 LTR or higher given the
availability of a specific plugin for the QSWAT+ to build the catchment
model, and the SWAT+ Editor to configure and run simulations; the SWAT+
installer bundles QSWAT+ and the Editor, and QSWAT+ requires SWAT+
Editor v3.0+

|                                                                                     |                                                                                                     |                                                                                                                     |
| ----------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| **Tool**                                                                            | **Type**                                                                                            | **Role in this workflow**                                                                                           |
| [<span class="underline">QGIS</span>](https://qgis.org/download/)                   | Desktop GIS                                                                                         | Data prep, watershed delineation, HRU definition, mapping, results viewing.                                         |
| QSWAT+ (QGIS plugin included in swat + installer hereafter)                         | SWAT+ pre/post-processor                                                                            | Build sub-basins, LSUs, HRUs; export to SWAT+; visualize outputs and compare scenarios.                             |
| [<span class="underline">SWAT+ Editor</span>](https://swat.tamu.edu/software/plus/) | Model [<span class="underline">editor/runner</span>](https://swatplus.gitbook.io/docs/installation) | Import project DB, set weather data and print options, run SWAT+, write outputs to SQLite for QSWAT+ visualization. |

*Table 2 – used tools and role in the workflow, all tools are free to
use.*

### Methodology

#### Step 1 - Data acquisition and preparation

This step assembles regional inputs and prepares a coherent catchment
dataset before any model run. Acquire the base geospatial layers (e.g.,
5 m DTM from the Emilia-Romagna Geoportal, regional soil map, 2023
land-use shapefile) and **clip them to a single area-of-interest mask**.
Reproject to a **common CRS**, align **resolution and extent**, and fix
No Data or geometry issues to ensure clean overlays. Build a **land-use
and soil crosswalk** so that classes and attributes match the categories
and parameters expected later in the analysis; include slope derivation
where needed to support HRU structuring in subsequent steps. (Figure 2).

Prepare meteorological inputs as **station-based daily Time Series** in
the model’s required text format. For each gauge provide **ID, name,
latitude, longitude, elevation**, and a file with daily values; use the
documented variable set and **units** and apply the specified
**missing-value code**. Typical variables are precipitation and max/min
temperature, with solar radiation, wind, and relative humidity either
provided or simulated by the weather generator. During runs, each
sub-basin is associated with the **nearest** available precipitation and
temperature stations.

**Read the model documentation first** to confirm exact fields and
layouts. Keep the simulation period consistent with the available time
frame (e.g. from ARPAE ground stations).

The following images (Figure 3) show the basin analysed within
**Co-Innovation Lab 3**, together with the results of the first tests
carried out with **SWAT+** on the study area in terms of **Full HRU**
and **Actual HRU**. It should be noted that the simulations are still
ongoing; therefore, the results presented here are only **preliminary**.

<table>
<thead>
<tr class="header">
<th><p><img src="/content/drive/MyDrive/GECO_RESEARCH/17_R&amp;D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/ER-Lab3_FIAs_draft2_media/media/image5.png" style="width:3.00661in;height:1.83403in" alt="Immagine che contiene Aerofotogrammetria, Vista aerea, mappa, aereo Il contenuto generato dall&#39;IA potrebbe non essere corretto." /></p>
<p>A</p></th>
<th><p><img src="/content/drive/MyDrive/GECO_RESEARCH/17_R&amp;D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/ER-Lab3_FIAs_draft2_media/media/image6.png" style="width:3.18472in;height:1.78245in" alt="Immagine che contiene mappa Il contenuto generato dall&#39;IA potrebbe non essere corretto." /></p>
<p>B</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><img src="/content/drive/MyDrive/GECO_RESEARCH/17_R&amp;D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/ER-Lab3_FIAs_draft2_media/media/image7.png" style="width:2.92433in;height:1.79167in" alt="Immagine che contiene mappa, testo Il contenuto generato dall&#39;IA potrebbe non essere corretto." /></p>
<p>C</p></td>
<td><p><img src="/content/drive/MyDrive/GECO_RESEARCH/17_R&amp;D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/ER-Lab3_FIAs_draft2_media/media/image8.png" style="width:3.03915in;height:1.75586in" alt="Immagine che contiene mappa, testo Il contenuto generato dall&#39;IA potrebbe non essere corretto." /></p>
<p>D</p></td>
</tr>
</tbody>
</table>

Figure Example of preprocessing of geospatial base layers clipped to the
area of interest. Figure A represents the preliminary watershed
identified from the first simulations; Figure B shows the basin with the
DEM background; Figure C illustrates the Full HRUs and Figure D the
basin with the Actual HRUs (see note for the definition of Full and
Actual HRUs).

  - ##### Note: Difference between Full HRU and Actual HRU

> **Full HRU**: all unique combinations of land use, soil type, and
> slope are represented, even if they cover a very small area. This
> allows for maximum spatial detail but increases the number of HRUs and
> computational effort. **Actual HRU**: only HRUs above user-defined
> thresholds are kept, while smaller ones are merged into larger units.
> This reduces model complexity and simulation time, at the cost of some
> spatial detail.

#### Step 2 - Model setup and run.

Load the pre-processed geospatial layers and station-based
meteorological series into the modelling environment and define the
study area (Galeata–Santa Sofia) and time window for the **baseline**.
Use the same spatial framework and forcing prepared in Step 1.

Initialize the model with the catchment topology, soil–land-use
attributes, and daily climate forcing so that it reproduces present
hydro-geological processes. Configure a suitable warm-up and the daily
time step.

The baseline run must yield decision-ready outputs for the key
indicators tracked in Table 1: **runoff peak** and **base-flow** at the
outlet, **infiltration/storage proxies**, and **water-quality/erosion
indicators** (here we focus on **water flow, soil erosion, and nutrient
dynamics**). Results are saved as tables and can be linked to
sub-basin/HRU layers for inspection in GIS.

Baseline processing, in brief: perform **DEM-based topographic
processing** to delineate watershed, sub-basins, and channels; then
**assign attributes** by intersecting land use, soils, and slope to
create **HRUs**; finally **run the daily water-balance and water-quality
simulation** so outputs can be mapped and analyzed at
**HRU/LSU/channel** level, including sediment.

](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/ER-Lab3_FIAs_draft2_media/media/image9.png)](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/ER-Lab3_FIAs_draft2_media/media/image10.png)

Figure – example of topographic processing delineates the watershed,
sub-basins, and channels from the DEM. After reading grids and
intersecting land use, soils, and slope, potential HRUs are created as
polygons, enabling HRU-level mapping and analysis, source
[<span class="underline">QSWAT+
manual</span>](https://1905549715-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FgsvY4UbwriwcK1CI5lan%2Fuploads%2FgHq0X4ezLSWlotZ8Llyv%2FQSWATPlus%20Manual_v3.0.pdf?alt=media&token=dcaf77fa-a670-4a62-86d6-4451d593e69b).
The images represent an illustrative example and are not related to our
case study, as the modeling is still in progress and consistent results
are not yet available.

  - ##### Note — interface options

> *This tutorial targets QSWAT+ within QGIS. However, the SWAT+
> toolchain can be used without the GIS interface by working directly
> with the SWAT+ Editor and its runners. If you prefer not to use QGIS,
> consult the official [<span class="underline">SWAT+ software
> page</span>](https://swat.tamu.edu/software/plus/) for alternative
> installers and workflows, then keep project databases and input
> folders consistent with this tutorial.*

#### Step 3 - Analysis and interpretation

We convert the baseline run into decision-ready indicators by extracting
outlet runoff peak and base-flow, computing infiltration/storage
proxies, and reading water-quality and erosion metrics (N, P, SS) at
sub-basin and HRU level, consistent with the Lab 3 scope.  
Results are inspected as tables and geospatial layers in GIS to map
HRU/sub-basin patterns, plot time series, and export summaries for
reporting; this locates runoff hot spots, sediment sources, and reaches
with elevated nutrient.  
Relate spatial signals to soils, land use, slope, and drainage, then
record where baseline conditions meet objectives and where they do not.
This becomes the key indicators baseline and the sole reference for Step
4 comparisons.

Use two standard outputs (Figure 4): **a static HRU map** and an outlet
flow time series. The HRU map is generated as a static shapefile with
aggregated metrics ready for GIS analysis; the outlet series is plotted
with **SWATGraph options** and can be compared with recorded values, for
example a gauged hydrograph.  
If a gauge exists at basin closure, compare simulated and observed
discharge and **iteratively refine the baseline setup before proceeding
to Step 4,** also quality parameters may be compared in output Vs
observed values.

](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/ER-Lab3_FIAs_draft2_media/media/image11.png)

](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/ER-Lab3_FIAs_draft2_media/media/image12.png)

Figure  - Top: Static HRU results (Figure 38). Bottom: Outlet discharge
time series (Figure 45). The static view exports HRU polygons with model
metrics for GIS analysis; the time series plots simulated flow at basin
closure and supports calibration against observed hydrographs, source
[<span class="underline">QSWAT+
manual</span>](https://1905549715-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FgsvY4UbwriwcK1CI5lan%2Fuploads%2FgHq0X4ezLSWlotZ8Llyv%2FQSWATPlus%20Manual_v3.0.pdf?alt=media&token=dcaf77fa-a670-4a62-86d6-4451d593e69b)

#### Step 4 - FIAs testing.

Duplicate the calibrated baseline, keep forcing, spatial setup, warm-up,
and print options identical, and introduce **Forested Infiltration
Areas** by **converting only the selected hillslope and riparian
polygons to forest where Lab 3 plans FIAs**. Do not change soil or
climate inputs. Re-run the same period so any change reflects the FIA
signal on the key indicators tracked in Table 1 (runoff peak, base-flow,
infiltration/storage proxies, N, P, SS).

Compare baseline and FIA by exporting static HRU/sub-basin layers and
plotting outlet hydrographs; map deltas in GIS and overlay hydrographs
to show peak attenuation and base-flow shifts. This mirrors the
project’s intended use of SWAT+ to test FIA scenarios against the
present conditions defined in Step 2–3. Use QSWAT+ **visualization
options** to generate static result layers and **SWATGraph** for
discharge time series at basin closure when inspecting differences.

Eventually introduce **Climate Change effect in weather forcings** to
test more climate related scenarios with/wo FIAs.

## Nursery-Scale Hazard: Irrigation Water Demand & Drought Resilience

### Description and context

The nursery in the Galeata–Santa Sofia area is analysed to quantify
**nursery plants** water requirements and support drought-resilient
irrigation scheduling. The assessment uses a field-scale
decision-support tool (IRRIFRAME; open alternative AquaCrop) that
ingests site-specific inputs—soil analyses from a specific season,
continuous soil-moisture readings, **coefficients (Kc) for nursery
plants**, local meteorology, and recorded irrigation events—and returns
**tabular demand estimates;** compatible **climate projections may be
explored for future demand**. This nursery workflow is methodologically
independent from the catchment analysis and informs operational water
management and planning.

Key indicators tracked in this tutorial at a Nursery-Scale are listed
hereafter:

|                                    |                                               |                   |                                                                                        |
| ---------------------------------- | --------------------------------------------- | ----------------- | -------------------------------------------------------------------------------------- |
| **Dimension**                      | **Indicator(s)**                              | **Unit**          | **Purpose**                                                                            |
| Irrigation demand                  | Crop water need (ETc for nursery plants)      | mm d⁻¹; mm/season | Computed from daily ETo and Kc by growth stage.                                        |
| Irrigation scheduling & efficiency | Irrigation advice (next date and event depth) | date; mm/event    | Event timing and depth from soil–plant water balance thresholds (“irrigation advice”). |

*Table 2 – key indicators tracked-Nursery scale-water demand.*

### Data sources and tools

At local scale, an irrigation-balance model (field, block, or nursery in
this example) needs **site-specific inputs** to compute **ETc
(**\[1\]**)** and get the **irrigation advice** (“when” and “how much”):
recent soil analyses, soil-moisture observations, crop coefficients for
nursery plants, daily meteorology, and irrigation logs. Outputs are
typically tabular; you may also consult the IRRIFRAME documentation
([<span class="underline">ENG</span>](https://www.irriframe.it/irriframe/Content/IrriFrame_Documentation_english_version.pdf)
leaflet,
[<span class="underline">ITA</span>](https://www.irriframe.it/irriframe/Content/Manuale_Irriframe.pdf)
manual) to get more details on how such water balance models works.

<table>
<tbody>
<tr class="odd">
<td><strong>Data type</strong></td>
<td><strong>Source</strong></td>
<td><strong>Role in workflow</strong></td>
<td><strong>Open / EU alternative</strong></td>
</tr>
<tr class="even">
<td>Soil analyses</td>
<td><p>Nursery lab tests (2024 season)</p>
<p>At regional scale (<a href="https://datacatalog.regione.emilia-romagna.it/catalogCTA/dataset/r_emiro_2023-08-02t140310"><span class="underline">open repo</span></a>)</p></td>
<td>Main soil properties like field capacity, wilting point, and soil parameters for the soil–plant water balance</td>
<td>European Soil Database &amp; soil properties ( <a href="https://esdac.jrc.ec.europa.eu/resource-type/european-soil-database-soil-properties"><span class="underline">open. Raster-vector</span></a>)</td>
</tr>
<tr class="odd">
<td>Soil-moisture readings</td>
<td>On-site sensors</td>
<td>Trigger thresholds and validation of advice</td>
<td><a href="https://cds.climate.copernicus.eu/datasets/satellite-soil-moisture?tab=overview"><span class="underline">Soil moisture gridded data from 1978 to present</span></a> (<span class="underline">coarse</span> 0.25°X0.25°)</td>
</tr>
<tr class="even">
<td>Nursery plants Kc and crop info</td>
<td>Nursery records (species, stage)</td>
<td>Compute ETc from ETo×Kc; scheduling by stage</td>
<td><a href="https://www.fao.org/4/x0490e/x0490e0b.htm"><span class="underline">FAO-56 Kc tables;</span></a> <a href="https://ayhoekstra.nl/pubs/Report16Vol2.pdf"><span class="underline">Chapagain and Hoekstra (2004)</span></a>.</td>
</tr>
<tr class="odd">
<td>Local meteorology (P, T, ET0) Daily</td>
<td>ARPAE DEXT3R station series</td>
<td><p>Drives ETo/ETc and advice.</p>
<p>(ETo may be computed with the <a href="https://www.fao.org/4/x0490e/x0490e08.htm"><span class="underline">Hargreaves equation</span></a>) if precipitation and air temperature series are the only for the site</p></td>
<td><a href="https://cds.climate.copernicus.eu/datasets/reanalysis-era5-land?tab=overview"><span class="underline">ERA5-Land hourly data from 1950 to present</span></a></td>
</tr>
<tr class="even">
<td>Irrigation cycles logs</td>
<td>Nursery records of past events</td>
<td>Compare applied vs recommended; fine-tune scheduling</td>
<td>—</td>
</tr>
</tbody>
</table>

*Table 3 – used data, an alternative dataset to replicate the assessment
outside the study area, when available*

  - ##### Climate change effects 

> *Bias-corrected climate-projection datasets may be incorporated, with
> particular focus on hydrogeological modelling.*
> 
> *For example [<span class="underline">Copernicus Temperature and
> precipitation climate impact indicators from 1970 to 2100 derived from
> European climate
> projections</span>](https://cds.climate.copernicus.eu/datasets/sis-hydrology-meteorology-derived-projections?tab=overview);
> [<span class="underline">Climate and energy indicators for Europe from
> 2005 to 2100 derived from climate projections</span>](about:blank).*

At local scale, we use an irrigation decision tool to compute **ETc**
and the **irrigation advice** (“when” and “how much”) from site soils,
nursery-plant Kc, daily meteorology, and irrigation logs. Primary option
is IRRIFRAME; AquaCrop is the open alternative. Outputs are tabular:

<table>
<tbody>
<tr class="odd">
<td><strong>Tool</strong></td>
<td><strong>Type</strong></td>
<td><strong>Role in this workflow</strong></td>
</tr>
<tr class="even">
<td><a href="https://www.consorziocer.it/irrinet/"><strong><span class="underline">IRRIFRAME</span></strong> <span class="underline"> </span></a> (ANBI/CER)</td>
<td><p>Proprietary <a href="https://www.irriframe.it/irriframe/Content/IrriFrame_Documentation_english_version.pdf"><span class="underline">Cloud DSS</span></a></p>
<p>Working in ER</p></td>
<td>Produces nursery-plant water requirement and operational <strong>irrigation advice</strong> from soil analyses, optional soil-moisture readings, Kc, local daily ETo/meteorology, and applied-irrigation logs; returns next irrigation date and event depth for scheduling and water-saving</td>
</tr>
<tr class="odd">
<td><a href="https://www.fao.org/aquacrop/en/"><strong><span class="underline">AquaCrop</span></strong> <span class="underline"> </span></a> (FAO)</td>
<td><a href="https://openknowledge.fao.org/server/api/core/bitstreams/ccfd6f4c-2900-4fb2-9a91-e0a93b1cbbda/content"><span class="underline">Open alternative</span></a></td>
<td>Open alternative when IRRIFRAME is unavailable; runs the soil–crop–climate water balance to estimate <strong>ETc</strong> and event depths, enabling comparable irrigation scheduling at nursery scale.</td>
</tr>
</tbody>
</table>

*Table 2 – used tools and role in the workflow, all tools are free to
use.*

### Methodology

#### Step 1 - Data acquisition and preparation

Assemble local inputs as clean, time-consistent series and tables:
current-season soil analyses, soil-moisture observations, nursery-plant
Kc by growth stage, daily ETo/precipitation/air temperature, and
irrigation logs. Keep phenology calendars and Kc tables aligned with
species and stages; the model will account for soil-water stress in the
irrigation advice.

Ensure soil parameters (field capacity, wilting point, texture) are
available to drive the soil–plant balance and use the irrigation log to
check “when” and “how much” against the model thresholds for event
depth. to illustrate typical inputs and fluxes

the following diagram is (from the IRRINET English manual) schematizes
of the soil–plant–atmosphere water-balance fluxes

  - ##### Note: tool specific formatting 

> *Use of alternative tools such as AquaCrop requires strict adherence
> to its input formats: the project file must reference climate files
> (e.g. ETo, temperature, rain) plus calendar, crop, irrigation/field
> management, soil profile, groundwater, initial/off-season and
> field-data files; consult the AquaCrop manual and match its file
> structures before any run.*

![Immagine che contiene testo, diagramma, schermata, Piano Il contenuto
generato dall'IA potrebbe non essere
corretto.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/ER-Lab3_FIAs_draft2_media/media/image13.png)

*Figure 5 – fluxes of input-output in the water balance model
implemented in IRRIFRAME, aimed at crop irrigation management at a field
scale, courtesy of
[<span class="underline">CER</span>](https://www.irriframe.it/irriframe/Content/IrriFrame_Documentation_english_version.pdf)*

#### Step 2 - Model setup and run.

The model advances a daily soil–plant water balance: it reads **ETo**,
**precipitation**, **air temperature**, and nursery-plant **Kc**;
computes **ETc = Kc × ETo**; updates soil water storage (inputs,
evapotranspiration, percolation); and checks depletion against
operational thresholds. When thresholds are exceeded, it outputs an
**irrigation advice** (next date and event depth) in tabular form.
Inputs are site/season, daily meteorology, soil parameters, Kc by growth
stage, and optional soil-moisture observations; exact formats and
thresholds follow the official documentation.

Open alternative: **AquaCrop** applies the same balance and provides
daily ET, **Kc (Tr)**, and **net irrigation requirement (Inet)** from
which ETc and event depth can be derived.

![1: Flowchart of the AquaCrop model. Dotted arrows indicate
processes... | Download Scientific
Diagram](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/ER-Lab3_FIAs_draft2_media/media/image14.png)

Figure - Source: Van Gaelen, H. (2012). The effect of field management
on yield and water productivity \[Master’s thesis, Katholieke
Universiteit Leuven\]. ResearchGate.
https://www.researchgate.net/publication/262952745\_The\_effect\_of\_field\_management\_on\_yield\_and\_water\_productivity

#### Step 3 - Analysis and interpretation

Use the graphical outputs to derive two decision variables: ETc (crop
water need) and the irrigation advice (next date and event depth).

](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/ER-Lab3_FIAs_draft2_media/media/image15.png)

You may then use a standard spreadsheet tool to make informing plots
like plot daily ETc with precipitation and temperature, then overlay
advised vs applied events from the nursery log to quantify compliance,
stress days, and potential savings.

Outputs remain tables (CSV p similar database ready) rather than maps;
and essentially provide data regarding the water requirements of the
crops, indicating how much water will need to be allocated for
irrigation in the nursery.

Users may aggregate to weekly or seasonal totals to size demand and
optimize cycles. These analyses inform operational scheduling at the
nursery and support resource-allocation and adaptation planning where
water is limited.

Step 4 - FIAs testing.

Set up a **scenario run** that mimics the hydrologic effect of Forested
Infiltration Areas at plot scale without changing crop demand logic.

Keep site, season, meteorology, and Kc identical to the baseline.
Represent the FIA as an **infiltration-enhancing configuration** of the
plot: increase rain storage and infiltration at the soil surface and
reduce direct runoff so that a larger share of rainfall becomes
**effective rainfall** in the soil balance.

In IRRIFRAME this follows the scheme where the soil surface layer
governs **infiltration rate, runoff, and effective rainfall** within the
field water-balance; you then let the advisory algorithm recompute the
**next irrigation date and event depth** from the soil-water thresholds.

With **AquaCrop**, you may build an analogous scenario by adjusting the
field/soil settings that control surface storage and runoff so more
water **infiltrates** and less is lost as **RO**; the daily balance
explicitly tracks **Surf**, **Infilt**, and **RO**, and program
parameters allow runoff control via CN logic. Request daily outputs and
compare **Inet/ET** and irrigation events between baseline and FIA
scenario.

Analyze as in Step 3 but per scenario: fewer or smaller advised events
indicate FIA benefit; unchanged Kc keeps plant demand constant, so
differences arise from enhanced **effective rainfall** and soil storage,
not from crop changes. Document the delta in seasonal irrigation
requirement and event count for reporting.

1.  **ETc (crop evapotranspiration):** water use of the crop under
    standard conditions. Units: mm d⁻¹ or mm per period. Computation:
    **ETc = Kc × ETo**; with water-stress adjustment the actual ET is
    **ETa = Kc × Ks × ETo**. Used to size irrigation depth once
    effective rainfall and soil storage are considered.
