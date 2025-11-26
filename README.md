## Green Hydrogen MCDA Analysis

This notebook performs a Multi-Criteria Decision Analysis (MCDA) to evaluate the potential of selected MENA countries for hydrogen production and export. The analysis utilizes various indicators across supply, demand, and risk categories, employing an Analytic Hierarchy Process (AHP) for weighting and including sensitivity analysis to assess the robustness of the results.

## Objective

To rank selected MENA countries based on their suitability for hydrogen ventures using a predefined set of criteria and weights under different scenarios.

## Data

The analysis uses hardcoded data for Oman, Kuwait, Saudi Arabia, Egypt, Algeria, and Qatar, covering supply, demand, and risk indicators. A detailed description of these indicators, their sources, and characteristics is provided in Tab. 1\.  
**Table 1\.**  Indicators dataset for MCDA analysis 

| Indicator | Unit | Code/Note | Source | Sign | Year/Period |
| :---- | :---- | ----- | :---- | :---: | :---: |
| S1. PVOUT | kWh/kWp/day | Tech report GSA 2.0; raster/point | Global Solar Atlas  \[63\] | \+ | 2025 |
| S2. Wind @100 m | m/s | Dataset v4 (250 m) | Global Wind Atlas (DTU) \[64\] | \+ | 2025 |
| S3. LCOE  | USD/KWh | Regional benchmarking | IRENA cost reports 2018 \[179\] | \- | 2018 |
| S4. Inverse water stress | Projected Score % | Baseline/projected 2030 | WRI Aqueduct 4.0 \[51\] | \- | 2030 |
| D1. LPI (logistics) | Score (1-5) | Complete dataset 2007-2023 | World Bank LPI 2023 \[180\] | \+ | 2023 |
| D2. LSCI (maritime connectivity) | Index, mean=100 in Q1-2023 | IS.SHP.GCNW.XQ | UNCTAD \[181\] | \+ | Q3-2025 |
| D3. Steel Production | Mt/Yr | Report 2025; NH3 outlook | worldsteel; IFA \[182\] | \+ | 2024 |
| D4. LNG export capacity | Number of LNG berths | Gas/LNG infrastructure | GIIGNL \[183\] | \+ | 2024 |
| R1. WGI Government Effectiveness | % | DataBank/metadata | World Bank WGI \[184\] | \+ | 2023 |
| R2. WGI Regulatory Quality | % | DataBank/metadata (average) | World Bank WGI \[184\] | \+ | 2023 |
| R3. Fossil rents dependence | % Of GDP | NY.GDP.TOTL.RT.ZS inverse | WDI (World Bank) \[185\] | \+ | 2020-2021 |

## Methodology

The MCDA process involves:

1\.  Data Preparation: Loading, winsorizing, and normalizing indicator data.  
2\.  Weighting Scenarios: Defining and applying AHP weights for base, supply-led, and risk-aware scenarios (Tab. 2).  
3\.  Score Calculation & Ranking: Calculating composite scores and ranking countries based on these scores.  
4\.  Sensitivity Analysis: Assessing ranking uncertainty through bootstrap simulation (Output DataFrame) and evaluating the impact of individual weight perturbations (Fig. 4).

## Outputs

### The notebook generates key outputs including:

#### CSV Tables:

Table\_1\_AHP\_Weights.csv: AHP and Entropy Weights Summary  
Table\_2\_Weight\_Intervals.csv: Bootstrap Intervals for Mean Weights  
Table\_3\_Ranking\_Updated.csv: Main Ranking and Uncertainty Statistics  
Table\_4\_Sub\_Scores.csv: Sub-scores (Supply, Demand, Risk)

#### PNG Figures:

Fig\_1\_Dirichlet\_Weights.png: Dirichlet-Based Weight Intervals (95% Confidence)  
Fig\_2\_Ranking\_Uncertainty.png: Ranking with Uncertainty Bars (Rank Variation)  
Fig\_3\_Spider\_Chart.png: Spider chart of Sub-scores (All Countries)  
Fig\_5\_Sensitivity\_Heatmap\_Updated.png: Global Sensitivity Heatmap (Rank Stability)

#### HTML Map:

Fig\_4\_Choropleth\_Map.html: Choropleth map S-Index (supply) and WRI Aqueduct in overlay

## Requirements

The analysis requires the following Python libraries: pandas, numpy, matplotlib, seaborn, geopandas, folium, requests, and zipfile.

Usage

Upload MCDA\_for\_GH\_Suitability.ipynb file and run it on your notebook environments

Or Follow the steps below

1\.  Upload the \`hydrogen\_mcda\_dataset.csv\` file and the \`ne\_10m\_admin\_0\_countries.zip\` shapefile to your notebook environment.  
2\. Copy and paste code from mcda\_for\_gh\_suitability.txt file into a new cell  
2\.  Run The cell in the notebook.  
3\.  Review the generated tables and figures and html Map in the output.

### **Thank You**
