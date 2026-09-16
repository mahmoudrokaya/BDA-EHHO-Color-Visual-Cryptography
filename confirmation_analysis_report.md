# Group 2 — 100-Image Validation Confirmation

- Completed runs: **2000/2000**
- Completion: **PASS**
- Budget compliance: **PASS**
- Frozen configuration: **N=30, B=600**
- Primary inferential unit: **100 paired images**; each algorithm is summarized by its median across five runs/image.

## Run-level descriptive summary

| algorithm              |   runs |   mean_best_score |   median_best_score |   sd_best_score |   median_runtime_s |   mean_runtime_s |   median_cache_hit_rate |
|:-----------------------|-------:|------------------:|--------------------:|----------------:|-------------------:|-----------------:|------------------------:|
| BDA-EHHO-VC-Calibrated |    500 |           4.99038 |             4.99471 |        0.425005 |            27.5475 |          25.4189 |                0.724903 |
| BEHHO-VC-Calibrated    |    500 |           4.99036 |             4.99465 |        0.425005 |            27.8611 |          26.8154 |                0.707432 |
| EHHO-VC                |    500 |           4.99034 |             4.99501 |        0.425007 |            15.7532 |          16.2665 |                0.824444 |
| HHO-VC                 |    500 |           4.99039 |             4.99513 |        0.424976 |            15.3623 |          15.2865 |                0.831111 |

## Image-level average ranks

| algorithm              |   mean_image_rank |
|:-----------------------|------------------:|
| EHHO-VC                |             2.27  |
| HHO-VC                 |             2.51  |
| BDA-EHHO-VC-Calibrated |             2.535 |
| BEHHO-VC-Calibrated    |             2.685 |

## Friedman omnibus test

Statistic: **5.499482**
p-value: **0.13867**

## Pairwise Wilcoxon + Holm

| algorithm_A         | algorithm_B            |   median_difference_A_minus_B |   bootstrap95_lo |   bootstrap95_hi |   wilcoxon_statistic |     p_raw |   rank_biserial_A_minus_B |   wins_A |   wins_B |   ties |   p_holm | significant_holm_0_05   |
|:--------------------|:-----------------------|------------------------------:|-----------------:|-----------------:|---------------------:|----------:|--------------------------:|---------:|---------:|-------:|---------:|:------------------------|
| HHO-VC              | EHHO-VC                |                   0           |      0           |      7.12138e-06 |                 1852 | 0.0767648 |                0.279298   |       33 |       42 |     25 | 0.383824 | False                   |
| HHO-VC              | BEHHO-VC-Calibrated    |                  -4.8587e-06  |     -0.000143738 |      0.000110358 |                 2509 | 0.960237  |               -0.00515358 |       50 |       48 |      2 | 1        | False                   |
| HHO-VC              | BDA-EHHO-VC-Calibrated |                  -2.62124e-05 |     -0.000162957 |      8.89495e-05 |                 2454 | 0.808468  |               -0.0274747  |       52 |       47 |      1 | 1        | False                   |
| EHHO-VC             | BEHHO-VC-Calibrated    |                  -9.2923e-05  |     -0.00015958  |     -1.31406e-05 |                 1846 | 0.0198335 |               -0.268604   |       62 |       36 |      2 | 0.119001 | False                   |
| EHHO-VC             | BDA-EHHO-VC-Calibrated |                  -4.6103e-05  |     -0.000187637 |      4.33579e-05 |                 2105 | 0.149195  |               -0.167273   |       55 |       44 |      1 | 0.596781 | False                   |
| BEHHO-VC-Calibrated | BDA-EHHO-VC-Calibrated |                   5.59376e-05 |     -8.71866e-05 |      0.00018088  |                 2359 | 0.569327  |                0.0650505  |       45 |       54 |      1 | 1        | False                   |

## Mechanism confirmation

| algorithm              |   runs |   mean_injections |   pct_runs_with_injection |   mean_diversity |   mean_final_diversity |   mean_bda_fraction |   mean_ehho_fraction |
|:-----------------------|-------:|------------------:|--------------------------:|-----------------:|-----------------------:|--------------------:|---------------------:|
| BEHHO-VC-Calibrated    |    500 |              3.05 |                      47.4 |         0.828023 |               0.800512 |           nan       |            nan       |
| BDA-EHHO-VC-Calibrated |    500 |            nan    |                     nan   |       nan        |             nan        |             0.48954 |              0.51046 |

Mechanism health: **PASS**

No further parameter tuning should be performed after this confirmation.