## Introduction and Objectives of the Climate Risk Assessment

### Regional context.

The [Vejrup Å
catchment](https://www.sdu.dk/en/forskning/arcadia/about-arcadia/arcadia-in-funen/lab2),
located in eastern Funen within [Odense](https://english.odense.dk/) and
Municipality (with smaller parts in
[Kerteminde](https://en.wikipedia.org/wiki/Kerteminde_Municipality) and
[Faaborg-Midtfyn](https://www.fmk.dk/)), is mainly exposed **to coastal
flooding from Odense Fjord**.

The area north of Kerteminde road is undergoing major land-use
transitions: agricultural land is being converted into commercial
developments, while low-lying coastal zones are designated for wetland
and salt marsh restoration.

Municipal climate adaptation strategies, as set out in the **[Odense
Climate Adaptation
Plan](https://www.odense.dk/byens-udvikling/klima/klimatilpasning/klimatilpasningsplan)
(**Figure 1**)**, foresee the withdrawal of coastal protection up to the
Kerteminde road. This retreat strategy is promoted within the framework
of **Den grønne trepart** (a collaboration platform between
municipalities, state, and stakeholders) and is intended to create space
for restored wetlands and salt marshes. These measures are expected to
mitigate coastal flooding, reduce nutrient runoff to the fjord, and
support biodiversity.

![A map with text and a map with red dots AI-generated content may be
incorrect.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/DEN-Lab2Vej_draft2_media/media/image1.png)

Figure - Climate risk assessment map from Odense Municipality climate
adaptation plan 2024.

This approach reflects a broader institutional shift toward adaptive
land-use planning, where flood risk management, ecological restoration,
and urban development are coordinated to reduce **coastal squeeze**, cut
CO₂ emissions, and provide multiple benefits for local communities and
ecosystems.

### Scope of the tutorial.

This tutorial describes a replicable Climate Risk Assessment (CRA)
workflow for the Vejrup Å catchment, addressing coastal flood hazards
caused by sea level rise and storm surges. The workflow uses
high-resolution elevation data, storm surge scenarios, coastal flood
simulations, and land-use information to map current and future
inundation zones.

The approach supports local adaptation planning by testing both
nature-based and traditional solutions identified in the catchment, such
as wetland restoration, salt marsh creation, and coastal protection
structures. These interventions are assessed for their capacity to
reduce inundation extent and depth while enabling sustainable land-use
transitions. Designed for transferability, the tutorial combines
national datasets with open European sources, allowing replication in
other coastal lowlands facing similar risks.

  - #### Disclaimer

> This tutorial is intended as a general workflow example and does not
> replace software-specific documentation (e.g., GIS, hydrological, or
> coastal modelling tools user/technical manuals). Users should already
> be familiar with the relevant geospatial data formats, data
> pre-processing techniques, and modelling concepts applicable to flood
> hazard assessment, as well as with the specific input/output
> requirements and run functionalities of the modelling software before
> attempting to replicate this workflow.

### CRA objectives.

The CRA for the Vejrup Å catchment aims to:

  - Identify areas exposed to **coastal flooding** from sea level rise
    and storm surges under different return periods and climate
    projections.

  - Map inundation zones using high-resolution topography and coastal
    flood simulations to assess the extent and depth of flooding.

  - Highlight were **wetland restoration** and **salt marsh creation**,
    together with coastal protection structures, can reduce flood risk.

  - Support **municipal planning** by linking flood hazard maps with
    land-use strategies and by indicating zones suitable for business
    development or nature restoration.

  - Provide a spatial basis for future assessments of **economic
    damage**, moving from hazard mapping toward damage-based evaluation.
    *In this tutorial, this component is addressed only at a qualitative
    level through overlay of land-use with flood maps.*

### Intended users.

The CRA results are primarily addressed to **municipal planners and
officers** in Odense, Kerteminde, and Faaborg-Midtfyn, who are
responsible for integrating flood risk into land-use and climate
adaptation strategies. They are also relevant for regional
decision-makers engaged in frameworks such as [*Den grønne
trepart*](https://fvm.dk/arbejdsomraader/landbrug/groen-trepart), where
spatial strategies for adaptation are evaluated.

Stakeholders involved in the ongoing **land-use transition**—such as the
conversion of agricultural land into wetlands, salt marshes, or
commercial districts—can use the outputs to guide interventions and
assess their feasibility. In addition, **civil protection services** and
**infrastructure managers** benefit from **hazard maps** that identify
vulnerable assets and support the prioritisation of protective measures.

## Flood Hazard – coastal. 

### Description and context

The Vejrup Å catchment is mainly exposed to coastal flooding from Odense
Fjord, driven by sea level rise and storm surges. Large low-lying areas
north of Kerteminde road are particularly vulnerable and have been
designated for restoration into wetlands and salt marshes under the
**Odense Climate Adaptation Plan**.

Coastal flood events threaten agricultural land, planned commercial
districts, and critical infrastructure, with risks expected to increase
under projected climate scenarios (IPCC RCP 8.5).

To address these challenges, local strategies promoted through **Den
grønne trepart** envisage the withdrawal of coastal protection to
Kerteminde road and the use of nature-based solutions—such as wetland
and salt marsh creation—combined with structural defences where
necessary. The overall aim is to “make room for nature facing the
fjord,” reducing flood risk while supporting biodiversity, nutrient
retention, and CO₂ reduction.

This tutorial therefore focuses on the workflow for assessing coastal
flooding, mapping hazard zones, and exploring the effectiveness of
adaptive measures in reducing inundation extent and depth.

| **Dimension**              | **Indicator(s)**                                                                                                                                                                                                                                                                     | **Unit**                                         | **Purpose**                                                                                              |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------ | -------------------------------------------------------------------------------------------------------- |
| Flood extent & water depth | Flooded area and maximum water depth under different return periods (e.g. 10, 20, 100 years; with climate projection for 2100). Water depth also provides the basis for typical damage assessment, which in this tutorial is only mentioned qualitatively and not developed further. | km², m                                           | Identify flood-prone zones, quantify severity, and classify exposure levels                              |
| Flood damage (qualitative) | Exposure of different land-use categories to flooding; potential damage estimated either as flooded area by land-use class (m²) or via depth–damage curves if available                                                                                                              | m² by land-use type, or qualitative damage class | Provide a first approximation of potential damages and support integration with external economic models |

Table 1 – key indicators tracked-Flood Hazard

### Data sources and tools

Flood risk assessment in the Vejrup Å catchment is based on
high-resolution topography, storm surge scenarios, hydrological forcing,
and land-use datasets provided by national authorities. These datasets
allow the simulation of coastal and inland flooding under current and
projected conditions. Where local datasets are not available, equivalent
open European sources can be used to ensure transferability of the
workflow to other regions.

<table>
<thead>
<tr class="header">
<th><strong>Data type</strong></th>
<th><strong>Source (national)</strong></th>
<th><strong>Role in workflow</strong></th>
<th><strong>Open/EU alternative</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>LiDAR-based Digital Terrain model (0,4 m grid)</td>
<td><a href="https://dataforsyningen.dk/data/930">GeoDanmark</a></td>
<td>Elevation base for flood modelling; identifies depressions and flow paths</td>
<td>Copernicus DEM - Global and European Digital Elevation Model <a href="https://dataspace.copernicus.eu/explore-data/data-collections/copernicus-contributing-missions/collections-description/COP-DEM"><span class="underline">(open – raster 30m, 10m for selected users)</span></a></td>
</tr>
<tr class="even">
<td>Storm surge and sea level rise (Table 4).</td>
<td>Local/national studies, IPCC RCP scenarios (variable return periods 5, 10, 20, 50, 100 and climate projections)</td>
<td>Defines marine flooding scenarios under current and climate change</td>
<td>Copernicus Climate Dat store <a href="https://cds.climate.copernicus.eu/datasets/sis-ecde-climate-indicators?tab=overview">Climate indicators for Europe from 1940 to 2100 derived from reanalysis and climate projections</a><br />
<br />
<a href="https://cds.climate.copernicus.eu/datasets/sis-water-level-change-indicators-cmip6?tab=overview">Global sea level change indicators from 1950 to 2050 derived from reanalysis and high resolution CMIP6 climate projections</a></td>
</tr>
<tr class="odd">
<td>Hydrological adaptation structures</td>
<td><a href="https://www.geodanmark.dk/">GeoDanmark</a></td>
<td>Representation of dikes, pumping stations, and barriers in models</td>
<td>None (site-specific)</td>
</tr>
<tr class="even">
<td>Building footprints</td>
<td><a href="https://dataforsyningen.dk/data/2677">GeoDanmark</a></td>
<td>Exposure analysis; identification of at-risk assets</td>
<td>OpenStreetMap building layer (<a href="https://osmbuildings.org/">vector, global)</a></td>
</tr>
<tr class="odd">
<td>Land use / land cover</td>
<td><a href="https://dataforsyningen.dk/data/996">GeoDanmark</a></td>
<td>Classification of flood-prone areas by land-use category for exposure and Damage assessment</td>
<td><p><strong>Copernicus</strong> <a href="https://land.copernicus.eu/en/products/urban-atlas"><strong>Urban Atlas</strong></a></p>
<p><a href="https://land.copernicus.eu/en/products/clc-backbone"><strong>CLCplus Backbone</strong></a></p></td>
</tr>
</tbody>
</table>

Table 3 – used data, an alternative dataset to replicate the assessment
outside the study area, when available

  - ##### Storme surge and Climate change effects 

> *The storm surge scenarios are selected following the IPCC 8.5 climate
> prognosis for a return period of 5, 10, 20, 50 and 100 years in 2022
> and 2100. The sea level rise (in cm) is estimated for each scenario in
> the following table:*
> 
> ![Immagine che contiene testo, schermata, numero, Carattere Il
> contenuto generato dall'IA potrebbe non essere
> corretto.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/DEN-Lab2Vej_draft2_media/media/image2.png)
> 
> Table 4 - Overview of storm surge data applied for risk assessment.

T**he flood hazard workflow** for the Vejrup Å catchment relies on a
combination **of GIS platforms and flood modelling tools (**Table
2**)**. GIS software provides the core environment for integrating
elevation, land-use, and exposure datasets, producing flood maps and
supporting spatial analysis.

For the simulation of coastal flooding from storm surge and sea level
rise, both proprietary and open-source tools can be used.

The choice of tool depends on data availability, licensing, and the
level of detail required, but in all cases the outputs include flood
extent and depth maps that support municipal adaptation planning and
evaluation of mitigation measures.

<table>
<thead>
<tr class="header">
<th><h3 id="tool"><strong>Tool</strong></h3></th>
<th><h3 id="type"><strong>Type</strong></h3></th>
<th><h3 id="role"><strong>Role</strong></h3></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><h3 id="qgis"><a href="https://qgis.org/">QGIS</a> </h3></td>
<td><h3 id="open">Open</h3></td>
<td><h3 id="core-environment-for-gis-analysis-map-production-overlay-of-hazard-and-exposure-layers">Core environment for GIS analysis, map production, overlay of hazard and exposure layers</h3></td>
</tr>
<tr class="even">
<td><a href="https://scalgo.com/">Scalgo Live</a></td>
<td><h3 id="proprietary">Proprietary</h3></td>
<td><h3 id="simulate-surface-water-dynamics-and-map-flood-prone-areas-across-the-catchment">Simulate surface water dynamics and map flood-prone areas across the catchment</h3></td>
</tr>
<tr class="odd">
<td><a href="https://saferplaces.co/">SaferPlaces</a></td>
<td><h3 id="proprietary-1">Proprietary</h3></td>
<td><h3 id="simulate-surface-water-dynamics-and-map-flood-prone-areas-across-the-catchment-include-damage-model">Simulate surface water dynamics and map flood-prone areas across the catchment, include damage model</h3></td>
</tr>
<tr class="even">
<td><h3 id="anuga"><a href="https://anuga.anu.edu.au/?utm_source=chatgpt.com">ANUGA</a></h3></td>
<td><h3 id="open-1">Open</h3></td>
<td><h3 id="open-source-hydrodynamic-model-for-simulating-coastal-inundation-storm-surge-tsunami-wave-run-up.">Open-source hydrodynamic model for simulating coastal inundation (storm surge, tsunami, wave run-up). </h3></td>
</tr>
</tbody>
</table>

Table 2 – used tools and role in the Coastal Flood Hazard workflow, when
available a free similar alternative to proprietary solutions is
provided.

### Methodology

#### Step 1 - Data acquisition and preparation

High-resolution LiDAR-based DEM (0.4 m, Figure 2) from national
geoportal forms the base for flood simulations. Coastal protection
features (dikes, pumping stations) and building footprints from the same
source may be added to refine topography and catch actual status.

  - ##### Note on DEM resolution.

> When using very high-resolution LiDAR DEMs (e.g. 0.4 m), the data can
> become too heavy for hydraulic modelling. A practical solution is to
> down sample to 1–2 m resolution, which is still reasonable for flood
> modelling. This can be done through mosaicking and resampling in GIS
> software (e.g. QGIS) or by using command-line tools such as GDAL. For
> example:
> 
> gdalwarp --config GDAL\_NUM\_THREADS ALL\_CPUS -r bilinear -tr 1,2 1,2
> -t\_srs EPSG:25832 -co COMPRESS=LZW -co BIGTIFF=YES -co PREDICTOR=2
> c:/folder1/\*.tif c:/folder1/mosaic.tif
> 
> For further reference, see the GDAL [*gdalwarp
> documentation*](https://gdal.org/en/stable/programs/gdalwarp.html).

![Immagine che contiene pendio, neve, bianco e nero Il contenuto
generato dall'IA potrebbe non essere
corretto.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/DEN-Lab2Vej_draft2_media/media/image3.png)
![Immagine che contiene Aerofotogrammetria, mappa, aereo, Vista aerea Il
contenuto generato dall'IA potrebbe non essere
corretto.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/DEN-Lab2Vej_draft2_media/media/image4.png)

Figure 2 – example of Lidar DTM along the coast from GeoDanmark
geoportal (down sampled @ 1,2 m ) compared to satellite map, obstacles
such as buildings and trees are filtered from the terrain surface.
Underwater topography is not represented.

High-resolution LiDAR-based DEM (0.4 m) from SDFI provides the elevation
base for coastal flood simulations. Hydrological forcing is defined by
**storm surge and sea level rise scenarios** following IPCC RCP 8.5 for
2022–2100, with return periods of 5, 10, 20, 50, and 100 years (Table
4). These scenarios set the boundary conditions for marine inundation.

**Land-use layers** (agriculture, urban, restoration areas), together
with building footprints and municipal planning data, are added in GIS
to represent ongoing conversions into business districts or nature
restoration (wetlands and salt marshes) and actual “ante operam” status.

**Coastal protection structures** such as dikes and levees, along with
critical infrastructure, must also be included in the model.

Where no ready-to-use geospatial layers exist, these features can be
digitized manually in GIS to ensure that protective capacity is
correctly represented in the flood simulations.

Depending on the platform, they may also be overlaid directly onto the
DEM, with the exact format adapted to the input requirements and
capabilities of the chosen flood simulation tool.

#### Step 2 – Model setup and run.

The coastal flood model is configured using the prepared DEM, storm
surge levels, and sea level rise increments. Using the flood modelling
tool of choice (Table 2), storm surge return periods (e.g. 5, 10, 20,
50, 100 years) ,eventually worsened to consider sea level rise
projections in climate change conditions (Table 4),are combined to
delineate areas below the water thresholds (Figure 4

Building footprints, land-use layers, and coastal protection structures
are integrated in the simulation to ensure that exposure and defences
are correctly represented.

Model outputs typically include raster-vector classified flood maps by
depth range (e.g. \<25 cm, 25–50 cm, 50–100 cm, \>100 cm) and by return
period (Figure 2, Figure 3) showing inundation extent and water depth:

These maps allow a first evaluation of coastal flood hazard, and they
form the basis for the subsequent overlay with land use and planning
data in step 3.

![A screenshot of a map AI-generated content may be
incorrect.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/DEN-Lab2Vej_draft2_media/media/image5.png)

Figure 3 – example of large, flooded area with 10 cm marine water by a
100-year storm surge in 2100 in Odense Fjord catchment area.

](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/DEN-Lab2Vej_draft2_media/media/image6.png)![Immagine
che contiene Aerofotogrammetria, Vista aerea, mappa, aereo Il contenuto
generato dall'IA potrebbe non essere
corretto.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/DEN-Lab2Vej_draft2_media/media/image7.png)

Figure 4 – example of detailed costal flood inundation model for actual
(T100, 1,72 m a.s.l. ) and projected (T100 2100, 2,52 m a.s.l. ) surge
conditions ,(courtesy of
[SaferPlaces](https://saferplaces.co/rimini-and-climate-change-the-added-value-of-the-sea-park-parco-del-mare/)
platform).

![Immagine che contiene testo, schermata, diagramma, linea Il contenuto
generato dall'IA potrebbe non essere
corretto.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/DEN-Lab2Vej_draft2_media/media/image8.png)

Figure 5 - Workflow to obtain flood risk map using one of the flood
models listed in Table 2

#### Step 3 – Analysis and interpretation

Flood extent and depth maps generated in Step 2 are imported into GIS
for post-processing and interpretation. The results are overlaid with
land-use layers, municipal planning zones, and building footprints to
identify which categories of land and infrastructure are most affected
under different storm surge scenarios.

The classification of flood depth ranges (e.g. \<25 cm, 25–50 cm, 50–100
cm, \>100 cm) supports the identification of vulnerability hotspots. By
intersecting hazard outputs with agriculture, commercial areas,
residential zones, and planned restoration sites, it is possible to
estimate which surfaces and assets are exposed and also generate simple
spatial statistics as the key indicators mentioned in Table 1.

](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/DEN-Lab2Vej_draft2_media/media/image9.png)

Figure – example of overlay of basic land use-cover map with flood areas
in climate change scenarios in GIs environment.

Although a full damage model is not implemented in this tutorial, the
analysis provides a **qualitative assessment of potential flood
damage**, based on the overlap between flood maps and land-use
categories. This forms the basis for future extensions where
depth–damage curves could translate hazard into economic loss
estimates.

  - ##### Note: damage assessment.

> *Note all modelling suites can be complemented with damage estimation
> modules. These typically require intersecting flood hazard outputs
> (e.g. water depth rasters) with asset value layers and applying water
> depth–damage curves. This can be performed, when not embedded in the
> flood assessment tool, separately within the GIS environment or via
> external models.*
> 
> *For a more advanced implementation of this methodology, including
> regionalized vulnerability functions, see for example:*
> 
> ***Cost-benefit analysis of coastal flood defence measures in the
> North Adriatic Sea  
> **Amadio, M., Essenfelder, A.H., Bagli, S., …Mysiak, J., Roberts, S.  
> Natural Hazards and Earth System Sciences, 2022, 22(1), pp.
> 265–286, <https://doi.org/10.5194/nhess-22-265-2022>*
