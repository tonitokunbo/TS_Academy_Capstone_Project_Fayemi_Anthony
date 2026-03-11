| ARIMA(2,2,3) | 18,389,114 | ₦3,907 | 3.92% | Baseline |
| SARIMAX(1,2,1)(0,1,1,12) + exog | — | — | 1.16% | ✅ Primary — Food CPI |

> All primary models exceed the project target of MAPE < 5%

### GARCH Results

| Target | α (ARCH) | β (GARCH) | α + β | ν (d.f.) |
|---|---|---|---|---|
| Basket Cost | 0.8319 | 0.1681 | 1.0000 | 3.91 |
| Food CPI | — | — | ≈ 1.0000 | 4.90 |

> IGARCH persistence confirmed for both series — volatility shocks
> do not decay, consistent with a permanent structural break

### 6-Month Forward Forecasts

| Month | Basket Cost (₦) | Food CPI |
|---|---|---|
| November 2025 | ~94,500 | ~1,210 |
| December 2025 | ~93,200 | ~1,195 |
| January 2026 | ~92,800 | ~1,180 |
| February 2026 | ~92,100 | ~1,165 |
| March 2026 | ~91,600 | ~1,150 |
| April 2026 | ~91,200 | ~1,140 |

> Forecasts assume fuel price and exchange rate held at
> 3-month rolling average of last observed values.
> Wide confidence intervals apply — see notebook for full uncertainty bands.

---

## 💡 Key Findings

1. The June 2023 shock was the dominant event of the decade
Basket cost nearly tripled within 18 months of the subsidy removal.
Food CPI almost doubled. No prior event, not the 2016 recession,
the 2019 border closure, or COVID-19, produced a comparable
structural level shift.

2. Fuel price is the most important macro driver post-shock
The rolling 12-month correlation between fuel price and basket cost
rose from r = 0.27 (pre-shock) to r = 0.72 (post-shock) and remained
sustained, confirming fuel became a continuous structural driver
of food costs after subsidy removal.

3. Local staples were hit hardest, not imports
Yam (+473%), Potatoes (+349%), Local Rice (+341%), Brown Beans (+333%),
and Maize (+316%) were the top 5 most affected commodities — all
locally produced. Fuel cost transmission through transport and logistics
proved as destructive as import price channels.

4. Exogenous variables are essential — not optional
SARIMAX without exog variables forecast the wrong direction entirely
in the test period — projecting continued CPI growth while actual
Food CPI was declining. Including fuel price, exchange rate, and
shock dummies corrected both direction and magnitude.

5. Forecast uncertainty is permanent and asymmetric
IGARCH persistence (α + β = 1.0) and fat-tailed residuals (ν < 5)
in both targets confirm that post-shock Nigeria operates in a
fundamentally more uncertain food price environment. Normal-distribution
confidence intervals would systematically understate downside risk.


## Dependenciespandas
numpy
matplotlib
seaborn
statsmodels
arch
scipy
sklearn

---

## Important Notes

- Test set: Basket cost data for Nov 2025 – Jan 2026 was identified
  as forward-filled. All MAPE/MAE evaluations use the confirmed
  Aug – Oct 2025 test period only.
- Forecast assumptions: Forward projections assume constant macro
  conditions based on a 3-month rolling average. Any significant policy
  change would shift results materially.
- GARCH limitation: With ~30 post-shock observations, GARCH
  parameter estimates carry wide confidence intervals. Results are
  directionally valid but should be treated as indicative.
- Causality: High correlations throughout this project reflect
  co-movement, not established causal relationships. Models are
  optimised for forecasting accuracy, not causal identification.

---

## About This Project

This repository is a personal submission for the **TS Academy Group 7 Track 3
Capstone Project** — a group forecasting project on Nigerian food prices.

The full group project was developed collaboratively across four
sub-teams covering EDA, stationarity testing, basket price modelling,
and Food CPI forecasting. This personal repository contains the complete
end-to-end analysis independently reproduced and documented.

Programme: TS Academy — Time Series Analysis Track 3
Topic: Nigerian Food Basket Price & Food CPI Forecasting
Tools: Python, statsmodels, arch, pandas, matplotlib

---

## License

This project is submitted for educational purposes as part of the
TS Academy programme.

Dataset sourced from the National Bureau of
Statistics (NBS) Nigeria. All analysis and code are original work.
