# 📈 Implied Volatility Surface & Options Analysis

<p align="center">
  <strong>From Market Data to Quantitative Options Modeling</strong>
</p>

<p align="center">
  A Python-based quantitative finance project exploring real-world options data, option pricing, implied volatility, and volatility surface construction.
</p>

<p align="center">
  ![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
  ![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)
  ![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
  ![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
</p>

---

## 🧭 Overview

The objective of this project is to build a quantitative workflow that connects **mathematical finance, numerical methods, and real market data**.

Starting with SPY and AAPL option chains, the project investigates how option prices behave across strike prices and expiration dates, how market data should be cleaned, and how theoretical pricing relationships can be used to evaluate option prices.

The longer-term goal is to construct an implied volatility surface and explore its applications in pricing, risk analysis, and market-implied distributions.

## ✅ Completed Work

### 01 · Market Data Collection

- Retrieved SPY and AAPL option chains using `yfinance`.
- Collected call and put contracts across multiple expiration dates.
- Examined strike prices, bid and ask quotes, last prices, volume, and open interest.
- Recorded underlying prices, expiration dates, and time to maturity.
- Saved downloaded datasets locally in Parquet format.

### 02 · Exploratory Data Analysis

- Inspected dataset structure, data types, and missing values.
- Examined quote availability and bid–ask information.
- Compared option contracts across strikes and expirations.
- Identified potential stale-price issues in the downloaded snapshot.

### 03 · Data Cleaning

Applied a sequence of filters to prepare the option data for further modeling:

| Filter | Purpose |
|---|---|
| Minimum maturity | Exclude options with very short remaining lives |
| Moneyness range | Restrict strikes to a selected range around the underlying price |
| OTM selection | Retain out-of-the-money calls and puts |
| Positive open interest | Exclude contracts with no reported outstanding positions |

The cleaning process also tracks row counts after filtering, making it possible to evaluate how each criterion affects the dataset.

### 04 · Option Price Visualization

- Plotted call and put prices against strike prices.
- Examined expected price patterns across strikes.
- Measured how often adjacent observations followed the expected monotonicity patterns.
- Investigated deviations that may arise from noisy or stale prices.

### 05 · Mathematical Foundations

Studied option payoffs and no-arbitrage relationships, including:

- Call and put payoff functions at expiration.
- Time to maturity and log-moneyness.
- European option no-arbitrage bounds.
- Put–call parity and its derivation using portfolios with identical expiration payoffs.

For European options with continuous dividend yield \(q\), put–call parity is

\[
C-P=Se^{-qT}-Ke^{-rT}
\]

where \(C\) and \(P\) are call and put prices, \(S\) is the underlying price, \(K\) is the strike, \(T\) is time to maturity, and \(r\) is the risk-free interest rate.

The relationship provides a theoretical consistency check under its assumptions.

---

## 📊 Data Snapshot

The initial exploratory download produced the following results:

| Metric | SPY | AAPL |
|---|---:|---:|
| Raw option rows | 3,579 | 1,247 |
| Cleaned option rows | 1,310 | 270 |
| Observations retained | 36.6% | 21.7% |
| Expirations retained | 9 | 9 |

These figures describe the downloaded snapshot and may change when the data is refreshed.

> **Data quality note:** Many contracts lacked usable bid–ask quotes. Last traded prices were used as an exploratory fallback, so the current results should not be interpreted as live executable prices or evidence of arbitrage.

---

## 🛠️ Technology Stack

| Tool | Application |
|---|---|
| Python | Main programming language |
| `yfinance` | Market and options data retrieval |
| `pandas` | Data manipulation and cleaning |
| `NumPy` | Numerical computation |
| `Matplotlib` | Data visualization |
| Jupyter Notebook | Interactive research and experimentation |
| Parquet | Local dataset storage |

## 🗂️ Project Structure

```text
iv-surface/
│
├── data/                   # Raw and processed datasets
├── figures/                # Generated plots
├── src/                    # Reusable Python modules
│
├── 01_data_pipeline.ipynb
├── 02_black_scholes_greeks.ipynb
├── 03_implied_volatility.ipynb
├── 04_volatility_smile_term_structure.ipynb
├── 05_svi_surface.ipynb
├── 06_risk_density_strategies.ipynb
├── 07_app_preparation.ipynb
│
├── app.py                  # Planned Streamlit application
└── README.md
```

*The notebook sequence describes the intended project structure. Components that have not been implemented yet are planned work.*

---

## 🚀 Research Roadmap

- [ ] Improve quote quality and validate market data.
- [ ] Implement Black–Scholes pricing and option Greeks.
- [ ] Numerically solve for implied volatility.
- [ ] Analyze volatility smiles and term structures.
- [ ] Fit an implied volatility surface using SVI.
- [ ] Investigate arbitrage consistency and surface behavior.
- [ ] Explore option-implied risk measures and distributions.
- [ ] Build an interactive Streamlit application.

## 🎯 Project Goals

By the end of this project, the aim is to develop a reproducible workflow for:

- Translating mathematical finance theory into Python.
- Processing and validating real options market data.
- Applying numerical methods to option pricing.
- Understanding implied volatility across strikes and maturities.
- Communicating quantitative results through visualizations and an interactive application.

---

<p align="center">
  <strong>Mathematics · Programming · Quantitative Finance</strong>
  <br/>
  Building from theory to implementation, one model at a time.
</p>
