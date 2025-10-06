## Introduction and Objectives of the Climate Risk Assessment

### Regional context.

](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/SWE-Lab2Hel_BGi_draft2_media/media/image1.png)[Helsingborg
Municipality](https://en.wikipedia.org/wiki/Helsingborg_Municipality),
located in the Skåne region of southern Sweden, includes urban,
peri-urban, and agricultural landscapes shaped by a network of small
streams, culverts, and historical wetlands. The municipality and its
upstream catchments face increasing risks from pluvial flooding, high
flows, and extreme rainfall events, driven by changing climate patterns.
Urban expansion and infrastructure have fragmented ecological corridors,
reducing connectivity between key ecological value cores such as
wetlands, swamp forests, and deciduous forests. At the same time,
protected areas, including Natura 2000 sites, and existing ecological
assets provide opportunities for targeted Blue-Green Infrastructure
([BGI](https://www.sciencedirect.com/science/article/abs/pii/S0040162520313548))
interventions. These can mitigate flood risks, restore hydrological
continuity, and strengthen ecological resilience at the catchment scale.

Figure 1 - Location of the Helsingborg municipalitiy s in Skåne.

### Scope of the tutorial.

This tutorial presents a replicable Climate Risk Assessment (CRA)
workflow for identifying optimal locations for Blue-Green Infrastructure
(BGI) in Helsingborg. The focus is on nature-based measures—such as
[two-stage
ditches](https://knowledge4policy.ec.europa.eu/publication/ritobacken_en),
floodplains, and [wetland
restoration](https://climate-adapt.eea.europa.eu/en/metadata/case-studies/urban-storm-water-management-in-augustenborg-malmo)
(Figure 2) that can both mitigate flooding and enhance ecological
connectivity. The GIS-based approach combines hydrological and
ecological spatial datasets, including flood hazard layers, depressions,
historical wetlands, and ecological value cores, to identify
multifunctional priority areas. The method supports integration of BGI
into local and regional adaptation strategies, providing decision-makers
with spatially explicit, evidence-based guidance for restoration
planning under current and future climate conditions.

  - #### Disclaimer

> This tutorial is intended as a general workflow example and does not
> replace software-specific documentation (e.g., GIS, hydrological,
> hydraulic tools user/technical manuals). Users should already be
> familiar with the relevant geospatial data formats, data
> pre-processing techniques, and modelling concepts applicable to their
> hazard of interest (e.g., flood mapping.), as well as with the
> specific input/output requirements and run functionalities of the
> modelling software before attempting to replicate this workflow

](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/SWE-Lab2Hel_BGi_draft2_media/media/image3.jpeg)

Figure 2 - Illustration of two-stage ditches in Helsingborg and
vegetation in a ditch (top) , and Blue-green corridors in the
agricultural landscape in Helsingborg municipality (bottom)

### CRA objectives.

The Helsingborg CRA aims to:

  - **Identify priority sites** for BGI that address both pluvial and
    fluvial flood risks while improving ecological connectivity.

  - **Link ecological value cores**—including wetlands, swamp forests,
    and deciduous forests—through restored corridors along streams and
    culverts.

  - **Integrate hydrological and ecological criteria** to select
    multifunctional intervention areas, prioritising locations with
    overlapping flood vulnerability and restoration potential.

  - **Support planning and policy** by providing spatial evidence for
    land-use strategies, climate adaptation plans, and ecological
    restoration projects.

  - **Enable replication** of the workflow in other regions by relying
    on GIS-based analysis and datasets that have open or EU-wide
    equivalents.

### Intended Users

The CRA results are intended for local and regional policymakers,
municipal planners, and environmental authorities responsible for
climate adaptation and ecological management in Helsingborg. They
provide spatial guidance for:

  - Strategic land-use planning and flood risk reduction.

  - Implementation of targeted nature-based solutions and restoration
    projects.

  - Integration of ecological connectivity into urban and regional
    planning frameworks.

Stakeholders such as water management agencies, conservation
organisations, and infrastructure planners can also use the outputs to
prioritise interventions that deliver combined hydrological and
ecological benefits.

## Flood mitigation and Ecological Resilience – Helsingborg

### Description and context

Helsingborg and its upstream catchments are exposed to pluvial flooding
and high flows during extreme rainfall events, which threaten urban
areas, agricultural land, and ecological assets. The combination of
impervious urban surfaces, altered watercourses, and fragmented
ecological corridors increases runoff and reduces natural retention
capacity. Historical wetlands, low-lying depressions, and designated
floodplain restoration areas offer opportunities to restore hydrological
functions. Strategic Blue-Green Infrastructure (BGI) interventions—such
as two-stage ditches, floodplain reconnection, and wetland creation—can
mitigate flood risks while enhancing ecological connectivity between key
value cores. This dual focus supports climate adaptation by improving
water balance and strengthening landscape-scale ecological network. This
includes mapping hazard-prone areas, evaluating current and potential
connectivity of habitats, and prioritising interventions that deliver
both climate adaptation and biodiversity benefits.

| **Dimension**                | **Indicator(s)**                                                                          | **Unit**            | **Purpose**                                                                                           |
| ---------------------------- | ----------------------------------------------------------------------------------------- | ------------------- | ----------------------------------------------------------------------------------------------------- |
| Flood extent and water depth | Flood extent and water depth, linked to event intensity (return period, climate scenario) | km², m              | Identify flood-prone areas, inform mitigation strategies, and assess changes after BGI implementation |
| Ecological connectivity      | Overlap zones between flood-risk areas and ecological value cores / linkages              | N/A, visual overlay | Locate multifunctional zones where BGI can reduce flood impacts and improve habitat connectivity      |

Table 1 – key indicators tracked.

### Data sources and tools

The CRA uses high-resolution **topographic, hydrological, and ecological
datasets** from regional and national geoportals, complemented by
thematic data from specialised agencies. Core inputs include LiDAR-based
DEMs (Figure 2), rainfall and flow statistics, flood hazard maps,
historical wetland inventories, ecological value core layers, and Natura
2000 boundaries. Flood modelling tools support data processing and
visualization, both proprietary and free to use to foster replication in
other contexts.

The table below summarizes key datasets, their role in the workflow, and
potential open or EU-wide equivalents for transferability:

<table>
<thead>
<tr class="header">
<th><strong>Data Type</strong></th>
<th><strong>Source</strong></th>
<th><strong>Role in Workflow</strong></th>
<th><strong>Open/EU Alternative</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>LiDAR-based DEM</td>
<td>Regional/National Geoportal</td>
<td>Detect surface depressions, analyse micro-topography for flood accumulation and ecological connectivity</td>
<td>Copernicus DEM - Global and European Digital Elevation Model <a href="https://dataspace.copernicus.eu/explore-data/data-collections/copernicus-contributing-missions/collections-description/COP-DEM"><span class="underline">(open – raster 30m, 10m for selected users)</span></a></td>
</tr>
<tr class="even">
<td>Rainfall map by return period</td>
<td>Vattenatlas</td>
<td>Input for pluvial flood modelling and hazard mapping</td>
<td>ERA5 <a href="https://cds.climate.copernicus.eu/datasets/sis-european-risk-extreme-precipitation-indicators?tab=overview">extreme precipitation indicators</a></td>
</tr>
<tr class="odd">
<td>Extreme and maximum flow data</td>
<td>MSB; Vattenatlas</td>
<td>Peak river flow estimation under design scenarios</td>
<td>Copernicus Climate Dat store <a href="https://cds.climate.copernicus.eu/datasets/sis-hydrology-variables-derived-projections?tab=download">“Hydrology-related climate impact indicators from 1970 to 2100 derived from bias adjusted European climate projections”</a></td>
</tr>
<tr class="even">
<td>Historical wetlands</td>
<td>Vattenatlas</td>
<td>Identify potential restoration areas and historical flood retention zones</td>
<td>Copernicus <a href="https://land.copernicus.eu/en/products/global-dynamic-land-cover/land-cover-2020-raster-10-m-global-annual">Land Cover 2020 (raster 10 m), global, annual - version 1</a>, includes wetlands delineation</td>
</tr>
<tr class="odd">
<td>Potential floodplain restoration</td>
<td>County Administrative Board</td>
<td>Support planning for natural flood retention measures</td>
<td>No EU-wide equivalent (context-specific)</td>
</tr>
<tr class="even">
<td>Water connectivity links</td>
<td>County Administrative Board</td>
<td>Identify hydrological corridors and link ecological value cores</td>
<td><a href="https://land.copernicus.eu/en/products/eu-hydro">EU-Hydro River Network Database 2006-2012 (vector), Europe</a></td>
</tr>
<tr class="odd">
<td>Catchment boundaries</td>
<td>County Administrative Board</td>
<td>Provide spatial reference for hydrological and ecological analysis</td>
<td><a href="https://land.copernicus.eu/en/products/eu-hydro">EU-Hydro River Network Database 2006-2012 (vector), Europe</a></td>
</tr>
<tr class="even">
<td>Ecological value cores – deciduous forest, swamp forest, wetland</td>
<td>County Administrative Board</td>
<td>Locate existing high-value ecosystems for connectivity planning</td>
<td>Copernicus High Resolution Layer: <a href="https://land.copernicus.eu/en/products/high-resolution-layer-forests-and-tree-cover">High Resolution Layer Tree Cover and Forests</a><br />
Copernicus <a href="https://land.copernicus.eu/en/products/global-dynamic-land-cover/land-cover-2020-raster-10-m-global-annual">Land Cover 2020 (raster 10 m), global, annual - version 1</a>, includes wetlands delineation</td>
</tr>
<tr class="odd">
<td>Natura 2000 sites</td>
<td>County Administrative Board</td>
<td>Identify legally protected ecological zones</td>
<td>EEA Natura 2000 Database (<a href="https://www.eea.europa.eu/data-and-maps/data/natura-14/natura-2000-spatial-data">vector, Europe-wide</a>)</td>
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

](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/SWE-Lab2Hel_BGi_draft2_media/media/image9.png)

![Immagine che contiene Aerofotogrammetria, Vista aerea, mappa, aereo Il
contenuto generato dall'IA potrebbe non essere
corretto.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/SWE-Lab2Hel_BGi_draft2_media/media/image10.png)

Figure 3 – example of Lidar DTM, one of the main driver of flood risk
assessment, for Helsingborg area compared to satellite map; obstacles
such as buildings and trees are filtered from the DTM surface.

The workflow combines proprietary and open-source **tools** for GIS
processing, flood hazard analysis, and hydrological-ecological
connectivity mapping. Proprietary platforms are used for advanced
analysis and visualisation, while open-source alternatives have been
identified so that the method can be replicated in other contexts:

| **Tool**                                                                     | **Type**    | **Role in Workflow**                                                                                                                                                                                                                                          |
| ---------------------------------------------------------------------------- | ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [ArcGIS Pro](https://www.esri.com/en-us/arcgis/products/arcgis-pro/overview) | Proprietary | GIS platform for overlaying ecological and flood layers, digitising connectivity corridors, and producing BGI priority maps                                                                                                                                   |
| [<span class="underline">QGIS</span>](https://qgis.org/)                     | Open        | Open alternative for overlaying ecological and flood layers, digitising connectivity corridors, and producing BGI priority maps                                                                                                                               |
| [Scalgo Live](https://scalgo.com/)                                           | Proprietary | Visualises surface water accumulation, identifies depressions and overland flow paths under heavy rainfall or high flow scenarios. Generates base flood hazard layers (e.g. 100-year rainfall, low points, extreme flows) used to delineate flood-prone areas |
| [SaferPlaces](https://saferplaces.co/)                                       | Proprietary | Visualises surface water accumulation, identifies depressions and overland flow paths under heavy rainfall or high flow scenarios. Generates base flood hazard layers (e.g. 100-year rainfall, low points, extreme flows) used to delineate flood-prone areas |
| [TauDEM](https://hydrology.usu.edu/taudem/taudem5/)                          | Open        | Topographic analysis for flow paths and watershed delineation                                                                                                                                                                                                 |
| [HEC-RAS](https://www.hec.usace.army.mil/software/hec-ras/download.aspx)     | Open        | Hydraulic modelling for flood scenarios, estimation of flood extent and water depth                                                                                                                                                                           |

Table 2 – used tools and role in the workflow, when available a free
similar alternative to proprietary solutions is provided.

### Methodology

#### Step 1 - Data acquisition and preparation

The first stage of the workflow consists in gathering and **preparing
all spatial datasets** needed for the analysis, ensuring that they share
the **same projection** (identified by a unique EPSG code , like
[3006](https://epsg.io/3006) fort the example) **and are clipped** to
the extent of the area of interest( e.g. Helsingborg Municipality(
including and its upstream contributing catchments.

High-resolution **topography** from a LiDAR-based DEM (Figure 2)
provides the basis for identifying surface depressions, micro-topography
features, and potential flow accumulation zones; if unavailable, the
Copernicus DEM can serve as an alternative.

Hydrological inputs include rainfall maps for different return periods
and extreme flow statistics from sources (such as MSB and Vattenatlas),
which define the magnitude and frequency of flood scenarios. Where
available, official flood hazard maps—showing extent and depth for
selected return periods—should be loaded; otherwise, they can be
produced using compatible hydraulic or hydrological modelling tools.

**Ecological datasets**, including value cores for wetlands, swamp
forests, and deciduous forests, as well as Natura 2000 sites and **water
connectivity links** from the County Administrative Board, are then
added to capture biodiversity and connectivity priorities. Layers
showing historical wetlands and designated floodplain restoration areas
are included to identify locations with natural retention potential.
(Figure 2).

The **contributing catchment boundaries** provide a reference framework
for structuring the analysis at hydrological unit level. Before moving
forward, all layers should be checked for resolution consistency, format
compatibility, and completeness of attributes. When national datasets
are not available, equivalent open or EU-wide sources listed in the data
table can be used to replicate the process.

  - ##### Domain extent 

> *It should be noted, however, that adopting the full contributing
> catchment as model domain may result in an **excessively large
> computational extent.** In such cases, it is advisable to first
> perform a hydrological assessment of peak discharges / flood waves in
> the modelled river, so that the hydraulic risk model can be restricted
> to the areas actually affected by flooding and targeted for
> Nature-Based Solutions. This approach avoids unnecessarily large DEM
> inputs and reduces computational load without compromising the
> relevance of the analysis.*

![Immagine che contiene mappa, testo, atlante Il contenuto generato
dall'IA potrebbe non essere
corretto.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/SWE-Lab2Hel_BGi_draft2_media/media/image11.jpeg)

Figure 4 example map showing value cores and connectivity map obtained
via GIS overlaying of key layers.

#### Step 2 - Model setup and run.

Once spatial data are in place, the key task is to **simulate flood
processes** to locate where hydraulic risk overlaps ecological
opportunity. The procedure begins with **terrain morphology analysis to
pinpoint depressions, low-lying storage zones, and overland main flow
pathways** easily activated during high-flow conditions. This can be
achieved using hydro morphological tools that compute flow direction,
accumulation, and potential storage segmentations.

These analyses are directly applicable in simplified, zero-dimensional
(0D) modelling approaches, where storage zones and flood retention areas
are identified based solely on terrain input—no need for complex
hydraulic simulations. Such 0D methods are often employed to represent,
beside simplified flood models, also rapid, intense rainfall events
(e.g., urban flash floods), and are useful when computational resources
are limited or rapid assessments are needed (\[1\]).

Example of depression delineating using terrain morphology analysis in
reported in (Figure 3)

![Immagine che contiene mappa Il contenuto generato dall'IA potrebbe non
essere
corretto.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/SWE-Lab2Hel_BGi_draft2_media/media/image12.png)

Figure 5 – example of depression detection via raster-based analysis of
DTM (courtesy of [SaferPlaces](https://saferplaces.co/))

The initial morphological analysis already provides valuable insight
into potential intervention areas. By extracting flow directions and
delineating depressions or temporary storage zones from the DEM, it is
possible to generate maps of flow paths and inundation-prone areas. When
these outputs are overlaid in the GIS environment, they offer a first
spatial indication of where Blue-Green Infrastructure could be located
to maximise retention capacity and align with natural hydrological
processes (Figure 4).

![Immagine che contiene testo, mappa, atlante, schermata Il contenuto
generato dall'IA potrebbe non essere
corretto.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/SWE-Lab2Hel_BGi_draft2_media/media/image13.png)

![Immagine che contiene mappa, testo, atlante Il contenuto generato
dall'IA potrebbe non essere
corretto.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/SWE-Lab2Hel_BGi_draft2_media/media/image14.jpeg)

Figure 6 example of Flow paths and flood zones detection via Flood
Modeling tools, overlayed in GIS environment to base maps.

Next, flood hazard layers representing extent and water depth for target
return periods (e.g., 10-, 50-, 100-year events).

If hydraulic simulation is carried out, the choice of modelling approach
should reflect both the availability of topographic information and the
computational resources at hand. In some cases, a very simple
scheme—such as the zero-dimensional (0D) approach introduced earlier,
based on storage areas and flood routing—may be sufficient. Where higher
detail is possible, the analysis can instead rely on more refined
methods, such as a two-dimensional inundation model of the river channel
and adjacent flood-prone areas.

![Immagine che contiene mappa, testo Il contenuto generato dall'IA
potrebbe non essere
corretto.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/SWE-Lab2Hel_BGi_draft2_media/media/image15.png)

Figure 7 - Example of 2D flood model of a flood volume upstream of an
urban area (courtesy of [SaferPlaces](https://saferplaces.co/))

#### Step 3: Ecological connectivity mapping and priority area selection

At this stage, the analysis shifts from purely hydrological aspects to
the i**ntegration of ecological structures.** The first step is to
combine the official **ecological value cores—such as wetlands, swamp
forests, and deciduous forests—with the water connectivity links**
provided by the County Administrative Board. This allows the
identification of existing ecological nodes and corridors across the
landscape. Where gaps exist, new potential connections can be drawn
manually along streams, ditches, or culverts, thereby sketching a
conceptual network that could restore or reinforce continuity.

The next step is to ove**rlay this ecological layer with the
flood-related outputs prepared in Step 2.** Particular attention is
given to areas where depressions, historical wetlands, or high-flow
zones overlap with ecological corridors, since these locations represent
multifunctional opportunities: they can serve as flood retention areas
while simultaneously strengthening habitat connectivity.

Priority **should be given to polygons where several favourable
conditions coincide**—for example, significant storage potential in a
depression, proximity to existing ecological value cores, or alignment
with known flood pathways. These areas could then be **digitised into a
dedicated GIS layer**, (e.g. “BGI intervention opportunities.”)

Each polygon can be characterized with **basic attributes such as**
approximate storage volume, connectivity function, or degree of overlap
with hazard zones.

The outcome of this step is a **spatially explicit shortlist of
candidate sites where Blue-Green Infrastructure measures are most likely
to deliver combined benefits** for flood mitigation and ecological
resilience. This dataset will serve as the foundation for testing
hydraulic performance and ranking interventions in the following step.

#### 4 – Hydraulic Re-Simulation and Performance Assessment of Proposed BGI Sites

Once candidate intervention areas have been identified, the next step is
to test their potential effectiveness in reducing flood risk. This is
done by **incorporating** the proposed Blue-Green Infrastructure (BGI)
polygons—such a**s wetlands, two-stage ditches, or restored
floodplains—into the hydraulic simulation domain prepared in Step 2.**
Each intervention area is assigned **basic hydraulic properties**, for
example an indicative storage volume, infiltration capacity, or
connectivity to adjacent flow paths. These attributes are simplified but
sufficient to represent the effect of the intervention within the chosen
modelling framework.

The hydraulic model is then re-run under the same flood scenarios
previously simulated, this time including the BGI elements. The outputs
are compared against the baseline to quantify changes in flood extent
and depth. Ty**pical performance indicators include the reduction in
flooded area, the decrease in maximum water depth within a buffer zone,
or the total volume of water retained.** These results can be stored as
attributes within the GIS layer of BGI polygons, creating a spatially
explicit database of intervention benefits.

This procedure may be repeated for multiple return periods or climate
scenarios to evaluate the robustness of BGI measures under varying
conditions. The outcome is a ranked set of candidate sites, where
hydrological performance can be weighed together with ecological
connectivity benefits. Such basic multi-criteria assessment supports
decision-makers in prioritising those interventions that deliver the
highest combined resilience gains.

1.  <https://www.mdpi.com/2073-4441/12/6>
