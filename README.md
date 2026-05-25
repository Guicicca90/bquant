<div align="center">

# bquant

**Quantitative analysis toolkit for Brazilian financial, economic, and urban data.**

![Python](https://img.shields.io/badge/Python-0d1117?style=for-the-badge&logo=python&logoColor=58a6ff)
![pandas](https://img.shields.io/badge/pandas-0d1117?style=for-the-badge&logo=pandas&logoColor=58a6ff)
![statsmodels](https://img.shields.io/badge/statsmodels-0d1117?style=for-the-badge&logoColor=58a6ff)
![BigQuery](https://img.shields.io/badge/BigQuery-0d1117?style=for-the-badge&logo=googlebigquery&logoColor=58a6ff)

</div>

---

Personal research infrastructure for Brazilian asset markets and urban economics — built incrementally while studying time series theory, geodata, and financial econometrics to support real projects in production.

---

## `econ/` — Macroeconomic & Time Series

### Time series analysis (`timeseries_eda.py`)

Built around a key insight from studying rolling window statistics:

> A time series with **constant variance** over rolling windows supports the stationarity hypothesis — unit root closer to zero, as tested by Augmented Dickey-Fuller. A series with **increasing variance** indicates error accumulation over time, a hallmark of non-stationarity.

The scatterplot of a non-stationary series shows a visible pattern (error structure with trend); a stationary series looks like a near-random walk — constant variance, no accumulation.

**Implemented methods:**
- Stationarity tests: ADF (Augmented Dickey-Fuller), KPSS
- ACF (Autocorrelation Function) — measures linear correlation between a series at time *t* and its value at *t-k*, **including influence of all intermediate lags**
- PACF (Partial Autocorrelation) — isolates the direct relationship between *t* and *t-k*, controlling for intermediate lags
- ARIMA order selection from ACF/PACF patterns
- ARCH-LM volatility test (heteroskedasticity in residuals)
- Rolling mean/std visualization for structural break detection

### Macro indicators pipeline (`economia_pipeline.py`, `fipezap.py`)
- Selic, IPCA, IGPM, IBC-BR — scraped monthly from BCB, FGV, IBGE
- FipeZAP index: price/m² by city, type, rooms — with fallback chain for missing combinations
- IGMI-R real estate profitability index by state capital

### Financial markets (`mercados.py`)
- B3 and CVM data ingestion — asset prices, return series, portfolio statistics
- S&P 500 return attribution (notebooks)

---

## `geo/` — Geodata & Urban Intelligence

`GeoPipeline` — a full enrichment pipeline that joins and normalizes data from 8+ sources into parquet files consumed by [urban-space](https://github.com/Guicicca90/urban-space) and [solo-inteligente](https://github.com/Guicicca90/solo-inteligente).

| Module | What it processes |
|--------|------------------|
| `iptu_sp.py` | São Paulo IPTU — 11M+ parcels, fiscal value, lot area, zoning |
| `rais_geo.py` | RAIS labor market — employment, wages, sector composition by municipality |
| `idh_udh.py` | HDI and Urban Development Index by census unit (sub-municipal) |
| `indicadores_munic.py` | IPEA + ONU composite socioeconomic indicators by municipality |
| `estabmun.py` | Business establishment density and sector composition |
| `pipeline_geo.py` | Orchestrates all sources → normalized parquet files via `cKDTree` spatial joins |
| `ceps.py` | CEP geocoding and proximity assignment to UDH units |
| `delegacias.py` | Public safety data — police district boundaries and occurrence rates |
| `popmun.py` | Population, area, and density by municipality |

Spatial joins use `scipy.spatial.cKDTree` for fast nearest-neighbor matching between point datasets (CEPs, properties) and polygon centroids (UDH, districts).

---

## Data sources

| Source | Module | Used for |
|--------|--------|----------|
| GeoSampa (PMSP) | `geo/` | IPTU, zoning, land use |
| IPEA | `geo/` | Socioeconomic development indices |
| RAIS (MTE) | `geo/` | Labor market by municipality |
| ONU / UDH | `geo/` | Sub-municipal HDI |
| BCB | `econ/` | Selic, IGMI-R, IVG-R |
| FIPE / FipeZAP | `econ/` | Real estate price index |
| B3 / CVM | `econ/` | Asset prices |

---

*Feeds directly into [urban-space](https://github.com/Guicicca90/urban-space) and [solo-inteligente](https://github.com/Guicicca90/solo-inteligente).*
