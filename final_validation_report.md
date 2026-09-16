# Group 3 — Final Objective Validation

- Runs: **24/24**
- Completion: **PASS**
- Budget compliance: **PASS**
- Nonempty archives: **PASS**
- Nondominated archives: **PASS**
- Diversity health: **PASS**
- BDA/EHHO balance: **PASS**
- All four objectives active within every run: **PASS**

## Summary

|   runs |   mean_archive_size |   median_archive_size |   median_runtime_s |   mean_runtime_s |   mean_bda_fraction |   mean_ehho_fraction |   diversity_healthy_runs_pct |   f1_mean_span |   f2_mean_span |   f3_mean_span |   f4_mean_span |
|-------:|--------------------:|----------------------:|-------------------:|-----------------:|--------------------:|---------------------:|-----------------------------:|---------------:|---------------:|---------------:|---------------:|
|     24 |              85.875 |                   100 |            131.246 |          119.499 |            0.494079 |             0.505921 |                          100 |      0.0433551 |     0.00137031 |     0.00046266 |       0.765959 |

## Frozen objectives

1. f1: normalized reconstruction MSE.
2. f2: mean absolute secret-share Pearson correlation (S2).
3. f3: mean normalized clean-vs-damaged reconstruction MSE under 5%, 10%, and 20% central Share-1 block erasure (B1).
4. f4: mean RGB group count / 255.

## Decision

**GROUP3_OBJECTIVES_FROZEN_PASS**