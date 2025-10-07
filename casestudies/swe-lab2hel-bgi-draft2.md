# swe lab2hel bgi draft2

### Introduction and Objectives of the Climate Risk Assessment

#### Regional context

Helsingborg Municipality (https://en.wikipedia.org/wiki/Helsingborg\_Municipality), located in the Skåne region of southern Sweden, includes urban, peri-urban, and agricultural landscapes shaped by a network of small streams, culverts, and historical wetlands. The municipality and its upstream catchments face increasing risks from pluvial flooding, high flows, and extreme rainfall events, driven by changing climate patterns. Urban expansion and infrastructure have fragmented ecological corridors, reducing connectivity between key ecological value cores such as wetlands, swamp forests, and deciduous forests. At the same time, protected areas, including Natura 2000 sites, and existing ecological assets provide opportunities for targeted Blue-Green Infrastructure (BGI) interventions. These can mitigate flood risks, restore hydrological continuity, and strengthen ecological resilience at the catchment scale.

Figure 1 - Location of the Helsingborg municipality in Skåne.

#### Scope of the tutorial

This tutorial presents a replicable Climate Risk Assessment (CRA) workflow for identifying optimal locations for Blue-Green Infrastructure (BGI) in Helsingborg. The focus is on nature-based measures—such as [two-stage ditches](https://knowledge4policy.ec.europa.eu/publication/ritobacken_en), floodplains, and [wetland restoration](https://climate-adapt.eea.europa.eu/en/metadata/case-studies/urban-storm-water-management-in-augustenborg-malmo) (Figure 2)—that can both mitigate flooding and enhance ecological connectivity. The GIS-based approach combines hydrological and ecological spatial datasets, including flood hazard layers, depressions, historical wetlands, and ecological value cores, to identify multifunctional priority areas. The method supports integration of BGI into local and regional adaptation strategies, providing decision-makers with spatially explicit, evidence-based guidance for restoration planning under current and future climate conditions.

{% hint style="info" %}
Disclaimer

This tutorial is intended as a general workflow example and does not replace software-specific documentation (e.g., GIS, hydrological, hydraulic tools user/technical manuals). Users should already be familiar with the relevant geospatial data formats, data pre-processing techniques, and modelling concepts applicable to their hazard of interest (e.g., flood mapping), as well as with the specific input/output requirements and run functionalities of the modelling software before attempting to replicate this workflow.
{% endhint %}

Figure 2 - Illustration of two-stage ditches in Helsingborg and vegetation in a ditch (top), and Blue-green corridors in the agricultural landscape in Helsingborg municipality (bottom)

#### CRA objectives

The Helsingborg CRA aims to:

* Identify priority sites for BGI that address both pluvial and fluvial flood risks while improving ecological connectivity.
* Link ecological value cores—including wetlands, swamp forests, and deciduous forests—through restored corridors along streams and culverts.
* Integrate hydrological and ecological criteria to select multifunctional intervention areas, prioritising locations with overlapping flood vulnerability and restoration potential.
* Support planning and policy by providing spatial evidence for land-use strategies, climate adaptation plans, and ecological restoration projects.
* Enable replication of the workflow in other regions by relying on GIS-based analysis and datasets that have open or EU-wide equivalents.

#### Intended users

The CRA results are intended for local and regional policymakers, municipal planners, and environmental authorities responsible for climate adaptation and ecological management in Helsingborg. They provide spatial guidance for:

* Strategic land-use planning and flood risk reduction.
* Implementation of targeted nature-based solutions and restoration projects.
* Integration of ecological connectivity into urban and regional planning frameworks.

Stakeholders such as water management agencies, conservation organisations, and infrastructure planners can also use the outputs to prioritise interventions that deliver combined hydrological and ecological benefits.

### Flood mitigation and Ecological Resilience – Helsingborg

#### Description and context

Helsingborg and its upstream catchments are exposed to pluvial flooding and high flows during extreme rainfall events, which threaten urban areas, agricultural land, and ecological assets. The combination of impervious urban surfaces, altered watercourses, and fragmented ecological corridors increases runoff and reduces natural retention capacity. Historical wetlands, low-lying depressions, and designated floodplain restoration areas offer opportunities to restore hydrological functions. Strategic Blue-Green Infrastructure (BGI) interventions—such as two-stage ditches, floodplain reconnection, and wetland creation—can mitigate flood risks while enhancing ecological connectivity between key value cores. This dual focus supports climate adaptation by improving water balance and strengthening landscape-scale ecological networks. The workflow includes mapping hazard-prone areas, evaluating current and potential connectivity of habitats, and prioritising interventions that deliver both climate adaptation and biodiversity benefits.

| Dimension                    | Indicator(s)                                                                              |                Unit | Purpose                                                                                               |
| ---------------------------- | ----------------------------------------------------------------------------------------- | ------------------: | ----------------------------------------------------------------------------------------------------- |
| Flood extent and water depth | Flood extent and water depth, linked to event intensity (return period, climate scenario) |              km², m | Identify flood-prone areas, inform mitigation strategies, and assess changes after BGI implementation |
| Ecological connectivity      | Overlap zones between flood-risk areas and ecological value cores / linkages              | N/A, visual overlay | Locate multifunctional zones where BGI can reduce flood impacts and improve habitat connectivity      |

Table 1 – key indicators tracked.

#### Data sources and tools

The CRA uses high-resolution topographic, hydrological, and ecological datasets from regional and national geoportals, complemented by thematic data from specialised agencies. Core inputs include LiDAR-based DEMs (Figure 3), rainfall and flow statistics, flood hazard maps, historical wetland inventories, ecological value core layers, and Natura 2000 boundaries. Flood modelling tools support data processing and visualization, both proprietary and free to use to foster replication in other contexts.

The table below summarizes key datasets, their role in the workflow, and potential open or EU-wide equivalents for transferability:

| **Data Type**                                                    | **Source**                  | **Role in Workflow**                                                                                    | **Open/EU Alternative**                                                                                                                                                                                                                                                                                                                                                                                                 |
| ---------------------------------------------------------------- | --------------------------- | ------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| LiDAR-based DEM                                                  | Regional/National Geoportal | Detect surface depressions, analyse micro-topography for flood accumulation and ecological connectivity | Copernicus DEM - Global and European Digital Elevation Model [(open – raster 30m, 10m for selected users)](https://dataspace.copernicus.eu/explore-data/data-collections/copernicus-contributing-missions/collections-description/COP-DEM)                                                                                                                                                                              |
| Rainfall map by return period                                    | Vattenatlas                 | Input for pluvial flood modelling and hazard mapping                                                    | ERA5 [extreme precipitation indicators](https://cds.climate.copernicus.eu/datasets/sis-european-risk-extreme-precipitation-indicators?tab=overview)                                                                                                                                                                                                                                                                     |
| Extreme and maximum flow data                                    | MSB; Vattenatlas            | Peak river flow estimation under design scenarios                                                       | Copernicus Climate Data store [“Hydrology-related climate impact indicators from 1970 to 2100 derived from bias adjusted European climate projections”](https://cds.climate.copernicus.eu/datasets/sis-hydrology-variables-derived-projections?tab=download)                                                                                                                                                            |
| Historical wetlands                                              | Vattenatlas                 | Identify potential restoration areas and historical flood retention zones                               | Copernicus [Land Cover 2020 (raster 10 m), global, annual - version 1](https://land.copernicus.eu/en/products/global-dynamic-land-cover/land-cover-2020-raster-10-m-global-annual), includes wetlands delineation                                                                                                                                                                                                       |
| Potential floodplain restoration                                 | County Administrative Board | Support planning for natural flood retention measures                                                   | No EU-wide equivalent (context-specific)                                                                                                                                                                                                                                                                                                                                                                                |
| Water connectivity links                                         | County Administrative Board | Identify hydrological corridors and link ecological value cores                                         | [EU-Hydro River Network Database 2006-2012 (vector), Europe](https://land.copernicus.eu/en/products/eu-hydro)                                                                                                                                                                                                                                                                                                           |
| Catchment boundaries                                             | County Administrative Board | Provide spatial reference for hydrological and ecological analysis                                      | [EU-Hydro River Network Database 2006-2012 (vector), Europe](https://land.copernicus.eu/en/products/eu-hydro)                                                                                                                                                                                                                                                                                                           |
| Ecological value cores – deciduous forest, swamp forest, wetland | County Administrative Board | Locate existing high-value ecosystems for connectivity planning                                         | <p>Copernicus High Resolution Layer: <a href="https://land.copernicus.eu/en/products/high-resolution-layer-forests-and-tree-cover">High Resolution Layer Tree Cover and Forests</a><br>Copernicus <a href="https://land.copernicus.eu/en/products/global-dynamic-land-cover/land-cover-2020-raster-10-m-global-annual">Land Cover 2020 (raster 10 m), global, annual - version 1</a>, includes wetlands delineation</p> |
| Natura 2000 sites                                                | County Administrative Board | Identify legally protected ecological zones                                                             | EEA Natura 2000 Database ([vector, Europe-wide](https://www.eea.europa.eu/data-and-maps/data/natura-14/natura-2000-spatial-data))                                                                                                                                                                                                                                                                                       |

Table 3 – used data, and alternative datasets to replicate the assessment outside the study area when available.

{% hint style="info" %}
Climate change effects in hydrological extremes

Although the current workflow does not incorporate official climate projections, a first approximation of future flood hazards, if not available from local studies, may be derived using open datasets from the Copernicus Climate Data Store. These include bias-adjusted impact indicators such as daily river discharge extremes under different climate scenarios (e.g. RCP 8.5).

A practical example of this approach has been implemented [here](https://www.euspa.europa.eu/newsroom-events/success-stories/copernicus-hydropower-flood-assessments) for a hydropower site in Switzerland, where Copernicus climate projections, coupled with limited gauging station statistics for basic downscaling, were used to estimate future 100-year flood discharges and run simplified hydraulic simulations to assess potential downstream impacts.
{% endhint %}

Figure 3 – example of LiDAR DTM, one of the main drivers of flood risk assessment for the Helsingborg area compared to satellite map; obstacles such as buildings and trees are filtered from the DTM surface.

The workflow combines proprietary and open-source tools for GIS processing, flood hazard analysis, and hydrological-ecological connectivity mapping. Proprietary platforms are used for advanced analysis and visualisation, while open-source alternatives have been identified so that the method can be replicated in other contexts:

| Tool                                                                         | Type        | Role in Workflow                                                                                                                                                                                                                                              |
| ---------------------------------------------------------------------------- | ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [ArcGIS Pro](https://www.esri.com/en-us/arcgis/products/arcgis-pro/overview) | Proprietary | GIS platform for overlaying ecological and flood layers, digitising connectivity corridors, and producing BGI priority maps                                                                                                                                   |
| [QGIS](https://qgis.org/)                                                    | Open        | Open alternative for overlaying ecological and flood layers, digitising connectivity corridors, and producing BGI priority maps                                                                                                                               |
| [Scalgo Live](https://scalgo.com/)                                           | Proprietary | Visualises surface water accumulation, identifies depressions and overland flow paths under heavy rainfall or high flow scenarios. Generates base flood hazard layers (e.g. 100-year rainfall, low points, extreme flows) used to delineate flood-prone areas |
| [SaferPlaces](https://saferplaces.co/)                                       | Proprietary | Visualises surface water accumulation, identifies depressions and overland flow paths under heavy rainfall or high flow scenarios. Generates base flood hazard layers (e.g. 100-year rainfall, low points, extreme flows) used to delineate flood-prone areas |
| [TauDEM](https://hydrology.usu.edu/taudem/taudem5/)                          | Open        | Topographic analysis for flow paths and watershed delineation                                                                                                                                                                                                 |
| [HEC-RAS](https://www.hec.usace.army.mil/software/hec-ras/download.aspx)     | Open        | Hydraulic modelling for flood scenarios, estimation of flood extent and water depth                                                                                                                                                                           |

Table 2 – used tools and role in the workflow; where available, a free similar alternative to proprietary solutions is provided.

#### Methodology

{% stepper %}
{% step %}
### Data acquisition and preparation

Gather and prepare all spatial datasets needed for the analysis, ensuring they share the same projection (identified by a unique EPSG code, like [3006](https://epsg.io/3006) for the example) and are clipped to the extent of the area of interest (e.g., Helsingborg Municipality including its upstream contributing catchments).

Key inputs and checks:

* High-resolution topography from a LiDAR-based DEM to identify surface depressions, micro-topography features, and potential flow accumulation zones (Copernicus DEM as alternative if LiDAR unavailable).
* Rainfall maps for different return periods and extreme flow statistics (e.g., MSB, Vattenatlas).
* Official flood hazard maps for selected return periods if available; otherwise produce using hydraulic/hydrological modelling tools.
* Ecological datasets: value cores for wetlands, swamp forests, deciduous forests, Natura 2000 sites, water connectivity links, historical wetlands, and designated floodplain restoration areas.
* Contributing catchment boundaries for hydrological unit referencing.

Ensure resolution consistency, format compatibility, and attribute completeness. When national datasets are not available, use the open/EU alternatives listed earlier.

{% hint style="warning" %}
Domain extent

Adopting the full contributing catchment as model domain may result in an excessively large computational extent. Consider first performing a hydrological assessment of peak discharges / flood waves to restrict the hydraulic risk model to areas actually affected by flooding and targeted for Nature-Based Solutions. This reduces DEM inputs and computational load without compromising relevance.
{% endhint %}
{% endstep %}

{% step %}
### Model setup and run

Simulate flood processes to locate where hydraulic risk overlaps ecological opportunity. Start with terrain morphology analyses to pinpoint depressions, low-lying storage zones, and overland main flow pathways using flow direction and accumulation computations.

Approaches:

* 0D (zero-dimensional) methods: identify storage zones and retention areas solely from terrain input; suitable for rapid assessments or limited computational resources (e.g., urban flash floods).
* 2D inundation models: where higher detail is possible, use two-dimensional hydraulic modelling of river channels and adjacent flood-prone areas.

Produce flood hazard layers representing extent and water depth for target return periods (e.g., 10-, 50-, 100-year events). Use morphological outputs (flow paths, depressions, temporary storage zones) overlaid in GIS to obtain initial spatial indications of suitable BGI locations.

Example illustrations: depression detection, flow paths, and flood zones obtained via flood modelling tools.
{% endstep %}

{% step %}
### Ecological connectivity mapping and priority area selection

Integrate ecological structures by combining ecological value cores (wetlands, swamp forests, deciduous forests) with water connectivity links to identify existing nodes and corridors. Where gaps exist, sketch potential connections along streams, ditches, or culverts.

Overlay ecological networks with flood-related outputs from the modelling step. Prioritise polygons where:

* Depressions, historical wetlands, or high-flow zones overlap with ecological corridors.
* Significant storage potential coincides with proximity to existing ecological value cores or known flood pathways.

Digitise selected polygons into a dedicated GIS layer (e.g., “BGI intervention opportunities”) and attribute each polygon with characteristics such as approximate storage volume, connectivity function, and degree of overlap with hazard zones.

Output: spatially explicit shortlist of candidate sites where BGI measures can deliver combined benefits for flood mitigation and ecological resilience.
{% endstep %}

{% step %}
### Hydraulic re-simulation and performance assessment of proposed BGI sites

Test candidate intervention areas by incorporating proposed BGI polygons (wetlands, two-stage ditches, restored floodplains) into the hydraulic simulation domain. Assign simplified hydraulic properties to each intervention area (indicative storage volume, infiltration capacity, connectivity to flow paths).

Re-run hydraulic models for the same flood scenarios including the BGI elements. Compare outputs to baseline to quantify changes in flood extent and depth. Typical performance indicators:

* Reduction in flooded area.
* Decrease in maximum water depth within buffer zones.
* Total volume of water retained.

Store results as attributes within the BGI polygons layer to create a spatial database of intervention benefits. Repeat for multiple return periods or climate scenarios where needed to evaluate robustness. Use results for multi-criteria ranking combining hydrological performance and ecological connectivity.

References:

* https://www.mdpi.com/2073-4441/12/6
{% endstep %}
{% endstepper %}

Figure 4 – example map showing value cores and connectivity map obtained via GIS overlaying of key layers.

Figure 5 – example of depression detection via raster-based analysis of DTM (courtesy of SaferPlaces)

Figure 6 – examples of flow paths and flood zones detected via flood modelling tools and overlaid in the GIS environment.

Figure 7 – Example of 2D flood model of a flood volume upstream of an urban area (courtesy of SaferPlaces)

References

* https://www.mdpi.com/2073-4441/12/6
