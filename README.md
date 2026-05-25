<div align="center">

# bquant

**Quantitative analysis toolkit for Brazilian financial and economic data.**

![Python](https://img.shields.io/badge/Python-0d1117?style=for-the-badge&logo=python&logoColor=58a6ff)
![pandas](https://img.shields.io/badge/pandas-0d1117?style=for-the-badge&logo=pandas&logoColor=58a6ff)
![statsmodels](https://img.shields.io/badge/statsmodels-0d1117?style=for-the-badge&logoColor=58a6ff)
![BigQuery](https://img.shields.io/badge/BigQuery-0d1117?style=for-the-badge&logo=googlebigquery&logoColor=58a6ff)

</div>

---

Built as personal research infrastructure for Brazilian asset markets and urban economics — from exploratory notebooks to reusable pipelines.

---

## Modules

### `econ/` — Macroeconomic & Financial Markets
- **`timeseries_eda.py`** — stationarity testing (ADF, KPSS), ACF/PACF, ARIMA modeling, volatility analysis (ARCH-LM)
- **`economia_pipeline.py`** — macro indicators pipeline: Selic, IPCA, IGPM, FIPEZAP, IGMI-R
- **`mercados.py`** — B3 and CVM data ingestion, asset return analysis, portfolio statistics
- **`fipezap.py`** — real estate price index time series for Brazilian markets
- **`econ_utils.py`** — shared utilities for normalization, date handling, and series transformation

### `geo/` — Geodata & Urban Intelligence
- **`iptu_sp.py`** — São Paulo IPTU public records ingestion and feature engineering
- **`rais_geo.py`** — RAIS labor market data aggregated by municipality
- **`idh_udh.py`** — HDI and urban development index by census unit
- **`indicadores_munic.py`** — composite socioeconomic indicators by municipality (IPEA, ONU)
- **`estabmun.py`** — business establishment density and sector composition per municipality
- **`pipeline_geo.py`** — full enrichment pipeline: joins socioeconomic + spatial layers
- **`ceps.py`**, **`delegacias.py`**, **`popmun.py`** — address, public safety, and population data by area

### `notebooks/` — Research & Exploration
- S&P 500 asset analysis and return attribution

---

## Data sources

| Source | Module | Used for |
|--------|--------|----------|
| GeoSampa (PMSP) | `geo/` | Zoning, IPTU, land use |
| IPEA | `geo/` | Socioeconomic indicators |
| RAIS (MTE) | `geo/` | Labor market by municipality |
| BCB / FipeZAP | `econ/` | Real estate and interest rate indices |
| B3 / CVM | `econ/` | Asset prices and financial market data |

---

*The `geo/` module feeds directly into [urban-space](https://github.com/MaxPower90/urban-space) — property pricing and terrain scouting.*
