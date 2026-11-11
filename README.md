# Time Series Forecasting: Linear Trends, Hybrid and Multistep Models

A step-by-step Jupyter notebook that walks through core time series forecasting techniques. Each section introduces one idea, applies it to a real dataset, and interprets the result.

## What's covered

| # | Section | Key ideas |
|---|---------|-----------|
| 1 | Setup and Data | Imports, plotting style, helper functions, store-sales data loading |
| 2 | Linear Regression with Time-Series Features | Time-step (trend) and lag (serial dependence) features |
| 3 | Trend | Moving averages, `DeterministicProcess`, linear and polynomial trends, extrapolation risk |
| 4 | Seasonality | Periodograms, weekly indicators, Fourier terms, holiday effects, one model per store and product family |
| 5 | Lags and Leads as Features | Autoregressive features, lagged search terms, lagged promotions and leads |
| 6 | Hybrid Models | Linear trend + XGBoost on residuals, a reusable hybrid class |
| 7 | Multistep Forecasting | Direct (multi-output) and chained (DirRec) strategies |
| 8 | Conclusions | Key findings and trade-offs |

## Key findings

- **Calendar features go a long way.** Trend, weekly indicators and Fourier terms explain most of the structure in daily store sales.
- **Trend extrapolation is fragile.** A cubic trend gave a stable forecast, while an order-11 polynomial fit history tightly and then forecast far too high.
- **Autoregressive features work but lag at turning points.** Flu visits have a lag-1 correlation of 0.95, but the forecast trails the actual peak by about a week.
- **Leads can be more informative than lags.** Upcoming promotions correlated more strongly with sales (0.61 at lead 3) than past promotions did (0.23 at lag 3).
- **Hybrids combine complementary strengths.** A linear trend plus a residual learner captures both trend and seasonality, but only as well as the trend stage allows.
- **More flexible is not always better.** For 8-week flu forecasts, XGBoost cut training RMSE from 540.6 to 195.8 but raised test RMSE from 697.9 to 798.0.


## Datasets

Make sure the folder (`Data_104/`) in the path and contains all the datasets used for this demonstration.

| File | Used for |
|------|----------|
| `train.csv` | Store sales (Favorita Store Sales competition data) |
| `holidays_events.csv` | National and regional holiday calendar |
| `book_sales.csv` | Small bookstore example |
| `tunnel.csv` | Daily tunnel traffic |
| `flu-trends.csv` | Weekly flu doctor visits and Google search volumes |
| `us-retail-sales.csv` | Monthly US retail sales by industry |


## Requirements

- Python 3.9+
- numpy, pandas, scipy
- matplotlib, seaborn
- scikit-learn
- statsmodels
- xgboost
- jupyter

Install everything with:

```bash
pip install numpy pandas scipy matplotlib seaborn scikit-learn statsmodels xgboost jupyter
```

## Getting started

```bash

jupyter notebook ssc_timeseries_4cast.ipynb
```

Run the cells top to bottom, since later sections reuse the helpers and datasets loaded in Section 1.

## Repository structure

```
.
├── ssc_timeseries_4cast.ipynb
├── Data_104/           
└── README.md
```

