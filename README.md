# bquant

Quantitative analysis toolkit for Brazilian financial and economic data.

Built incrementally as a personal research infrastructure — from exploratory notebooks to reusable pipelines.

---

## Modules

### `econ` — Macroeconomic & Time Series
- Stationarity testing (ADF, KPSS)
- ARIMA modeling with auto-order selection
- Volatility analysis (ARCH-LM)
- Macro indicators: Selic, IPCA, IGPM, FIPEZAP, IGMI-R

### `geo` — Geodata Enrichment
- Municipality-level socioeconomic data (IPEA, RAIS, ONU)
- GeoSampa integration for São Paulo spatial data
- Zoning and land use feature engineering

### `notebooks` — Research & Exploration
- Financial market data pipelines (B3, CVM)
- Asset return analysis and portfolio statistics
- Credit market indicators

---

## Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?style=flat&logo=pandas&logoColor=white)
![statsmodels](https://img.shields.io/badge/statsmodels-4DABCF?style=flat)
![BigQuery](https://img.shields.io/badge/BigQuery-669DF6?style=flat&logo=googlebigquery&logoColor=white)

---

## Context

Part of a larger research effort on Brazilian real estate and credit markets.
The `geo` module feeds directly into [urban-space](https://github.com/MaxPower90/urban-space).
