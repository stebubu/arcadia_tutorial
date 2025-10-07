# aut lab1 er dr draft2

### Introduction and Objectives of the Climate Risk Assessment

#### Regional context

Lower Austria is a predominantly rural, arable landscape where agriculture is the primary exposure unit for climate risk analysis. The regional CRA focuses on agricultural areas and evaluates risks at municipal and state scales.

Innovation Lab 1 addresses water-related extremes—intense precipitation and drought—framed as “too little and too much water.” NbS such as multifunctional hedgerows are considered to reduce water-induced soil erosion and drought impacts in crop areas.

Figure 1 - physical map of Lower Austria. Source: https://maps-austria.com/lower-austria-map

Figure 2 – example of existing hedges which have not been removed but included and extended in the ecoplus business park Wolkersdorf. Picture by ecoplus.

Under future climate conditions, both hazards are expected to intensify. The CRA therefore couples climate projections with exposure and vulnerability in farmland to quantify changing erosion and drought risks.

Figure 3 - year-old multi-use hedge in Absdorf (Wagram). The hedge will be extended to create a habitat network during Lab 1. Picture by K. Deim (ABB).

{% hint style="warning" %}
Disclaimer

This tutorial is intended as a general workflow example for Innovation Lab 1 and does not replace software-specific documentation (e.g., GIS, hydrological or crop/soil erosion modelling tools user/technical manuals). Users should already be familiar with the relevant geospatial data formats, data pre-processing techniques, and modelling concepts applicable to extreme precipitation, soil erosion, and agricultural drought, as well as with the specific input/output requirements and run functionalities of the modelling software before attempting to replicate this workflow.
{% endhint %}

#### CRA objectives

The Lower Austria CRA aims to:

* Characterize current and future hazard conditions for water-induced soil erosion and agricultural drought in arable land using EURO-CORDEX and ÖKS15 projections together with national topographic and exposure datasets.
* Quantify spatial risk and identify hotspots at municipal and state levels to support evidence-based adaptation and coordination of local measures.
* Evaluate the effectiveness of multifunctional hedgerows as a Nature-based Solution to reduce erosion and drought impacts (and wind erosion where relevant) and indicate where they deliver the highest benefits.
* Provide a transferable methodology that links risk assessment with targeted adaptation planning and can be replicated by substituting datasets and adjusting parameters.
* Inform adaptive planning under uncertainty through a co-developed process that combines spatial risk with adaptation potential.

#### Intended users

The Climate Risk Assessment developed in Innovation Lab 1 is designed to support both broad-scale strategic planning at the state level and the coordination of local adaptation measures in rural, arable regions of Lower Austria. It addresses stakeholders from science and administration who are directly involved in land-use planning and climate adaptation, and it is co-developed together with partners from the pilot region.

By combining spatial risk assessment with adaptation potential, the CRA is intended to inform decision-making processes and help authorities and practitioners prioritize actions and align them with long-term climate resilience goals.

***

### Hazard – Soil erosion

#### Description and context

The assessment of soil erosion in Innovation Lab 1 focuses on water-induced processes affecting arable land in Lower Austria. The CRA applies the Revised Universal Soil Loss Equation (RUSLE) to estimate average annual soil loss and to evaluate how erosion risks may evolve under changing climate conditions. The approach builds on an Austria-wide erosion risk study (Schmaltz et al., 2023) and refines it for the regional scale by incorporating updated climate projections and local exposure patterns.

Future scenarios are produced by coupling the RUSLE framework with EURO-CORDEX precipitation and temperature projections under different Representative Concentration Pathways (RCPs). The resulting analysis provides a spatially explicit view of soil erosion risks, serving as a basis for testing adaptation measures such as multifunctional hedgerows and for informing land-use planning in agricultural landscapes.

| Dimension               | Indicator(s)                                                   | Unit                       | Purpose                                                                                |
| ----------------------- | -------------------------------------------------------------- | -------------------------- | -------------------------------------------------------------------------------------- |
| Soil loss               | Average annual soil erosion from cropland estimated with RUSLE | t/ha/yr                    | Quantify baseline and future erosion risk                                              |
| Rainfall erosivity      | R-Factor from climate projections and station data             | MJ mm ha-1 h-1 yr-1        | Represent intensity of precipitation as driver of erosion, may change in CC conditions |
| Topography              | LS-Factor (slope length and steepness)                         | dimensionless              | Capture terrain influence on erosion susceptibility, used to simulate Nbs effect       |
| Land cover & management | C-Factor reflecting crops, practices, and NbS (hedgerows)      | dimensionless              | Assess effect of land use and measures on erosion rates, used to simulate Nbs effect   |
| Exposure                | Extent of arable land at municipal and state level             | hectares                   | Define spatial units where erosion risk is calculated                                  |
| Vulnerability           | Socio-economic farming characteristics                         | index (municipality level) | Integrate social dimension into erosion risk assessment                                |

Table 1 – key indicators tracked — Erosion Hazard

#### Data sources and tools

The soil erosion workflow in Innovation Lab 1 builds on the Austrian national erosion risk assessment described by Schmaltz et al. (2023), adapting it to the regional scale of Lower Austria.

The approach combines high-resolution national datasets with climate projections to parameterize the RUSLE model. Hazard drivers such as rainfall erosivity, soil erodibility, topography, and land management are derived from Austrian sources including ÖKS15 climate scenarios, the 10 m DEM, INVEKOS crop parcel data, and national soil maps. These are complemented by socio-economic data (Farm Structure Survey) to integrate exposure and vulnerability.

To ensure that the workflow can be replicated in other regions, European open datasets provide equivalent substitutes: Copernicus DEM for topography, the Copernicus Climate Data Store for climate projections and impact indicators, and ESDAC for soil parameters. This dual setup—national where available, European where needed—guarantees both local accuracy and transferability.

| Data type                                        | Source                           | Role in workflow                                                                                     | Open/EU alternative                               |
| ------------------------------------------------ | -------------------------------- | ---------------------------------------------------------------------------------------------------- | ------------------------------------------------- |
| Climate projections (precipitation, temperature) | ÖKS15 (Austrian scenarios, 1 km) | Input for rainfall erosivity (R-factor), baseline and future scenarios                               | Copernicus EURO-CORDEX (12.5 km /0.11°)           |
| Meteorological observations                      | Austrian weather station network | Calibration and validation of rainfall erosivity                                                     | ERA5-Land post-processed daily statistics; E-OBS  |
| Topography                                       | National DEM Austria (10 m)      | Derivation of LS-factor (slope, flow accumulation)                                                   | Copernicus DEM - Global and European DEM          |
| Land use and crop data                           | INVEKOS parcel dataset           | Agricultural fields and crop information; Input for C-factor and definition of arable exposure units | CORINE Land Cover 2018 (100 m)                    |
| Soil properties                                  | Austrian national soil maps      | Input for K-factor (soil erodibility)                                                                | ESDAC datasets (K at 500 m; R, C, P products)     |
| Agricultural structure and socioeconomics        | Farm Structure Survey            | Vulnerability indicators (farm structure, income dependency, demographics) at municipal level        | Eurostat Geospatial data from agricultural census |

Table 2 – used data, and alternative datasets to replicate the assessment outside the study area, when available

Climate change effects

The rainfall erosivity factor (R) is available from ESDAC as a baseline dataset for the EU and Switzerland, derived from high-resolution pluviograph data and interpolated to a 500 m grid (Panagos et al., 2015). In addition to the baseline, ESDAC also provides future projections of R under climate change, calculated from bias-corrected regional climate model outputs (EURO-CORDEX). These projections indicate a general increase in rainfall erosivity towards 2050, especially in central and northern Europe, reflecting the expected intensification of extreme precipitation. Users can therefore choose between present-day R for baseline assessments and climate-adjusted R layers for scenario analyses in RUSLE applications.

Figure 4 - Example layer showing reference parcels and digitized landscape elements defined by Agrarmarkt Austria under the EU Horizontal CAP Regulation, annually updated, enabling precise linkage of soil erosion modelling results with field-scale agricultural units.

Figure 5 - large-scale assessments, vulnerability proxies are available from Eurostat’s experimental geospatial agricultural census datasets (multi-resolution grids, 1–80 km), providing spatially harmonised indicators on farm number, cultivated areas, farmer demographics (age, gender), livestock, labour, and production methods. While coarser in scale, these can serve as vulnerability layers when regional data are unavailable.

The soil erosion workflow is implemented using a RUSLE-based modelling approach, adapted to the regional scale of Lower Austria.

To handle geospatial data, preprocess inputs, and visualize outputs, a GIS platform such as QGIS is used. This provides the necessary functionality to manage raster and vector datasets, derive topographic parameters from the DEM, and integrate climate and land-use data.

The combination of RUSLE calculations with GIS processing ensures that erosion risk can be mapped consistently across agricultural areas and aggregated at municipal and state levels for decision support.

| Tool                                         | Type                   | Role                                                                                                                                                                                   |
| -------------------------------------------- | ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| RUSLE (Revised Universal Soil Loss Equation) | Open / empirical model | Core model to estimate average annual soil loss under current and future climate scenarios.                                                                                            |
| QGIS                                         | Open-source GIS        | Data preprocessing, derivation of LS-factor (via SAGA GIS tools), conversion of land use and soil/parcel data into necessary RUSLE factors, mapping and visualization of erosion risk. |

Table 3 – used tools and role in the Erosion Hazard workflow, all tools are free to use.

Note on deriving R, K, C and P factors

The calculation of soil erodibility (K), cover/management (C) and support practices (P) requires reclassification of local datasets (soil maps, crop parcels, or land management layers) using standard lookup tables. In the Austrian case, this could be done following the methodology of Schmaltz et al. (2023), where K is assigned to soil units, and C and P are linked to INVEKOS crop and management information.

For replication in regions where only European data are available, users may apply the pre-computed ESDAC layers (R, K at 500 m; C, P at 100 m). However, these products are relatively coarse. To increase accuracy, users may invest time in deriving R, K, C and P from more detailed meteorological, soil or parcel datasets when available, using the lookup values provided in the referenced ESDAC resources.

Figure 6 – example of 10 m Lidar derived DTM from Austrian geoportal (left) and corresponding LS factor derived in QGIS (right)

Figure 7 – examples of Rainfall Erosivity R \[MJ mm ha-1 h-1 yr-1] (left) and Soil Erodibility (K-Factor, right) from ESDAC databases.

Methodology

{% stepper %}
{% step %}
### Step 1 — Data acquisition and preparation

The first step of the workflow is the collection and preprocessing of all input datasets required to parameterize the RUSLE model. When local and national datasets are available, each factor must be recalculated specifically for the study area.

* Topography (LS-factor): directly derived from the DEM using the LS-factor function of SAGA GIS within QGIS. This ensures a spatially explicit representation of slope length and steepness adapted to local terrain conditions.
* Rainfall erosivity (R-factor), soil erodibility (K-factor), cover-management (C-factor), and support practice (P-factor): require reclassification of local data sources. Values are assigned using lookup tables based on soil maps, parcel and crop information, and national climate data.

Preprocessing includes harmonizing coordinate systems, resampling datasets to a common resolution, and rasterizing vector inputs such as field parcels or management practices.

As an alternative, where local data are not available, users may rely on the precomputed ESDAC products (R at 500 m, K/C/P at 100 m). These datasets are coarser in resolution but provide a consistent and harmonised European baseline for exploratory assessments and large-scale applications.
{% endstep %}

{% step %}
### Step 2 — Model setup and run

The modelling step corresponds to the direct application of the RUSLE formula, i.e. the multiplication of all prepared factor layers via basic raster calculator (map algebra) in GIS:

E = R × K × LS × C × P

where E is the estimated average annual soil loss (t ha⁻¹ yr⁻¹).

Each factor layer (R, K, LS, C, P) must be derived or reclassified from local datasets and harmonised to the same projection and resolution prior to calculation.

For methodological details and reference values of the factors, consult the key sources referenced (Panagos et al., SAGA-GIS documentation, ESDAC products). For simplicity, example maps may be derived directly from the RUSLE2015 soil erosion dataset published by ESDAC.
{% endstep %}

{% step %}
### Step 3 — Analysis and interpretation

The erosion hazard map derived from the RUSLE model provides the core spatial output. Analysis focuses on transforming raw model outputs into planning-relevant information:

* Aggregate the raster of mean annual soil loss (t ha⁻¹ yr⁻¹) to larger territorial units (e.g., municipal and state boundaries) to support comparison and planning.
* Identify erosion hotspots by applying thresholds to the raster map and overlaying them with cropland exposure.
* Run scenario comparisons under different climate projections (EURO-CORDEX, ÖKS15) to quantify expected changes in hazard.
* Integrate socio-economic vulnerability indicators at municipal level (farm structure, dependence on agricultural income) to highlight where physical risk coincides with lower adaptive capacity.

Figure 8 – Left: extract from the RUSLE2015 soil erosion dataset (ESDAC), showing estimated average annual soil loss (t ha⁻¹ yr⁻¹). Right: overlay of the same erosion map with INVEKOS reference parcels enabling direct linkage to field-scale agricultural units.
{% endstep %}

{% step %}
### Step 4 — NbS testing

Testing of Nature-based Solutions focuses on the introduction of multifunctional hedgerows in arable land as a measure to mitigate soil erosion. Within the RUSLE framework, the presence of hedgerows is represented through adjustments of LS- and C-factors:

* C-factor: hedgerows increase permanent vegetative cover, reduce raindrop impact and promote soil stability. Simulate this by assigning lower C values to cropland areas adjacent to or intersected by hedgerows.
* LS-factor: hedgerows interrupt slope length and alter runoff pathways, reducing the effective contributing area upslope of a pixel. Simulate by shortening slope lengths or by recalculating LS with breaks introduced along hedgerow alignments, or by modifying the DTM to account for morphological changes induced by NbS before reprocessing.

Repeat the RUSLE workflow with adjusted LS and C values representing hedgerow implementation. Compare "with" and "without NbS" maps to quantify potential reductions of annual soil loss and identify where hedgerows deliver the highest benefit.
{% endstep %}
{% endstepper %}

***

### Hazard – Agricultural drought

#### Description and context

The second hazard assessed in Innovation Lab 1 is agricultural drought, understood here as the insufficient availability of soil water to sustain crop growth during the vegetation period. Drought is assessed using an indicator-based method that combines climate variables (precipitation and temperature) with soil and land use characteristics to estimate water deficit conditions in cropland. Climate change scenarios (EURO-CORDEX, ÖKS15) are used to explore how frequency and severity of droughts may evolve under future conditions.

The objective is to provide spatially explicit drought hazard maps, comparable with the erosion analysis, and to identify where agricultural areas are most exposed to prolonged soil moisture deficits.

| Dimension | Indicator(s)                                                                   | Unit         | Purpose                                                            |
| --------- | ------------------------------------------------------------------------------ | ------------ | ------------------------------------------------------------------ |
| Hazard    | Potential crop yield loss in rainfed conditions (derived from ETa / ETn ratio) | % yield loss | Quantify drought stress on crops under baseline and future climate |

Table 4 – key indicators tracked — Agricultural Drought Hazard

#### Data sources

The assessment of agricultural drought in Innovation Lab 1 is explicitly based on the CLIMAAX Risk Workflow for agricultural systems. This CRA methodology follows an indicator-based approach that combines climate drivers, soil water holding capacity, crop exposure, and vulnerability information to derive potential yield losses under rainfed conditions. The full methodological description is available in the CLIMAAX Risk Workflow for agricultural systems.

For the regional application in Lower Austria, the CRA uses ÖKS15 climate scenarios (1 km), EURO-CORDEX simulations (12.5 km), and national meteorological observations as the basis for calculating reference evapotranspiration (ET₀) and effective evapotranspiration (ETₐ).

Soil water holding capacity is derived from national soil maps, while exposure is defined through the INVEKOS parcel dataset with crop-specific attributes. National agricultural statistics provide information on crop production and economic value, while irrigation distribution and socio-economic data from the Farm Structure Survey represent the main vulnerability layers. Elevation and climate zoning are also included.

To ensure replicability outside Austria, equivalent European open datasets can be used, such as Copernicus CDS (precipitation, temperature, evapotranspiration indices), ESDAC (soil hydraulic properties), MapSPAM/FAO-IIASA GAEZ (crop maps, yields, irrigation, climate zones), the Copernicus DEM, and Eurostat agricultural census data.

| Data type                                        | Source (Austria)                 | Role in workflow                                                 | Open/EU alternative                     |
| ------------------------------------------------ | -------------------------------- | ---------------------------------------------------------------- | --------------------------------------- |
| Climate projections (precipitation, temperature) | ÖKS15 (Austrian scenarios, 1 km) | Input for ET₀, ETn, ETa and drought hazard calculation           | Copernicus EURO-CORDEX (12.5 km /0.11°) |
| Meteorological observations                      | Austrian weather station network | Input for ET₀, ETn, ETa and drought hazard calculation           | ERA5-Land; E-OBS                        |
| Elevation                                        | National DEM Austria (10 m)      | Derivation of topographic effects and climate zoning             | Copernicus DEM                          |
| Thermal climate zones                            | —                                | Crop-specific growing conditions and evapotranspiration          | FAO-IIASA GAEZ climate zones; FGGD      |
| Soil available water capacity (AWC)              | —                                | Soil buffering capacity against drought                          | Hengl and Gupta (2019)                  |
| Crop distribution                                | INVEKOS parcel dataset           | Definition of crop types, derive Crop production map for Austria | CORINE Land Cover 2018                  |
| Crop-specific information                        | —                                | Specific parameters needed for the hazard assessment             | CLIMAAX Handbook crop table             |
| Crop production \[ton]                           | —                                | Crop production to calculate exposure                            | MapSPAM repository                      |
| Crops aggregated value                           | —                                | Second exposure dataset                                          | FAO-GAEZ                                |
| Irrigation availability                          | —                                | Cropland full-irrigation availability to define vulnerability    | GAEZ v5 — Share of irrigated land       |

Table 5 – used data, and alternative datasets to replicate the assessment outside the study area, when available

References and resources

* https://esdac.jrc.ec.europa.eu/themes/rusle2015
* https://savoursoilpermaculture.com/the-ecological-significance-of-hedgerows-a-multidimensional-approach/
* https://www.sciencedirect.com/science/article/abs/pii/S1161030109000653
