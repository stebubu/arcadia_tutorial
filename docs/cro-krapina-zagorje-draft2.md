## Introduction and Objectives of the Climate Risk Assessment

### Regional context.

The [<span class="underline">Krapina-Zagorje
County</span>](https://en.wikipedia.org/wiki/Krapina-Zagorje_County) ,
in northwestern Croatia near the Slovenian border, is a predominantly
rural area with dispersed settlements, agricultural land, and forested
hills, alongside small urban centres providing regional services. Two
Innovation Labs serve as focal points for local experimentation with
Nature-Based Solutions (NbS): the City of Zabok, where urban greening
and the reGENERATOR cultural hub form the core of planned interventions,
and the Hum na Sutli – Pregrada – Desinić area, focusing on slope
stabilisation and erosion prevention in landslide-prone terrain.

![re-GENERATOR - Grad
Zabok](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/CRO-Krapina-Zagorje_draft2_media/media/image8.png)

> *Figure 1 Center for urban culture reGENERATOR in the City of Zabok,
> (c) [<span class="underline">Grad
> Zabok</span>](https://www.zabok.hr/re-generator/)*

[<span class="underline">Zagreb</span>](https://en.wikipedia.org/wiki/Zagreb),
Croatia’s capital and largest urban area, provides a contrasting
metropolitan context. With dense urban development, critical
infrastructure, and strong demographic and economic dynamics, the Zagreb
Innovation Lab addresses **NbS for urban microclimate regulation,
stormwater management, and resilience of public spaces**. Its focus
complements the more rural and small-town setting of Krapina-Zagorje,
together illustrating the diversity of regional challenges.

![Immagine che contiene pianta, albero, erba, Aerofotogrammetria Il
contenuto generato dall'IA potrebbe non essere
corretto.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/CRO-Krapina-Zagorje_draft2_media/media/image14.png)

*Figure 2 Therapeutic garden established as part of the proGIreg project
at the co-Innovation lab Sljeme, Sesvete, (c)
[<span class="underline">proGIreg</span>](https://progireg.eu/fileadmin/user_upload/Zagreb/ProGIreg_NBS3_Therapy_Garden_Zagreb.pdf)*

![Immagine che contiene Aerofotogrammetria, aria aperta, aereo, Vista
aerea Il contenuto generato dall'IA potrebbe non essere
corretto.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/CRO-Krapina-Zagorje_draft2_media/media/image6.jpg)

*Figure 3 Former slaughterhouse and livestock market Zagrepčanka, City
of Zagreb, (c) [<span class="underline">Grad
Zagreb</span>](https://www.zagreb.hr/zagrepcanka/173671)*

Climatic conditions across both regions reflect continental patterns
with marked seasonality in temperature and precipitation. Historical
records highlight variability in rainfall intensity, heat extremes, and
local wind events, while flood hazard maps delineate areas vulnerable to
riverine and pluvial flooding.

The Climate Risk Assessment (CRA) presented here focuses on **three main
hazards—floods, heatwaves, and windstorms**—to illustrate the
methodology through a simplified tutorial example. These hazards were
selected because they capture some of the most relevant interactions
with demographic, infrastructural, and environmental vulnerabilities,
and can be consistently assessed with harmonized datasets. However, this
does **not exhaust the full range of climate hazards** relevant to the
Krapina-Zagorje and Zagreb regions. As highlighted in the original CRA
documents and the IVAVIA methodology, additional hazards such as
droughts, fires, erosion, and impacts on biodiversity, health, tourism,
and infrastructure may also play a critical role and should be
considered in comprehensive regional assessments.

](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/CRO-Krapina-Zagorje_draft2_media/media/image5.png)

*Figure 4 - model regions and the Krapina-Zagorje and Zagreb area.*

### Scope of the tutorial.

This tutorial presents a simplified and replicable Climate Risk
Assessment (CRA) workflow for two Croatian regions—**Krapina-Zagorje
County** and the **City of Zagreb**—as part of broader climate change
mitigation and adaptation efforts. For demonstration purposes, the CRA
focuses on **three hazards of cross-regional relevance: floods,
heatwaves, and windstorms**.

The workflow combines meteorological time series, European climate
indicators (Copernicus), regional modelling outputs (RegCM4), and flood
probability maps from the Joint Research Centre. While applied here to
selected local contexts (urban and rural), the approach is
**transferable**: regions can reproduce the steps by substituting local
datasets and adjusting parameters to their hazard profile.

  - ##### Disclaimer

> This tutorial serves as a **didactic example** and does not replace
> software-specific documentation (e.g., GIS, hydrological or climate
> modelling tools). Users are expected to be familiar with basic
> geospatial data formats, pre-processing techniques, and modelling
> concepts. The workflow illustrates methodological steps rather than
> providing exhaustive operational guidance; comprehensive assessments
> should integrate additional hazards and sectoral indicators in line
> with the **IVAVIA methodology** and stakeholder priorities.

### CRA objectives.

The Climate Risk Assessment (CRA) developed for the **Krapina-Zagorje**
and **Zagreb** regions aims to characterize risks associated with
**floods, heatwaves, and windstorms**, using historical meteorological
data, European climate indicators, and regional hazard mapping.

The main objectives are to:

  - > Identify and analyse the key climate threats affecting the
    > regions.

  - > Assess risks as the combination of hazard probability and
    > potential adverse impacts on exposed populations, infrastructures,
    > and buildings.

  - > Provide a structured, evidence-based foundation for regional
    > decision-making and adaptation planning.

  - > Support the integration of climate risk considerations into
    > policies and strategies at local and regional level.

Unlike other tutorials that focus primarily on **Nature-Based Solutions
(NbS) design and evaluation**, this workflow is explicitly cantered on
**Climate Risk Assessment as a first step**. The emphasis is on
producing **robust evidence of climate threats and vulnerabilities**,
which can then serve as a baseline to inform, prioritize, and later
complement NbS design. T

The CRA applies the [<span class="underline">**IVAVIA
methodology**,</span>](https://www.researchgate.net/publication/330005248_IVAVIA_Impact_and_Vulnerability_Analysis_of_Vital_Infrastructures_and_Built-Up_Areas_13th_International_Conference_CRITIS_2018_Kaunas_Lithuania_September_24-26_2018_Revised_Selected_Papers)
integrating hazard, exposure, sensitivity, and adaptive capacity into a
clear and replicable framework for climate risk analysis.

### Intended users.

  
The Climate Risk Assessment (CRA) developed for the **Krapina-Zagorje**
and **Zagreb** regions is designed for a broad spectrum of users
involved in climate adaptation and risk management.

Regional and municipal authorities can use the results to integrate
climate risks into **spatial planning, infrastructure development, and
local policies**. **Civil protection agencies** benefit from the outputs
to enhance preparedness and emergency response capacity, while
**policymakers** at county and city levels gain an evidence base for
designing long-term adaptation strategies.

The CRA is also relevant for **environmental organizations, research
institutions, and NGOs**, which can apply the findings to support
conservation, sustainability initiatives, and the promotion of
nature-based approaches. In both urban (Zagreb) and rural
(Krapina-Zagorje) contexts, the CRA provides a **structured, data-driven
foundation** for decision-making, ensuring that adaptation measures are
tailored to the vulnerabilities and priorities of the regions.

## Integrated Multi-Hazard Climate Risk Assessment Workflow (IVAVIA-based)

### Description and context

The Integrated Multi-Hazard Climate Risk Assessment Workflow
(IVAVIA-based) presented here covers both the **Krapina-Zagorje** and
**Zagreb** regions. While the former is a predominantly rural inland
county with dispersed settlements, agricultural land, and forested
hills, and the latter a major urban centre with dense built-up areas and
critical infrastructures, both regions are increasingly exposed to
climate-related risks.

In this tutorial, the Climate Risk Assessment (CRA) focuses on three
hazards of primary concern: **floods, heatwaves, and windstorms**. These
hazards interact with local vulnerabilities in demographic,
infrastructural, and environmental systems, shaping overall exposure and
risk. The workflow provides a structured basis for integrating climate
data with socio-economic information to support adaptation planning.

The table below summarizes the **key indicators** selected for
illustrative purposes at this stage. It serves as an introductory
overview; the detailed calculation of each indicator is developed in the
methodology section of the workflow.

| **Dimension**    | **Indicator(s)**                                               | **Unit**                                 | **Purpose**                                                         |
| ---------------- | -------------------------------------------------------------- | ---------------------------------------- | ------------------------------------------------------------------- |
| Flood hazard     | Flood probability zones (fluvial/pluvial)                      | Map classes / % area                     | Identify areas exposed to flooding; provide spatial hazard baseline |
| Heatwave hazard  | Number of hot days / temperature extremes                      | Days per year / °C                       | Capture intensity and frequency of extreme heat events              |
| Windstorm hazard | Maximum wind speed (daily/monthly)                             | m/s                                      | Characterize occurrence and magnitude of damaging wind events       |
| Exposure         | Population density in hazard-prone areas                       | Inhabitants/km²                          | Quantify people and assets potentially affected                     |
| Exposure         | Built environment (building footprints, infrastructure assets) | Count, km², or km (depending on dataset) | Identify physical assets and infrastructure at risk                 |

*Table 1 – key indicators tracked- multi-Hazard CRA*

### Data sources and tools

The Climate Risk Assessment (CRA) for the Krapina–Zagorje and Zagreb
regions relies on a combination of **meteorological observations, hazard
maps, and geospatial datasets** describing exposure and vulnerability.

**Historical climate data** are provided by the Croatian Meteorological
and Hydrological Service (DHMZ), with daily and monthly values of
temperature, precipitation, and wind speed. These allow the derivation
of indicators such as hot days, extreme precipitation, and windstorm
intensity. (Figure 3)

**Flood hazard information** is supported by national flood probability
maps, complemented—where local access is restricted—by European-scale
products from JRC and Copernicus.

**Exposure layers** include **population density grids** (from census or
global datasets such as World Pop) and **building footprints** (from the
DGU portal or OpenStreetMap). Administrative boundaries from national
registries or global sources (e.g., GADM) delineate the study areas.

In line with the IVAVIA methodology, vulnerability is addressed through
socio-economic indicators and adaptive capacity proxies, **though in
this tutorial only simplified examples are included.**

![Immagine che contiene mappa, testo, atlante Il contenuto generato
dall'IA potrebbe non essere
corretto.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/CRO-Krapina-Zagorje_draft2_media/media/image12.png)

*Figure 5 – example of precipitation monitoring statins network in the
area , source
[<span class="underline">DMZH</span>](https://meteo.hr/infrastruktura_e.php?section=mreze_postaja&param=pmm&el=kisomjerne)*

  - ##### Datasets for a hybrid workflow

> The tutorial adopts a **hybrid workflow**, combining GIS-based spatial
> layers (e.g., flood maps, population, buildings) with non-spatial
> outputs such as composite indicators, charts, and time series. For
> replicability, most examples are based on openly available European
> datasets (e.g., Copernicus climate indicators, ERA5-Land), while
> national datasets—when available—should replace them for higher
> accuracy.

<table>
<thead>
<tr class="header">
<th><strong>Data type / Dimension</strong></th>
<th><strong>Source (local / national)</strong></th>
<th><strong>Role in workflow</strong></th>
<th><strong>Open/EU alternative</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Flood hazard</strong></td>
<td>Flood probability maps (national agencies, e.g. DGU)</td>
<td>Define areas exposed to riverine and pluvial flooding</td>
<td><a href="https://data.jrc.ec.europa.eu/dataset/1d128b6c-a4ee-4858-9e34-6210707f3c81"><span class="underline">River flood hazard maps for Europe and the Mediterranean Basin region</span></a> (fluvial flood only), see note after the table</td>
</tr>
<tr class="even">
<td><strong>Precipitation extremes</strong></td>
<td><p><a href="https://meteo.hr/index_en.php"><span class="underline">DHMZ</span></a> – Krapina Main Meteorological Station (1994–2020, daily/monthly precipitation, extremes)</p>
<p>(upon request)</p>
<p><a href="https://repozitorij.meteo.hr/en/islandora/object/meteo%3A11"><span class="underline">RegCM4</span></a> baseline grid 12.5 km (HPC Velebit, EURO-CORDEX downscaled reanalysis)</p>
<p>Include climate projections (see note after the table)</p></td>
<td><p>Input for flood hazard (pluvial flooding)</p>
<p>and used as standalone hazard indicator</p></td>
<td><p><a href="https://cds.climate.copernicus.eu/datasets/reanalysis-era5-land?tab=download"><span class="underline">ERA5-Land hourly data from 1950 to present</span></a></p>
<p>(5 km)</p>
<p><a href="https://cds.climate.copernicus.eu/datasets/sis-ecde-climate-indicators?tab=overview"><span class="underline">Climate indicators for Europe from 1940 to 2100</span></a> derived from reanalysis <span class="underline">and climate projections (0.25°)</span></p></td>
</tr>
<tr class="odd">
<td><strong>Heatwave hazard</strong></td>
<td><p><a href="https://meteo.hr/index_en.php"><span class="underline">DHMZ</span></a> – Krapina Main Meteorological Station (temperature, hot days, extremes, 1994–2020)</p>
<p><a href="https://repozitorij.meteo.hr/en/islandora/object/meteo%3A11"><span class="underline">RegCM4</span></a> baseline grid 12.5 km (HPC Velebit, EURO-CORDEX downscaled reanalysis)</p>
<p>Include climate projections (see note after the table)</p></td>
<td>Derive indicators of extreme heat and heatwaves</td>
<td><p><a href="https://cds.climate.copernicus.eu/datasets/reanalysis-era5-land?tab=download"><span class="underline">ERA5-Land hourly data from 1950 to present</span></a></p>
<p>(5 km)</p>
<p><a href="https://cds.climate.copernicus.eu/datasets/sis-ecde-climate-indicators?tab=overview"><span class="underline">Climate indicators for Europe from 1940 to 2100</span></a> derived from reanalysis <span class="underline">and climate projections (0.25°)</span></p></td>
</tr>
<tr class="even">
<td><strong>Windstorm hazard</strong></td>
<td><p><a href="https://meteo.hr/index_en.php"><span class="underline">DHMZ</span></a> – Krapina Main Meteorological Station (wind speed, 1994–2020)</p>
<p><a href="https://repozitorij.meteo.hr/en/islandora/object/meteo%3A11"><span class="underline">RegCM4</span></a> baseline grid 12.5 km (HPC Velebit, EURO-CORDEX downscaled reanalysis)</p>
<p>Include climate projections (see note after the table)</p></td>
<td>Characterize occurrence and intensity of wind hazards</td>
<td><p><a href="https://cds.climate.copernicus.eu/datasets/reanalysis-era5-land?tab=download"><span class="underline">ERA5-Land hourly data from 1950 to present</span></a></p>
<p>(5 km)</p>
<p><a href="https://cds.climate.copernicus.eu/datasets/sis-ecde-climate-indicators?tab=overview"><span class="underline">Climate indicators for Europe from 1940 to 2100</span></a> derived from reanalysis <span class="underline">and climate projections (0.25°)</span></p></td>
</tr>
<tr class="odd">
<td><strong>Exposure – Population</strong></td>
<td>Local statistical datasets (county census; Croatian) may be restricted</td>
<td>Quantify people potentially affected</td>
<td><p><a href="https://dx.doi.org/10.5258/SOTON/WP00646"><span class="underline">World pop Hub</span></a> (raster 100m)</p>
<p><a href="https://data.humdata.org/dataset/croatia-high-resolution-population-density-maps-demographic-estimates"><span class="underline">The Humanitarian Data Exchange</span></a></p></td>
</tr>
<tr class="even">
<td><strong>Exposure – Built environment</strong></td>
<td><a href="https://geoportal.dgu.hr/?utm_source=chatgpt.com#/menu/podaci-i-servisi"><span class="underline">DGU GIS portal</span></a> (may be limited to registered users)</td>
<td>Identify exposed assets and infrastructure</td>
<td>OpenStreetMap building layer (<a href="https://osmbuildings.org/"><span class="underline">vector, global)</span></a></td>
</tr>
<tr class="odd">
<td><strong>Administrative boundaries</strong></td>
<td><a href="https://geoportal.dgu.hr/?utm_source=chatgpt.com#/menu/podaci-i-servisi"><span class="underline">DGU GIS portal</span></a> (may be limited to registered users)</td>
<td>Isolate area/city of interest</td>
<td><a href="https://gadm.org/download_country.html"><span class="underline">gadm.org</span></a></td>
</tr>
</tbody>
</table>

*Table 2 – used data, an alternative dataset to replicate the assessment
outside the study area, when available*

  - ##### Climate change effects 

> *Future risk assessment integrates climate projections from*
> *[<span class="underline">RegCM4</span>](https://repozitorij.meteo.hr/en/islandora/object/meteo%3A11)
> (12.5 km resolution, EURO-CORDEX/Med-CORDEX) and Copernicus climate
> indicators (0.25°). These provide annual indicators and time series
> under RCP 4.5 and RCP 8.5 for the near future (2011–2040) and
> mid-century (2041–2070). While national datasets (e.g., RegCM4)
> provide finer spatial and temporal detail, European datasets offer
> pre-aggregated indicators, simplifying their direct use in CRA
> workflows.*

  - ##### Note – Flood hazard maps  
    *The flood hazard component here relies on large-scale European products, which mainly represent fluvial flooding at coarse resolution. More accurate pluvial and riverine flood risk maps should be included whenever available from national or regional agencies. Users seeking high-resolution analysis can refer to dedicated tutorials on flood modelling, which use local DEMs and hydrological data.*

Given the orientation of this tutorial toward climate risk assessment
based on time-series and geospatial data, the main operational
requirement is a GIS platform. In practice, beyond the use of standard
office suites or spreadsheets for tabular data management, GIS is the
only tool strictly necessary to implement the workflow described here.

Some operations (e.g., raster aggregation, downscaling, or customized
indicator computation from high-frequency data) can be automated through
simple scripting using libraries such as GDAL or CDO. However, such
tasks fall outside the scope of this tutorial, which focuses on
demonstrating the CRA workflow through existing, user-friendly tools.

](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/CRO-Krapina-Zagorje_draft2_media/media/image25.png)

*Figure 6 - Comparison of spatial resolution and processing level
between national and European datasets. Left: near-surface air
temperature (TAS, 2 m) from the Croatian RegCM4 regional climate model
at \~12.5 km resolution, shown here as a raw climate variable with
sub-daily (3-hourly) time steps. Right: annual hot days indicator
(number of days with Tmax \> 30 °C) from the Copernicus Climate
Indicators dataset at 0.25° resolution (\~25 km). The figure highlights
both the finer spatial detail of the national dataset and the advantage
of the European dataset in providing pre-aggregated annual indicators
ready for risk assessment. (note that also EU based dataset like
ERA5-Land hourly data may provide higher resolution).*

| **Tool**                                                 | **Type** | **Role**                                                                                                                        |
| -------------------------------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------- |
| [<span class="underline">QGIS</span>](https://qgis.org/) | Open     | Core platform for loading datasets, overlaying hazard and exposure layers, computing zonal statistics, and visualizing results. |

*Table 3 – used tools and role in the Multi-Hazard Climate Risk
Assessment Workflow*

### Methodology

#### Step 1 - Data acquisition and preparation

In this step we focus on climate indicators available in harmonized
European datasets that correspond directly to those recommended by the
IVAVIA methodology.

The workflow begins by loading into a GIS platform the multiband raster
file containing annual climate indicators of interest. Although provided
on a relatively coarse 0.25° grid, these datasets already deliver
pre-computed annual statistics such as yearly counts (e.g., number of
hot days), annual maxima (e.g., maximum 5-day precipitation), or annual
extremes (e.g., extreme wind speed days). Each band represents a year,
allowing the raster to be handled as a temporal stack. Importantly,
these are not long-term means, but annual statistics derived from daily
climate data, making them consistent with IVAVIA’s requirements.

Raster layers are then clipped to the study area using administrative
boundaries (from national or open European shapefiles). For this
tutorial, four indicators have been selected among the many available
and indicated in the IVAVIA guidelines just for the sake of two
illustrating the methodology:

  - > **Heat hazard →** Hot days (days with Tmax \> 30 °C)

  - > **Precipitation hazard →** Extreme precipitation days (days above
    > the 95th percentile, 1981–2010)

  - > **Wind hazard →** Extreme wind speed days (days above the 98th
    > percentile, 1981–2010)

  - > **Flood hazard →** River flood depth maps from JRC datasets (e.g.,
    > 100-year return period)

These indicators are extracted as time series for any pixel of interest
(e.g., the area covering Hum na Sutli or Zagreb or another area ) and
can be exported to CSV format directly from QGIS using available plugins
such as [*<span class="underline">Value
Tool</span>*](https://plugins.qgis.org/plugins/valuetool/). Figure 5
shows an example of population density grids and building footprints
overlaid with flood hazard data, while Figure 6 illustrates time series
extracted from current and projected climate datasets.

](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/CRO-Krapina-Zagorje_draft2_media/media/image17.png)

*Figure 7 – Example of exposure and flood hazard integration. Left:
raster map of population density for a selected age group (100 m
resolution) overlaid with building footprint polygons in an urban area
of the Krapina–Zagorje region. Right: building footprint polygons
overlaid with the 100-year flood extent from the JRC European river
flood hazard dataset. Together, these maps illustrate how demographic,
structural, and hazard layers can be combined in GIS to represent
exposure to climate risks, in line with the IVAVIA methodology.*

](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/CRO-Krapina-Zagorje_draft2_media/media/image24.png)

*Figure 8 – Extracted time series of meteorological indicators in
current and climate change projection (example of extracted time series
in the lower table)*

  - ##### Note – local data.

> While this tutorial uses widely available European datasets, the same
> procedure applies to local station data (e.g., from DHMZ in Croatia),
> either for single stations or as averages of multiple stations.

  - ##### Note – high-frequency/resolution geographical datasets. Scripting processing 

> When national or European data are available at higher
> spatial/temporal resolution (e.g., RegCM4 outputs, hourly ERA5-Land
> data), indicators must be derived from sub-daily rasters rather than
> pre-aggregated annual layers. This usually requires simple scripting
> (e.g., with
> [<span class="underline">GDAL</span>](https://gdal.org/en/stable/) or
> [<span class="underline">CDO</span>](https://code.mpimet.mpg.de/projects/cdo/wiki/tutorial))
> rather than standard GIS tools. Script construction is beyond the
> scope of this tutorial but remains a valid option for advanced users.

#### Step 2 – Indicators and normalization

##### Hazard 

Hazard - wind, precipitation, heat (time series)

Following the IVAVIA methodology (Appendix D), meteorological hazard
indicators were normalised with the min–max method, using the minimum
and maximum across the full series (baseline + RCP8.5 projections).
Annual values were aggregated into 30-year climatological windows
(1991–2020, 2021–2050, 2041–2070, 2071–2100), and the mean

![Immagine che contiene testo, Carattere, linea, bianco Il contenuto
generato dall'IA potrebbe non essere
corretto.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/CRO-Krapina-Zagorje_draft2_media/media/image2.png)

within each window was normalised as:

where X<sup>∗</sup> is the 30-year mean, and Xmin, Xmax​ are the minimum
and maximum values of the full historical + projected series.

  - ###### Note – normalization. 

> *Dataset-derived minima and maxima spread values across \[0,1\], but
> may misrepresent extremes if observed values cover only part of the
> plausible range. In such cases, thresholds from literature or records
> should be applied, with stakeholder agreement and documentation.*

Example of the 3-time series like indicators once normalized for one of
the areas of interest are reported in the following table.

| Window    | Wind means (d/yr) | Wind min | Wind max | Wind norm  | Hot days mean (d/yr) | Hot min | Hot max | Hot norm   | Extreme precip mean (d/yr) | Precip min | Precip max | Precip norm |
| --------- | ----------------- | -------- | -------- | ---------- | -------------------- | ------- | ------- | ---------- | -------------------------- | ---------- | ---------- | ----------- |
| 1991–2020 | 7.1667            | 0        | 17       | **0.4216** | 15.0667              | 0       | 114     | **0.1322** | 6.7667                     | 0          | 23         | **0.2942**  |
| 2021–2050 | 7.0               | 0        | 17       | **0.4118** | 22.9333              | 0       | 114     | **0.2011** | 9.7333                     | 0          | 23         | **0.4232**  |
| 2041–2070 | 6.8667            | 0        | 17       | **0.4039** | 32.8                 | 0       | 114     | **0.2877** | 9.5667                     | 0          | 23         | **0.4168**  |
| 2071–2100 | 6.9286            | 0        | 17       | **0.4076** | 59.5357              | 0       | 114     | **0.5222** | 10.8966                    | 0          | 23         | **0.4738**  |

*Table 4 - thirty-year mean values and normalised scores of hazard
indicators (wind, heat, precipitation) for the baseline period
(1991–2020) and three future climate windows under RCP8.5.*

For this tutorial, time-series indicators are assumed spatially uniform
over the study area—i.e., one pixel represents the whole exposed
population/assets. This is a simplification: local topography or
drainage strongly modulates impacts. More advanced assessments would
convert time-series indicators into pluvial flood or urban heat island
maps (see dedicated tutorials).

In the next section, we address hazard indicators that are **spatially
distributed,** focusing in this tutorial on flood hazard maps.

**Hazard – flood (map)**

Flood hazard is derived from raster water-depth maps (e.g., 100-year
return period). The raster is clipped to the study polygon, and zonal
statistics provide mean, minimum, and maximum depths.

The mean depth is then normalised as:

![Immagine che contiene Carattere, testo, linea, numero Il contenuto
generato dall'IA potrebbe non essere
corretto.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/CRO-Krapina-Zagorje_draft2_media/media/image11.png)

where:

  - > Hfloodraw ​ = mean depth (m) in the polygon,

  - > Hmin ​ = reference minimum (0 m),

  - > Hmax ​ = reference maximum (either the maximum observed depth
    > across a larger domain or a fixed threshold from
    > literature/experts, e.g. 2 m).

*Example over one of the areas of interest* mean = 0.97 m, min = 0.11 m,
max = 2.55 m → Hflood​=0.37.

##### Sensitivity

According to the IVAVIA methodology, sensitivity describes the intrinsic
characteristics of exposed elements that determine how strongly they are
affected by hazards. It is independent of hazard extent and instead
reflects the fragility of people, infrastructure, or systems. In this
workflow, **illustrative sensitivity indicators are proposed for each
hazard**, based on available demographic and structural data.

  - > **Heat hazard (Hot days):** sensitivity expressed by the
    > demographic structure, with the share of elderly (\>65) and
    > children (\<15) serving as a proxy for groups more vulnerable to
    > heat impacts.

  - > **Wind hazard (Extreme wind speed days):** sensitivity linked to
    > building fragility; in absence of detailed data, the density of
    > residential buildings is used as a proxy.

  - > **Precipitation hazard (Extreme precipitation days):** sensitivity
    > reflecting the capacity of the urban environment to manage intense
    > rainfall. A practical proxy adopted here is the share of
    > impermeable surfaces, which increases susceptibility to pluvial
    > flooding.

  - > **Flood hazard (River flood depth maps):** sensitivity expressed
    > by the structural fragility of buildings; in the absence of
    > detailed attributes, a proxy is the share of ground-floor
    > residential area within the total building footprint.

All sensitivity indicators can be derived with standard GIS overlays and
zonal statistics. To keep the tutorial concise, no full implementation
is provided; instead, normalized values (0–1) are assumed for
illustrative purposes.

  - ###### Note – Methodological caveat: 

> The indicators shown here are only operational examples. IVAVIA (see
> Appendix on sensitivity indicators) recommends defining
> context-specific indicators based on local data and hazard
> characteristics. Possible alternatives include socio-economic status,
> critical infrastructure, or health service coverage**. Because
> sensitivity is highly context-dependent, indicator selection should be
> validated with stakeholders and supported by reliable evidence.**

<table>
<thead>
<tr class="header">
<th><blockquote>
<p><strong>Dimension</strong></p>
</blockquote></th>
<th><blockquote>
<p><strong>Indicator(s)</strong></p>
</blockquote></th>
<th><blockquote>
<p><strong>Unit</strong></p>
</blockquote></th>
<th><strong>Normalized Value (0–1)</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><blockquote>
<p>Heat hazard</p>
</blockquote></td>
<td><blockquote>
<p>Share of elderly (&gt;65) and children (&lt;15) in total population</p>
</blockquote></td>
<td><blockquote>
<p>% of total population</p>
</blockquote></td>
<td><blockquote>
<p>0.41</p>
</blockquote></td>
</tr>
<tr class="even">
<td><blockquote>
<p>Wind hazard</p>
</blockquote></td>
<td><blockquote>
<p>Density of residential buildings</p>
</blockquote></td>
<td><blockquote>
<p>Building of fragile type / total</p>
</blockquote></td>
<td><blockquote>
<p>0.61</p>
</blockquote></td>
</tr>
<tr class="odd">
<td><blockquote>
<p>Precipitation hazard</p>
</blockquote></td>
<td><blockquote>
<p>Share of impermeable surfaces</p>
</blockquote></td>
<td><blockquote>
<p>% of total area</p>
</blockquote></td>
<td><blockquote>
<p>0.75</p>
</blockquote></td>
</tr>
<tr class="even">
<td><blockquote>
<p>Flood hazard</p>
</blockquote></td>
<td><blockquote>
<p>Share of ground-floor residential area in building footprints</p>
</blockquote></td>
<td><blockquote>
<p>% of total building footprint</p>
</blockquote></td>
<td><blockquote>
<p>0.54</p>
</blockquote></td>
</tr>
</tbody>
</table>

*Table 5 - Proposed illustrative sensitivity indicators for the four
hazards considered. These indicators are derived from demographic and
structural datasets and serve as operational examples for this workflow.
According to IVAVIA, final indicator selection should be adapted to
**local data availability and validated with stakeholders.***

To visually illustrate how sensitivity interacts with exposure and
adaptive capacity, the IVAVIA methodology provides impact chains that
link climate hazards to sectoral impacts. For example, the impact chain
for **heatwaves and public health** (IVAVIA Guideline, Appendix C) shows
how demographic characteristics such as the proportion of elderly or
children, combined with coping capacity factors like availability of
health services, shape the final vulnerability of a community. This
schematic representation supports the interpretation of the simplified
sensitivity indicators adopted in this tutorial.

![Immagine che contiene testo, schermata, diagramma, Carattere Il
contenuto generato dall'IA potrebbe non essere
corretto.](/content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/CRO-Krapina-Zagorje_draft2_media/media/image16.png)

*Figure 9 - Example of an IVAVIA impact chain for heatwaves and public
health. The diagram illustrates how hazard indicators (e.g., frequency
of heatwaves) interact with sensitivity factors (e.g., share of elderly
population, population density, building typologies) and adaptive
capacity elements (e.g., health services, early warning systems) to
determine the overall level of vulnerability and impacts on public
health. Source: IVAVIA Guideline v3, Appendix C*

##### Exposure 

According to the IVAVIA methodology, exposure refers to the presence and
distribution of people, buildings, or infrastructures located within
areas potentially affected by climate hazards. Unlike sensitivity, which
captures intrinsic fragility, exposure quantifies how many assets are
actually situated in hazard zones.

  - ###### Note – Methodological caveat: 

> *In this tutorial, exposure indicators are derived from a limited set
> of available datasets—population density grids (100 m resolution) and
> building footprint polygons. The approach varies by hazard type and is
> presented here for didactic purposes only. The IVAVIA guidelines
> provide broader examples, validated with stakeholders, for tailoring
> exposure assessment to local contexts.*

  - > **Heat, Wind, and Precipitation hazards**: Since these indicators
    > are represented as uniform time-series values across the study
    > area, exposure is assumed to be total (value = 1), meaning all
    > population and buildings are equally affected.

  - > **Flood hazard:** Exposure is spatially differentiated and
    > calculated by intersecting the flood depth map with building
    > footprints and population grids. Metrics such as the share of
    > residential floor area or population within the 100-year
    > floodplain can be used. In this example, the normalized exposure
    > index is estimated at ≈ 0.25.

As with sensitivity, exposure can be derived through standard GIS
overlay and zonal statistics, without requiring advanced examples here.
Population exposure is obtained by summing grid values within hazard
zones, while building exposure is calculated from the footprint area
intersecting the hazard extent.

##### Adaptation Capacity 

According to the IVAVIA methodology, adaptation capacity refers to the
ability of institutions, infrastructure, and communities to anticipate,
absorb, and recover from climate hazard impacts. Unlike sensitivity or
exposure, which can be measured with demographic or structural datasets,
adaptation capacity is context-specific and often linked to governance
quality, preparedness, and technical measures.

  - ###### Note – Methodological caveat:  
    In this workflow, adaptation capacity indicators are introduced only as hypothetical examples, since robust local data (e.g., levee length, drainage network capacity, emergency planning) are not readily available for either Krapina–Zagorje or Zagreb. As underlined in IVAVIA (Section 4.2), qualitative or categorical indicators—such as the presence of early-warning systems, enforcement of building codes, or stakeholder perceptions—can also be used. In practice, **these indicators should be locally validated, but here simplified values are applied to complete the Climate Risk Assessment framework.**

<!-- end list -->

  - > **Heat hazard (hot days)**: Capacity may include health services,
    > social support, cooling shelters, or urban greening. Example
    > value: 0.6 (moderate preparedness).

  - > **Wind hazard (extreme wind speed days)**: Linked to building
    > standards, warning systems, and civil protection readiness.
    > Example value: 0.5 (partial preparedness).

  - > **Precipitation hazard (extreme precipitation days):** Reflects
    > drainage and green infrastructure performance. Example value: 0.4
    > (limited capacity).

  - > Flood hazard (river flood depth maps): Based on structural
    > defences, contingency planning, and operational readiness. Example
    > value: 0.3 (low preparedness).

These values are purely illustrative. In operational settings, IVAVIA
recommends a mix of quantitative metrics (e.g., kilometres of levees,
share of urban green areas) and qualitative indicators (e.g., presence
of emergency plans), depending on hazard type and data availability.

#### Step 3 – Risk Aggregation and Results

##### Risk score 

According to the IVAVIA methodology, the final risk score is obtained by
integrating hazard (H), exposure (EX), and vulnerability (V) into a
composite index. Vulnerability itself is calculated as a function of
sensitivity (SE) and adaptive capacity (AC), following the aggregation
approaches described in Section 5.2 of the guidelines:

](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/CRO-Krapina-Zagorje_draft2_media/media/image13.png)

Several methods for combining SE and AC are provided in IVAVIA, ranging
from additive models to compensatory approaches. For the sake of clarity
and didactic value, this tutorial applies the first aggregation method
suggested by IVAVIA—the weighted arithmetic mean—under the simplifying
assumption of unitary weights. In this configuration, sensitivity and
adaptive capacity contribute equally to vulnerability, and hazard,
exposure, and vulnerability contribute equally to the final risk score:

](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/CRO-Krapina-Zagorje_draft2_media/media/image1.emf)

With C=(1-AC) .

This choice ensures consistency with IVAVIA while keeping the workflow
simple and transparent. In real-world applications, the relative weights
of the components should be carefully defined and validated with local
stakeholders, as recommended by the methodology.

The following tables report the illustrative normalized values used for
each of the four hazards in the example area. These values are not
observed or refined values, but didactic approximations introduced to
demonstrate the workflow:

| Dimension         | Indicator                                          | Normalized Value | Composite Score                |
| ----------------- | -------------------------------------------------- | ---------------- | ------------------------------ |
| Hazard            | Number of hot days                                 | 0.52             | H = 0.52                       |
| Sensitivity       | Share of elderly and children in population        | 0.41             |                                |
| Adaptive Capacity | Health/social systems, greening programs (assumed) | 0.60             | V = (0.41+(1-0.60))/2 = 0.41   |
| Exposure          | Population and buildings (area-wide)               | 1.00             | EX = 1.00                      |
| Risk              | Composite Risk Score                               |                  | R = (0.52+0.41+1.00)/3 = 0.643 |

*  
Table 6 - Heat Hazard (Hot Days)*

| Dimension         | Indicator                                     | Normalized Value | Composite Score                 |
| ----------------- | --------------------------------------------- | ---------------- | ------------------------------- |
| Hazard            | Extreme wind speed days                       | 0.41             | H = 0.41                        |
| Sensitivity       | Density of residential buildings              | 0.61             |                                 |
| Adaptive Capacity | Building standards, warning systems (assumed) | 0.50             | V = (0.61+(1-0.50))/2 = 0.555   |
| Exposure          | Population and buildings (area-wide)          | 1.00             | EX = 1.00                       |
| Risk              | Composite Risk Score                          |                  | R = (0.41+0.555+1.00)/3 = 0.655 |

*Table 7 - Wind Hazard (Extreme Wind Speed Days)*

| Dimension         | Indicator                               | Normalized Value | Composite Score                 |
| ----------------- | --------------------------------------- | ---------------- | ------------------------------- |
| Hazard            | Extreme precipitation days              | 0.47             | H = 0.47                        |
| Sensitivity       | Share of impermeable surfaces           | 0.75             |                                 |
| Adaptive Capacity | Drainage/green infrastructure (assumed) | 0.40             | V = (0.75+(1-0.40))/2 = 0.675   |
| Exposure          | Population and buildings (area-wide)    | 1.00             | EX = 1.00                       |
| Risk              | Composite Risk Score                    |                  | R = (0.47+0.675+1.00)/3 = 0.715 |

*Table 8 - Precipitation Hazard (Extreme Precipitation Days)*

| Dimension         | Indicator                                     | Normalized Value | Composite Score                |
| ----------------- | --------------------------------------------- | ---------------- | ------------------------------ |
| Hazard            | Mean flood depth (100-yr return period)       | 0.37             | H = 0.37                       |
| Sensitivity       | Share of ground-floor residential area        | 0.54             |                                |
| Adaptive Capacity | Flood defences, emergency readiness (assumed) | 0.30             | V = (0.54+(1-0.30))/2 = 0.62   |
| Exposure          | Share of population/buildings in flood zone   | 0.25             | EX = 0.25                      |
| Risk              | Composite Risk Score                          |                  | R = (0.37+0.62+0.25)/3 = 0.413 |

*Table 9 - Flood Hazard (River Flood Depth Maps)*

##### Outputs and Visualizations

In addition to tabular calculations, this CRA workflow highlights the
importance of **visual outputs for effective communication of results.**
Graphs and maps make trends and spatial patterns accessible to both
experts and non-specialist stakeholders, bridging the gap between
technical analysis and decision-making.

**Time-series plots** illustrate the temporal evolution of hazard
indicators (e.g., hot days, extreme precipitation days, wind extremes)
under historical and RCP8.5 scenarios. They enable comparison of
baseline and projected conditions, making the dynamics of climate risk
more tangible. In this example, two indicators—frequency of extreme
precipitation days and hot days—show a marked upward trend, underlining
the urgency of adaptation and mitigation measures.

**Geospatial maps** complement this temporal perspective by showing the
spatial distribution of risks. Flood hazard maps combined with exposure
layers (e.g., population grids or building footprints) identify
vulnerable hotspots, supporting emergency preparedness and
prioritization of adaptation measures. More complex composite maps can
integrate multiple hazards, sensitivity, and adaptive capacity, helping
to capture cross-sectoral vulnerabilities.

Together, **time series and maps** form a dual perspective: temporal
trends highlight how risks evolve under climate change, while spatial
layers reveal where impacts concentrate. This dual approach is essential
for developing policy briefs, planning documents, and awareness tools
that translate CRA results into actionable strategies.

  - ###### Adjusting climate trends with local data 

> Many global or regional reanalysis or observational datasets (e.g.,
> ERA5) overlap in time with future model projections (e.g., CMIP6).
> This overlap allows for **statistical downscaling** — particularly,
> **quantile mapping** techniques — to adjust large-scale datasets to
> local contexts while preserving climate change signals and extreme
> tails. Recent studies using *Quantile Delta Mapping (QDM)* and models
> like *Quantile-Preserving Localized-Analog Downscaling (QPLAD)*
> demonstrate that it is possible to correct biases and downscale
> climate variables without distorting trends in extremes( see also
> [<span class="underline">Gergel, D. R. et. Ala,
> 2024</span>](https://gmd.copernicus.org/articles/17/191/2024))

](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/CRO-Krapina-Zagorje_draft2_media/media/image15.png)

*Figure 10 - Combined plots of Hot Days (top), Extreme Wind Speed Days
(middle), and Frequency of Extreme Precipitation Days (bottom),
comparing historical reanalysis data with climate change projections
under RCP 8.5 (Copernicus datasets). The shaded rectangle highlights the
temporal overlap between reanalysis and projection datasets, which can
be exploited for statistical downscaling methods (e.g., quantile
mapping). The figures show a clear upward trend for heat- and
precipitation-related indicators, supporting the need for targeted
adaptation strategies.*

](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/CRO-Krapina-Zagorje_draft2_media/media/image19.png)

*Figure 11- example of geospatial map Displaying hazard zones such as
flood risk maps:*

](content/drive/MyDrive/GECO_RESEARCH/17_R&D_ARCADIA_HORIZ_GIS_10112023_S/WP8/Tutorials/gitbook_repo/_tmp_assets/CRO-Krapina-Zagorje_draft2_media/media/image18.png)

*Figure 12 example of geospatial maps displaying hazard zones such as
flood risk maps, erosion risk maps, fire risk maps, landslide risk
maps:*

## Annex – Sectoral Climate Risk Models (from Zagreb case study)

This annex reports sectoral examples of climate hazard and risk models
as developed in the Zagreb Climate Risk Assessment, based on the IVAVIA
methodology (RESIN project). These examples illustrate how hazard,
exposure, sensitivity, and adaptive capacity indicators can be combined
into composite vulnerability and risk indices.

The tables reproduced here summarize, for each sector, examples of
relevant indicators of **hazard (H)**, **exposure (EX)**, **sensitivity
(SE)**, and **adaptive capacity (AC)**. Their aggregation into
**vulnerability (V)** and final **risk (R)** scores follows the
methodological framework described in Chapter 5 of the IVAVIA
guidelines.

The annexed tables are provided as illustrative examples and complement
the simplified tutorial workflow developed for the Krapina–Zagorje and
Zagreb regions. They show how sectoral detail can be introduced in
operational CRAs when more granular datasets and local expertise are
available.

  - ##### Example: Water Management – Flood Risk and Vulnerability

> The final table attached in this annex presents a structured example
> of calculation for the **Water Management sector**, focused on flood
> hazard. Normalized values are shown for hazard, sensitivity, adaptive
> capacity, and exposure indicators, together with the composite
> vulnerability score and overall risk rating.
> 
> This structured calculation demonstrates the logic of the IVAVIA
> framework:

  - > Hazard intensity (frequency of extreme rainfall, maximum daily
    > precipitation) is quantified and normalized.

  - > Sensitivity includes past flood occurrences and infrastructure
    > fragility.

  - > Adaptive capacity reflects the state of flood defenses, drainage,
    > and preparedness of services.

  - > Exposure measures the density of population and infrastructure
    > within the flood-prone area.

  - > Vulnerability is aggregated as a function of sensitivity and
    > coping capacity.

  - > The final risk rating integrates hazard, exposure, and
    > vulnerability.

*Table 10 - an example of risk elements and indicators that were used in
the CRA*

<table>
<thead>
<tr class="header">
<th>RISK ELEMENTS</th>
<th>DESCRIPTION</th>
<th>INDICATORS</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Threat (hazard)</td>
<td><ul>
<li><blockquote>
<p>Drought</p>
</blockquote></li>
<li><blockquote>
<p>Flood</p>
</blockquote></li>
<li><blockquote>
<p>Storm</p>
</blockquote></li>
<li><blockquote>
<p>Heatwave</p>
</blockquote></li>
<li><blockquote>
<p>Fire</p>
</blockquote></li>
</ul></td>
<td><p>IPCC Scenarios: RCP 4.5 and RCP8.5 for the period 2040–2070 compared to the period 1980–2010.</p>
<ul>
<li><blockquote>
<p>Change in mean maximum temperature (°C)</p>
</blockquote></li>
<li><blockquote>
<p>Change in the number of warm nights (Tmin ≥ 20 °C)</p>
</blockquote></li>
<li><blockquote>
<p>Change in the number of very hot days (Tmax ≥ 30 °C)</p>
</blockquote></li>
<li><blockquote>
<p>Change in the number of consecutive dry days (precipitation &lt; 1 mm)</p>
</blockquote></li>
<li><blockquote>
<p>Change in the number of consecutive rainy days (precipitation &gt; 1 mm)</p>
</blockquote></li>
<li><blockquote>
<p>Change in the number of days with heavy precipitation (&gt; 20 mm)</p>
</blockquote></li>
<li><blockquote>
<p>Change in the maximum 1-day precipitation (Rx1d)</p>
</blockquote></li>
<li><blockquote>
<p>Erosion</p>
</blockquote></li>
</ul></td>
</tr>
<tr class="even">
<td>Exposure</td>
<td>Exposure of people and infrastructure to potential future climate impacts.</td>
<td><ul>
<li><blockquote>
<p>Population density in settlements</p>
</blockquote></li>
<li><blockquote>
<p>Road and railway infrastructure</p>
</blockquote></li>
<li><blockquote>
<p>Hospitals and health center</p>
</blockquote></li>
<li><blockquote>
<p>Industrial facilities</p>
</blockquote></li>
<li><blockquote>
<p>Waste disposal sites</p>
</blockquote></li>
</ul></td>
</tr>
<tr class="odd">
<td>Sensitivity</td>
<td>Socio-economic data that may be affected by climate change hazards. Indicators should reflect changes over time.</td>
<td><ul>
<li><blockquote>
<p>Number of inhabitants</p>
</blockquote></li>
<li><blockquote>
<p>Youth population</p>
</blockquote></li>
<li><blockquote>
<p>Elderly population</p>
</blockquote></li>
<li><blockquote>
<p>Settlement density</p>
</blockquote></li>
<li><blockquote>
<p>Projected changes in population and migration</p>
</blockquote></li>
</ul></td>
</tr>
<tr class="even">
<td>Adaptation capacity</td>
<td>Data related to the capacity to adapt to the occurrence of hazards, which can reflect changes over time.</td>
<td><ul>
<li><blockquote>
<p>Number of hospitals/doctors per capita</p>
</blockquote></li>
<li><blockquote>
<p>Proportion of green areas in cities</p>
</blockquote></li>
<li><blockquote>
<p>Length of built levees</p>
</blockquote></li>
<li><blockquote>
<p>Level of public education</p>
</blockquote></li>
<li><blockquote>
<p>GDP per capita</p>
</blockquote></li>
</ul></td>
</tr>
</tbody>
</table>

Below are the models that were used in the CRA for analyzed sectors:

**<span class="underline">WATER MANAGMENT</span>**

<table>
<thead>
<tr class="header">
<th><strong>HAZARD: FLOODS</strong></th>
<th><ul>
<li><blockquote>
<p>Maximum 1-day precipitation (Rx1d)</p>
</blockquote></li>
<li><blockquote>
<p>Number of days with heavy rainfall (&gt; 20 mm)</p>
</blockquote></li>
<li><blockquote>
<p>Number of consecutive rainy days (precipitation &gt; 1 mm)</p>
</blockquote></li>
</ul></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>EXPOSURE</strong></td>
<td><ul>
<li><blockquote>
<p>population density (number of inhabitants/km²)</p>
</blockquote></li>
<li><blockquote>
<p>number of water supply connections</p>
</blockquote></li>
<li><blockquote>
<p>length of the public drainage network in the area affected by flooding</p>
</blockquote></li>
</ul></td>
</tr>
<tr class="even">
<td><strong>SENSITIVITY</strong></td>
<td><ul>
<li><blockquote>
<p>occurrence of floods in the area of the City of Zagreb</p>
</blockquote></li>
<li><blockquote>
<p>safety of water intended for human consumption</p>
</blockquote></li>
<li><blockquote>
<p>percentage of households without a water supply network</p>
</blockquote></li>
</ul></td>
</tr>
<tr class="odd">
<td><strong>ADAPTATION CAPACITY</strong></td>
<td><ul>
<li><blockquote>
<p>flood defense system</p>
</blockquote></li>
<li><blockquote>
<p>assessment of the readiness of flood protection services</p>
</blockquote></li>
<li><blockquote>
<p>functionality of the public drainage system</p>
</blockquote></li>
<li><blockquote>
<p>integrated approach to managing urban stormwater drainage</p>
</blockquote></li>
</ul></td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr class="header">
<th><strong>HAZARD: DROUGHT</strong></th>
<th><ul>
<li><blockquote>
<p>average maximum daily air temperature</p>
</blockquote></li>
<li><blockquote>
<p>number of very hot days (Tmax ≥ 30 °C)</p>
</blockquote></li>
<li><blockquote>
<p>number of consecutive dry days (precipitation &lt; 1 mm)</p>
</blockquote></li>
</ul></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>EXPOSURE</strong></td>
<td><ul>
<li><blockquote>
<p>population density (number of inhabitants/km²)</p>
</blockquote></li>
<li><blockquote>
<p>number of water supply connections</p>
</blockquote></li>
<li><blockquote>
<p>increase in the number of water consumers during peak summer tourist months</p>
</blockquote></li>
</ul></td>
</tr>
<tr class="even">
<td><strong>SENSITIVITY</strong></td>
<td><ul>
<li><blockquote>
<p>average annual water consumption</p>
</blockquote></li>
<li><blockquote>
<p>losses in the water supply network</p>
</blockquote></li>
<li><blockquote>
<p>quantitative status of groundwater</p>
</blockquote></li>
</ul></td>
</tr>
<tr class="odd">
<td><strong>ADAPTATION CAPACITY</strong></td>
<td><ul>
<li><blockquote>
<p>level of education of the population</p>
</blockquote></li>
<li><blockquote>
<p>sustainable water management</p>
</blockquote></li>
<li><blockquote>
<p>regulations on water use restrictions</p>
</blockquote></li>
</ul></td>
</tr>
</tbody>
</table>

**<span class="underline">AGRICULTURE</span>**

<table>
<thead>
<tr class="header">
<th><strong>HAZARD: DROUGHT</strong></th>
<th><ul>
<li><blockquote>
<p>average maximum daily air temperature</p>
</blockquote></li>
<li><blockquote>
<p>number of very hot days (Tmax ≥ 30 °C)</p>
</blockquote></li>
<li><blockquote>
<p>number of consecutive dry days (precipitation &lt; 1 mm)</p>
</blockquote></li>
</ul></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>EXPOSURE</strong></td>
<td><ul>
<li><blockquote>
<p>number of agricultural holdings</p>
</blockquote></li>
<li><blockquote>
<p>share of ARKOD areas in the total area of the City</p>
</blockquote></li>
<li><blockquote>
<p>share of employees in the agriculture sector relative to total employment</p>
</blockquote></li>
</ul></td>
</tr>
<tr class="even">
<td><strong>SENSITIVITY</strong></td>
<td><ul>
<li><blockquote>
<p>structure of agricultural land and distribution of drought-sensitive crops</p>
</blockquote></li>
<li><blockquote>
<p>soil quality, i.e., the percentage of humus content in the soil</p>
</blockquote></li>
<li><blockquote>
<p>estimated material damage in the economy as a percentage of the budget</p>
</blockquote></li>
</ul></td>
</tr>
<tr class="odd">
<td><strong>ADAPTATION CAPACITY</strong></td>
<td><ul>
<li><blockquote>
<p>availability of water for irrigation</p>
</blockquote></li>
<li><blockquote>
<p>institutional and financial support for farmers</p>
</blockquote></li>
<li><blockquote>
<p>level of education of farmers</p>
</blockquote></li>
<li><blockquote>
<p>age structure of farmers</p>
</blockquote></li>
<li><blockquote>
<p>GDP per capita (financial capacity for using modern technologies)</p>
</blockquote></li>
</ul></td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr class="header">
<th><strong>HAZARD: FLOODS</strong></th>
<th><ul>
<li><blockquote>
<p>number of consecutive rainy days (precipitation &gt; 1 mm)</p>
</blockquote></li>
<li><blockquote>
<p>number of days with heavy precipitation (&gt; 20 mm)</p>
</blockquote></li>
<li><blockquote>
<p>highest 1-day precipitation amount (Rx1d)</p>
</blockquote></li>
</ul></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>EXPOSURE</strong></td>
<td><ul>
<li><blockquote>
<p>area of agricultural land at risk of flooding</p>
</blockquote></li>
<li><blockquote>
<p>area of agricultural land at risk of erosion</p>
</blockquote></li>
<li><blockquote>
<p>number of agricultural holdings</p>
</blockquote></li>
</ul></td>
</tr>
<tr class="even">
<td><strong>SENSITIVITY</strong></td>
<td><ul>
<li><blockquote>
<p>estimated material damage in the economy (%)</p>
</blockquote></li>
<li><blockquote>
<p>soil water retention capacity</p>
</blockquote></li>
</ul></td>
</tr>
<tr class="odd">
<td><strong>ADAPTATION CAPACITY</strong></td>
<td><ul>
<li><blockquote>
<p>existing flood defense systems</p>
</blockquote></li>
<li><blockquote>
<p>existing green infrastructure</p>
</blockquote></li>
<li><blockquote>
<p>drainage systems</p>
</blockquote></li>
</ul></td>
</tr>
</tbody>
</table>

**<span class="underline">FORESTRY</span>**

<table>
<thead>
<tr class="header">
<th><strong>HAZARD: FIRE</strong></th>
<th><ul>
<li><blockquote>
<p>average daily maximum air temperature</p>
</blockquote></li>
<li><blockquote>
<p>number of very hot days (Tmax ≥ 30 °C)</p>
</blockquote></li>
<li><blockquote>
<p>number of consecutive dry days (precipitation &lt; 1 mm)</p>
</blockquote></li>
</ul></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>EXPOSURE</strong></td>
<td><ul>
<li><blockquote>
<p>areas covered by forest land and urban parks</p>
</blockquote></li>
<li><blockquote>
<p>share of employees in forestry relative to total employment</p>
</blockquote></li>
</ul></td>
</tr>
<tr class="even">
<td><strong>SENSITIVITY</strong></td>
<td><ul>
<li><blockquote>
<p>SSR index of average seasonal fire severity</p>
</blockquote></li>
<li><blockquote>
<p>area of forests affected by a high level of fire danger (ha)</p>
</blockquote></li>
<li><blockquote>
<p>age of forests (ha)</p>
</blockquote></li>
<li><blockquote>
<p>burned area in the recent period (ha)</p>
</blockquote></li>
<li><blockquote>
<p>forest management</p>
</blockquote></li>
</ul></td>
</tr>
<tr class="odd">
<td><strong>ADAPTATION CAPACITY</strong></td>
<td><ul>
<li><blockquote>
<p>existence of institutional and technical capacity for preventing, managing, and restoring forest fires</p>
</blockquote></li>
<li><blockquote>
<p>sufficient spatial density of firebreaks</p>
</blockquote></li>
<li><blockquote>
<p>existence of an annual forest and urban park fire protection plan</p>
</blockquote></li>
</ul></td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr class="header">
<th><strong>HAZARD: STORM</strong></th>
<th><ul>
<li><blockquote>
<p>increase in the number of storm events</p>
</blockquote></li>
</ul></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>EXPOSURE</strong></td>
<td><ul>
<li><blockquote>
<p>areas covered by forest land, urban forests, city parks, tree-lined avenues, gardens, and individual trees</p>
</blockquote></li>
</ul></td>
</tr>
<tr class="even">
<td><strong>SENSITIVITY</strong></td>
<td><ul>
<li><blockquote>
<p>age of the forest</p>
</blockquote></li>
<li><blockquote>
<p>health condition of the forest</p>
</blockquote></li>
<li><blockquote>
<p>biodiversity of the forest</p>
</blockquote></li>
<li><blockquote>
<p>tree species present</p>
</blockquote></li>
<li><blockquote>
<p>forest stand density</p>
</blockquote></li>
</ul></td>
</tr>
<tr class="odd">
<td><strong>ADAPTATION CAPACITY</strong></td>
<td><ul>
<li><blockquote>
<p>forest maintenance (private/state)</p>
</blockquote></li>
<li><blockquote>
<p>planting plan (particularly regarding tree species selection) and management of urban forests</p>
</blockquote></li>
</ul></td>
</tr>
</tbody>
</table>

**<span class="underline">HEALTH</span>**

<table>
<thead>
<tr class="header">
<th><strong>HAZARD: HEATHWAVE</strong></th>
<th><ul>
<li><blockquote>
<p>average daily air temperature</p>
</blockquote></li>
<li><blockquote>
<p>number of hot days (Tmax ≥ 30 °C)</p>
</blockquote></li>
<li><blockquote>
<p>number of tropical nights (Tmin &gt; 20 °C)</p>
</blockquote></li>
</ul></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>EXPOSURE</strong></td>
<td><ul>
<li><blockquote>
<p>average population density (number of inhabitants/km²)</p>
</blockquote></li>
<li><blockquote>
<p>number of employees in occupations exposed to atmospheric influences (agriculture, forestry, construction)</p>
</blockquote></li>
<li><blockquote>
<p>sensitive institutions in areas with elevated temperatures (urban heat islands)</p>
</blockquote></li>
</ul></td>
</tr>
<tr class="even">
<td><strong>SENSITIVITY</strong></td>
<td><ul>
<li><blockquote>
<p>built-up area of settlements (km²)</p>
</blockquote></li>
<li><blockquote>
<p>share of population in sensitive age groups (%) (&lt;18, &gt;65)</p>
</blockquote></li>
<li><blockquote>
<p>share of vulnerable population (%) (disabled, pregnant women)</p>
</blockquote></li>
</ul></td>
</tr>
<tr class="odd">
<td><strong>ADAPTATION CAPACITY</strong></td>
<td><ul>
<li><blockquote>
<p>share of urban green and blue infrastructure in the urban area of the city (%)</p>
</blockquote></li>
<li><blockquote>
<p>availability of healthcare services</p>
</blockquote></li>
<li><blockquote>
<p>coverage of the area by emergency services</p>
</blockquote></li>
<li><blockquote>
<p>level of education of the population</p>
</blockquote></li>
<li><blockquote>
<p>system for warning residents about the occurrence of heatwaves</p>
</blockquote></li>
<li><blockquote>
<p>share of non-compliant results (according to health and environmental criteria) in urban environment monitoring (air, water, soil, food)</p>
</blockquote></li>
</ul></td>
</tr>
</tbody>
</table>

**<span class="underline">TOURISM</span>**

<table>
<thead>
<tr class="header">
<th><strong>HAZARD: HEATHWAVE</strong></th>
<th><ul>
<li><blockquote>
<p>average daily air temperature</p>
</blockquote></li>
<li><blockquote>
<p>number of hot days (Tmax ≥ 30 °C)</p>
</blockquote></li>
<li><blockquote>
<p>number of tropical nights (Tmin &gt; 20 °C)</p>
</blockquote></li>
</ul></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>EXPOSURE</strong></td>
<td><ul>
<li><blockquote>
<p>number of employees in the accommodation and food preparation and service sectors</p>
</blockquote></li>
<li><blockquote>
<p>increase in the number of residents during peak tourist months</p>
</blockquote></li>
</ul></td>
</tr>
<tr class="even">
<td><strong>SENSITIVITY</strong></td>
<td><ul>
<li><blockquote>
<p>tourism development index</p>
</blockquote></li>
<li><blockquote>
<p>tourism intensity indicator</p>
</blockquote></li>
</ul></td>
</tr>
<tr class="odd">
<td><strong>ADAPTATION CAPACITY</strong></td>
<td><ul>
<li><blockquote>
<p>development of diversified tourism offers</p>
</blockquote></li>
<li><blockquote>
<p>investment in marketing</p>
</blockquote></li>
<li><blockquote>
<p>planning and development documents for the tourism sector that consider climate change</p>
</blockquote></li>
<li><blockquote>
<p>greenery and water availability</p>
</blockquote></li>
</ul></td>
</tr>
</tbody>
</table>

**<span class="underline">BIODIVERSITY</span>**

<table>
<thead>
<tr class="header">
<th><strong>HAZARD: TEMPERATURE AND PERCIPITATION CHANGE</strong></th>
<th><ul>
<li><blockquote>
<p>average daily air temperature</p>
</blockquote></li>
<li><blockquote>
<p>number of hot days (Tmax ≥ 30 °C)</p>
</blockquote></li>
<li><blockquote>
<p>number of tropical nights (Tmin &gt; 20°C)</p>
</blockquote></li>
<li><blockquote>
<p>number of consecutive rainy days (precipitation &gt; 1 mm)</p>
</blockquote></li>
<li><blockquote>
<p>number of days with heavy precipitation (&gt; 20 mm)</p>
</blockquote></li>
<li><blockquote>
<p>highest 1-day precipitation amount (Rx1d)</p>
</blockquote></li>
</ul></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>EXPOSURE</strong></td>
<td><ul>
<li><blockquote>
<p>share of rare and endangered habitats</p>
</blockquote></li>
</ul></td>
</tr>
<tr class="even">
<td><strong>SENSITIVITY</strong></td>
<td><ul>
<li><blockquote>
<p>sensitive species</p>
</blockquote></li>
<li><blockquote>
<p>share of sensitive habitats</p>
</blockquote></li>
</ul></td>
</tr>
<tr class="odd">
<td><strong>ADAPTATION CAPACITY</strong></td>
<td><ul>
<li><blockquote>
<p>share of protected areas</p>
</blockquote></li>
<li><blockquote>
<p>ecological network</p>
</blockquote></li>
<li><blockquote>
<p>development of urban biodiversity</p>
</blockquote></li>
</ul></td>
</tr>
</tbody>
</table>

**<span class="underline">BUILDINGS</span>**

<table>
<thead>
<tr class="header">
<th><strong>HAZARD: FLOODS</strong></th>
<th><ul>
<li><blockquote>
<p>number of consecutive rainy days (precipitation &gt; 1 mm)</p>
</blockquote></li>
<li><blockquote>
<p>number of days with heavy precipitation (&gt; 20 mm)</p>
</blockquote></li>
<li><blockquote>
<p>highest 1-day precipitation amount (Rx1d)</p>
</blockquote></li>
</ul></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>EXPOSURE</strong></td>
<td><ul>
<li><blockquote>
<p>level of area development (%)</p>
</blockquote></li>
</ul></td>
</tr>
<tr class="even">
<td><strong>SENSITIVITY</strong></td>
<td><ul>
<li><blockquote>
<p>share of buildings in flood-prone areas</p>
</blockquote></li>
<li><blockquote>
<p>share of buildings in areas exposed to erosion</p>
</blockquote></li>
<li><blockquote>
<p>share of buildings in landslide-prone areas</p>
</blockquote></li>
</ul></td>
</tr>
<tr class="odd">
<td><strong>ADAPTATION CAPACITY</strong></td>
<td><ul>
<li><blockquote>
<p>existing flood protection system</p>
</blockquote></li>
<li><blockquote>
<p>readiness of operational forces for flood protection</p>
</blockquote></li>
<li><blockquote>
<p>functionality of the public drainage system</p>
</blockquote></li>
<li><blockquote>
<p>share of urban green and blue infrastructure in the urban area of the city (%)</p>
</blockquote></li>
</ul></td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr class="header">
<th><strong>HAZARD: STORM</strong></th>
<th><ul>
<li><blockquote>
<p>increase in the number of storm events</p>
</blockquote></li>
</ul></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>EXPOSURE</strong></td>
<td><ul>
<li><blockquote>
<p>share of buildings in the developed part of the construction area</p>
</blockquote></li>
</ul></td>
</tr>
<tr class="even">
<td><strong>SENSITIVITY</strong></td>
<td><ul>
<li><blockquote>
<p>number or percentage of (public/residential) buildings damaged due to extreme weather conditions/events</p>
</blockquote></li>
</ul></td>
</tr>
<tr class="odd">
<td><strong>ADAPTATION CAPACITY</strong></td>
<td><ul>
<li><blockquote>
<p>level of education of the population</p>
</blockquote></li>
<li><blockquote>
<p>implementation of guidelines for building climate-resilient infrastructure into building regulations and spatial plans</p>
</blockquote></li>
</ul></td>
</tr>
</tbody>
</table>

**<span class="underline">TRANSPORT</span>**

<table>
<thead>
<tr class="header">
<th><strong>HAZARD: FLOODS</strong></th>
<th><ul>
<li><blockquote>
<p>number of consecutive rainy days (precipitation &gt; 1 mm)</p>
</blockquote></li>
<li><blockquote>
<p>number of days with heavy precipitation (&gt; 20 mm)</p>
</blockquote></li>
<li><blockquote>
<p>highest 1-day precipitation amount (Rx1d)</p>
</blockquote></li>
</ul></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>EXPOSURE</strong></td>
<td><ul>
<li><blockquote>
<p>share of transport surfaces in the city</p>
</blockquote></li>
</ul></td>
</tr>
<tr class="even">
<td><strong>SENSITIVITY</strong></td>
<td><ul>
<li><blockquote>
<p>share of transportation routes at risk of flooding</p>
</blockquote></li>
<li><blockquote>
<p>assessment of transportation routes at risk</p>
</blockquote></li>
<li><blockquote>
<p>transportation routes in areas exposed to erosion</p>
</blockquote></li>
<li><blockquote>
<p>transportation routes in landslide-prone areas</p>
</blockquote></li>
</ul></td>
</tr>
<tr class="odd">
<td><strong>ADAPTATION CAPACITY</strong></td>
<td><ul>
<li><blockquote>
<p>existing flood protection system</p>
</blockquote></li>
<li><blockquote>
<p>functionality of the public drainage system</p>
</blockquote></li>
<li><blockquote>
<p>readiness of operational forces for flood protection</p>
</blockquote></li>
<li><blockquote>
<p>share of urban green and blue infrastructure in the urban area of the city (%)</p>
</blockquote></li>
</ul></td>
</tr>
</tbody>
</table>

**<span class="underline">ENERGETICS</span>**

<table>
<thead>
<tr class="header">
<th><strong>HAZARD: HEATHWAVE</strong></th>
<th><ul>
<li><blockquote>
<p>average daily air temperature</p>
</blockquote></li>
<li><blockquote>
<p>number of hot days (Tmax ≥ 30 °C)</p>
</blockquote></li>
<li><blockquote>
<p>number of tropical nights (Tmin &gt; 20 °C)</p>
</blockquote></li>
</ul></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>EXPOSURE</strong></td>
<td><ul>
<li><blockquote>
<p>total number of network users</p>
</blockquote></li>
<li><blockquote>
<p>total length of overhead power lines (km)</p>
</blockquote></li>
</ul></td>
</tr>
<tr class="even">
<td><strong>SENSITIVITY</strong></td>
<td><ul>
<li><blockquote>
<p>number of power outages per network user</p>
</blockquote></li>
</ul></td>
</tr>
<tr class="odd">
<td><strong>ADAPTATION CAPACITY</strong></td>
<td><ul>
<li><blockquote>
<p>implemented systems and procedures in case of power outages</p>
</blockquote></li>
<li><blockquote>
<p>connectivity of the electricity network in the City of Zagreb</p>
</blockquote></li>
<li><blockquote>
<p>number of connected solar power plants</p>
</blockquote></li>
<li><blockquote>
<p>energy efficiency of buildings</p>
</blockquote></li>
</ul></td>
</tr>
</tbody>
</table>

| WATER MANAGMENT SECTOR – FLOOD RISK AND VULNERABILITY          |                            |                          |
| -------------------------------------------------------------- | -------------------------- | ------------------------ |
|                                                                | Normalized Indicator Value | Overall Risk Calculation |
| HAZARD (H)                                                     |                            |                          |
| Number of consecutive rainy days (precipitation \> 1 mm)       | 0,54                       | 0,55                     |
| Number of days with heavy rainfall (\> 20 mm)                  | 0,59                       |                          |
| Maximum 1-day precipitation (Rx1d)                             | 0,52                       |                          |
| SENSITIVITY (SE)                                               |                            |                          |
| Occurrence of floods                                           | 1,00                       | 0,38                     |
| Safety and water quality                                       | 0,10                       |                          |
| Percentage of households without a water supply network        | 0,03                       |                          |
| ADAPTIVE CAPACITY (AC)                                         |                            |                          |
| Flood protection system                                        | 0,50                       | 0,53                     |
| Readiness of flood protection services                         | 0,10                       |                          |
| Functionality of the public drainage system:                   | 0,80                       |                          |
| Integrated approach to managing urban stormwater drainage      | 0,70                       |                          |
| Composite vulnerability indicator V= f(SE, AC)                 | 0,45                       |                          |
| EXPOSURE (EX)                                                  |                            |                          |
| Population density                                             | 1,00                       | 0,81                     |
| Number of water supply connections (% of population)           | 0,97                       |                          |
| Length of public drainage network in the flood-prone area (km) | 0,45                       |                          |
| RISK= f(H, V, EX)                                              |                            |                          |
| Overall Risk Rating                                            | 0,60                       |                          |

*Table 11 - Example of composite risk calculation following the IVAVIA
methodology. The table reports normalized values for hazard
(precipitation-based indicators), sensitivity (flood occurrence and
infrastructure fragility), adaptive capacity (defense systems, drainage
functionality, and preparedness), and exposure (population and
infrastructure in flood-prone areas). These elements are combined to
derive the composite vulnerability indicator and the final overall risk
rating.*
