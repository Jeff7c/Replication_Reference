# Index Effect Reference, 2000–2020

## Possible errors and coverage limits

This is a modern-sample adaptation of Shleifer (1986), Tables I–II, not a reproduction of the original historical estimates. Differences may arise from announcement timing, estimation windows, missing returns, data revisions, and sample exclusions. Announcements are assumed to occur after market close. The 2000–2009 / 2010–2020 split is descriptive, not the original regime split.

The market model uses estimation windows [-250, -21] and [+61, +250], with at least 120 valid trading days per side. These are implementation choices. Reported t-statistics now use the Ruback first-order serial-correlation adjustment cited by Shleifer. The variance-estimation endpoints and finite-sample denominators remain explicit implementation choices because Shleifer does not fully specify them. Original news-based exclusions are not replicated.

## Replication scope

The assignment targets **Shleifer’s Tables I and II**, both of which concern additions. The supplied Greenwood–Sammon directory contains additions and deletions for 2000–2020; deletions are not required in these two tables. Greenwood–Sammon supplies the modern events, not the table definitions or precomputed returns.

The event windows and market-model cumulative prediction errors match the requested analyses. **The Ruback variance formula is now used; historical sample partitions and incompletely documented calibration details remain adaptation choices.** **The 2000–2009 / 2010–2020 split was chosen by this replication for descriptive comparison; it is not specified by Shleifer and does not represent a verified notification-regime change in 2010.**

- **Original Table I:** 1966–1975 versus September 1976–1983, separating the periods before and after S&P introduced its early-warning notification service. The change affected how promptly index changes were communicated and how precisely announcement dates could be identified.
- **Original Table II:** the full September 1976–1983 sample, with early September 1976–1980 and later 1981–1983 subsamples, examining persistence within the post-service period.

This replication instead uses 2000–2009 and 2010–2020 in both tables, with the full 2000–2020 sample also shown in Table II. It therefore does not reproduce the original distinction between regime comparison (Table I) and subperiod comparison within the later regime (Table II). These results are therefore a modern-sample reference with disclosed methodological changes, not an exact original-method answer key.

## Files

| File | Contents and units |
|---|---|
| [table1.csv](table1.csv) | Abnormal returns before, on, and after the announcement reaction day; early and later samples. |
| [table2.csv](table2.csv) | Cumulative abnormal returns from the reaction day through 5, 10, 20, and 60 trading days; full and subsample results. |

Return cells show **percent (Ruback-adjusted t-statistic)**. `N events` counts additions. No clustered standard errors are used. These are the complete result tables for student comparison.

## Sample and calculation

The sample contains **427 S&P 500 additions**: 230 in 2000–2009 and 197 in 2010–2020. Of 515 unique candidate events, 86 lack sufficient pre-event estimation data and 2 lack sufficient post-event estimation data. All table rows use the same complete events within each sample.

Greenwood–Sammon’s event directory supplies identifiers and announcement dates. Stock returns and the CRSP value-weighted market return are read from the supplied Parquet file. Abnormal returns are calculated independently as market-model residuals, summed over trading days, then averaged equally across events. Pre-event estimates apply through AD; post-event estimates apply after AD.

**AD** is the first trading day strictly after the recorded announcement date. Window endpoints are included: AD through AD+60 contains 61 daily returns.

The reported statistic is

$$t=\frac{CAPE[a,b]}{\sqrt{Q\hat\gamma_0+2(Q-1)\hat\gamma_1}},\qquad Q=b-a+1.$$

Here $\hat\gamma_0$ is the time-series variance of average prediction errors (APE), and $\hat\gamma_1$ is their lag-one covariance, estimated outside [-20, +60] using the existing pre/post estimation intervals. Only relative days observed for every event in the relevant sample enter APE; adjacent pairs never bridge missing days or the event window. There is no additional division by the number of events. The full and early samples use 268 calibration days (266 adjacent pairs); the later sample uses 420 (418). Sample variance and pairwise covariance use denominators M−1 and P−1, respectively. These calibration details are disclosed rather than attributed to the authors’ original code.

## Table I — Abnormal Returns Around Inclusion

| Event window | Early 2000–2009 | Later 2010–2020 |
|---|---:|---:|
| AD−20 through AD−1 | -0.786% (-0.94) | 0.004% (0.01) |
| AD | 2.947% (16.78) | 0.959% (7.42) |
| AD+1 through AD+10 | -0.114% (-0.19) | -0.694% (-1.73) |
| AD+11 through AD+20 | -0.968% (-1.64) | 0.221% (0.55) |
| N events | 230 | 197 |

## Table II — Persistence of Abnormal Returns

| Event window | Full 2000–2020 | Early 2000–2009 | Later 2010–2020 |
|---|---:|---:|---:|
| AD | 2.030% (18.00) | 2.947% (16.78) | 0.959% (7.42) |
| AD through AD+5 | 1.866% (6.68) | 2.956% (6.50) | 0.593% (1.91) |
| AD through AD+10 | 1.648% (4.35) | 2.833% (4.58) | 0.265% (0.63) |
| AD through AD+20 | 1.229% (2.35) | 1.865% (2.18) | 0.486% (0.84) |
| AD through AD+60 | 0.556% (0.62) | 0.652% (0.45) | 0.445% (0.45) |
| N events | 427 | 230 | 197 |

The announcement effect is positive and smaller in the later sample. The full-sample 60-day estimate has a t-statistic of 0.62, giving little evidence against zero; this does not establish complete reversal. The tables do not formally test the difference between periods.

Sources: [Shleifer (1986)](https://doi.org/10.1111/j.1540-6261.1986.tb04518.x); [Greenwood and Sammon (2025)](https://doi.org/10.1111/jofi.13410).

Variance formula cross-check: [Cleveland Fed Economic Review, 1985 Q3, event-study appendix A1–A2](https://fraser.stlouisfed.org/files/docs/publications/frbclevreview/rev_frbclev_1985q3.pdf), explicitly following Ruback (1982).
