# E4 — Multi-Objective Comparative Experiment

## Design

- 100 BSDS500 validation images.
- 5 runs per image.
- Frozen N=30, B=600.
- Four single-objective methods reused from Group 2; they were not rerun.
- MO-BDA–EHHO newly executed with the frozen four-objective formulation.
- All attained solutions re-evaluated under one common independent E4 evaluation realization per image/run.
- Primary inferential unit: image median across five runs.

## Set-level Pareto summary

| algorithm              |   runs |   median_hv |   mean_hv |   median_igd |   mean_igd |   median_epsilon |   mean_epsilon |   median_set_size |   mean_set_size |
|:-----------------------|-------:|------------:|----------:|-------------:|-----------:|-----------------:|---------------:|------------------:|----------------:|
| BDA-EHHO-VC-Calibrated |    500 |   0.086843  |  0.124638 |   0.696131   |  0.72702   |        0.792923  |      0.782736  |                 1 |           1     |
| BEHHO-VC-Calibrated    |    500 |   0.0899063 |  0.123434 |   0.73504    |  0.762556  |        0.816517  |      0.795549  |                 1 |           1     |
| EHHO-VC                |    500 |   0.0771896 |  0.118972 |   0.750159   |  0.778148  |        0.849937  |      0.820467  |                 1 |           1     |
| HHO-VC                 |    500 |   0.0699562 |  0.120093 |   0.757179   |  0.786969  |        0.85525   |      0.817181  |                 1 |           1     |
| MO-BDA-EHHO-VC         |    500 |   0.911157  |  0.907846 |   0.00718277 |  0.0142024 |        0.0481749 |      0.0703706 |                40 |          43.294 |

## Representative-solution summary

| algorithm              |   runs |   median_f1 |   median_f2 |   median_f3 |   median_f4 |
|:-----------------------|-------:|------------:|------------:|------------:|------------:|
| BDA-EHHO-VC-Calibrated |    500 |    0.440734 |  0.00196688 |   0.058239  |    0.310458 |
| BEHHO-VC-Calibrated    |    500 |    0.445796 |  0.001992   |   0.0582383 |    0.243791 |
| EHHO-VC                |    500 |    0.445732 |  0.00197505 |   0.0582308 |    0.224183 |
| HHO-VC                 |    500 |    0.445619 |  0.00198652 |   0.0582383 |    0.243791 |
| MO-BDA-EHHO-VC         |    500 |    0.428441 |  0.00161393 |   0.0581369 |    0.123529 |

## Omnibus tests

| metric                 |   friedman_statistic |   friedman_p |
|:-----------------------|---------------------:|-------------:|
| hypervolume            |             210.124  |  2.49893e-44 |
| igd                    |             219.948  |  1.92395e-46 |
| epsilon_additive       |             218.392  |  4.15867e-46 |
| eval_f1_reconstruction |             154.363  |  2.36388e-32 |
| eval_f2_security       |             160.965  |  9.07722e-34 |
| eval_f3_robustness     |             130.035  |  3.82669e-27 |
| eval_f4_complexity     |              85.6609 |  1.09834e-17 |

## Pairwise comparisons against MO-BDA–EHHO

| metric                 | algorithm_A            | algorithm_B    |   median_difference_A_minus_MO |   wilcoxon_statistic |       p_raw |   rank_biserial_A_minus_MO |   wins_MO |   wins_A |   ties |      p_holm | significant_holm_0_05   |
|:-----------------------|:-----------------------|:---------------|-------------------------------:|---------------------:|------------:|---------------------------:|----------:|---------:|-------:|------------:|:------------------------|
| hypervolume            | HHO-VC                 | MO-BDA-EHHO-VC |                   -0.813282    |                  0   | 3.89656e-18 |                  -1        |       100 |        0 |      0 | 1.55862e-17 | True                    |
| hypervolume            | EHHO-VC                | MO-BDA-EHHO-VC |                   -0.819099    |                  0   | 3.89656e-18 |                  -1        |       100 |        0 |      0 | 1.55862e-17 | True                    |
| hypervolume            | BEHHO-VC-Calibrated    | MO-BDA-EHHO-VC |                   -0.800149    |                  0   | 3.89656e-18 |                  -1        |       100 |        0 |      0 | 1.55862e-17 | True                    |
| hypervolume            | BDA-EHHO-VC-Calibrated | MO-BDA-EHHO-VC |                   -0.791324    |                  0   | 3.89656e-18 |                  -1        |       100 |        0 |      0 | 1.55862e-17 | True                    |
| igd                    | HHO-VC                 | MO-BDA-EHHO-VC |                    0.757005    |                  0   | 3.89656e-18 |                   1        |       100 |        0 |      0 | 1.55862e-17 | True                    |
| igd                    | EHHO-VC                | MO-BDA-EHHO-VC |                    0.743475    |                  0   | 3.89656e-18 |                   1        |       100 |        0 |      0 | 1.55862e-17 | True                    |
| igd                    | BEHHO-VC-Calibrated    | MO-BDA-EHHO-VC |                    0.747438    |                  0   | 3.89656e-18 |                   1        |       100 |        0 |      0 | 1.55862e-17 | True                    |
| igd                    | BDA-EHHO-VC-Calibrated | MO-BDA-EHHO-VC |                    0.684693    |                  0   | 3.89656e-18 |                   1        |       100 |        0 |      0 | 1.55862e-17 | True                    |
| epsilon_additive       | HHO-VC                 | MO-BDA-EHHO-VC |                    0.79832     |                  0   | 3.89634e-18 |                   1        |       100 |        0 |      0 | 1.55774e-17 | True                    |
| epsilon_additive       | EHHO-VC                | MO-BDA-EHHO-VC |                    0.799822    |                  0   | 3.89568e-18 |                   1        |       100 |        0 |      0 | 1.55774e-17 | True                    |
| epsilon_additive       | BEHHO-VC-Calibrated    | MO-BDA-EHHO-VC |                    0.7611      |                  0   | 3.89568e-18 |                   1        |       100 |        0 |      0 | 1.55774e-17 | True                    |
| epsilon_additive       | BDA-EHHO-VC-Calibrated | MO-BDA-EHHO-VC |                    0.731908    |                  0   | 3.89436e-18 |                   1        |       100 |        0 |      0 | 1.55774e-17 | True                    |
| eval_f1_reconstruction | HHO-VC                 | MO-BDA-EHHO-VC |                    0.0104199   |                 99   | 7.3431e-17  |                   0.960792 |        91 |        9 |      0 | 2.93724e-16 | True                    |
| eval_f1_reconstruction | EHHO-VC                | MO-BDA-EHHO-VC |                    0.0100244   |                133   | 1.96051e-16 |                   0.947327 |        90 |       10 |      0 | 4.41225e-16 | True                    |
| eval_f1_reconstruction | BEHHO-VC-Calibrated    | MO-BDA-EHHO-VC |                    0.0107984   |                123   | 1.47075e-16 |                   0.951287 |        92 |        8 |      0 | 4.41225e-16 | True                    |
| eval_f1_reconstruction | BDA-EHHO-VC-Calibrated | MO-BDA-EHHO-VC |                    0.00681094  |                296   | 1.80193e-14 |                   0.882772 |        89 |       11 |      0 | 1.80193e-14 | True                    |
| eval_f2_security       | HHO-VC                 | MO-BDA-EHHO-VC |                    0.000328927 |                147   | 2.92604e-16 |                   0.941782 |        94 |        6 |      0 | 8.77812e-16 | True                    |
| eval_f2_security       | EHHO-VC                | MO-BDA-EHHO-VC |                    0.000304721 |                229   | 2.9173e-15  |                   0.909307 |        93 |        7 |      0 | 2.9173e-15  | True                    |
| eval_f2_security       | BEHHO-VC-Calibrated    | MO-BDA-EHHO-VC |                    0.000325139 |                 88   | 5.32897e-17 |                   0.965149 |        97 |        3 |      0 | 2.13159e-16 | True                    |
| eval_f2_security       | BDA-EHHO-VC-Calibrated | MO-BDA-EHHO-VC |                    0.000312083 |                154   | 3.57161e-16 |                   0.93901  |        93 |        7 |      0 | 8.77812e-16 | True                    |
| eval_f3_robustness     | HHO-VC                 | MO-BDA-EHHO-VC |                    9.85889e-05 |                154   | 3.5709e-16  |                   0.93901  |        93 |        7 |      0 | 1.42836e-15 | True                    |
| eval_f3_robustness     | EHHO-VC                | MO-BDA-EHHO-VC |                    0.000100028 |                215   | 1.98042e-15 |                   0.914851 |        88 |       12 |      0 | 3.96083e-15 | True                    |
| eval_f3_robustness     | BEHHO-VC-Calibrated    | MO-BDA-EHHO-VC |                    9.10328e-05 |                183   | 8.10545e-16 |                   0.927525 |        90 |       10 |      0 | 2.43164e-15 | True                    |
| eval_f3_robustness     | BDA-EHHO-VC-Calibrated | MO-BDA-EHHO-VC |                    0.000102907 |                243   | 4.28597e-15 |                   0.903762 |        87 |       13 |      0 | 4.28597e-15 | True                    |
| eval_f4_complexity     | HHO-VC                 | MO-BDA-EHHO-VC |                    0.0777778   |               1044.5 | 3.60437e-07 |                   0.589697 |        70 |       29 |      1 | 7.20874e-07 | True                    |
| eval_f4_complexity     | EHHO-VC                | MO-BDA-EHHO-VC |                    0.0823529   |               1095.5 | 8.87356e-07 |                   0.566139 |        66 |       34 |      0 | 8.87356e-07 | True                    |
| eval_f4_complexity     | BEHHO-VC-Calibrated    | MO-BDA-EHHO-VC |                    0.118954    |                556   | 1.28701e-11 |                   0.779802 |        80 |       20 |      0 | 3.86103e-11 | True                    |
| eval_f4_complexity     | BDA-EHHO-VC-Calibrated | MO-BDA-EHHO-VC |                    0.180392    |                 97   | 6.9273e-17  |                   0.961584 |        92 |        8 |      0 | 2.77092e-16 | True                    |

## Interpretation

The principal E4 evidence is set-level Pareto quality (hypervolume, IGD, additive epsilon). The representative compromise analysis is secondary.