# Group 2 Calibrated Pilot Rerun

## Completion and fairness

- Completed runs: **96/96**
- Completion check: **PASS**
- Common evaluation-budget compliance: **PASS**

## Algorithm summary

| algorithm              |   runs |   mean_best_score |   median_best_score |   sd_best_score |   mean_paired_rank |   median_runtime_s |   mean_runtime_s |
|:-----------------------|-------:|------------------:|--------------------:|----------------:|-------------------:|-------------------:|-----------------:|
| BDA-EHHO-VC-Calibrated |     24 |           5.05663 |             5.04251 |        0.481319 |            2.33333 |            61.4453 |          61.0407 |
| BEHHO-VC-Calibrated    |     24 |           5.0567  |             5.04298 |        0.481317 |            2.5     |            58.3077 |          56.2846 |
| HHO-VC                 |     24 |           5.05682 |             5.04397 |        0.481413 |            2.5625  |            57.4829 |          55.1337 |
| EHHO-VC                |     24 |           5.05683 |             5.04402 |        0.481372 |            2.60417 |            56.1083 |          56.0934 |

## Mechanism diagnostics

| algorithm              |   runs |   mean_injections |   pct_runs_with_injection |   mean_diversity |   mean_final_diversity |   mean_bda_fraction |   mean_ehho_fraction |
|:-----------------------|-------:|------------------:|--------------------------:|-----------------:|-----------------------:|--------------------:|---------------------:|
| BEHHO-VC-Calibrated    |     24 |              2.75 |                      62.5 |         0.821819 |               0.812726 |          nan        |           nan        |
| BDA-EHHO-VC-Calibrated |     24 |            nan    |                     nan   |       nan        |             nan        |            0.491042 |             0.508958 |

## Paired score spread

- Median within-block score spread: **0.00072155**
- Maximum within-block score spread: **0.00248293**

## Mechanism health

- Calibrated BEHHO injection-active runs: **62.50%**
- Calibrated hybrid mean BDA fraction: **0.491**
- Calibrated hybrid mean EHHO fraction: **0.509**
- Mechanism health check: **PASS**

## Decision rule

Proceed to the 24-image screen only if completion, budget compliance, and mechanism health pass. Algorithm ranking here is descriptive only.