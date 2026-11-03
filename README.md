# How accurate are the NBP's inflation forecasts?

The National Bank of Poland (NBP) publishes inflation forecasts three times a year in its Inflation Report. This project checks how well those forecasts matched actual inflation from 2008 to 2025, and whether three simple models of my own can beat them.

## What I did

1. Collected 157 NBP forecasts (2008–2025) for the current year, one year ahead and two years ahead, and matched them with actual CPI inflation from GUS.
2. Measured how big the misses are and tested whether the NBP has a bias (too high or too low on average).
3. Built three models. Each was only allowed to use data that existed when the NBP made its forecast:
   - a naive guess (inflation stays at last year's level)
   - an AR(1) model (uses past inflation only)
   - a multi-variable model (adds wage growth, the oil price in złoty and the EUR/PLN rate)
4. Used the Diebold–Mariano test to check whether the differences between forecasts are real or just luck.

## Main results

Average miss in percentage points:

| Forecast | NBP | AR(1) | Multi-variable | Naive |
|---|---|---|---|---|
| Current year | 0.39 | 2.06 | 2.15 | 2.09 |
| One year ahead | 1.92 | 3.07 | 2.93 | 3.61 |
| Two years ahead | 2.39 | 2.99 | 3.53 | 3.73 |

- The NBP has no statistically significant bias, but its misses grow the further ahead it tries to predict.
- The NBP beats all three models at every horizon, and every one of those gaps is statistically significant.
- Adding wages, oil and the euro barely improved on AR(1). 
- Every model failed in the 2021–2023 inflation shock.

## Important Files:

- `analysis_clean.ipynb`: the full analysis
- `nbp_forecasts.csv`: NBP forecasts and actual inflation
- `gus_annual_cpi.csv`: annual CPI inflation, 2000–2025
- `inflation_drivers.csv`: yearly wage growth, oil price change in złoty and EUR/PLN change, 2000–2025

## Sources Used:

- NBP Inflation Reports (forecast figures as reported by PAP, ISBnews and other Polish media)
- GUS: annual CPI and average gross wage in the national economy
- U.S. Energy Information Administration: Brent oil price (Poland imports it and pays the world price set in dollars)
- OECD and the Federal Reserve (via FRED): exchange rates

