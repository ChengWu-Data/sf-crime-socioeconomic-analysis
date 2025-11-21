# Socioeconomic Drivers of Crime in San Francisco

This repository hosts an econometric and forecasting study on how socioeconomic factors relate to crime patterns in San Francisco.

Using ~**913k incident-level crime records** linked to **ACS census-tract panel data (2017–2022)**, the project builds a pipeline for:

- Spatial joining police incident data to census tracts  
- Constructing a tract–year panel dataset  
- Estimating fixed-effects and count models for crime rates  
- Exploring time dynamics with ARIMAX/SARIMAX-style forecasting

> ⚠️ Note: Parts of the original data loading and cleaning code were based on course-provided starter material. This repo focuses on my contributions in panel construction, modeling design, and interpretation.

---

## 💡 Research Question

> Is crime “about the economy”?  
> Specifically, how do **inequality, unemployment, education, mobility, and population change** relate to crime patterns across time and space?

---

## 🧱 Data & Construction

- **Crime data:**  
  - ~913,732 incident-level records from SF Open Data  
  - Fields include date, location (lat/long), offense type, resolution

- **Socioeconomic data:**  
  - ACS 5-year estimates at census tract level  
  - Variables: income, unemployment, Gini/inequality measures, education, transit usage, racial composition, etc.

- **Key engineering steps:**
  - Convert crime data to a GeoDataFrame and **spatially join** to census tracts
  - Aggregate to a **tract × year** panel
  - Create derived features:
    - changes in crime counts and rates
    - mobility & density metrics
    - time dummies (pre-/post-COVID, crisis periods, etc.)

---

## 📊 Methods

The analysis compares several modeling approaches:

- **Fixed-effects models** for panel data
  - tract fixed effects to control for unobserved heterogeneity
  - year dummies for macro shocks

- **Count models**
  - Poisson and **Negative Binomial** to handle over-dispersion
  - log crime counts and crime rates as outcomes

- **Time-series & forecasting**
  - ARIMAX / SARIMAX-style models on aggregated crime series
  - inclusion of economic covariates and event indicators (e.g., COVID, policy changes)

---

## 🔍 Key Findings (High-Level)

- **Mobility & density are robust predictors**  
  Higher public transit usage and mobility is consistently associated with higher crime rates across several categories.

- **Inequality & unemployment behave differently than naive expectations**  
  At the tract level, some models show *negative* associations once mobility and other factors are controlled, suggesting complex confounding and spatial sorting rather than a simple “more inequality → more crime” story.

- **Education has asymmetric effects**  
  Higher bachelor’s degree share tends to reduce violent/public order crime while correlating with higher reported property crime (e.g., more valuable targets, different reporting behavior).

- **COVID-era shifts**  
  Public order crimes decline while some property-related metrics rise, consistent with changes in activity patterns.

These are framed as **model-based associations**, not causal claims.

---

## 🧩 Why This Project Matters (for Analytics / BA / DS Roles)

This project is less about policing policy and more about:

- Designing and maintaining a **large-scale data pipeline** (geo joins, panel construction, aggregation)
- Choosing appropriate models for **count data, panel structure, and over-dispersion**
- Understanding the limits of individual-level prediction vs. **aggregate-level inference**
- Turning complex statistical output into **clear narratives for decision-makers**

The same skills are directly applicable to:

- demand & risk forecasting  
- operational analytics (branch performance, region targeting)  
- resource allocation models for business or public sector

---

## 📁 Repository Structure

```text
.
├── notebooks/
│   └── sf_crime_socioecon_analysis.ipynb   # main analysis notebook
├── report/
│   ├── Socioeconomic_Attributes_and_Crime.pdf
│   └── main.tex                            # LaTeX source (optional)
├── data/
│   └── README_DATA.md                      # links & notes about data sources
└── env/
    └── requirements.txt                    # optional environment file
```
---
Raw datasets not included due to size and licensing.

---

## 🛠 Tech Stack

**Languages & Analysis**  
Python, pandas, numpy  

**Spatial & Aggregation**  
geopandas, shapely  

**Modeling & Visualization**  
statsmodels, matplotlib, seaborn

---

## 📎 Acknowledgements

Crime data: San Francisco Open Data Portal  
Socioeconomic data: U.S. Census Bureau, American Community Survey (ACS)  
