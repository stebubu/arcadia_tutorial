## Introduction and Objectives of the Climate Risk Assessment

### Regional context.

### [Lower Austria](https://en.wikipedia.org/wiki/Lower_Austria) is a predominantly rural, arable landscape where agriculture is the primary exposure unit for climate risk analysis. The regional CRA focuses on a**gricultural areas and evaluates risks at municipal and state scales.** 

### Innovation Lab 1 addresses water-related extremes—intense precipitation and drought—framed as **“too little and too much water.”** **NbS** such as [multifunctional hedgerows](https://resist-project.eu/story/nature-based-solutions-in-rural-areas-hedgerows-and-traditional-bocages/) are considered to reduce **water-induced soil erosion and drought impacts** in crop areas. 

Figure 1 - p physical map of Lower Austria. Source:
https://maps-austria.com/lower-austria-map

### Under **future climate conditions**, both hazards are expected to intensify. The CRA therefore couples climate projections with exposure and vulnerability in farmland to quantify changing erosion and drought risks. 

](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/AUT-Lab1_Er_Dr_draft2_media/media/image2.jpeg)

Figure 2 – example of Existing hedges which have not been removed but
included and extended in the ecoplus business park Wolkersdorf. Picture
by ecoplus.

### The assessment is co-developed with regional partners to support evidence-based adaptation, informing state-level strategy and coordination of local measures and land-use planning. 

### Scope of the tutorial.

This tutorial sets out a replicable Climate Risk Assessment for Lower
Austria’s Innovation Lab 1, written to be followed by practitioners who
need to reproduce the work in other regions. It explains how to
**evaluate risk for two agricultural hazards—water-induced soil erosion
and agricultural drought**—and how to test multifunctional hedgerows as
an adaptation option under the overarching theme of “too little and too
much water.”

The assessment targets **arable land and is designed to inform decisions
at both state and municipal levels** by linking spatial risk with
adaptation potential, so that stakeholders can prioritize where and how
to implement measures. Co-development with regional partners ensures
that the workflow supports real planning needs and coordination of local
actions.

**Transferability is explicit:** users may replace European inputs with
national or local datasets, adjust parameters, and adapt visualizations
without altering the core logic of the workflow. The expected outcome is
a **portable methodology** that connects risk assessment to targeted
adaptation planning.

The tutorial also states the main boundaries of the approach.
**Uncertainty in regional climate** projections and variability in
**hedgerow performance** across soils, topographies, and practices limit
precision; **prolonged drought followed by intense rainfall may exceed
NbS capacity**, so results should feed an adaptive planning process.

![Immagine che contiene aria aperta, erba, cielo, uccello Il contenuto
generato dall'IA potrebbe non essere
corretto.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/AUT-Lab1_Er_Dr_draft2_media/media/image3.jpeg)

Figure 3 - year-old multi-use hedge in Absdorf (Wagram). The hedge will
be extended to create a habitat network during Lab 1. Picture by K. Deim
(ABB).

  - #### Disclaimer

> *This tutorial is intended as a general workflow example for
> Innovation Lab 1 and does not replace software-specific documentation
> (e.g., GIS, hydrological or crop/soil erosion modelling tools
> user/technical manuals). Users should already be familiar with the
> relevant geospatial data formats, data pre-processing techniques, and
> modelling concepts applicable to extreme precipitation, soil erosion,
> and agricultural drought, as well as with the specific input/output
> requirements and run functionalities of the modelling software before
> attempting to replicate this workflow.*

### CRA objectives.

The Lower Austria CRA aims to:

  - Characterize **current and future** hazard conditions for
    **water-induced soil erosion and agricultural drought** in arable
    land using EURO-CORDEX and ÖKS15 projections together with national
    topographic and exposure datasets.

  - Quantify **spatial risk and identify hotspots at municipal and state
    levels** to support evidence-based adaptation and coordination of
    local measures.

  - Evaluate the effectiveness of **multifunctional hedgerows** as a
    Nature-based Solution to reduce erosion and drought impacts (and
    wind erosion where relevant) and indicate where they deliver the
    highest benefits.

  - Provide a **transferable methodology** that links risk assessment
    with targeted adaptation planning and can be replicated by
    substituting datasets and adjusting parameters.

  - **Inform adaptive planning under uncertainty** through a
    co-developed process that combines spatial risk with adaptation
    potential.

### Intended users.

The Climate Risk Assessment developed in Innovation Lab 1 is designed to
support both **broad-scale strategic planning at the state level** and
the **coordination of local adaptation measures** in rural, arable
regions of Lower Austria. It addresses stakeholders from **science and
administration** who are directly involved in **land-use planning and
climate adaptation**, and it is co-developed together with partners from
the pilot region.

By combining spatial risk assessment with adaptation potential, the CRA
is intended to inform **decision-making processes and help authorities
and practitioners** prioritize actions and align them with long-term
climate resilience goals.

## Hazard – Soil erosion.

### Description and context

The assessment of soil erosion in Innovation Lab 1 focuses on
**water-induced processes affecting arable land** in Lower Austria. The
CRA applies the Revised Universal Soil Loss Equation (RUSLE) to estimate
average annual soil loss and to evaluate how erosion risks may evolve
under changing climate conditions. The approach builds on an
Austria-wide erosion risk study ([Schmaltz et
al., 2023](https://www.sciencedirect.com/science/article/pii/S0167880923002499))
and refines it for the regional scale by incorporating **updated climate
projections and local exposure patterns**.

Future scenarios are produced by coupling the RUSLE framework with
EURO-CORDEX precipitation and temperature projections under different
Representative Concentration Pathways (RCPs). The resulting analysis
provides a **spatially explicit view of soil erosion risks**, serving as
a basis for testing adaptation measures such as multifunctional
hedgerows and for informing land-use planning in agricultural
landscapes.

| **Dimension**           | **Indicator(s)**                                               | **Unit**                   | **Purpose**                                                                            |
| ----------------------- | -------------------------------------------------------------- | -------------------------- | -------------------------------------------------------------------------------------- |
| Soil loss               | Average annual soil erosion from cropland estimated with RUSLE | t/ha/yr                    | Quantify baseline and future erosion risk                                              |
| Rainfall erosivity      | R-Factor from climate projections and station data             | MJ mm ha-1 h-1 yr-1        | Represent intensity of precipitation as driver of erosion, may change in CC conditions |
| Topography              | LS-Factor (slope length and steepness)                         | dimensionless              | Capture terrain influence on erosion susceptibility, used to simulate Nbs effect       |
| Land cover & management | C-Factor reflecting crops, practices, and NbS (hedgerows)      | dimensionless              | Assess effect of land use and measures on erosion rates, used to simulate Nbs effect   |
| Exposure                | Extent of arable land at municipal and state level             | hectares                   | Define spatial units where erosion risk is calculated                                  |
| Vulnerability           | Socio-economic farming characteristics                         | index (municipality level) | Integrate social dimension into erosion risk assessment                                |

Table 1 – key indicators tracked-Erosion Hazard

### Data sources and tools

The soil erosion workflow in Innovation Lab 1 builds on the Austrian
national erosion **risk assessment described by [Schmaltz et al.
(2023)](https://www.sciencedirect.com/science/article/pii/S0167880923002499)**,
adapting it to the regional scale of Lower Austria.

The approach combines **high-resolution national datasets with climate
projections** to parameterize the RUSLE model. Hazard drivers such as
rainfall erosivity, soil erodibility, topography, and land management
are derived from Austrian sources including **ÖKS15 climate scenarios,
the 10 m DEM, INVEKOS crop parcel data, and national soil maps**. These
are complemented by socio-economic data (Farm Structure Survey) to
integrate exposure and vulnerability.

To ensure that the workflow can be replicated in other regions, European
open datasets provide equivalent substitutes: Copernicus DEM for
topography, the Copernicus Climate Data Store for climate projections
and impact indicators, and ESDAC for soil parameters. This dual
setup—national where available, European where needed—guarantees both
local accuracy and transferability.

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
<td>Climate projections (precipitation, temperature)</td>
<td><a href="https://data.hub.geosphere.at/group/oks15"><strong>ÖKS15</strong></a> (Austrian scenarios, 1 km),</td>
<td>Input for rainfall erosivity (R-factor), baseline and future scenarios</td>
<td>Copernicus <a href="https://cds.climate.copernicus.eu/datasets/projections-cordex-domains-single-levels?tab=overview"><strong>EURO-CORDEX</strong></a> (12.5 km /0.11°)</td>
</tr>
<tr class="even">
<td>Meteorological observations</td>
<td><a href="https://data.hub.geosphere.at/group/stationsdaten">Austrian weather station network</a></td>
<td>Calibration and validation of rainfall erosivity</td>
<td><p>ERA5-Land post-processed daily statistics from 1950 to present ( <a href="https://cds.climate.copernicus.eu/datasets/derived-era5-land-daily-statistics?tab=overview"><span class="underline">open, raster</span></a>)</p>
<p>Daily gridded observational dataset for precipitation, temperature, E-OBS <a href="https://surfobs.climate.copernicus.eu/dataaccess/access_eobs.php"><span class="underline">(open , gridded )</span></a>,</p></td>
</tr>
<tr class="odd">
<td>Topography</td>
<td><a href="https://www.data.gv.at/katalog/en/dataset/b5de6975-417b-4320-afdb-eb2a9e2a1dbf#additional-info"><strong>National DEM Austria</strong></a> (10 m)</td>
<td>Derivation of LS-factor (slope, flow accumulation)</td>
<td>Copernicus DEM - Global and European Digital Elevation Model <a href="https://dataspace.copernicus.eu/explore-data/data-collections/copernicus-contributing-missions/collections-description/COP-DEM"><span class="underline">(open – raster 30m, 10m for selected users)</span></a></td>
</tr>
<tr class="even">
<td>Land use and crop data</td>
<td><a href="https://www.data.gv.at/katalog/dataset?tags=INVEKOS"><strong>INVEKOS</strong></a> parcel dataset</td>
<td>Agricultural fields and crop information Input for C-factor and definition of arable exposure units</td>
<td><a href="https://land.copernicus.eu/en/products/corine-land-cover/clc2018"><span class="underline">CORINE Land Cover 2018 (vector/raster 100 m), Europe, 6-yearly</span></a></td>
</tr>
<tr class="odd">
<td>Soil properties</td>
<td><a href="https://geometadatensuche.inspire.gv.at/metadatensuche/inspire/ita/catalog.search#/search?any=soil">Austrian national soil maps</a></td>
<td>Input for K-factor (soil erodibility)</td>
<td>ESDAC datasets (500 m <a href="https://esdac.jrc.ec.europa.eu/content/soil-erodibility-k-factor-high-resolution-dataset-europe">K</a>-<a href="https://esdac.jrc.ec.europa.eu/content/rainfall-erosivity-european-union-and-switzerland">R</a> factor, 100 m <a href="https://esdac.jrc.ec.europa.eu/content/cover-management-factor-c-factor-eu">C</a>, and <a href="https://esdac.jrc.ec.europa.eu/content/support-practices-factor-p-factor-eu">P</a>-factors)</td>
</tr>
<tr class="even">
<td>Agricultural structure and socioeconomics</td>
<td>Austrian <a href="https://www.statistik.at/en/about-us/surveys/agriculture-and-forestry/farm-structure-survey"><strong>Farm Structure Survey</strong></a></td>
<td>Vulnerability indicators (farm structure, income dependency, demographics) at municipal level</td>
<td><a href="https://ec.europa.eu/eurostat/web/experimental-statistics/geospatial-data-agricultural-census">Eurostat Geospatial data from agricultural census</a></td>
</tr>
</tbody>
</table>

Table 2 – used data, an alternative dataset to replicate the assessment
outside the study area, when available

  - ##### *Climate change effects* 

> *The rainfall erosivity factor (R) is available from*
> *[ESDAC](https://esdac.jrc.ec.europa.eu/content/rainfall-erosivity-european-union-and-switzerland)
> as a baseline dataset for the EU and Switzerland, derived from
> high-resolution pluviograph data and interpolated to a 500 m grid
> (Panagos et al., 2015). In addition to the baseline, ESDAC also
> provides future projections of R under climate change, calculated from
> bias-corrected regional climate model outputs (EURO-CORDEX). These
> projections indicate a general increase in rainfall erosivity towards
> 2050, especially in central and northern Europe, reflecting the
> expected intensification of extreme precipitation. Users can therefore
> choose between present-day R for baseline assessments and
> climate-adjusted R layers for scenario analyses in RUSLE
> applications.*

![Immagine che contiene mappa, Aerofotogrammetria, Vista aerea, aria
aperta Il contenuto generato dall'IA potrebbe non essere
corretto.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/AUT-Lab1_Er_Dr_draft2_media/media/image4.png)

Figure 4 - Example layer showing reference parcels and digitized
landscape elements defined by Agrarmarkt Austria under the EU Horizontal
CAP Regulation, annually updated, enabling precise linkage of soil
erosion modelling results with field-scale agricultural units.

![Immagine che contiene testo, schermata, quadrato, diagramma Il
contenuto generato dall'IA potrebbe non essere
corretto.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/AUT-Lab1_Er_Dr_draft2_media/media/image5.png)

Figure 5 - large-scale assessments, vulnerability proxies are available
from Eurostat’s experimental geospatial agricultural census datasets
(multi-resolution grids, 1–80 km), providing spatially harmonised
indicators on farm number, cultivated areas, farmer demographics (age,
gender), livestock, labour, and production methods. While coarser in
scale, these can serve as vulnerability layers when regional data are
unavailable.

The soil erosion workflow is implemented using a **RUSLE-based modelling
approach**, adapted to the regional scale of Lower Austria. The model
itself is not a standalone application but is coded and executed within
a spatial analysis environment. **RUSLE is essentially a multiplicative
model: once all factor layers (R, K, LS, C, P) are prepared,** the
application reduces to a raster-based calculation in GIS, as will be
detailed later in the methodological section.

To handle geospatial data, preprocess inputs, and visualize outputs, a
**GIS platform such as QGIS** is used. This provides the necessary
functionality to manage raster and vector datasets, derive topographic
parameters from the DEM, and integrate climate and land-use data.

The combination of RUSLE calculations with GIS processing ensures that
erosion risk can be **mapped consistently** across agricultural areas
and aggregated at municipal and state levels for decision support.

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
<td>RUSLE (Revised Universal Soil Loss Equation)</td>
<td>Open / empirical model</td>
<td><p>Core model to estimate average annual soil loss under current and future climate scenarios.</p>
<p>(see note)</p></td>
</tr>
<tr class="even">
<td><a href="https://qgis.org/">QGIS</a></td>
<td>Open-source GIS</td>
<td>Data preprocessing, derivation of LS-factor (directly through SAGA GIS tools), conversion of land use and soil/parcel data into necessary RUSLE factors mapping and visualization of erosion risk.</td>
</tr>
</tbody>
</table>

Table 3 – used tools and role in the Erosion Hazard workflow, all tools
are free to use.

  - ##### Note on deriving R K, C and P factors.

> *The calculation of soil erodibility (K), cover/management (C) and
> support practices (P) requires **reclassification of local datasets**
> (soil maps, crop parcels, or land management layers) using standard
> **lookup tables**. In the Austrian case, this could be done following
> the methodology of* *[**Schmaltz et al.
> (2023)**](https://www.sciencedirect.com/science/article/pii/S0167880923002499),
> where K is assigned to soil units, and C and P are linked to INVEKOS
> crop and management information.*
> 
> *For replication in regions where only European data are available,
> **users may apply the pre-computed ESDAC layers (R, K at 500 m; C, P
> at 100 m)**. However, these products are relatively coarse. To
> increase accuracy, user may invest time in deriving
> [R](https://www.sciencedirect.com/science/article/pii/S004896971500011X)
> [K](https://www.sciencedirect.com/science/article/pii/S0048969714001727),
> [C](https://www.sciencedirect.com/science/article/pii/S0264837715001611)
> and
> [P](https://www.sciencedirect.com/science/article/pii/S1462901115000611)
> from more detailed meteorological , spoil or parcel datasets when
> available, using the lookup values provided in in the ref. article
> from the European Soil Data Centre.*

### Methodology

#### Step 1 - Data acquisition and preparation

The first step of the workflow is the collection and preprocessing of
all input datasets required to parameterize the RUSLE model. **When
local and national datasets are available, each factor must be
recalculated specifically for the study area.**

  - Topography (LS-factor): **directly derived from the DEM** using the
    LS-factor function of SAGA GIS within QGIS. This ensures a spatially
    explicit representation of slope length and steepness adapted to
    local terrain conditions.

  - Rainfall erosivity (R-factor), soil erodibility (K-factor),
    cover-management (C-factor), and support practice (P-factor):
    require **reclassification of local data sources.** Values are
    assigned using lookup tables based on soil maps, parcel and crop
    information, and national climate data, as described in the previous
    section.

Preprocessing: includes harmonizing coordinate systems, resampling
datasets to a common resolution, and rasterizing vector inputs such as
field parcels or management practices.

As an alternative, where local data are not available, users may rely on
the precomputed ESDAC products (R at 500 m, K/C/P at 100 m). These
datasets are coarser in resolution but provide a consistent and
harmonised European baseline for exploratory assessments and large-scale
applications, as illustrated in the example maps provided below.

](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/AUT-Lab1_Er_Dr_draft2_media/media/image6.png)

Figure 6 – example of 10 m Lidar derived DTM from Austrian
geoportal(left() and corresponding Ls factor derived in Qgis (right)

](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/AUT-Lab1_Er_Dr_draft2_media/media/image7.png)

Figure 7 – examples of Rainfall Erosivity R \[MJ mm
ha<sup>-1</sup> h<sup>-1</sup> yr<sup>-1</sup>\] \[ (left) and Soil
Erodibility (K- Factor, right) from ESACD databases.

Step 2 - Model setup and run.

The modelling step corresponds to the direct application of the RUSLE
formula, i.e. the **multiplication of all prepared factor layers** via
basic *raster calculator* (*map algebra*) in GIS:

E=R×K×LS×C×P

where E is the estimated average annual soil loss (“Erosion”) in **t
ha⁻¹ yr⁻¹**, see also (\[1\])

Each factor layer (R, K, LS, C, P) had been previously (Step 2) derived
or reclassified from local datasets, harmonised to the same projection
and resolution.

The resulting erosion map provides the **annual mean soil loss rate**,
which represents the standard output unit for RUSLE applications.

For methodological details and reference values of the factors, users
cloud also consult the following key sources:

  - **[R-factor](https://www.sciencedirect.com/science/article/pii/S004896971500011X)
    (rainfall erosivity):** Panagos et al., 2015 (*Science of the Total
    Environment*) – ESDAC dataset for Europe.

  - **[K-factor](https://www.sciencedirect.com/science/article/pii/S0048969714001727)
    (soil erodibility):** Panagos et al., 2014 (*Geoderma*) – European
    soil erodibility map.

  - **LS-factor (topography):** [SAGA-GIS Tool
    Library](https://saga-gis.sourceforge.io/saga_tool_doc/8.1.1/ta_hydrology_25.html)

  - [*C*](https://www.sciencedirect.com/science/article/pii/S0264837715001611)**-
    and**
    [*P*](https://www.sciencedirect.com/science/article/pii/S1462901115000611)**-factors
    (cover and practices):** Panagos et al., 2015 (*Environmental
    Modelling & Software*) – European C and P factor datasets.

For simplicity, the soil erosion map (E \[t ha⁻¹ yr⁻¹\]) presented below
(Figure 8) is derived directly from the [**RUSLE2015 soil erosion
dataset**](https://esdac.jrc.ec.europa.eu/content/soil-erosion-water-rusle2015/)
published by ESDAC, following the above described methodology

#### Step 3 - Analysis and interpretation

The erosion hazard map derived from the RUSLE model provides the core
spatial output, but its value lies in how the results are analysed and
interpreted. In Innovation Lab 1, this step focuses on transforming raw
model outputs into information that can support planning and
decision-making.

First, the raster of mean annual soil loss (*t ha⁻¹ yr⁻¹*) can be
**aggregated from small to larger territorial unit ( e.g. municipal and
state boundaries** (as in the example of Figure 8), allowing direct
comparison across relevant administrative units and integration into
existing planning frameworks. This allows local authorities to identify
where erosion risk is systematically higher within their jurisdiction.

Second, the analysis highlights **erosion hotspots** by applying
thresholds to the raster map and overlaying them with cropland exposure.
These hotspots indicate priority areas for targeted interventions,
including the implementation of multifunctional hedgerows and other
Nature-based Solutions.

Third, **scenario comparisons** are undertaken. Results can be analysed
**under different climate projections** (EURO-CORDEX, ÖKS15) to quantify
the expected increase in hazard due to climate change.

Finally, the interpretation integrates **socio-economic vulnerability
indicators** **at municipal level**, such as farm structure and
dependence on agricultural income. This combination of hazard, exposure,
and vulnerability highlights areas where physical risk coincides with
lower adaptive capacity, providing a risk-oriented basis for
prioritisation.

](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/AUT-Lab1_Er_Dr_draft2_media/media/image8.png)
![Immagine che contiene mappa, testo, atlante Il contenuto generato
dall'IA potrebbe non essere
corretto.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/AUT-Lab1_Er_Dr_draft2_media/media/image9.png)

![Immagine che contiene rosso, mappa, Policromia, Bordeaux Il contenuto
generato dall'IA potrebbe non essere
corretto.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/AUT-Lab1_Er_Dr_draft2_media/media/image10.png)

Figure 8 – Left: extract from the RUSLE2015 soil erosion dataset
(ESDAC), showing estimated average annual soil loss (t ha⁻¹ yr⁻¹) for a
selected area in Austria, derived from the harmonised European layers of
R, K, LS, C and P factors. Right: overlay of the same erosion map with
INVEKOS reference parcels (Agrarmarkt Austria, 2025-1, Table 2), which
represent agricultural blocks and digitised landscape elements under the
EU CAP regulation. This integration allows soil erosion estimates to be
directly linked to field-scale agricultural units. Aggregation example
over larger territorial unit is provided in the lower figure.

#### Step 4 - NbS testing. 

The testing of Nature-based Solutions (NbS) focuses on the introduction
of **multifunctional hedgerows** in arable land as a measure to mitigate
soil erosion. Within the RUSLE framework, the presence of hedgerows does
not require changes to the hazard drivers (R, K) but can be represented
through adjustments of the **LS- and C-factors**.

  - **C-factor (cover and management):** hedgerows increase permanent
    vegetative cover, reduce raindrop impact and promote soil stability
    (\[2\],\[3\]). This effect is simulated by assigning lower C values
    to cropland areas adjacent to or intersected by hedgerows.

  - **LS-factor (slope length and steepness):** the establishment of
    hedgerows effectively interrupts slope length and alters runoff
    pathways, reducing the effective contributing area upslope of a
    pixel. In GIS terms this can be simulated by shortening slope
    lengths or by recalculating LS with breaks introduced along hedgerow
    alignments **modifying DTM to count for new morphology induced by
    NBS before reprocessing.**

The workflow in steps 2 and 3 shall then be repeated with adjusted LS
and C values representing hedgerow implementation. The comparison of
“with” and “without NbS” maps quantify the potential reduction of
annual soil loss, highlighting those hotspots where hedgerows deliver
the highest benefit.

## Hazard – Agricultural drought.

### Description and context

The second hazard assessed in Innovation Lab 1 is **agricultural
drought**, understood here as the insufficient availability of soil
water to sustain crop growth during the vegetation period. In the
context of Lower Austria, drought has become an increasingly relevant
climate risk alongside water-induced soil erosion. While the region is
traditionally well supplied with rainfall, recent summers have shown
more frequent dry spells and heat periods, affecting yields and farm
income.

Within the CRA, drought is approached through an **indicator-based
method** that combines climate variables (precipitation and temperature)
with soil and land use characteristics to estimate water deficit
conditions in cropland. Climate change scenarios (EURO-CORDEX, ÖKS15)
are used to explore how frequency and severity of droughts may evolve
under future conditions.

The objective is to provide **spatially explicit drought hazard maps**,
comparable with the erosion analysis, and to identify where agricultural
areas are most exposed to prolonged soil moisture deficits. These
results allow stakeholders to evaluate the relative importance of “too
little water” in comparison to “too much water” and to consider
adaptation options at both municipal and regional planning levels.

| **Dimension** | **Indicator(s)**                                                               | **Unit**     | **Purpose**                                                        |
| ------------- | ------------------------------------------------------------------------------ | ------------ | ------------------------------------------------------------------ |
| Hazard        | Potential crop yield loss in rainfed conditions (derived from ETₐ / ETₙ ratio) | % yield loss | Quantify drought stress on crops under baseline and future climate |

Table 4 – key indicators tracked-Agricultural Drought Hazard

### Data sources 

The assessment of agricultural drought in Innovation Lab 1 is explicitly
based on the [**CLIMAAX Risk Workflow for agricultural
systems**](https://handbook.climaax.eu/notebooks/workflows/DROUGHTS/02_agriculture_drought/AGRICULTURE_Risk_workflow_description.html).
By design this CRA methodology follows an **indicator-based approach**
that combines climate drivers, soil water holding capacity, crop
exposure, and vulnerability information to derive **potential yield
losses under rainfed conditions**.

In this section we therefore focus only on the **datasets required to
apply the workflow**, both at Austrian and European scale. The full
methodological description is not repeated here but is entirely referred
to the official [**CLIMAAX Risk Workflow for agricultural
systems**](https://handbook.climaax.eu/notebooks/workflows/DROUGHTS/02_agriculture_drought/AGRICULTURE_Risk_workflow_description.html).

For the regional application in Lower Austria, the CRA uses **ÖKS15
climate scenarios** (1 km), **EURO-CORDEX simulations** (12.5 km), and
national meteorological observations as the basis for calculating
reference evapotranspiration (ET₀) and effective evapotranspiration
(ETₐ).

Soil water holding capacity is derived from **national soil maps**,
while exposure is defined through the **INVEKOS parcel dataset** with
crop-specific attributes.

**National agricultural statistics** provide information on crop
production and economic value, while irrigation distribution and
socio-economic data from the **Farm Structure Survey** represent the
main vulnerability layers.

Elevation and climate zoning are also included to reflect topographic
and thermal conditions influencing crop growth.

To ensure replicability outside Austria, equivalent **European open
datasets** can be used, such as **Copernicus CDS** (precipitation,
temperature, evapotranspiration indices), **ESDAC** (soil hydraulic
properties), **MapSPAM/FAO-IIASA GAEZ** (crop maps, yields, irrigation,
climate zones), the **Copernicus DEM**, and **Eurostat agricultural
census data**. This dual setup allows both accurate local analysis and
transferability to other regions.

<table>
<thead>
<tr class="header">
<th><strong>Data type</strong></th>
<th><strong>Source (Austria)</strong></th>
<th><strong>Role in workflow</strong></th>
<th><strong>Open/EU alternative</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Climate projections (precipitation, temperature)</td>
<td><a href="https://data.hub.geosphere.at/group/oks15"><strong>ÖKS15</strong></a> (Austrian scenarios, 1 km),</td>
<td>Input for ET₀, ETₙ, ETₐ and drought hazard calculation</td>
<td>Copernicus <a href="https://cds.climate.copernicus.eu/datasets/projections-cordex-domains-single-levels?tab=overview"><strong>EURO-CORDEX</strong></a> (12.5 km /0.11°)</td>
</tr>
<tr class="even">
<td>Meteorological observations</td>
<td><a href="https://data.hub.geosphere.at/group/stationsdaten">Austrian weather station network</a></td>
<td>Input for ET₀, ETₙ, ETₐ and drought hazard calculation</td>
<td><p>ERA5-Land post-processed daily statistics from 1950 to present ( <a href="https://cds.climate.copernicus.eu/datasets/derived-era5-land-daily-statistics?tab=overview"><span class="underline">open, raster</span></a>)</p>
<p>Daily gridded observational dataset for precipitation, temperature, E-OBS <a href="https://surfobs.climate.copernicus.eu/dataaccess/access_eobs.php"><span class="underline">(open , gridded )</span></a>,</p></td>
</tr>
<tr class="odd">
<td>Elevation</td>
<td><a href="https://www.data.gv.at/katalog/en/dataset/b5de6975-417b-4320-afdb-eb2a9e2a1dbf#additional-info"><strong>National DEM Austria</strong></a> (10 m)</td>
<td>Derivation of topographic effects and climate zoning</td>
<td>Copernicus DEM - Global and European Digital Elevation Model <a href="https://dataspace.copernicus.eu/explore-data/data-collections/copernicus-contributing-missions/collections-description/COP-DEM"><span class="underline">(open – raster 30m, 10m for selected users)</span></a></td>
</tr>
<tr class="even">
<td>Thermal climate zones</td>
<td></td>
<td>Crop-specific growing conditions and evapotranspiration</td>
<td><p><a href="https://www.gaez.iiasa.ac.at/">FAO-IIASA GAEZ</a> climate zones</p>
<p>Thermal climate zones of the world (<a href="https://data.apps.fao.org/catalog/iso/68790fd0-690c-11db-a5a5-000d939bc5d8">FGGD</a>)</p></td>
</tr>
<tr class="odd">
<td>Soil available water capacity (AWC)</td>
<td></td>
<td>Soil buffering capacity against drought</td>
<td><a href="https://zenodo.org/records/2629149">Hengl and Gupta (2019)</a></td>
</tr>
<tr class="even">
<td>Crop distribution</td>
<td><a href="https://www.data.gv.at/katalog/dataset?tags=INVEKOS">INVEKOS</a> parcel dataset</td>
<td>Definition of crop types, derive Crop production map for Austria</td>
<td><a href="https://land.copernicus.eu/en/products/corine-land-cover/clc2018"><span class="underline">CORINE Land Cover 2018 (vector/raster 100 m), Europe, 6-yearly</span></a></td>
</tr>
<tr class="odd">
<td>crop-specific information</td>
<td></td>
<td>specific paramters needed for the hazard assessment</td>
<td><a href="https://handbook.climaax.eu/notebooks/workflows/DROUGHTS/02_agriculture_drought/crop_table.html">Climaxx Handbook</a></td>
</tr>
<tr class="even">
<td>Crop production [ton]</td>
<td></td>
<td> crop production to calculate exposure ( first exposure dataset)</td>
<td> <a href="https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/SWPENT">MapSPAM repository</a></td>
</tr>
<tr class="odd">
<td>crops aggregated value</td>
<td></td>
<td>second exposure dataset </td>
<td>FAO-GAEZ <a href="https://www.fao.org/gaez/en/">Global Agro-Ecological Zones</a> </td>
</tr>
<tr class="even">
<td>Irrigation availability</td>
<td></td>
<td>cropland full-irrigation availability to define vulnerability</td>
<td>GAEZ v5  <a href="https://data.apps.fao.org/catalog/iso/5e11e7c5-9088-4f1a-80df-04ef026bd726">Share of irrigated land</a></td>
</tr>
</tbody>
</table>

Table 5 – used data, an alternative dataset to replicate the assessment
outside the study area, when ava

1.  <https://esdac.jrc.ec.europa.eu/themes/rusle2015>

2.  <https://savoursoilpermaculture.com/the-ecological-significance-of-hedgerows-a-multidimensional-approach/>

3.  <https://www.sciencedirect.com/science/article/abs/pii/S1161030109000653>
