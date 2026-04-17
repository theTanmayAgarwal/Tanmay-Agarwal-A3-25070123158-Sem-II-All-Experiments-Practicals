# COVID-19 Data Analysis Project

---

| Field            | Details                                      |
|------------------|----------------------------------------------|
| **Student Name** | Tanmay Agarwal                               |
| **PRN**          | 25070123158                                  |
| **Batch**        | EnTC A3                                      |
| **Course / Subject** | Data Analysis with Python               |
| **Experiment No.** | Experiment 19 & 20 (with Advanced Self-Learning Extension) |
| **Date**         | 15 April 2026                                |
| **Title**        | **COVID-19 Data Analysis Project**           |

---

## Table of Contents

1. [Abstract](#1-abstract)
2. [Objectives](#2-objectives)
3. [Dataset Description](#3-dataset-description)
4. [Tools and Technologies Used](#4-tools-and-technologies-used)
5. [Methodology](#5-methodology)
6. [Analysis and Visualizations](#6-analysis-and-visualizations)
7. [Key Insights](#7-key-insights)
8. [Summary / Conclusion](#8-summary--conclusion)
9. [Future Scope](#9-future-scope)
10. [References](#10-references)

---

## 1. Abstract

The COVID-19 pandemic, declared a global health emergency by the World Health Organization in March 2020, resulted in an unprecedented scale of human suffering and healthcare strain across every continent. Understanding the spread, progression, and comparative impact of the virus across countries and regions is critical for both retrospective learning and future pandemic preparedness. This project presents a comprehensive data-driven analysis of the COVID-19 pandemic using a publicly available time-series dataset spanning January 2020 to May 2021.

The analysis is implemented entirely in Python using a Jupyter Notebook environment and is structured across two formal laboratory experiments (Experiment 19 and Experiment 20), supplemented by an advanced self-learning extension. The dataset employed is `covid_19_data.csv`, which contains daily observations of confirmed cases, deaths, and recovered cases at the country and province level across approximately 180 countries and territories worldwide.

The project begins with foundational data preprocessing tasks — including column removal, data type conversion, and the derivation of a new feature (`Active` cases) — followed by a systematic Exploratory Data Analysis (EDA). In Experiment 19, a global overview is developed: the latest-date snapshot of the data is extracted, country-level aggregations are performed using `groupby`, and key statistics for individual countries (India, China, Spain, Germany) are retrieved and compared. A Plotly choropleth world map is rendered to provide a geographic perspective on confirmed case distribution. In Experiment 20, the analysis is narrowed to a country-level deep-dive into Spain, examining its province-wise distribution, identifying the most affected province using `max()` and `idxmax()`, and generating a country-specific choropleth map.

The advanced self-learning extension introduces eight sophisticated analytical techniques that extend well beyond the standard syllabus. These include: (1) computation of epidemiologically significant mortality and recovery rates using vectorized arithmetic; (2) multi-metric country ranking using the Pandas `rank()` method with `method='dense'`; (3) a global time-series line plot using `groupby` on observation dates to visualize the cumulative trajectory of the pandemic over 16 months; (4) a Seaborn correlation heatmap using `df.corr()` to examine inter-metric relationships across all six numeric COVID variables; (5) a 7-day rolling average analysis using `diff()` and `rolling(7).mean()` to smooth epidemic curves for India, the US, and Brazil; (6) a grouped bar chart constructed with offset `matplotlib` bars for side-by-side multi-metric comparison of the top 10 countries; (7) a Pandas `pivot_table()` summarizing monthly peak confirmed cases for the top 8 countries; and (8) a horizontal barplot ranking the top 5 and bottom 5 countries by recovery rate using `nlargest()` and `nsmallest()`.

The primary libraries employed throughout this project are `pandas` and `numpy` for data manipulation, `matplotlib` and `seaborn` for static visualization, and `plotly.express` and `plotly.graph_objects` for interactive geographic maps. The project demonstrates a robust command of data preprocessing, feature engineering, exploratory analysis, statistical computation, and multi-layered visualization — collectively providing actionable insights into the global impact of COVID-19.

---

## 2. Objectives

The project is guided by the following clearly defined objectives:

- To load, inspect, and preprocess the COVID-19 dataset by removing irrelevant columns, correcting data types, and engineering derived features such as `Active` cases.
- To extract and analyze the most recent (latest-date) snapshot of the dataset to identify the current state of the pandemic across all countries and territories.
- To perform country-level aggregation using `groupby` and summarize key metrics — Confirmed, Deaths, Recovered, and Active cases — for individual countries of interest, including India, China, Spain, and Germany.
- To identify the top 20 countries by confirmed case count and visualize the geographic distribution of the pandemic using an interactive Plotly choropleth world map.
- To conduct a focused country-level analysis on Spain, including an examination of its province-wise distribution of cases, identification of the most affected province, and generation of a Spain-specific choropleth map.
- To compute and compare epidemiological rates — specifically the Mortality Rate and Recovery Rate — for all countries in the dataset, providing a normalized measure of pandemic severity beyond raw case counts.
- To perform multi-dimensional country ranking using the Pandas `rank()` function to compare nations simultaneously across confirmed cases, deaths, and mortality rate.
- To reconstruct the global epidemic curve by aggregating daily observations and plotting a time-series line chart of Confirmed, Recovered, and Deaths from January 2020 to May 2021.
- To assess correlations among all key COVID-19 numeric metrics using a Seaborn heatmap of the Pearson correlation matrix.
- To apply signal smoothing techniques — specifically the 7-day rolling average — to daily new case data for India, the US, and Brazil, in order to identify epidemic waves and filter out reporting noise.
- To build a grouped bar chart and a pivot table to enable structured, multi-dimensional comparisons of pandemic outcomes across countries and time periods.
- To identify the best and worst performing countries by recovery rate using `nlargest()` and `nsmallest()` filtering.
- To demonstrate proficiency in Python-based data analysis techniques and produce a polished, reproducible, well-documented analytical project.

---

## 3. Dataset Description

### Dataset File

```
covid_19_data.csv
```

### Source

The dataset is a well-known public COVID-19 tracking dataset, widely used in academic and research settings. It is structured as a time-series record of daily pandemic statistics at the sub-national (province/state) and national (country/region) level.

### Coverage

- **Time Range:** January 2020 to May 2021 (approximately 16 months)
- **Geographic Scope:** Approximately 180 countries and territories
- **Granularity:** Daily observations, with some countries reporting at the province/state level

### Original Columns

| Column Name       | Data Type (Original) | Description                                                     |
|-------------------|---------------------|-----------------------------------------------------------------|
| `SNo`             | Integer              | Serial number — row index (dropped during preprocessing)        |
| `ObservationDate` | String → DateTime    | Date of the observation record                                  |
| `Province/State`  | String               | Sub-national region (many entries are null for country-level)   |
| `Country/Region`  | String               | Name of the country or territory                                |
| `Last Update`     | String               | Timestamp of last update (dropped during preprocessing)         |
| `Confirmed`       | Float → Integer      | Cumulative confirmed COVID-19 cases                             |
| `Deaths`          | Float → Integer      | Cumulative COVID-19 deaths                                      |
| `Recovered`       | Float → Integer      | Cumulative recovered cases                                      |

### Derived / Engineered Columns

| Column Name          | Derived From                             | Description                                      |
|----------------------|------------------------------------------|--------------------------------------------------|
| `Active`             | `Confirmed - Recovered - Deaths`         | Estimated currently active (unresolved) cases    |
| `Mortality_Rate_%`   | `(Deaths / Confirmed) * 100`             | Percentage of confirmed cases that resulted in death |
| `Recovery_Rate_%`    | `(Recovered / Confirmed) * 100`          | Percentage of confirmed cases that resulted in recovery |
| `Rank_Confirmed`     | `rank()` on Confirmed                    | Country rank by total confirmed cases            |
| `Rank_Deaths`        | `rank()` on Deaths                       | Country rank by total deaths                     |
| `Rank_Mortality`     | `rank()` on Mortality_Rate_%             | Country rank by mortality rate                   |
| `Daily_New`          | `Confirmed.diff()`                       | Daily new cases (first-order difference)         |
| `Rolling_7d`         | `Daily_New.rolling(7).mean()`            | 7-day rolling average of daily new cases         |
| `Month`              | `ObservationDate.dt.to_period('M')`      | Month-year string used for pivot table grouping  |

### Key Observations about the Dataset

- The `Recovered` column contains `0` values for the United States throughout most of the dataset. This is a known reporting discrepancy — the US ceased reporting recovery counts at the national level and is not an actual zero-recovery figure.
- `Province/State` is sparsely populated; many countries report only at the national level, making this column null-heavy.
- Case counts are **cumulative** (monotonically increasing), not daily new cases. Daily new cases must be derived using `.diff()`.

---

## 4. Tools and Technologies Used

### Programming Language

- **Python 3.x** — The primary language for all data loading, processing, analysis, and visualization tasks.

### Development Environment

- **Jupyter Notebook** — An interactive, cell-based execution environment that supports inline visualization and reproducible analysis. Hosted on Google Colab for this project.

### Libraries

| Library                     | Version    | Purpose                                                                                          |
|-----------------------------|------------|--------------------------------------------------------------------------------------------------|
| `pandas`                    | Standard   | Core data manipulation: DataFrames, `groupby`, `pivot_table`, `merge`, `rank`, filtering, type casting |
| `numpy`                     | Standard   | Numerical operations, `NaN` handling, vectorized arithmetic for rate calculations                |
| `matplotlib.pyplot`         | Standard   | Static chart construction: line plots, bar charts, horizontal barplots, subplot layouts          |
| `matplotlib.ticker`         | Standard   | Custom axis formatters (e.g., comma-separated large numbers: `1,000,000`)                       |
| `seaborn`                   | Standard   | Statistical visualization: correlation heatmap; global theme and palette configuration           |
| `plotly.express`            | Standard   | Interactive choropleth world maps and country-level geographic visualizations                    |
| `plotly.graph_objects`      | Standard   | Low-level Plotly figure construction for custom map configurations                               |
| `warnings`                  | Built-in   | Suppression of non-critical runtime warnings to maintain clean notebook output                   |

---

## 5. Methodology

The project follows a systematic analytical pipeline progressing from raw data ingestion through multi-level visualization. Each step is described in detail below.

### Step 1 — Data Loading and Initial Inspection

The dataset is loaded from a CSV file using `pd.read_csv()`. Initial inspection is performed using:

- `data.head()` — to view the first five rows and understand the column structure.
- `data.tail()` — to confirm the dataset's end records and time range.
- `data.info()` — to inspect column names, non-null counts, and initial inferred data types.

```python
import pandas as pd
import numpy as np

data = pd.read_csv("/content/covid_19_data.csv")
data.head()
data.info()
```

### Step 2 — Data Cleaning

Two columns — `SNo` (a meaningless sequential index) and `Last Update` (a redundant timestamp not used in analysis) — are removed using `data.drop()`:

```python
data = data.drop(['SNo', 'Last Update'], axis=1)
```

This reduces noise and ensures downstream operations are performed only on analytically relevant fields.

### Step 3 — Data Type Conversion

The initial data types inferred by `pandas` are incorrect for analytical use:

- `ObservationDate` is loaded as a generic `object` (string) and must be converted to `datetime64[ns]` to enable date-based filtering, sorting, and time-series operations.
- `Confirmed`, `Deaths`, and `Recovered` are loaded as `float64` (due to missing values in the source file) and are converted to `int64` for cleaner arithmetic and display.

```python
data['ObservationDate'] = data['ObservationDate'].astype('datetime64[ns]')
data['Confirmed']       = data['Confirmed'].astype('int64')
data['Deaths']          = data['Deaths'].astype('int64')
data['Recovered']       = data['Recovered'].astype('int64')
```

### Step 4 — Feature Engineering

A derived column, `Active`, is computed as the difference between confirmed, recovered, and death counts. This provides an estimate of the number of unresolved (currently infected) cases at any given point:

```python
data['Active'] = data['Confirmed'] - data['Recovered'] - data['Deaths']
```

### Step 5 — Latest-Date Snapshot Extraction

The most recent date in the dataset is identified using `data['ObservationDate'].max()`. A filtered DataFrame, `latest_data`, is constructed to hold only records from this date, enabling analysis of the state of the pandemic at its last recorded moment:

```python
latest_data = data[data['ObservationDate'] == data['ObservationDate'].max()]
```

### Step 6 — Country-Level Aggregation

Using `groupby` on `Country/Region`, the latest-date data is aggregated (summed) to produce a single-row-per-country summary DataFrame called `countries`. This is essential because some countries (notably China, Australia, and Canada) have province-level rows that must be summed to obtain national totals:

```python
countries = latest_data.groupby("Country/Region")[["Confirmed", "Deaths", "Active"]].sum().reset_index()
```

Specific country lookups (India, China — referred to as "Mainland China" — Spain, and Germany) are performed using boolean filtering on this aggregated DataFrame.

### Step 7 — Geographic Visualization (World Map)

A Plotly `choropleth` map is rendered using the `country names` location mode, with `Confirmed` cases mapped to a `YlGnBu` color scale. This provides an immediate geographic overview of which countries bore the heaviest case burden:

```python
import plotly.express as px

world_map = px.choropleth(
    countries,
    locations="Country/Region",
    locationmode="country names",
    color="Confirmed",
    color_continuous_scale="YlGnBu",
    range_color=[1, 10000000]
)
world_map.show()
```

### Step 8 — Top 20 Countries Ranking

The `groupby` result is sorted by `Confirmed` in descending order to rank the top 20 most affected countries, with both confirmed and recovered counts displayed.

### Step 9 — Spain Deep-Dive (Experiment 20)

The dataset is filtered to rows where `Country/Region == 'Spain'`. Province-level analysis is performed:

- `nunique()` gives the count of distinct provinces.
- `unique()` lists all province names.
- `mode()` identifies the most frequently reported province/state entry.
- A latest-date filter extracts Spain's snapshot, followed by a `groupby` on `Province/State` to identify the hardest-hit province.
- A Plotly choropleth map is generated specifically for Spain using the `Magma` color scale.

### Step 10 — Epidemiological Rate Computation (Advanced)

A fuller version of the `countries` DataFrame (`countries_full`) is built, including `Recovered` in the aggregation. Mortality and recovery rates are computed using vectorized Pandas arithmetic:

```python
countries_full['Mortality_Rate_%'] = (
    countries_full['Deaths'] / countries_full['Confirmed'].replace(0, float('nan'))
) * 100

countries_full['Recovery_Rate_%'] = (
    countries_full['Recovered'] / countries_full['Confirmed'].replace(0, float('nan'))
) * 100
```

Division by zero is handled by replacing `0` with `NaN` before the operation.

### Step 11 — Multi-Metric Country Ranking

The Pandas `.rank()` method with `method='dense'` and `ascending=False` is applied to assign competitive rankings across three dimensions — confirmed cases, deaths, and mortality rate — enabling a multi-dimensional comparison of countries:

```python
countries_full['Rank_Confirmed'] = countries_full['Confirmed'].rank(method='dense', ascending=False).astype(int)
```

### Step 12 — Global Time-Series Line Plot

All country rows are aggregated by `ObservationDate` using `groupby` to produce a global daily total. The resulting time-series is plotted using `matplotlib` with three lines (Confirmed, Recovered, Deaths) and a custom y-axis formatter for readability.

### Step 13 — Correlation Heatmap

The Pearson correlation matrix is computed on six numeric columns using `.corr()`. A `seaborn.heatmap()` with the `coolwarm` palette, `annot=True`, and `fmt='.2f'` renders the matrix as a visually interpretable grid.

### Step 14 — 7-Day Rolling Average

A reusable function `get_country_daily_rolling()` encapsulates the full pipeline for a given country:

1. Filter rows to the country.
2. Aggregate by date (in case of province-level rows).
3. Compute `Daily_New` using `.diff()`, clipped at 0 to remove negative corrections.
4. Compute the 7-day rolling mean using `.rolling(7).mean()`.

This is applied for India, the US, and Brazil, and rendered as a 3-panel subplot with combined bar and line charts.

### Step 15 — Grouped Bar Chart

Manual x-axis offset computation (`i - width`, `i`, `i + width`) is used to place three bars side-by-side for each country in the top 10, enabling direct visual comparison of Confirmed, Recovered, and Deaths.

### Step 16 — Pivot Table

`pd.pivot_table()` reshapes the data into a Country × Month matrix, using `aggfunc='max'` to capture the end-of-month cumulative peak:

```python
pivot = data_pt_filtered.pivot_table(
    index='Country/Region',
    columns='Month',
    values='Confirmed',
    aggfunc='max'
).fillna(0).astype(int)
```

### Step 17 — Recovery Rate Ranking

Countries with fewer than 1,000 confirmed cases or with zero recorded recoveries are filtered out. The remaining countries are ranked using `nlargest(5)` and `nsmallest(5)` on `Recovery_Rate_%`, and visualized as dual horizontal barplots.

---

## 6. Analysis and Visualizations

### 6.1 Exploratory Data Analysis (EDA)

Initial exploration established the dataset's dimensions, temporal range, and column characteristics. The latest observation date was confirmed as 29 May 2021. At this snapshot, the dataset captured data for over 180 distinct countries and territories, with some represented at both national and sub-national granularity. Country-level filtering for India, China (Mainland China), Spain, and Germany provided a targeted comparison of how differently the pandemic manifested across these four nations in terms of confirmed cases, deaths, and active caseloads.

### 6.2 World Map Choropleth (Plotly — Global)

The interactive choropleth world map uses a continuous `YlGnBu` color scale, with deeper blue shading indicating higher confirmed case burdens. The range is calibrated from 1 to 10,000,000, effectively highlighting the stark disparity between highly affected nations (United States, India, Brazil) and those with comparatively low counts. This visualization allows for immediate geographic pattern recognition — notably the concentration of severe outbreaks in North America, South Asia, and South America.

### 6.3 Top 20 Countries by Confirmed Cases

A tabular ranking of the top 20 countries by confirmed case count, including both confirmed and recovered totals, provides a quantitative foundation for subsequent comparative analyses. The United States, India, and Brazil consistently occupy the top three positions.

### 6.4 Spain Province-Level Analysis

Experiment 20 narrows the geographic scope to Spain. The province-level analysis reveals the number of distinct reporting regions within Spain and uses `groupby` aggregation to identify the most affected province by confirmed case count. A separate choropleth map is rendered for Spain using the `Magma` color scale, reinforcing the country-level burden data.

### 6.5 Mortality Rate and Recovery Rate Table

The computed rate table for the top 10 countries by confirmed cases presents normalized epidemiological metrics that contextualise the raw numbers. Mexico consistently shows one of the highest mortality rates among major countries, reflecting documented issues with under-testing and hospital capacity saturation. India's relatively low mortality rate (approximately 1.2%) despite its enormous absolute case count is a notable pattern, partially attributable to demographic factors. The United States shows a `Recovery_Rate` of 0% for reasons of data reporting, not actual patient outcomes.

### 6.6 Multi-Metric Country Ranking Table

The multi-dimensional ranking table reveals that a country's rank by confirmed case count does not necessarily correspond to its rank by mortality rate. Germany, for instance, ranks highly by confirmed cases but significantly lower by mortality rate, reflecting effective healthcare infrastructure. This dissociation between volume-based and rate-based rankings is a key analytical insight that underscores the importance of normalizing metrics.

### 6.7 Global Time-Series Line Plot

The time-series line chart spans January 2020 to May 2021, plotting the global cumulative totals for Confirmed (red), Recovered (green), and Deaths (purple) on a shared axis. The chart reveals a near-flat period through early 2020, followed by gradual growth through mid-2020, then a sharp exponential acceleration beginning in late 2020 and continuing into 2021. The recovery curve tracks the confirmed curve with a temporal lag, indicating globally sustained treatment capacity. The deaths curve remains proportionally flat, visually confirming a global case fatality rate in the 2–3% range.

### 6.8 Correlation Heatmap (Seaborn)

The heatmap of the Pearson correlation matrix covers six variables: Confirmed, Deaths, Recovered, Active, Mortality Rate, and Recovery Rate. The `coolwarm` color scheme maps positive correlations to red and negative to blue, with annotated values in each cell. The visualization makes several relationships immediately apparent and is discussed in detail under Key Insights.

### 6.9 7-Day Rolling Average — India, US, and Brazil

The three-panel subplot compares the epidemic curves of India, the United States, and Brazil using a combined bar-and-line presentation. Raw daily new cases are shown as semi-transparent bars; the 7-day rolling average overlays these as a solid line, filtering the weekly reporting noise inherent in public health data submissions. Each country's panel uses a distinct color palette for visual differentiation. This is one of the most analytically rich charts in the project, capturing wave timing, peak intensity, and post-peak trajectory simultaneously.

### 6.10 Grouped Bar Chart — Top 10 Countries

The side-by-side grouped bar chart displays three bars per country (Confirmed, Recovered, Deaths) for the top 10 nations. The manual offset calculation ensures no overlapping between bar groups. The y-axis is formatted with comma-separated values for readability at the scale of tens of millions. The chart makes the US reporting anomaly for recovered cases visually obvious, while also clearly illustrating that deaths represent a small fraction of total cases across all major countries.

### 6.11 Pivot Table — Country × Month

The pivot table restructures the data into a matrix with countries as rows and calendar months (January 2020 to May 2021) as columns, with each cell containing the maximum (end-of-month) confirmed case total for that country. The table is filtered to the top 8 countries for readability. Month-over-month changes can be computed from adjacent columns to derive approximate monthly new case counts for each country, providing a tabular complement to the line chart.

### 6.12 Top and Bottom 5 Countries by Recovery Rate

The dual horizontal barplot presents the five countries with the highest recovery rates (shown in green) alongside the five with the lowest (shown in red), with percentage labels embedded within each bar. The chart is filtered to exclude countries with fewer than 1,000 confirmed cases (to eliminate statistical outliers from small nations) and countries with zero recorded recoveries (to exclude data gaps). This visualization provides a direct comparative measure of healthcare system performance.

---

## 7. Key Insights

- **The United States recorded the highest total confirmed COVID-19 cases** among all countries in the dataset as of 29 May 2021, followed by India and Brazil — a pattern consistent across all public datasets covering this period.

- **India's mortality rate was approximately 1.2%** despite accumulating one of the world's largest absolute case burdens, which may be partially attributed to a younger median population age compared to high-mortality nations like Mexico.

- **Mexico exhibited one of the highest mortality rates** among major countries with significant caseloads, reflecting both documented under-testing (which inflates the rate) and documented hospital capacity challenges during peak transmission.

- **The United States shows a Recovery Rate of 0% in this dataset**, which is a known reporting artifact — the US ceased nationally consolidated reporting of recovered cases and this should not be interpreted as an absence of recoveries.

- **Confirmed cases and Deaths are very highly correlated (approximately 0.95)** at the country level, confirming that the absolute scale of an outbreak is the strongest predictor of total death toll.

- **Mortality Rate shows a weaker correlation with Confirmed cases** than Deaths does, establishing that raw caseload alone does not determine death rate — healthcare capacity, testing coverage, and population demographics are significant moderating factors.

- **Recovery Rate and Mortality Rate are negatively correlated**, as logically expected: countries where a larger proportion of patients recovered also recorded lower proportional death rates.

- **India's Second Wave (Delta variant, April–May 2021)** is the single sharpest epidemic peak visible in the 7-day rolling average analysis, surpassing the scale and speed of rise of the US holiday surge of January 2021.

- **The US epidemic curve shows a multi-wave structure** with a broad first wave through 2020 and a sharp second peak in January 2021, after which cases declined substantially — corresponding with the commencement of mass vaccination.

- **Brazil demonstrated the most sustained high-plateau epidemic trajectory** among the three countries compared in the rolling average analysis, with multiple surges and no clear sustained decline within the dataset's timeframe.

- **Month-over-month exponential growth** is clearly visible in the pivot table from March 2020 onward, with growth rates tapering in mid-2020 before accelerating again in late 2020 through early 2021.

- **Countries with high recovery rates** in the filtered ranking typically reflect both strong primary healthcare infrastructure and consistent national-level recovery case reporting practices.

- **The 7-day rolling average technique** is standard in epidemiology precisely because raw daily counts are distorted by weekend reporting lags. Smoothing over a 7-day window eliminates this artifact without introducing meaningful lag relative to the actual wave trend.

- **Spain's most affected province** (identified via `groupby` aggregation on the latest-date Spain subset) demonstrates that even within a single country, the pandemic's impact was spatially concentrated rather than uniformly distributed.

---

## 8. Summary / Conclusion

This project constitutes a thorough, multi-layered analysis of the COVID-19 pandemic as recorded in a time-series dataset spanning January 2020 to May 2021. Beginning with rigorous data preprocessing — including type conversion, column removal, and the derivation of active case counts — the analysis progressively increases in analytical sophistication across the two formal experiments and the advanced self-learning extension.

Experiment 19 established the global overview: the latest-date snapshot was extracted, country-level aggregations were performed, selected countries were individually inspected, and an interactive choropleth world map was generated to visually communicate the geographic distribution of the pandemic's burden. Experiment 20 deepened the analysis with a country-specific investigation of Spain, demonstrating the application of province-level `groupby` operations, modal value identification, and targeted geographic visualization.

The advanced extension, comprising eight distinct analytical modules, demonstrated that the data contained significantly more analytical depth than the core experiments uncovered. Epidemiological rate computation provided normalized comparison metrics that raw case counts cannot. Multi-metric ranking exposed the non-linear relationship between case volume and health system outcomes. The global time-series chart provided the clearest visual narrative of the pandemic's entire trajectory. The correlation heatmap revealed that while scale and mortality are strongly linked in absolute terms, the death *rate* is determined by factors beyond case count alone. The rolling average analysis revealed the precise structure of epidemic waves in the three most affected countries. The pivot table offered a compact but information-dense summary of 16 months of pandemic progression across eight nations.

From this project, it is evident that effective pandemic data analysis requires both breadth (understanding global patterns) and depth (understanding country-specific dynamics and normalized metrics). Python's data analysis ecosystem — particularly `pandas`, `matplotlib`, `seaborn`, and `plotly` — provides a comprehensive and accessible toolkit for performing this type of analysis at scale. The project also reinforces the critical lesson that data quality issues (such as the US recovery reporting gap) must be identified and explicitly handled before drawing analytical conclusions.

---

## 9. Future Scope

The following extensions and improvements could meaningfully enhance this project:

- **Vaccination Data Integration:** Merging COVID-19 vaccination rollout data (available from Our World in Data and official government sources) with the case/death time series would allow analysis of the quantitative impact of vaccination on case and mortality trajectories — specifically, whether countries with earlier and faster rollouts saw steeper post-vaccination declines.

- **Machine Learning Forecasting:** Applying time-series forecasting models such as Facebook Prophet, ARIMA, or LSTM recurrent neural networks to the global confirmed case trend or country-specific epidemic curves would enable forward-looking projections and validation of model accuracy against known outcomes post-May 2021.

- **Population-Normalized Metrics:** All current analyses are based on absolute counts, which heavily favours large-population nations. Normalizing by population (e.g., cases per million, deaths per million) would enable fairer inter-country comparisons and would likely reveal different leaders and laggards in pandemic management.

- **Variant-Level Analysis:** Integrating variant sequencing data (e.g., GISAID database) with the case timeline would allow visualization of how the emergence of specific variants (Alpha, Delta, Omicron) correlates with observed changes in case trajectory, severity, and mortality rate.

- **Interactive Dashboard:** Converting the static and Plotly visualizations into a fully interactive web dashboard using Streamlit or Dash would enable end-users to dynamically select countries, date ranges, and metrics — making the analysis accessible to non-technical audiences and stakeholders.

- **Excess Mortality Analysis:** Many countries are believed to have significantly under-counted COVID-19 deaths. Incorporating excess mortality data (comparing actual deaths in 2020–2021 to historical baseline death rates) would provide a more accurate measure of the pandemic's true lethal impact.

- **Healthcare Infrastructure Correlation:** Correlating COVID outcomes (mortality rate, recovery rate) with national healthcare capacity indicators such as hospital beds per thousand people, physicians per thousand, and healthcare expenditure as a percentage of GDP would allow evidence-based assessment of which structural factors most strongly predicted pandemic outcomes.

- **Extension of Dataset:** The current dataset ends in May 2021. Extending the analysis to cover the Omicron wave (late 2021 through 2022) and the post-pandemic transition period would provide a complete picture of the pandemic's full lifecycle.

---

## 10. References

1. World Health Organization (WHO). *COVID-19 Dashboard.* https://covid19.who.int/

2. Johns Hopkins University Center for Systems Science and Engineering (JHU CSSE). *COVID-19 Data Repository.* https://github.com/CSSEGISandData/COVID-19

3. McKinney, W. (2017). *Python for Data Analysis: Data Wrangling with Pandas, NumPy, and IPython* (2nd ed.). O'Reilly Media.

4. VanderPlas, J. (2016). *Python Data Science Handbook.* O'Reilly Media. https://jakevdp.github.io/PythonDataScienceHandbook/

5. Waskom, M. et al. (2021). *Seaborn: Statistical Data Visualization.* Journal of Open Source Software, 6(60), 3021. https://doi.org/10.21105/joss.03021

6. Hunter, J. D. (2007). *Matplotlib: A 2D Graphics Environment.* Computing in Science & Engineering, 9(3), 90–95.

7. Plotly Technologies Inc. *Plotly Python Open Source Graphing Library.* https://plotly.com/python/

8. Our World in Data. *Coronavirus Pandemic (COVID-19) Statistics and Research.* https://ourworldindata.org/coronavirus

9. pandas Development Team. *pandas Documentation.* https://pandas.pydata.org/docs/

10. NumPy Developers. *NumPy Documentation.* https://numpy.org/doc/

---

*This project was developed as part of the laboratory curriculum for Exploratory Data Analysis with Python. All analysis is performed on publicly sourced data for educational purposes only.*

*Made by solely Tanmay Agarwal*
