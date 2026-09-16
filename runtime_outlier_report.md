# Runtime Outlier Audit — pilot

- Runs audited: **384**
- Runtime outliers flagged: **1**

## Configuration summary

| algorithm   |   population_size |   evaluation_budget |   runs |   median_runtime_s |   mean_runtime_s |   max_runtime_s |   outlier_count |
|:------------|------------------:|--------------------:|-------:|-------------------:|-----------------:|----------------:|----------------:|
| BDA-EHHO-VC |                10 |                 200 |     24 |            24.788  |          26.4304 |         43.606  |               0 |
| BDA-EHHO-VC |                10 |                 400 |     24 |            50.6724 |          53.1334 |         79.7431 |               0 |
| BDA-EHHO-VC |                20 |                 200 |     24 |            30.9136 |          27.5016 |         39.0146 |               0 |
| BDA-EHHO-VC |                20 |                 400 |     24 |            48.32   |          50.5303 |         82.5309 |               0 |
| BEHHO-VC    |                10 |                 200 |     24 |            24.9089 |          25.5284 |         42.9409 |               0 |
| BEHHO-VC    |                10 |                 400 |     24 |            51.6243 |          50.479  |         83.2853 |               0 |
| BEHHO-VC    |                20 |                 200 |     24 |            28.3492 |          27.6439 |         40.4973 |               0 |
| BEHHO-VC    |                20 |                 400 |     24 |            49.51   |          52.2654 |         80.2466 |               0 |
| EHHO-VC     |                10 |                 200 |     24 |            26.1582 |          25.306  |         41.7265 |               0 |
| EHHO-VC     |                10 |                 400 |     24 |            49.4707 |          48.957  |         77.7082 |               0 |
| EHHO-VC     |                20 |                 200 |     24 |            25.7904 |          26.4667 |         41.9211 |               0 |
| EHHO-VC     |                20 |                 400 |     24 |            50.6764 |          52.5387 |         76.9352 |               0 |
| HHO-VC      |                10 |                 200 |     24 |            23.7495 |          25.4992 |         40.763  |               0 |
| HHO-VC      |                10 |                 400 |     24 |            50.8286 |         588.656  |      12982.8    |               1 |
| HHO-VC      |                20 |                 200 |     24 |            23.9604 |          25.9024 |         43.0474 |               0 |
| HHO-VC      |                20 |                 400 |     24 |            55.3829 |          53.4399 |         78.4028 |               0 |

## Flagged runs

| experiment_id   |   run_index | algorithm   |   population_size |   evaluation_budget |   runtime_s |   robust_z_runtime |
|:----------------|------------:|:------------|------------------:|--------------------:|------------:|-------------------:|
| IMG_0090        |           1 | HHO-VC      |                10 |                 400 |     12982.8 |            539.438 |

Outliers are retained in the raw data. Median runtime should be the primary descriptive runtime statistic unless a rerun confirms a genuine algorithmic cause.