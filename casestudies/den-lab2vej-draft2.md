# den lab2vej draft2

### Introduction and Objectives of the Climate Risk Assessment

#### Regional context

The [Vejrup Å catchment](https://www.sdu.dk/en/forskning/arcadia/about-arcadia/arcadia-in-funen/lab2), located in eastern Funen within [Odense](https://english.odense.dk/) Municipality (with smaller parts in [Kerteminde](https://en.wikipedia.org/wiki/Kerteminde_Municipality) and [Faaborg-Midtfyn](https://www.fmk.dk/)), is mainly exposed **to coastal flooding from Odense Fjord**.

The area north of Kerteminde road is undergoing major land-use transitions: agricultural land is being converted into commercial developments, while low-lying coastal zones are designated for wetland and salt marsh restoration.

Municipal climate adaptation strategies, as set out in the [**Odense Climate Adaptation Plan**](https://www.odense.dk/byens-udvikling/klima/klimatilpasning/klimatilpasningsplan) (Figure 1), foresee the withdrawal of coastal protection up to the Kerteminde road. This retreat strategy is promoted within the framework of **Den grønne trepart** (a collaboration platform between municipalities, state, and stakeholders) and is intended to create space for restored wetlands and salt marshes. These measures are expected to mitigate coastal flooding, reduce nutrient runoff to the fjord, and support biodiversity.

Figure - Climate risk assessment map from Odense Municipality climate adaptation plan 2024.

This approach reflects a broader institutional shift toward adaptive land-use planning, where flood risk management, ecological restoration, and urban development are coordinated to reduce **coastal squeeze**, cut CO₂ emissions, and provide multiple benefits for local communities and ecosystems.

#### Scope of the tutorial

This tutorial describes a replicable Climate Risk Assessment (CRA) workflow for the Vejrup Å catchment, addressing coastal flood hazards caused by sea level rise and storm surges. The workflow uses high-resolution elevation data, storm surge scenarios, coastal flood simulations, and land-use information to map current and future inundation zones.

The approach supports local adaptation planning by testing both nature-based and traditional solutions identified in the catchment, such as wetland restoration, salt marsh creation, and coastal protection structures. These interventions are assessed for their capacity to reduce inundation extent and depth while enabling sustainable land-use transitions. Designed for transferability, the tutorial combines national datasets with open European sources, allowing replication in other coastal lowlands facing similar risks.

{% hint style="info" %}
This tutorial is intended as a general workflow example and does not replace software-specific documentation (e.g., GIS, hydrological, or coastal modelling tools user/technical manuals). Users should already be familiar with the relevant geospatial data formats, data pre-processing techniques, and modelling concepts applicable to flood hazard assessment, as well as with the specific input/output requirements and run functionalities of the modelling software before attempting to replicate this workflow.
{% endhint %}

#### CRA objectives

The CRA for the Vejrup Å catchment aims to:

* Identify areas exposed to **coastal flooding** from sea level rise and storm surges under different return periods and climate projections.
* Map inundation zones using high-resolution topography and coastal flood simulations to assess the extent and depth of flooding.
* Highlight where **wetland restoration** and **salt marsh creation**, together with coastal protection structures, can reduce flood risk.
* Support **municipal planning** by linking flood hazard maps with land-use strategies and by indicating zones suitable for business development or nature restoration.
* Provide a spatial basis for future assessments of **economic damage**, moving from hazard mapping toward damage-based evaluation. (In this tutorial, this component is addressed only at a qualitative level through overlay of land-use with flood maps.)

#### Intended users

The CRA results are primarily addressed to **municipal planners and officers** in Odense, Kerteminde, and Faaborg-Midtfyn, who are responsible for integrating flood risk into land-use and climate adaptation strategies. They are also relevant for regional decision-makers engaged in frameworks such as [_Den grønne trepart_](https://fvm.dk/arbejdsomraader/landbrug/groen-trepart), where spatial strategies for adaptation are evaluated.

Stakeholders involved in the ongoing **land-use transition**—such as the conversion of agricultural land into wetlands, salt marshes, or commercial districts—can use the outputs to guide interventions and assess their feasibility. In addition, **civil protection services** and **infrastructure managers** benefit from **hazard maps** that identify vulnerable assets and support the prioritisation of protective measures.

### Flood Hazard – coastal

#### Description and context

The Vejrup Å catchment is mainly exposed to coastal flooding from Odense Fjord, driven by sea level rise and storm surges. Large low-lying areas north of Kerteminde road are particularly vulnerable and have been designated for restoration into wetlands and salt marshes under the **Odense Climate Adaptation Plan**.

Coastal flood events threaten agricultural land, planned commercial districts, and critical infrastructure, with risks expected to increase under projected climate scenarios (IPCC RCP 8.5).

To address these challenges, local strategies promoted through **Den grønne trepart** envisage the withdrawal of coastal protection to Kerteminde road and the use of nature-based solutions—such as wetland and salt marsh creation—combined with structural defences where necessary. The overall aim is to “make room for nature facing the fjord,” reducing flood risk while supporting biodiversity, nutrient retention, and CO₂ reduction.

This tutorial therefore focuses on the workflow for assessing coastal flooding, mapping hazard zones, and exploring the effectiveness of adaptive measures in reducing inundation extent and depth.

| Dimension                  | Indicator(s)                                                                                                                                                                                                                                                                         | Unit                                             | Purpose                                                                                                  |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------ | -------------------------------------------------------------------------------------------------------- |
| Flood extent & water depth | Flooded area and maximum water depth under different return periods (e.g. 10, 20, 100 years; with climate projection for 2100). Water depth also provides the basis for typical damage assessment, which in this tutorial is only mentioned qualitatively and not developed further. | km², m                                           | Identify flood-prone zones, quantify severity, and classify exposure levels                              |
| Flood damage (qualitative) | Exposure of different land-use categories to flooding; potential damage estimated either as flooded area by land-use class (m²) or via depth–damage curves if available                                                                                                              | m² by land-use type, or qualitative damage class | Provide a first approximation of potential damages and support integration with external economic models |

Table 1 – key indicators tracked — Flood Hazard

#### Data sources and tools

Flood risk assessment in the Vejrup Å catchment is based on high-resolution topography, storm surge scenarios, hydrological forcing, and land-use datasets provided by national authorities. These datasets allow the simulation of coastal and inland flooding under current and projected conditions. Where local datasets are not available, equivalent open European sources can be used to ensure transferability of the workflow to other regions.

| Data type                                      | Source (national)                                                                                               | Role in workflow                                                                            | Open/EU alternative                                                                                                                                                                                                                                                                                                                                                          |
| ---------------------------------------------- | --------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| LiDAR-based Digital Terrain model (0,4 m grid) | [GeoDanmark](https://dataforsyningen.dk/data/930)                                                               | Elevation base for flood modelling; identifies depressions and flow paths                   | Copernicus DEM - Global and European Digital Elevation Model (open – raster 30m, 10m for selected users) https://dataspace.copernicus.eu/explore-data/data-collections/copernicus-contributing-missions/collections-description/COP-DEM                                                                                                                                      |
| Storm surge and sea level rise (Table 4).      | Local/national studies, IPCC RCP scenarios (variable return periods 5, 10, 20, 50, 100 and climate projections) | Defines marine flooding scenarios under current and climate change                          | Copernicus Climate Data Store — Climate indicators for Europe from 1940 to 2100 derived from reanalysis and climate projections: https://cds.climate.copernicus.eu/datasets/sis-ecde-climate-indicators?tab=overview ; Global sea level change indicators from 1950 to 2050: https://cds.climate.copernicus.eu/datasets/sis-water-level-change-indicators-cmip6?tab=overview |
| Hydrological adaptation structures             | [GeoDanmark](https://www.geodanmark.dk/)                                                                        | Representation of dikes, pumping stations, and barriers in models                           | None (site-specific)                                                                                                                                                                                                                                                                                                                                                         |
| Building footprints                            | [GeoDanmark](https://dataforsyningen.dk/data/2677)                                                              | Exposure analysis; identification of at-risk assets                                         | OpenStreetMap building layer (vector, global) https://osmbuildings.org/                                                                                                                                                                                                                                                                                                      |
| Land use / land cover                          | [GeoDanmark](https://dataforsyningen.dk/data/996)                                                               | Classification of flood-prone areas by land-use category for exposure and Damage assessment | Copernicus: Urban Atlas https://land.copernicus.eu/en/products/urban-atlas ; CLCplus Backbone https://land.copernicus.eu/en/products/clc-backbone                                                                                                                                                                                                                            |

Table 3 – used data, and alternative datasets to replicate the assessment outside the study area, when available

**Storm surge and Climate change effects**

> The storm surge scenarios are selected following the IPCC 8.5 climate prognosis for return periods of 5, 10, 20, 50 and 100 years in 2022 and 2100. The sea level rise (in cm) is estimated for each scenario in the following table:

Table 4 - Overview of storm surge data applied for risk assessment.

The flood hazard workflow for the Vejrup Å catchment relies on a combination of GIS platforms and flood modelling tools (Table 2). GIS software provides the core environment for integrating elevation, land-use, and exposure datasets, producing flood maps and supporting spatial analysis.

For the simulation of coastal flooding from storm surge and sea level rise, both proprietary and open-source tools can be used.

The choice of tool depends on data availability, licensing, and the level of detail required, but in all cases the outputs include flood extent and depth maps that support municipal adaptation planning and evaluation of mitigation measures.

| Tool                                                      | Type        | Role                                                                                                 |
| --------------------------------------------------------- | ----------- | ---------------------------------------------------------------------------------------------------- |
| [QGIS](https://qgis.org/)                                 | Open        | Core environment for GIS analysis, map production, overlay of hazard and exposure layers             |
| [Scalgo Live](https://scalgo.com/)                        | Proprietary | Simulate surface water dynamics and map flood-prone areas across the catchment                       |
| [SaferPlaces](https://saferplaces.co/)                    | Proprietary | Simulate surface water dynamics and map flood-prone areas across the catchment, include damage model |
| [ANUGA](https://anuga.anu.edu.au/?utm_source=chatgpt.com) | Open        | Open-source hydrodynamic model for simulating coastal inundation (storm surge, tsunami, wave run-up) |

Table 2 – tools and role in the Coastal Flood Hazard workflow

#### Methodology

{% stepper %}
{% step %}
### Data acquisition and preparation

High-resolution LiDAR-based DEM (0.4 m, Figure 2) from the national geoportal forms the base for flood simulations. Coastal protection features (dikes, pumping stations) and building footprints from the same source may be added to refine topography and capture actual status.

{% hint style="info" %}
When using very high-resolution LiDAR DEMs (e.g. 0.4 m), the data can become too heavy for hydraulic modelling. A practical solution is to downsample to 1–2 m resolution, which is still reasonable for flood modelling. This can be done through mosaicking and resampling in GIS software (e.g. QGIS) or by using command-line tools such as GDAL.
{% endhint %}

Example GDAL command (resampling / mosaicking):

{% code title="gdalwarp downsample example" %}
```bash
gdalwarp --config GDAL_NUM_THREADS ALL_CPUS -r bilinear -tr 1,2 1,2 -t_srs EPSG:25832 -co COMPRESS=LZW -co BIGTIFF=YES -co PREDICTOR=2 c:/folder1/*.tif c:/folder1/mosaic.tif
```
{% endcode %}

Figure 2 – example of Lidar DTM along the coast from GeoDanmark geoportal (down sampled @ 1.2 m) compared to satellite map. Obstacles such as buildings and trees are filtered from the terrain surface. Underwater topography is not represented.

Additional notes:

* High-resolution LiDAR-based DEM (0.4 m) from SDFI provides the elevation base for coastal flood simulations.
* Hydrological forcing is defined by **storm surge and sea level rise scenarios** following IPCC RCP 8.5 for 2022–2100, with return periods of 5, 10, 20, 50, and 100 years (Table 4). These scenarios set the boundary conditions for marine inundation.
* **Land-use layers** (agriculture, urban, restoration areas), together with building footprints and municipal planning data, are added in GIS to represent ongoing conversions into business districts or nature restoration (wetlands and salt marshes) and actual “ante operam” status.
* **Coastal protection structures** such as dikes and levees, along with critical infrastructure, must also be included in the model. Where no ready-to-use geospatial layers exist, these features can be digitized manually in GIS to ensure that protective capacity is correctly represented.
{% endstep %}

{% step %}
### Model setup and run

The coastal flood model is configured using the prepared DEM, storm surge levels, and sea level rise increments. Using the flood modelling tool of choice (see Table 2), storm surge return periods (e.g. 5, 10, 20, 50, 100 years), possibly worsened to consider sea level rise projections in climate change conditions (Table 4), are combined to delineate areas below the water thresholds.

Building footprints, land-use layers, and coastal protection structures are integrated in the simulation to ensure that exposure and defences are correctly represented.

Typical model outputs:

* Raster/vector classified flood maps by depth range (e.g. <25 cm, 25–50 cm, 50–100 cm, >100 cm)
* Maps by return period showing inundation extent and water depth

These outputs enable a first evaluation of coastal flood hazard and form the basis for overlay with land use and planning data in the following step.

Figure 3 – example of large, flooded area with 10 cm marine water by a 100-year storm surge in 2100 in Odense Fjord catchment area.

Figure 4 – example of detailed coastal flood inundation model for actual (T100, 1.72 m a.s.l.) and projected (T100 2100, 2.52 m a.s.l.) surge conditions (courtesy of [SaferPlaces](https://saferplaces.co/rimini-and-climate-change-the-added-value-of-the-sea-park-parco-del-mare/)).
{% endstep %}

{% step %}
### Analysis and interpretation

Flood extent and depth maps generated in the model run are imported into GIS for post-processing and interpretation. The results are overlaid with land-use layers, municipal planning zones, and building footprints to identify which categories of land and infrastructure are most affected under different storm surge scenarios.

The classification of flood depth ranges (e.g. <25 cm, 25–50 cm, 50–100 cm, >100 cm) supports the identification of vulnerability hotspots. By intersecting hazard outputs with agriculture, commercial areas, residential zones, and planned restoration sites, it is possible to estimate which surfaces and assets are exposed and also generate simple spatial statistics as the key indicators mentioned in Table 1.

Although a full damage model is not implemented in this tutorial, the analysis provides a **qualitative assessment of potential flood damage**, based on the overlap between flood maps and land-use categories. This forms the basis for future extensions where depth–damage curves could translate hazard into economic loss estimates.

{% hint style="info" %}
Note: All modelling suites can be complemented with damage estimation modules. These typically require intersecting flood hazard outputs (e.g. water depth rasters) with asset value layers and applying water depth–damage curves. This can be performed, when not embedded in the flood assessment tool, separately within the GIS environment or via external models.
{% endhint %}

For an advanced implementation of this methodology, including regionalized vulnerability functions, see for example:

* Amadio, M., Essenfelder, A.H., Bagli, S., … Mysiak, J., Roberts, S. (2022). Cost-benefit analysis of coastal flood defence measures in the North Adriatic Sea. Natural Hazards and Earth System Sciences, 22(1), pp. 265–286. https://doi.org/10.5194/nhess-22-265-2022
{% endstep %}
{% endstepper %}
