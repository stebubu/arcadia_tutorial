# cro krapina zagorje draft2

### Introduction and Objectives of the Climate Risk Assessment

#### Regional context

The [Krapina-Zagorje County](https://en.wikipedia.org/wiki/Krapina-Zagorje_County), in northwestern Croatia near the Slovenian border, is predominantly rural with dispersed settlements, agricultural land, and forested hills, alongside small urban centres providing regional services. Two Innovation Labs serve as focal points for local experimentation with Nature-Based Solutions (NbS): the City of Zabok (urban greening and the reGENERATOR cultural hub) and the Hum na Sutli – Pregrada – Desinić area (slope stabilisation and erosion prevention in landslide-prone terrain).

> Figure 1 Center for urban culture reGENERATOR in the City of Zabok, (c) [Grad Zabok](https://www.zabok.hr/re-generator/)

[Zagreb](https://en.wikipedia.org/wiki/Zagreb), Croatia’s capital and largest urban area, provides a contrasting metropolitan context: dense urban development, critical infrastructure, and strong demographic/economic dynamics. The Zagreb Innovation Lab addresses NbS for urban microclimate regulation, stormwater management, and resilience of public spaces—complementing the rural/small-town setting of Krapina-Zagorje and illustrating regional diversity.

_Figure 2 Therapeutic garden established as part of the proGIreg project at the co-Innovation lab Sljeme, Sesvete, (c)_ [_proGIreg_](https://progireg.eu/fileadmin/user_upload/Zagreb/ProGIreg_NBS3_Therapy_Garden_Zagreb.pdf)

_Figure 3 Former slaughterhouse and livestock market Zagrepčanka, City of Zagreb, (c)_ [_Grad Zagreb_](https://www.zagreb.hr/zagrepcanka/173671)

Climatic conditions across both regions reflect continental patterns with marked seasonality in temperature and precipitation. Historical records highlight variability in rainfall intensity, heat extremes, and local wind events, while flood hazard maps delineate areas vulnerable to riverine and pluvial flooding.

This Climate Risk Assessment (CRA) focuses on three main hazards—floods, heatwaves, and windstorms—to illustrate the methodology through a simplified tutorial example. These hazards were selected for their relevance to demographic, infrastructural, and environmental vulnerabilities and because they can be consistently assessed with harmonized datasets. This selection does not exhaust the full range of relevant hazards (e.g., droughts, fires, erosion, biodiversity impacts, health, tourism, infrastructure impacts) which should be considered in comprehensive regional assessments.

_Figure 4 - model regions and the Krapina-Zagorje and Zagreb area._

#### Scope of the tutorial

This tutorial presents a simplified and replicable CRA workflow for two Croatian regions—Krapina-Zagorje County and the City of Zagreb—focusing on three cross-regional hazards: floods, heatwaves, and windstorms.

The workflow combines meteorological time series, European climate indicators (Copernicus), regional modelling outputs (RegCM4), and flood probability maps from the Joint Research Centre. While applied to urban and rural contexts here, the approach is transferable: regions can reproduce the steps by substituting local datasets and adjusting parameters to their hazard profile.

{% hint style="info" %}
Disclaimer

This tutorial is a didactic example and does not replace software-specific documentation (e.g., GIS, hydrological or climate modelling tools). Users should be familiar with basic geospatial data formats, pre-processing techniques, and modelling concepts. The workflow illustrates methodological steps rather than exhaustive operational guidance; comprehensive assessments should integrate additional hazards and sectoral indicators in line with the IVAVIA methodology and stakeholder priorities.
{% endhint %}

#### CRA objectives

The CRA developed for the Krapina-Zagorje and Zagreb regions aims to characterize risks associated with floods, heatwaves, and windstorms using historical meteorological data, European climate indicators, and regional hazard mapping.

Main objectives:

* Identify and analyse the key climate threats affecting the regions.
* Assess risks as the combination of hazard probability and potential adverse impacts on exposed populations, infrastructures, and buildings.
* Provide a structured, evidence-based foundation for regional decision-making and adaptation planning.
* Support the integration of climate risk considerations into policies and strategies at local and regional level.

This workflow centres on Climate Risk Assessment as a first step to produce robust evidence of climate threats and vulnerabilities, which can then inform, prioritize, and later complement NbS design.

The CRA applies the [IVAVIA methodology](https://www.researchgate.net/publication/330005248_IVAVIA_Impact_and_Vulnerability_Analysis_of_Vital_Infrastructures_and_Built-Up_Areas_13th_International_Conference_CRITIS_2018_Kaunas_Lithuania_September_24-26_2018_Revised_Selected_Papers), integrating hazard, exposure, sensitivity, and adaptive capacity into a clear and replicable framework.

#### Intended users

Intended users include:

* Regional and municipal authorities (spatial planning, infrastructure, local policies).
* Civil protection agencies (preparedness and emergency response).
* Policymakers at county and city levels (long-term adaptation strategies).
* Environmental organizations, research institutions, and NGOs (conservation, sustainability, NbS promotion).

The CRA provides a structured, data-driven foundation for decision-making in both urban (Zagreb) and rural (Krapina-Zagorje) contexts.

***

### Integrated Multi-Hazard Climate Risk Assessment Workflow (IVAVIA-based)

#### Description and context

This IVAVIA-based workflow covers both Krapina-Zagorje and Zagreb regions. The CRA focuses on floods, heatwaves, and windstorms. The workflow integrates climate data with socio-economic information to support adaptation planning.

Key indicators selected for illustrative purposes:

| Dimension    | Indicator(s)                                            | Unit                                  | Purpose                                                             |
| ------------ | ------------------------------------------------------- | ------------------------------------- | ------------------------------------------------------------------- |
| Flood hazard | Flood probability zones (fluvial/pluvial)               | Map classes / % area                  | Identify areas exposed to flooding; provide spatial hazard baseline |
| Heatwave     | Number of hot days / temperature extremes               | Days per year / °C                    | Capture intensity and frequency of extreme heat events              |
| Windstorm    | Maximum wind speed (daily/monthly)                      | m/s                                   | Characterize occurrence and magnitude of damaging wind events       |
| Exposure     | Population density in hazard-prone areas                | Inhabitants/km²                       | Quantify people and assets potentially affected                     |
| Exposure     | Built environment (building footprints, infrastructure) | Count, km², or km (depending dataset) | Identify physical assets and infrastructure at risk                 |

_Table 1 – key indicators tracked — multi-hazard CRA_

#### Data sources and tools

CRA relies on meteorological observations, hazard maps, and geospatial datasets describing exposure and vulnerability.

* Historical climate data: Croatian Meteorological and Hydrological Service (DHMZ) — daily/monthly temperature, precipitation, wind speed.
* Flood hazard: national flood probability maps; European products from JRC and Copernicus where local access is restricted.
* Exposure layers: population density grids (census or WorldPop), building footprints (DGU portal or OpenStreetMap), administrative boundaries (national registries or GADM).

Vulnerability is addressed through socio-economic indicators and adaptive capacity proxies; this tutorial includes simplified examples.

_Figure 5 – example of precipitation monitoring stations network, source_ [_DMZH_](https://meteo.hr/infrastruktura_e.php?section=mreze_postaja\&param=pmm\&el=kisomjerne)

Datasets for a hybrid workflow:

* The tutorial adopts a hybrid workflow combining GIS-based spatial layers (flood maps, population, buildings) with non-spatial outputs (composite indicators, charts, time series). Examples mainly use openly available European datasets (Copernicus, ERA5-Land); national datasets should replace them where available.

Data table (selected rows):

| Data type / Dimension        | Source (local / national)                             | Role in workflow                                                          | Open/EU alternative                                                                                                                                                                                       |
| ---------------------------- | ----------------------------------------------------- | ------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Flood hazard                 | Flood probability maps (national agencies, e.g., DGU) | Define areas exposed to riverine and pluvial flooding                     | River flood hazard maps for Europe (JRC) https://data.jrc.ec.europa.eu/dataset/1d128b6c-a4ee-4858-9e34-6210707f3c81                                                                                       |
| Precipitation extremes       | DHMZ / RegCM4 baseline grid 12.5 km                   | Input for flood hazard (pluvial flooding) and standalone hazard indicator | ERA5-Land https://cds.climate.copernicus.eu/datasets/reanalysis-era5-land?tab=download; Copernicus Climate Indicators https://cds.climate.copernicus.eu/datasets/sis-ecde-climate-indicators?tab=overview |
| Exposure – Population        | Local census (may be restricted)                      | Quantify people potentially affected                                      | WorldPop https://dx.doi.org/10.5258/SOTON/WP00646; HDX Croatia population https://data.humdata.org/dataset/croatia-high-resolution-population-density-maps-demographic-estimates                          |
| Exposure – Built environment | DGU GIS portal (may be limited)                       | Identify exposed assets and infrastructure                                | OpenStreetMap building layer https://osmbuildings.org/                                                                                                                                                    |
| Administrative boundaries    | DGU GIS portal (may be limited)                       | Isolate area/city of interest                                             | GADM https://gadm.org/download\_country.html                                                                                                                                                              |

_Table 2 – used data, alternative datasets to replicate the assessment outside the study area_

Climate change effects:

* Future risk assessment integrates RegCM4 (12.5 km, EURO-CORDEX/Med-CORDEX) and Copernicus climate indicators (0.25°) under RCP4.5 and RCP8.5 for near future (2011–2040) and mid-century (2041–2070). National datasets provide finer detail; European datasets provide pre-aggregated indicators ready for CRA workflows.

Note – Flood hazard maps:

* Large-scale European products mainly represent fluvial flooding at coarse resolution. Include more accurate pluvial and riverine maps from national/regional agencies when available.

Tools:

| Tool                      | Type | Role                                                                                                                            |
| ------------------------- | ---- | ------------------------------------------------------------------------------------------------------------------------------- |
| [QGIS](https://qgis.org/) | Open | Core platform for loading datasets, overlaying hazard and exposure layers, computing zonal statistics, and visualizing results. |

_Table 3 – used tools and role in the Multi-Hazard CRA Workflow_

***

#### Methodology

{% stepper %}
{% step %}
### Step 1 — Data acquisition and preparation

* Load multiband raster files containing annual climate indicators (pre-computed annual statistics: yearly counts, annual maxima, annual extremes). Each band represents a year (temporal stack).
* Clip raster layers to the study area using administrative boundaries.
* Selected illustrative indicators:
  * Heat hazard → Hot days (days with Tmax > 30 °C)
  * Precipitation hazard → Extreme precipitation days (days above the 95th percentile, 1981–2010)
  * Wind hazard → Extreme wind speed days (days above the 98th percentile, 1981–2010)
  * Flood hazard → River flood depth maps (e.g., 100-year return period)
* Extract time series for pixels or polygons of interest and export to CSV from QGIS (e.g., using the Value Tool plugin).
* Note: For local station data or higher-frequency datasets (RegCM4, ERA5-Land hourly), derive indicators from sub-daily rasters—this typically requires scripting (GDAL, CDO).
{% endstep %}

{% step %}
### Step 2 — Indicators and normalization

Hazard (time series):

* Normalise meteorological hazard indicators with min–max method using minima and maxima across the full series (baseline + projections).
* Aggregate annual values into 30-year climatological windows (e.g., 1991–2020, 2021–2050, 2041–2070, 2071–2100) and normalise the mean within each window:

X\* = (X - Xmin) / (Xmax - Xmin)

Note: Dataset-derived minima/maxima spread values across \[0,1] but may misrepresent extremes; apply literature thresholds with stakeholder agreement if needed.

Example normalized 30-year means (illustrative):

| Window    | Wind norm | Hot norm | Precip norm |
| --------- | --------- | -------- | ----------- |
| 1991–2020 | 0.4216    | 0.1322   | 0.2942      |
| 2021–2050 | 0.4118    | 0.2011   | 0.4232      |
| 2041–2070 | 0.4039    | 0.2877   | 0.4168      |
| 2071–2100 | 0.4076    | 0.5222   | 0.4738      |

Hazard (flood map):

* Derive mean flood depth within polygon (zonal statistics). Normalise using a reference minimum and maximum (e.g., Hmin = 0 m; Hmax = maximum observed depth or literature threshold):

Hflood = (Hfloodraw - Hmin) / (Hmax - Hmin)

Example: mean = 0.97 m, min = 0.11 m, max = 2.55 m → Hflood = 0.37
{% endstep %}

{% step %}
### Step 3 — Sensitivity, Exposure, Adaptive Capacity, and Risk aggregation

Sensitivity (examples, normalized 0–1):

* Heat: share of elderly (>65) and children (<15) → 0.41
* Wind: density of residential (fragile) buildings → 0.61
* Precipitation: share of impermeable surfaces → 0.75
* Flood: share of ground-floor residential area in footprints → 0.54

Exposure:

* Heat/Wind/Precipitation (time-series uniform over area): assumed total EX = 1.00 (illustrative)
* Flood: spatially differentiated; intersect flood depth map with building footprints and population grids. Example normalized exposure ≈ 0.25

Adaptive capacity (illustrative examples):

* Heat: health services, cooling shelters, greening → 0.60
* Wind: building standards, warning systems → 0.50
* Precipitation: drainage and green infrastructure → 0.40
* Flood: structural defences and readiness → 0.30

Vulnerability aggregation:

* Following IVAVIA, combine sensitivity (SE) and adaptive capacity (AC). This tutorial uses a simple weighted arithmetic mean (unit weights) for didactic clarity:

V = (SE + (1 - AC)) / 2

Risk aggregation:

* Final risk score R integrates Hazard (H), Exposure (EX), and Vulnerability (V) equally:

R = (H + V + EX) / 3

Illustrative composite results (values are didactic approximations):

Heat Hazard (Hot Days)

* H = 0.52; SE = 0.41; AC = 0.60 → V = 0.41; EX = 1.00 → R = (0.52 + 0.41 + 1.00) / 3 = 0.643

Wind Hazard (Extreme Wind)

* H = 0.41; SE = 0.61; AC = 0.50 → V = 0.555; EX = 1.00 → R = (0.41 + 0.555 + 1.00) / 3 = 0.655

Precipitation Hazard (Extreme Precip)

* H = 0.47; SE = 0.75; AC = 0.40 → V = 0.675; EX = 1.00 → R = (0.47 + 0.675 + 1.00) / 3 = 0.715

Flood Hazard (100-yr mean depth)

* H = 0.37; SE = 0.54; AC = 0.30 → V = 0.62; EX = 0.25 → R = (0.37 + 0.62 + 0.25) / 3 = 0.413

Notes:

* IVAVIA provides several aggregation methods; weights should be defined and validated with stakeholders in operational settings.
* Sensitivity, exposure, and adaptive-capacity indicators should be adapted to local data and contexts.
{% endstep %}
{% endstepper %}

***

#### Outputs and visualizations

Effective communication requires visual outputs:

* Time-series plots: show temporal evolution of hazard indicators under historical and RCP scenarios (e.g., hot days, extreme precipitation days, wind extremes).
* Geospatial maps: display spatial distribution of risks, flood hazard overlaid with population or building footprints to identify vulnerable hotspots.
* Composite maps: integrate multiple hazards, sensitivity, and adaptive capacity to reveal cross-sectoral vulnerabilities.

Adjusting climate trends with local data:

* Statistical downscaling (e.g., quantile mapping, Quantile Delta Mapping, QPLAD) can correct biases and downscale large-scale datasets to local contexts without distorting trends in extremes (see Gergel et al., 2024).

_Figure 10 - Combined plots comparing historical reanalysis with RCP8.5 projections._

_Figure 11 - Example geospatial map displaying hazard zones such as flood risk maps._

_Figure 12 - Example maps: flood, erosion, fire, landslide risk._

***

### Annex — Sectoral Climate Risk Models (Zagreb case study examples)

This annex summarises sectoral examples of hazard, exposure, sensitivity, and adaptive capacity indicators used in the Zagreb CRA (IVAVIA-based). Tables illustrate how these indicators combine into vulnerability and risk indices. These are illustrative and should be adapted to local datasets and stakeholder inputs.

Example risk elements and indicators (selected highlights):

* Threat (hazard): IPCC scenarios RCP4.5/RCP8.5; change in Tmax, warm nights, very hot days, consecutive dry/rainy days, days with heavy precipitation (>20 mm), Rx1d.
* Exposure: population density, road/rail infrastructure, hospitals, industrial facilities, waste sites.
* Sensitivity: number of inhabitants, youth/elderly population, settlement density, projected demographic changes.
* Adaptive capacity: hospitals/doctors per capita, proportion of green areas, length of levees, education level, GDP per capita.

Sector examples (selected):

Water Management — Floods

* Hazard: Rx1d, days >20 mm, consecutive rainy days.
* Exposure: population density, water supply connections, length of drainage network.
* Sensitivity: past flood occurrence, water safety.
* Adaptive capacity: flood defences, readiness, drainage functionality, integrated urban stormwater management.

Agriculture — Drought & Floods

* Hazard: Tmax, very hot days, consecutive dry days; heavy precipitation indicators for floods.
* Exposure: number of agricultural holdings, ARKOD area share, employment in agriculture.
* Sensitivity: crop distribution, soil quality, estimated economic damage.
* Adaptive capacity: irrigation availability, institutional/financial support, farmers’ education.

Forestry — Fire & Storm

* Hazard: Tmax, very hot days, consecutive dry days, Storm event frequency.
* Exposure: forest areas, parks, employment in forestry.
* Sensitivity: SSR fire severity index, area at high fire danger, forest age/health.
* Adaptive capacity: institutional capacity, density of firebreaks, fire protection plans, forest maintenance.

Health — Heatwave

* Hazard: average daily temperature, hot days, tropical nights.
* Exposure: population density, workers in outdoor occupations, sensitive institutions.
* Sensitivity: built-up area, share of sensitive age groups, vulnerable population share.
* Adaptive capacity: share of urban green/blue infrastructure, healthcare availability, emergency coverage, heatwave warning systems.

Buildings, Transport, Energetics, Tourism, Biodiversity — similar sector-specific indicators described in the original annex.

Example composite risk summary for Water Management (illustrative):

| Element                              | Normalized Indicator Value |
| ------------------------------------ | -------------------------- |
| H: consecutive rainy days            | 0.54                       |
| H: days >20 mm                       | 0.59                       |
| H: Rx1d                              | 0.52                       |
| SE: occurrence of floods             | 1.00                       |
| SE: safety and water quality         | 0.10                       |
| SE: households w/o water supply      | 0.03                       |
| AC: flood protection system          | 0.50                       |
| AC: readiness                        | 0.10                       |
| AC: drainage functionality           | 0.80                       |
| AC: integrated stormwater management | 0.70                       |
| Composite V (f(SE,AC))               | 0.45                       |
| EX: population density               | 1.00                       |
| EX: water supply connections         | 0.97                       |
| EX: drainage length in flood area    | 0.45                       |
| Overall risk rating (R = f(H,V,EX))  | 0.60                       |

_Table 11 - Example composite risk calculation following IVAVIA (illustrative values)._

***

End of document.
