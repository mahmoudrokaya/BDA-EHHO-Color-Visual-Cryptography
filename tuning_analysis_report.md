# Group 2 Validation/Tuning Analysis — pilot

## Completion and fairness

- Completed runs: **384**
- Overall budget compliance: **100.00%**

## Common configuration ranking

The ranking below is for screening only. It uses one common population/budget configuration across all algorithms. Lower fitness and lower runtime are preferred.

|   population_size |   evaluation_budget |   mean_best_score |   median_best_score |   mean_paired_rank |   median_runtime_s |   mean_runtime_s |   total_runs |   median_block_score_spread |   max_block_score_spread |   normalized_score_loss |   normalized_runtime_cost |   balanced_screening_index |
|------------------:|--------------------:|------------------:|--------------------:|-------------------:|-------------------:|-----------------:|-------------:|----------------------------:|-------------------------:|------------------------:|--------------------------:|---------------------------:|
|                20 |                 400 |           5.05679 |             5.043   |                2.5 |            49.51   |          52.1936 |           96 |                 0.000725072 |               0.00214024 |                0        |                  0.96682  |                   0.290046 |
|                10 |                 400 |           5.05689 |             5.04345 |                2.5 |            50.3551 |         185.306  |           96 |                 0.000728052 |               0.00264717 |                0.50285  |                  1        |                   0.651995 |
|                20 |                 200 |           5.05698 |             5.04301 |                2.5 |            25.9018 |          26.8787 |           96 |                 0.000795233 |               0.00237713 |                0.972479 |                  0.039906 |                   0.692707 |
|                10 |                 200 |           5.05699 |             5.04302 |                2.5 |            24.8854 |          25.691  |           96 |                 0.000917691 |               0.00256993 |                1        |                  0        |                   0.7      |

## Pareto shortlist

|   population_size |   evaluation_budget |   mean_best_score |   median_best_score |   mean_paired_rank |   median_runtime_s |   mean_runtime_s |   total_runs |   median_block_score_spread |   max_block_score_spread |   normalized_score_loss |   normalized_runtime_cost |   balanced_screening_index |
|------------------:|--------------------:|------------------:|--------------------:|-------------------:|-------------------:|-----------------:|-------------:|----------------------------:|-------------------------:|------------------------:|--------------------------:|---------------------------:|
|                20 |                 400 |           5.05679 |             5.043   |                2.5 |            49.51   |          52.1936 |           96 |                 0.000725072 |               0.00214024 |                0        |                  0.96682  |                   0.290046 |
|                20 |                 200 |           5.05698 |             5.04301 |                2.5 |            25.9018 |          26.8787 |           96 |                 0.000795233 |               0.00237713 |                0.972479 |                  0.039906 |                   0.692707 |
|                10 |                 200 |           5.05699 |             5.04302 |                2.5 |            24.8854 |          25.691  |           96 |                 0.000917691 |               0.00256993 |                1        |                  0        |                   0.7      |

## Preliminary screening recommendation

The lowest balanced screening index in this profile is obtained by **population=20, budget=400**.

This is not automatically the final configuration. The recommendation must also be checked against mechanism diagnostics, convergence stability, and the next validation stage. Final settings are frozen only after the confirm profile.

## Mechanism diagnostics

| algorithm   |   population_size |   evaluation_budget |   runs |   mean_injections |   pct_runs_with_injection |   mean_diversity |   mean_final_diversity |   mean_bda_proposals |   mean_ehho_proposals |   mean_bda_fraction |
|:------------|------------------:|--------------------:|-------:|------------------:|--------------------------:|-----------------:|-----------------------:|---------------------:|----------------------:|--------------------:|
| EHHO-VC     |                10 |                 200 |     24 |         0.333333  |                  12.5     |         0.338569 |               0.291539 |             nan      |             nan       |          nan        |
| EHHO-VC     |                10 |                 400 |     24 |         0.708333  |                  12.5     |         0.306713 |               0.309551 |             nan      |             nan       |          nan        |
| EHHO-VC     |                20 |                 200 |     24 |         0.208333  |                   8.33333 |         0.397788 |               0.333275 |             nan      |             nan       |          nan        |
| EHHO-VC     |                20 |                 400 |     24 |         0.625     |                  16.6667  |         0.349945 |               0.304735 |             nan      |             nan       |          nan        |
| BEHHO-VC    |                10 |                 200 |     24 |         0         |                   0       |         0.775816 |               0.731944 |             nan      |             nan       |          nan        |
| BEHHO-VC    |                10 |                 400 |     24 |         0.0416667 |                   4.16667 |         0.76545  |               0.774375 |             nan      |             nan       |          nan        |
| BEHHO-VC    |                20 |                 200 |     24 |         0         |                   0       |         0.83988  |               0.831163 |             nan      |             nan       |          nan        |
| BEHHO-VC    |                20 |                 400 |     24 |         0         |                   0       |         0.839245 |               0.826597 |             nan      |             nan       |          nan        |
| BDA-EHHO-VC |                10 |                 200 |     24 |       nan         |                 nan       |       nan        |             nan        |              92.25   |               7.75    |            0.9225   |
| BDA-EHHO-VC |                10 |                 400 |     24 |       nan         |                 nan       |       nan        |             nan        |             183.292  |              16.7083  |            0.916458 |
| BDA-EHHO-VC |                20 |                 200 |     24 |       nan         |                 nan       |       nan        |             nan        |              93.4167 |               6.58333 |            0.934167 |
| BDA-EHHO-VC |                20 |                 400 |     24 |       nan         |                 nan       |       nan        |             nan        |             183.708  |              16.2917  |            0.918542 |