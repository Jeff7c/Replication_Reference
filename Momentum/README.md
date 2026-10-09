# Momentum: Jegadeesh and Titman (1993)

## Possible differences from the original paper

The original Tables I–III use 1965–1989 data; this replication evaluates 2002–2025 using modern CRSP data. Differences may also come from CRSP data revisions, delisting returns, the seven-calendar-day interpretation of a one-week skip, and the stated rules for missing returns and beta estimation. The goal is to reproduce the paper's analyses with current data, not its historical estimates.

The daily data begin in 2000. The longest 12/12 strategy needs prior returns and overlapping holding portfolios, so 2000–2001 is used for formation and the common evaluation period starts in 2002.

## Files

| File | Contents |
| --- | --- |
| [Jegadeesh_Titman_1993_replication.ipynb](Jegadeesh_Titman_1993_replication.ipynb) | Code for Tables I–III; reads the three supplied files in `data/` |
| [output/table1.csv](output/table1.csv) | 32 J/K strategies, with and without a one-week skip |
| [output/table2.csv](output/table2.csv) | Beta and average market capitalization of the 6/6 deciles |
| [output/table3a.csv](output/table3a.csv) | 6/6 returns within size and prior-year-beta groups |
| [output/table3b.csv](output/table3b.csv) | Market-model abnormal returns for those groups |

## Main results

**Table I: Winner minus loser monthly return** (percent). Panel A forms immediately; Panel B skips one week.

| J (months) | A: K=3 | A: K=6 | A: K=9 | A: K=12 | B: K=3 | B: K=6 | B: K=9 | B: K=12 |
| ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| 3 | 0.42% | 0.51% | 0.54% | 0.47% | 0.57% | 0.62% | 0.60% | 0.53% |
| 6 | 0.74% | 0.90% | 0.79% | 0.61% | 0.90% | 0.97% | 0.93% | 0.74% |
| 9 | 0.88% | 0.93% | 0.77% | 0.59% | 1.14% | 0.94% | 0.78% | 0.59% |
| 12 | 0.81% | 0.69% | 0.64% | 0.49% | 0.93% | 0.74% | 0.62% | 0.47% |

All 32 spreads are positive. For the immediate 6/6 strategy, the mean is **0.90%** (t = 2.34); with a one-week skip it is **0.97%** (t = 2.59).

**Table II: Immediate 6/6 portfolio characteristics.** Market capitalization is in USD millions.

| Portfolio | Market beta | Average market capitalization |
| --- | ---: | ---: |
| P1 | 1.725 | 1,781 |
| P10 | 1.205 | 5,551 |
| P10-P1 | -0.520 | — |

**Table III: Immediate 6/6 winner minus loser results.** Values are monthly percent; t-statistics are in parentheses. S1–S3 sort from small to large firms; B1–B3 sort from low to high prior-year beta.

| Group | Panel A: raw return | Panel B: market-model alpha |
| --- | ---: | ---: |
| All | 0.90% (2.34) | 1.26% (3.44) |
| S1 | 1.50% (3.09) | 1.90% (4.00) |
| S2 | 0.70% (1.70) | 1.13% (2.94) |
| S3 | 0.37% (1.14) | 0.67% (2.13) |
| B1 | 0.58% (1.77) | 0.82% (2.54) |
| B2 | 0.47% (1.31) | 0.83% (2.46) |
| B3 | 1.89% (3.86) | 2.18% (4.59) |

For the full sample, the joint equal-mean test in Panel A has p = 0.2050; the joint-alpha test in Panel B has p = 0.0082. The CSV files contain every decile and test statistic.

Open the notebook from this folder or the project root and run its cells in order. `cache/` holds intermediate calculations and can be rebuilt from `data/`; it is not a result. Returns in the CSV files are shown as percentages, with t-statistics in parentheses where applicable. Source: [Jegadeesh and Titman (1993)](https://doi.org/10.1111/j.1540-6261.1993.tb04702.x).
