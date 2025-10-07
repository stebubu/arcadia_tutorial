# den lab1 vollsmose draft2

### Introduction and Objectives of the Climate Risk Assessment

#### Regional context

The [Vollsmose](https://en.wikipedia.org/wiki/Vollsmose) district, located in the city of [Odense](https://english.odense.dk/), Denmark, is a dense urban neighbourhood currently undergoing a major renewal programme. The area faces multiple water-related risks linked to changing rainfall patterns, shallow groundwater, and diffuse surface pollution.

High-intensity precipitation events frequently exceed the drainage system’s capacity, leading to pluvial flooding. Elevated groundwater levels reduce the effectiveness of sewers and increase flood susceptibility. Untreated runoff entering local water bodies contributes to water quality degradation, threatening aquatic habitats and urban livability.

The combination of urban densification, climate change, and existing infrastructure limitations makes Vollsmose a priority site for testing integrated stormwater management approaches. In this context, Nature-Based Solutions (NbS) and Blue-Green Infrastructure (BGI) are central to the urban renewal strategy, aiming to retain, store, and treat stormwater locally, while also delivering co-benefits such as biodiversity enhancement, reduced carbon footprint, and improved urban quality of life.

#### Scope of the tutorial

This tutorial describes a replicable Climate Risk Assessment (CRA) workflow for urban stormwater management in the Vollsmose district. The focus is on two of the three interrelated hazards present in the area: pluvial flooding and surface water quality degradation.

The workflow combines high-resolution terrain and land-use datasets, precipitation and hydrological records, and drainage network data with modelling tools for runoff, drainage, and pollutant transport. It shows how to evaluate the effectiveness of Nature-Based Solutions (NbS) and Blue-Green Infrastructure (BGI) in retaining stormwater, reducing peak discharges, and improving water quality.

The approach is designed for transferability: it integrates both open European datasets (e.g. Copernicus) and local proprietary data (e.g. sewer network, utility monitoring) to ensure that similar assessments can be replicated in other urban contexts.

{% hint style="warning" %}
This tutorial is intended as a general workflow example and does not replace software-specific documentation (e.g. GIS, hydrological, or urban drainage modelling tools user/technical manuals). Users should already be familiar with relevant geospatial data formats, data pre-processing techniques, and modelling concepts for stormwater and water quality assessment, as well as with the specific input/output requirements and functionalities of the modelling software before attempting to replicate this workflow.
{% endhint %}

#### CRA objectives

The Vollsmose CRA aims to:

* Manage stormwater flooding — Identify zones where high-intensity rainfall exceeds drainage capacity and assess retention needs.
* Improve water quality — Quantify pollutant loads in stormwater and identify NbS that can retain and treat runoff before entering the wider system.
* Integrate NbS into planning — Support the design of sustainable drainage infrastructure, including rainwater basins, swales, and permeable surfaces, aligned with the urban renewal process.
* Promote multiple co-benefits — Link stormwater management to broader goals such as biodiversity support, low-carbon urban design, and improved urban livability.
* Enable scenario testing — Provide a framework for comparing baseline and NbS-enhanced conditions under current and future climate scenarios.

#### Intended Users

This Climate Risk Assessment is intended for urban planners and water managers involved in the renewal of the Vollsmose district. It supports the technical departments of Odense Municipality and the local utility company VandCenter Syd in designing sustainable drainage infrastructure under changing rainfall conditions.

The workflow also assists environmental consultants and landscape architects in evaluating the performance of Nature-Based Solutions (NbS) for stormwater retention and water quality improvement. Public health authorities may use the outputs to identify areas where stormwater pollution intersects with vulnerable communities.

In this context, the CRA results guide the planning and siting of stormwater storage basins and local retention/treatment systems, as well as the creation of ecological corridors and water-linked habitats. These NbS reduce peak flows, improve water quality, and generate co-benefits for biodiversity and urban livability.

### Flood Hazard – Pluvial stormwater mapping

#### Description and context

The first stage of the pluvial flooding assessment focuses on mapping surface runoff and identifying critical accumulation areas under intense rainfall events. High-resolution topographic data are combined with rainfall statistics to simulate overland flow pathways, depressions, and temporary storage zones.

Tools such as terrain-processing platforms using LiDAR-derived Digital Elevation Models (DEM) delineate flow paths, ponding areas, and stormwater storage potential. These outputs highlight where rainfall volumes concentrate during extreme events, providing a first screening of flood-prone zones within the urban fabric.

This mapping step does not simulate the hydraulic performance of the sewer network, but it delivers decision-ready layers for urban planners. The results support the siting and preliminary sizing of Nature-Based Solutions (NbS), such as stormwater retention basins or open drainage features, and establish the baseline conditions for more detailed drainage modelling.

| Dimension                  | Indicator(s)                                                 | Unit  | Purpose                                                         |
| -------------------------- | ------------------------------------------------------------ | ----- | --------------------------------------------------------------- |
| Flood extent / water depth | Flooded area, maximum water depth (linked to rainfall event) | m², m | Identify flood-prone zones and evaluate NbS retention potential |
| Stormwater volume          | Retained or delayed runoff in stormwater basins/NbS          | m³    | Quantify capacity to attenuate peak flows                       |

Table 1 — Key indicators tracked — Pluvial stormwater mapping

#### Data sources and tools

The runoff mapping workflow in Vollsmose relies on a combination of topographic, hydrological, and land-use datasets. High-resolution elevation models form the basis for identifying depressions, flow paths, and potential storage zones across the urban landscape. Rainfall observations provide the forcing conditions to simulate surface accumulation during intense events. Land cover and soil information are used to distinguish impermeable from permeable areas, while building footprints refine the representation of urban morphology and its influence on water routing.

For replication outside Denmark, open European datasets such as Copernicus DEM, CORINE Land Cover, and ERA5 precipitation data offer alternative inputs, albeit at coarser resolution. These allow the workflow to be applied beyond the local context, ensuring comparability and transferability across regions.

| **Data type**                                              | **Source**                                                        | **Role in workflow**                                                                                            | **Open/EU alternative**                                                                                                                                                                                                                    |
| ---------------------------------------------------------- | ----------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| LiDAR-based Digital Terrain model (0.4 m grid)             | [GeoDanmark](https://dataforsyningen.dk/data/930)                 | Elevation base for flood modelling; identifies depressions and flow paths                                       | Copernicus DEM - Global and European Digital Elevation Model [(open – raster 30m, 10m for selected users)](https://dataspace.copernicus.eu/explore-data/data-collections/copernicus-contributing-missions/collections-description/COP-DEM) |
| Rainfall observations (10‑minute cumulative precipitation) | [DMI Open Data](https://opendatadocs.dmi.govcloud.dk/DMIOpenData) | Used as forcing input for both pluvial flood impact mapping and urban drainage modelling.                       | [ERA5-Land hourly data from 1950 to present](https://cds.climate.copernicus.eu/datasets/reanalysis-era5-land?tab=download)                                                                                                                 |
| Assigned return time Rainfall height statistics            |                                                                   | Models urban flood exposure under extreme rainfall events, input to flood models alternative to riverine floods | **ERA5** [**extreme precipitation indicators**](https://cds.climate.copernicus.eu/datasets/sis-european-risk-extreme-precipitation-indicators?tab=overview)                                                                                |
| Land use / land cover                                      | [GeoDanmark](https://dataforsyningen.dk/data/996)                 | Classification of flood-prone areas by land-use category for exposure and damage assessment                     | **Copernicus** [**Urban Atlas**](https://land.copernicus.eu/en/products/urban-atlas); [**CLCplus Backbone**](https://land.copernicus.eu/en/products/clc-backbone)                                                                          |
| Soil texture / permeability maps                           |                                                                   | Supports estimation of infiltration and runoff coefficients                                                     | **Soil texture classes (USDA system) for 6 soil depths (0, 10, 30, 60, 100 and 200 cm) at 250 m (**[**Version v02**](https://zenodo.org/records/2525817)**)**                                                                              |
| Building footprints                                        | [GeoDanmark](https://dataforsyningen.dk/data/2677)                | Refine flow routing and adjust storage estimation                                                               | OpenStreetMap building layer ([vector, global)](https://osmbuildings.org/)                                                                                                                                                                 |

Table 2 — Used data and alternative datasets to replicate the assessment outside the study area, when available

Surface runoff mapping in Vollsmose combines proprietary platforms and open-source GIS environments. Terrain-based tools process high-resolution LiDAR elevation data to identify runoff pathways, ponding areas, and potential stormwater storage volumes. These results provide rapid, visual outputs that help planners screen flood-prone areas and evaluate the effectiveness of preliminary Nature-Based Solutions (NbS).

Cloud-based services, frequently offered as proprietary solutions, allow quick interactive scenario testing under different rainfall events, while open-source GIS software coupled with desktop-based alternatives may support integration of hazard layers with land use and exposure datasets using open resources.

The combination ensures that outputs can be both locally precise and transferable to other contexts using alternative datasets and open tools:

| Tool                                                                     | Type        | Role in workflow                                                                                                            |
| ------------------------------------------------------------------------ | ----------- | --------------------------------------------------------------------------------------------------------------------------- |
| [Scalgo Live](https://scalgo.com/)                                       | Proprietary | Terrain-based analysis of runoff pathways, depressions, and storage volumes                                                 |
| [SaferPlaces](https://saferplaces.co/)                                   | Proprietary | Terrain-hydrodynamic based analysis of runoff pathways, depressions, and storage volumes; includes damage assessment option |
| [HEC-RAS](https://www.hec.usace.army.mil/software/hec-ras/download.aspx) | Open        | Direct simulation of rainfall over the surface domain; produces depth and velocity maps of pluvial flooding (Rain on Grid)  |
| [QGIS](https://qgis.org/)                                                | Open        | GIS analysis, visualization, and overlay of hazard and exposure datasets                                                    |

Table 3 — Tools and role in the Stormwater Mapping hazard workflow

#### Methodology

{% stepper %}
{% step %}
### Step 1 — Data acquisition and preparation

The first step in the runoff mapping workflow is to collect and prepare spatial and hydrological datasets. A high-resolution Digital Terrain Model (DTM), typically derived from LiDAR surveys, is required to represent depressions, flow paths, and storage zones across the urban landscape.

Building footprints can be overlaid on the terrain to include such obstacles, remove artificial depressions generated by LiDAR filtering algorithms and improve the accuracy of flow routing.

Rainfall time series are used to define design storm events for the mapping simulations. These can be derived from national meteorological services (e.g. DMI) or from European datasets (e.g. ERA5-Land) when local data are not available. Land use and land cover data are harmonized to distinguish impervious from pervious areas, supporting runoff estimates and NbS siting.

All datasets are then converted into GIS-compatible formats and spatially aligned. Terrain and land cover layers are prepared for input into flood mapping tools.
{% endstep %}

{% step %}
### Note on DEM resolution

When using very high-resolution LiDAR DEMs (e.g. 0.4 m), the data can become too heavy for hydraulic modelling. A practical solution is to downsample to 1–2 m resolution, which is still reasonable for flood modelling. This can be done through mosaicking and resampling in GIS software (e.g. QGIS) or by using command-line tools such as GDAL. For example:

gdalwarp --config GDAL\_NUM\_THREADS ALL\_CPUS -r bilinear -tr 1,2 1,2 -t\_srs EPSG:25832 -co COMPRESS=LZW -co BIGTIFF=YES -co PREDICTOR=2 c:/folder1/\*.tif c:/folder1/mosaic.tif

For further reference, see the GDAL [gdalwarp documentation](https://gdal.org/en/stable/programs/gdalwarp.html).

Building footprints could be overlaid on the terrain to include obstacles, remove artificial depressions, and improve flow routing accuracy.
{% endstep %}

{% step %}
### Step 2 — Model setup and run

Import pre-processed terrain and rainfall datasets into mapping platforms to simulate stormwater accumulation and spread during intense precipitation. The LiDAR-derived terrain defines depressions and flow paths, while design storms provide the forcing input.

Model outputs: ponding areas, water depths, storage zones, and preferential flow directions. Approaches vary from static (zero-dimensional) screening models that convert rainfall to accumulated volumes, to 2D dynamic models that simulate time-varying surface routing and velocities.

Which approach to use depends on objectives and computational capacity.
{% endstep %}

{% step %}
### Note: role of land use/cover and soil properties

Depending on the modelling tool, soil properties and land cover can be included to represent infiltration processes and reduce effective rainfall. If missing, conservative assumptions are often used (e.g. fully impervious surfaces or standard runoff fractions per land cover) to represent short-duration extreme events.
{% endstep %}

{% step %}
### Step 3 — Analysis and interpretation

Interpret water depth and flood extent maps in a GIS environment by overlaying with exposure datasets (land cover, buildings, redevelopment areas). Derive indicators such as:

* Fraction of each land use polygon affected by inundation.
* Stormwater volume stored within each polygon.

These indicators help rank vulnerability and support NbS siting and sizing. More advanced overlays (e.g. building footprints + depth–damage curves) can provide proxy estimates of potential economic losses.
{% endstep %}

{% step %}
### Step 4 — Testing of measures

Emulate NbS by editing analysis terrain and related layers: insert depressions for new storage basins; add break lines or shallow channels to steer flow; adjust surface roughness or simple infiltration parameters. Re-run scenarios with the same design storms to compare baseline vs. NbS-enhanced conditions.

Interpret outputs with the same GIS procedures used for the baseline: quantify changes in flooded extent, shifts in flow paths, and additional temporary storage.
{% endstep %}
{% endstepper %}

(Figures illustrating LiDAR DTM comparisons, static vs dynamic model outputs, and GIS overlays are included in the original material.)

### Flood Hazard – Urban drainage and water quality modelling

#### Description and context

This second part focuses on stormwater management through simulation of the urban drainage system. While surface runoff mapping provides a first screening based on topography, this step examines how rainfall is conveyed and stored within the sewer network and associated detention structures.

Urban drainage and water quality models represent hydraulic behaviour of sewer pipes, basins, and outlets, simulate surcharge or flooding under extreme events, and estimate pollutant transport. By assigning typical pollutant concentrations to inflows (e.g. nitrogen, phosphorus, suspended solids), it becomes possible to test how NbS and alternative management options affect both hydraulic performance and water quality before discharge.

| Dimension               | Indicator(s)                                                       | Unit | Purpose                                                                                           |
| ----------------------- | ------------------------------------------------------------------ | ---- | ------------------------------------------------------------------------------------------------- |
| Drainage network load   | Peak discharge flow rate at critical nodes of the drainage network | m³/s | Identify where and when the drainage system is overloaded and may benefit from mitigation systems |
| Pollutant concentration | Nitrogen (N), Phosphorus (P), Suspended Solids (TSS) in stormwater | mg/L | Assess impact of runoff on receiving waters and performance of treatment NbS                      |

Table 4 — Key indicators tracked — Urban drainage and water quality modelling

#### Data sources and tools

Drainage and water quality modelling requires, in addition to terrain and rainfall data, operational and utility datasets describing the sewer system: pipe layouts, detention basins, outlet structures, and flow monitoring. Water quality inputs (build-up/wash-off parameters, event mean concentrations) are needed for pollutant simulations.

Because of the highly site-specific nature of urban drainage modelling, these datasets do not have generic European counterparts; the workflow therefore requires detailed local utility and monitoring data when implemented at full fidelity.

| Data type                                                                            | Source                                                                      | Role in workflow                                                                                             |
| ------------------------------------------------------------------------------------ | --------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| Drainage network geometry and attributes (pipes, nodes, basins, outlets)             | Local utility (VandCenter Syd) or municipal databases                       | Core structural input for hydraulic modelling: topology, diameters, slopes, detention volumes                |
| Inflow allocation per catchment                                                      | Derived from high-resolution DEM + land cover                               | Connects surface runoff volumes to network nodes; ensures consistency between runoff mapping and sewer model |
| Water quality parameters (build-up/wash-off, pollutant concentrations for N, P, TSS) | Local monitoring programmes or literature/default values (e.g. SWMM manual) | Define pollutant inputs to simulate stormwater quality; allows testing of NbS impacts on loads               |
| Operational flow/level data                                                          | Utility SCADA or monitoring stations                                        | Calibration/validation of hydraulic simulations; verify surcharge, storage, pollutant routing                |

Table 5 — Additional data used in the drainage system workflow

{% hint style="info" %}
In absence of local water quality monitoring data, suitable ranges for pollutant input parameters can be sourced from standard modelling references. The [SWMM 5.2 User Manual](https://www.epa.gov/system/files/documents/2022-04/swmm-users-manual-version-5.2.pdf) provides indications on default build-up and washoff functions as well as typical pollutant concentration values and decay coefficients. For regional/nordic examples, see e.g. [de Wit et al. 2020](https://oulurepo.oulu.fi/bitstream/handle/10024/28855/nbnfi-fe202101212289.pdf?sequence=1\&isAllowed=y).
{% endhint %}

Tools referenced:

| Tool                                                                                                            | Function                                                                          | Role in workflow                                                                                                             |
| --------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| [SWMM](https://www.epa.gov/water-research/storm-water-management-model-swmm) (EPA Storm Water Management Model) | Open-source rainfall–runoff, hydraulic routing, pollutant build-up/wash-off model | Core environment to represent sewer hydraulics and stormwater quality; test network under extreme rainfall and NbS scenarios |
| [MIKE URBAN](https://www.dhigroup.com/upload/campaigns/mike-urban-plus/MIKE-URBAN-Plus-highlight-flyer.pdf)     | Commercial sewer network modelling                                                | Detailed modelling and calibration with monitoring data                                                                      |

#### Methodology

{% stepper %}
{% step %}
### Step 1 — Data acquisition and preparation

Assemble datasets describing physical infrastructure and boundary conditions: sewer geometry (pipes, nodes, manholes, detention basins, outlets) and attributes (diameters, slopes, invert levels, storage capacities). Delineate sub catchments and connect them to network nodes to ensure consistency with surface runoff mapping.

Prepare rainfall time series (design storms or continuous observations) and pollutant input parameters (N, P, TSS concentrations, build-up/wash-off functions).
{% endstep %}

{% step %}
### Note on sub-catchment delineation

Sub-catchments can be delineated morphologically using high-resolution terrain data or via simplified methods (Thiessen polygons, GIS inference areas) around network inlets. Choose the method based on data availability while ensuring consistency with runoff mapping.
{% endstep %}

{% step %}
### Step 2 — Model setup and run

Build the schematic representation of the sewer system (nodes and links) from utility datasets. Assign rainfall time series to sub catchments to generate inflows. Hydraulic routing is performed using Saint-Venant equations or simplified wave formulations as supported by the tool.

Assign pollutant loads through build-up and washoff functions or event mean concentrations and route pollutants with flow to evaluate concentrations and loads across the network and at outlets.
{% endstep %}

{% step %}
### Step 3 — Analysis and interpretation

Analyse hydraulic outputs (flow rates, water levels, surcharge frequencies) to identify network vulnerabilities and prioritise interventions. Assess water quality outputs (pollutant concentrations and loads) at outlets or detention basins to understand impacts on receiving waters.

Combine model outputs with GIS overlays (land use, receptors) to rank vulnerable nodes, estimate exceedance probabilities, and assess pollutant reductions achievable by NbS.
{% endstep %}

{% step %}
### Step 4 — Testing of measures

Introduce NbS into the schematic model: retention/storage nodes (detention basins, green areas) to absorb peak inflows and delay discharges, and treatment-oriented NbS (biofiltration, vegetated retention) represented with pollutant removal functions.

Rerun simulations to quantify changes in: peak discharge at critical nodes; pollutant concentrations at selected outlets; and overall stormwater retention volumes. Compare baseline and NbS-enhanced scenarios to evaluate flood risk reduction, pollutant load decreases, and co-benefits.
{% endstep %}
{% endstepper %}

(Figures illustrating sewer model components, monitoring data examples, and example outputs from SWMM are included in the original material.)

#### Notes on interpretation and outputs

* Model outputs (node surcharge, overflow volumes) can be exported to GIS and mapped to identify recurrent flooding risk areas and prioritise NbS or network upgrades.
* Indicators to compare scenarios include peak discharge at nodes, pollutant concentrations at outlets (N, P, TSS), and retained stormwater volumes.

#### References and supporting material

<details>

<summary>Reference</summary>

1. https://orbit.dtu.dk/files/130797720/IN\_PC956\_B4\_1\_Flood\_Damage\_web.pdf

(See SWMM 5.2 User Manual and cited documents in-text for further technical guidance.)

</details>
