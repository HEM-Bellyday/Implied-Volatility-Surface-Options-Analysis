# Implied Volatility Surface & Options Analysis

A quantitative finance project exploring real-world options data, option pricing, implied volatility, and volatility surface construction using Python.

## Completed Work

### 1. Options Data Collection
- Downloaded SPY and AAPL option chains using `yfinance`.
- Collected calls and puts across multiple expiration dates.
- Captured strike prices, bid and ask quotes, last traded prices, volume, open interest, and Yahoo Finance implied volatility.
- Recorded underlying spot prices, expiration dates, time to maturity, and the risk-free rate.
- Saved raw option data locally in Parquet format.

### 2. Exploratory Data Analysis
- Inspected dataset structure, column types, and missing values.
- Compared call and put option quotes.
- Examined bid–ask quotes, strike prices, expirations, trading volume, and open interest.
- Investigated quote availability and identified potential stale-price issues.

### 3. Data Cleaning
- Applied filters based on time to maturity.
- Restricted strikes to a defined moneyness range.
- Retained out-of-the-money options.
- Filtered contracts using open interest.
- Recorded how many observations were removed by each filter.
- Compared the number of observations retained for SPY and AAPL.

### 4. Option Price Visualization
- Plotted call and put prices against strike prices.
- Examined whether call prices generally decrease and put prices generally increase with strike.
- Evaluated deviations from the expected price patterns.

### 5. Mathematical Foundations
- Reviewed call and put payoffs at expiration.
- Studied forward prices, log-moneyness, and European option no-arbitrage bounds.
- Formulated and proved put–call parity by comparing portfolios with identical expiration payoffs.

## Data Quality Considerations

The downloaded snapshot contained many zero bid and ask quotes. As a fallback for exploratory analysis, last traded prices were used when sufficient bid–ask quotes were unavailable.

These prices may be stale and should not be interpreted as reliable live-market quotes. The current plots and put–call parity comparisons are exploratory rather than evidence of executable arbitrage opportunities.

A further validation step is to obtain a snapshot with reliable bid–ask quotes and repeat the analysis.

## Technology Stack

- **Python** — quantitative analysis and data processing
- **pandas** — tabular data manipulation
- **NumPy** — numerical computation
- **Matplotlib** — data visualization
- **yfinance** — market and options data retrieval
- **Parquet** — local data storage
- **Jupyter Notebook** — interactive analysis

## Project Structure

```text
iv-surface/
├── data/
│   ├── raw_SPY.parquet
│   ├── raw_AAPL.parquet
│   └── market_meta.json
├── figures/
├── src/
├── 01_data_pipeline.ipynb
├── 02_black_scholes_greeks.ipynb
├── 03_implied_volatility.ipynb
├── 04_volatility_smile_term_structure.ipynb
├── 05_svi_surface.ipynb
├── 06_risk_density_strategies.ipynb
├── 07_app_preparation.ipynb
├── app.py
└── README.md
```

*Some folders and notebooks represent the planned project structure and may not yet contain completed work.*

## Next Steps

- Improve quote quality and validate the cleaned dataset.
- Implement Black–Scholes option pricing and Greeks.
- Calculate implied volatility numerically from observed option prices.
- Analyze volatility smiles and term structures.
- Fit an arbitrage-aware implied volatility surface.
- Explore risk measures and option-implied distributions.
- Build an interactive Streamlit application.

## Objective

Develop a reproducible quantitative finance workflow that connects mathematical theory, real options data, numerical methods, and practical financial analysis.
