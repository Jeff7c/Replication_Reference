# Fama–French Three-Factor Reference, 2000–2025

## Possible errors and coverage limits

Differences from the official benchmark may reflect security eligibility timing, Compustat history screening, share-class and CCM link handling, missing-return treatment, data revisions, and rounding. Their individual contributions have not been established. This implementation does not impose a strict two-year Compustat history requirement.

**MKT−RF covers January 2000–December 2025 (312 months). SMB and HML cover July 2001–December 2025 (294 months).** Their first 18 months are blank because formation-period data are missing. Blank values are not zero returns.

## Files

| File | Contents and units |
|---|---|
| [monthly_factors.csv](monthly_factors.csv) | Monthly constructed factors, official factors, and RF. Decimal returns: **0.01 = 1%**. |
| [summary_statistics.csv](summary_statistics.csv) | Monthly mean, sample standard deviation, minimum, and maximum, in **percent**. |
| [benchmark_comparison.csv](benchmark_comparison.csv) | Comparison periods, correlations, mean errors, and RMSE. Errors are in **percentage points**. |
| [cumulative_returns.png](cumulative_returns.png) | Cumulative returns for each factor, compared with the official benchmark. |

`constructed` denotes this replication; `benchmark` denotes the Kenneth French series. The official file uses the **2026-07 CRSP database release**. Comparisons use the same available months for each pair of series.

## Main results

MKT−RF is the market excess return, SMB is small minus big, and HML is high minus low book-to-market. SMB and HML are constructed from six size/B/M portfolios; the market factor is calculated separately.

| Factor | Months | Correlation | Mean error (pp/month) | RMSE (pp/month) |
|---|---:|---:|---:|---:|
| MKT−RF | 312 | 0.99998 | −0.00372 | 0.02644 |
| SMB | 294 | 0.99671 | +0.00490 | 0.21387 |
| HML | 294 | 0.99603 | −0.00194 | 0.27810 |

Error means constructed minus benchmark. Lower RMSE indicates closer monthly agreement. All three factors track the benchmark closely, but the results are not identical. Full descriptive statistics are in `summary_statistics.csv`.

## Cumulative returns

Each panel compounds monthly decimal returns as:

$$C_T=\prod_{t=1}^{T}(1+r_t)-1.$$

The chart displays this value in percent. Blue is constructed; dashed orange is the benchmark. Each pair starts at its first common available month.

![Cumulative factor returns](cumulative_returns.png)

These are factor-return illustrations, not fund NAVs. They are assignment diagnostics, not a reproduction of a specific figure in the 1993 paper. The implementation follows modern benchmark conventions, including the updated book-equity definition.

Source: [Kenneth French Data Library](https://mba.tuck.dartmouth.edu/pages/faculty/ken.french/data_library.html). 
