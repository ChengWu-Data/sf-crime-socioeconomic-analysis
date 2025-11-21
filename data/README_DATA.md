
# Data Sources & Access

This project does not include raw data files due to size and licensing constraints.

Instead, data can be downloaded from the following public sources:

---

## 📍 Crime Data — San Francisco

**Source:** SF Open Data  
https://data.sfgov.org/Public-Safety/Police-Department-Incidents/tmnf-yvry

Suggested fields to export:
- Incident Number
- Category / Subcategory
- Date / Time
- Latitude / Longitude
- Resolution
- Police District

Recommended format: CSV or GeoJSON

---

## 🌎 Socioeconomic Data — U.S. Census (ACS)

**Source:** American Community Survey  
https://www.census.gov/programs-surveys/acs

Suggested tables (5-year estimates):
| Category | ACS Table |
|----------|-----------|
| Population / mobility | B07001, B08006 |
| Education | B15003 |
| Income / inequality | B19013, B19083 |
| Employment | C23002 |
| Housing | DP04 |

Download by census tract for San Francisco County.

---

## 🔧 Data Processing Notes

- Convert ACS tables to tract → rename GEOID as key.
- Align years to crime timestamps (e.g., annual aggregation).
- Spatial joins performed using `shapely` + `geopandas.sjoin`.
- Panel structure: `tract × year`.

---

## 🔒 Licensing

All data belongs to its respective providers.  
This repository only includes derived datasets / code to transform publicly available sources.
