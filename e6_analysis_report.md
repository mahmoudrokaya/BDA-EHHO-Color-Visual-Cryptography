# E6 — Computational Efficiency and Convergence Analysis

## Paired benchmark design

- 12 common BSDS500 validation images.
- 2 independent runs/image.
- Five frozen methods.
- Frozen N=30, B=600.
- Deterministically randomized execution order within image/run.
- Separate objective/cache instance per method.
- Image median is the inferential unit for runtime.

## Paired runtime summary

| algorithm              |   runs |   median_runtime_s |   mean_runtime_s |   sd_runtime_s |   median_seconds_per_100_evals |   median_evals_per_second |   median_iterations |   median_cache_hit_rate |
|:-----------------------|-------:|-------------------:|-----------------:|---------------:|-------------------------------:|--------------------------:|--------------------:|------------------------:|
| BDA-EHHO-VC-Calibrated |     24 |            27.0558 |          22.264  |        8.86546 |                        4.50931 |                  22.1773  |                  10 |              0.724626   |
| BEHHO-VC-Calibrated    |     24 |            25.0086 |          22.9972 |        8.70673 |                        4.1681  |                  23.9991  |                  20 |              0.698835   |
| EHHO-VC                |     24 |            11.3985 |          12.3354 |        5.81029 |                        1.89976 |                  52.639   |                  13 |              0.8525     |
| HHO-VC                 |     24 |            11.0127 |          11.5058 |        5.16187 |                        1.83546 |                  54.4827  |                  11 |              0.834444   |
| MO-BDA-EHHO-VC         |     24 |           118.46   |         103.293  |       45.7814  |                       19.7433  |                   5.06539 |                  20 |              0.00166667 |

## Runtime omnibus test

- Friedman statistic: **43.533333**
- p-value: **8.01966e-09**

## Runtime pairwise comparisons against MO

| algorithm_A            | algorithm_B    |   median_runtime_difference_A_minus_MO_s |   wilcoxon_statistic |       p_raw |   rank_biserial_A_minus_MO |   wins_faster_MO |   wins_faster_A |   ties |     p_holm | significant_holm_0_05   |
|:-----------------------|:---------------|-----------------------------------------:|---------------------:|------------:|---------------------------:|-----------------:|----------------:|-------:|-----------:|:------------------------|
| HHO-VC                 | MO-BDA-EHHO-VC |                                -110.672  |                    0 | 0.000488281 |                         -1 |                0 |              12 |      0 | 0.00195312 | True                    |
| EHHO-VC                | MO-BDA-EHHO-VC |                                -111.444  |                    0 | 0.000488281 |                         -1 |                0 |              12 |      0 | 0.00195312 | True                    |
| BEHHO-VC-Calibrated    | MO-BDA-EHHO-VC |                                 -96.5633 |                    0 | 0.000488281 |                         -1 |                0 |              12 |      0 | 0.00195312 | True                    |
| BDA-EHHO-VC-Calibrated | MO-BDA-EHHO-VC |                                 -95.7477 |                    0 | 0.000488281 |                         -1 |                0 |              12 |      0 | 0.00195312 | True                    |

## Scalar-method convergence

Fractions indicate the proportion of the native convergence trace required to achieve 90%, 95%, or 99% of terminal scalar improvement.

| algorithm              |   median_fraction_to_90 |   median_fraction_to_95 |   median_fraction_to_99 |   median_trace_points |
|:-----------------------|------------------------:|------------------------:|------------------------:|----------------------:|
| BDA-EHHO-VC-Calibrated |                0.8      |                0.8      |                0.8      |                    10 |
| BEHHO-VC-Calibrated    |                0.725    |                0.75     |                0.75     |                    20 |
| EHHO-VC                |                0.332418 |                0.370879 |                0.461538 |                    13 |
| HHO-VC                 |                0.409091 |                0.5      |                0.545455 |                    11 |

## MO convergence

MO convergence is described separately using archive growth and final fixed-reference hypervolume; it is not treated as numerically equivalent to scalar best-fitness convergence.

|   runs |   median_fraction_to_90pct_final_archive |   median_fraction_to_95pct_final_archive |   median_fraction_to_99pct_final_archive |   median_final_hypervolume |   median_archive_size |
|-------:|-----------------------------------------:|-----------------------------------------:|-----------------------------------------:|---------------------------:|----------------------:|
|     24 |                                    0.575 |                                    0.625 |                                    0.675 |                   0.667185 |                    90 |

## Large-stage operational timing context

| stage                        | algorithm              |   runs |   median_runtime_s |   mean_runtime_s | paired_for_inference   |
|:-----------------------------|:-----------------------|-------:|-------------------:|-----------------:|:-----------------------|
| Group2_100Image_Confirmation | BDA-EHHO-VC-Calibrated |    500 |            27.5475 |          25.4189 | False                  |
| Group2_100Image_Confirmation | BEHHO-VC-Calibrated    |    500 |            27.8611 |          26.8154 | False                  |
| Group2_100Image_Confirmation | EHHO-VC                |    500 |            15.7532 |          16.2665 | False                  |
| Group2_100Image_Confirmation | HHO-VC                 |    500 |            15.3623 |          15.2865 | False                  |
| E4_MO_100Image               | MO-BDA-EHHO-VC         |    500 |           113.449  |         111.092  | False                  |

## Interpretation discipline

A slower MO runtime is expected because each candidate is evaluated on four objectives and an external Pareto archive is maintained. E6 should therefore report the computational premium explicitly rather than hide it. The benefit/cost interpretation should be linked to the much stronger E4 Pareto-set quality.