# E5 — Robustness and Security Experiments

## Design

- 100 BSDS500 validation images.
- 5 runs per image.
- Five frozen methods; no optimizer rerun.
- E4 representative solutions reused.
- Independent common E5 share-generation realization per image/run.
- Identical perturbation masks across methods within image/run.
- Primary inferential unit: image median across five runs.

## Security summary (lower is better)

| algorithm              |   sec_abs_corr |     sec_nmi |   sec_hist_overlap |   sec_similarity_nmse |
|:-----------------------|---------------:|------------:|-------------------:|----------------------:|
| BDA-EHHO-VC-Calibrated |     0.0019538  | 6.74514e-05 |          0.0201046 |              0.68335  |
| BEHHO-VC-Calibrated    |     0.00197766 | 6.71089e-05 |          0.0201046 |              0.683366 |
| EHHO-VC                |     0.00194662 | 6.66844e-05 |          0.0201046 |              0.683454 |
| HHO-VC                 |     0.00199518 | 6.66228e-05 |          0.0201046 |              0.683454 |
| MO-BDA-EHHO-VC         |     0.00197552 | 6.76156e-05 |          0.0201046 |              0.683327 |

## Primary robustness summary (lower is better)

| algorithm              |   rob_seen_central_delta_nmse |   rob_unseen_delta_nmse |   rob_allfamilies_delta_nmse |
|:-----------------------|------------------------------:|------------------------:|-----------------------------:|
| BDA-EHHO-VC-Calibrated |                     0.0811682 |                0.101504 |                    0.0974283 |
| BEHHO-VC-Calibrated    |                     0.0811643 |                0.101507 |                    0.0974347 |
| EHHO-VC                |                     0.0811678 |                0.1015   |                    0.0974302 |
| HHO-VC                 |                     0.0811674 |                0.101499 |                    0.09743   |
| MO-BDA-EHHO-VC         |                     0.0811794 |                0.101503 |                    0.0974369 |

## Perturbation-family robustness summary

| algorithm              | family        |   median_delta_nmse |   median_secret_nmse |   median_secret_psnr_db |
|:-----------------------|:--------------|--------------------:|---------------------:|------------------------:|
| BDA-EHHO-VC-Calibrated | bit_flip      |           0.162489  |             0.402488 |                 3.96046 |
| BDA-EHHO-VC-Calibrated | central_block |           0.0811682 |             0.420533 |                 3.76353 |
| BDA-EHHO-VC-Calibrated | crop_loss     |           0.0811077 |             0.421553 |                 3.75454 |
| BDA-EHHO-VC-Calibrated | pixel_dropout |           0.0812415 |             0.420737 |                 3.7616  |
| BDA-EHHO-VC-Calibrated | random_block  |           0.0811669 |             0.422388 |                 3.74425 |
| BEHHO-VC-Calibrated    | bit_flip      |           0.162489  |             0.403352 |                 3.94944 |
| BEHHO-VC-Calibrated    | central_block |           0.0811643 |             0.423317 |                 3.73562 |
| BEHHO-VC-Calibrated    | crop_loss     |           0.0811069 |             0.426053 |                 3.70744 |
| BEHHO-VC-Calibrated    | pixel_dropout |           0.0812522 |             0.424337 |                 3.72429 |
| BEHHO-VC-Calibrated    | random_block  |           0.0811658 |             0.425045 |                 3.71836 |
| EHHO-VC                | bit_flip      |           0.162489  |             0.403505 |                 3.9513  |
| EHHO-VC                | central_block |           0.0811678 |             0.423378 |                 3.73522 |
| EHHO-VC                | crop_loss     |           0.081107  |             0.425499 |                 3.71323 |
| EHHO-VC                | pixel_dropout |           0.0812519 |             0.424739 |                 3.72029 |
| EHHO-VC                | random_block  |           0.0811637 |             0.424829 |                 3.72009 |
| HHO-VC                 | bit_flip      |           0.162489  |             0.405072 |                 3.93383 |
| HHO-VC                 | central_block |           0.0811674 |             0.424959 |                 3.71715 |
| HHO-VC                 | crop_loss     |           0.0811086 |             0.425074 |                 3.71758 |
| HHO-VC                 | pixel_dropout |           0.0812534 |             0.425144 |                 3.71642 |
| HHO-VC                 | random_block  |           0.0811631 |             0.42631  |                 3.70389 |
| MO-BDA-EHHO-VC         | bit_flip      |           0.162489  |             0.393427 |                 4.058   |
| MO-BDA-EHHO-VC         | central_block |           0.0811794 |             0.409884 |                 3.87492 |
| MO-BDA-EHHO-VC         | crop_loss     |           0.0811029 |             0.411155 |                 3.86144 |
| MO-BDA-EHHO-VC         | pixel_dropout |           0.0812524 |             0.41071  |                 3.86596 |
| MO-BDA-EHHO-VC         | random_block  |           0.0811642 |             0.409491 |                 3.87861 |

## Omnibus tests

| metric                      |   friedman_statistic |   friedman_p |
|:----------------------------|---------------------:|-------------:|
| sec_abs_corr                |              3.16566 |     0.530496 |
| sec_nmi                     |              2.43725 |     0.655907 |
| sec_hist_overlap            |            nan       |   nan        |
| sec_similarity_nmse         |              1.11269 |     0.892254 |
| rob_seen_central_delta_nmse |              6.0426  |     0.19599  |
| rob_unseen_delta_nmse       |              5.44153 |     0.244917 |
| rob_allfamilies_delta_nmse  |              5.66381 |     0.225702 |

## Pairwise comparisons against MO-BDA–EHHO

| metric                      | algorithm_A            | algorithm_B    |   median_difference_A_minus_MO |   wilcoxon_statistic |       p_raw |   rank_biserial_A_minus_MO |   wins_MO |   wins_A |   ties |    p_holm | significant_holm_0_05   |
|:----------------------------|:-----------------------|:---------------|-------------------------------:|---------------------:|------------:|---------------------------:|----------:|---------:|-------:|----------:|:------------------------|
| sec_abs_corr                | HHO-VC                 | MO-BDA-EHHO-VC |                   -1.94881e-05 |               2472   |   0.855401  |                  0.0209901 |        47 |       53 |      0 | 1         | False                   |
| sec_abs_corr                | EHHO-VC                | MO-BDA-EHHO-VC |                    3.15641e-06 |               2414   |   0.702718  |                 -0.0439604 |        51 |       49 |      0 | 1         | False                   |
| sec_abs_corr                | BEHHO-VC-Calibrated    | MO-BDA-EHHO-VC |                   -2.21011e-05 |               2445   |   0.783266  |                 -0.0316832 |        50 |       50 |      0 | 1         | False                   |
| sec_abs_corr                | BDA-EHHO-VC-Calibrated | MO-BDA-EHHO-VC |                   -2.98486e-05 |               2293   |   0.42505   |                 -0.0918812 |        47 |       53 |      0 | 1         | False                   |
| sec_nmi                     | HHO-VC                 | MO-BDA-EHHO-VC |                   -7.59801e-08 |               2357   |   0.563508  |                 -0.0665347 |        48 |       52 |      0 | 1         | False                   |
| sec_nmi                     | EHHO-VC                | MO-BDA-EHHO-VC |                   -1.97782e-08 |               2391   |   0.644988  |                 -0.0530693 |        49 |       51 |      0 | 1         | False                   |
| sec_nmi                     | BEHHO-VC-Calibrated    | MO-BDA-EHHO-VC |                   -3.48592e-08 |               2485   |   0.89061   |                  0.0158416 |        50 |       50 |      0 | 1         | False                   |
| sec_nmi                     | BDA-EHHO-VC-Calibrated | MO-BDA-EHHO-VC |                   -1.3043e-08  |               2491   |   0.906937  |                 -0.0134653 |        49 |       51 |      0 | 1         | False                   |
| sec_hist_overlap            | HHO-VC                 | MO-BDA-EHHO-VC |                    0           |                  0   | nan         |                  0         |         0 |        0 |    100 | 0         | True                    |
| sec_hist_overlap            | EHHO-VC                | MO-BDA-EHHO-VC |                    0           |                  0   | nan         |                  0         |         0 |        0 |    100 | 0         | True                    |
| sec_hist_overlap            | BEHHO-VC-Calibrated    | MO-BDA-EHHO-VC |                    0           |                  0   | nan         |                  0         |         0 |        0 |    100 | 0         | True                    |
| sec_hist_overlap            | BDA-EHHO-VC-Calibrated | MO-BDA-EHHO-VC |                    0           |                  0   | nan         |                  0         |         0 |        0 |    100 | 0         | True                    |
| sec_similarity_nmse         | HHO-VC                 | MO-BDA-EHHO-VC |                   -1.61069e-06 |               2221   |   0.295907  |                  0.120396  |        49 |       51 |      0 | 1         | False                   |
| sec_similarity_nmse         | EHHO-VC                | MO-BDA-EHHO-VC |                   -3.3886e-06  |               2292   |   0.423057  |                  0.0922772 |        48 |       52 |      0 | 1         | False                   |
| sec_similarity_nmse         | BEHHO-VC-Calibrated    | MO-BDA-EHHO-VC |                    7.75715e-06 |               2386   |   0.632702  |                  0.0550495 |        51 |       49 |      0 | 1         | False                   |
| sec_similarity_nmse         | BDA-EHHO-VC-Calibrated | MO-BDA-EHHO-VC |                    2.87427e-06 |               2240   |   0.327124  |                  0.112871  |        52 |       48 |      0 | 1         | False                   |
| rob_seen_central_delta_nmse | HHO-VC                 | MO-BDA-EHHO-VC |                   -5.53213e-06 |               2290.5 |   0.420077  |                 -0.0928713 |        47 |       53 |      0 | 1         | False                   |
| rob_seen_central_delta_nmse | EHHO-VC                | MO-BDA-EHHO-VC |                    3.50818e-06 |               2273   |   0.386238  |                  0.099802  |        52 |       48 |      0 | 1         | False                   |
| rob_seen_central_delta_nmse | BEHHO-VC-Calibrated    | MO-BDA-EHHO-VC |                   -7.01636e-06 |               2346   |   0.538249  |                 -0.0708911 |        46 |       54 |      0 | 1         | False                   |
| rob_seen_central_delta_nmse | BDA-EHHO-VC-Calibrated | MO-BDA-EHHO-VC |                   -4.72255e-06 |               2432.5 |   0.75045   |                 -0.0366337 |        47 |       53 |      0 | 1         | False                   |
| rob_unseen_delta_nmse       | HHO-VC                 | MO-BDA-EHHO-VC |                   -7.92714e-06 |               2011.5 |   0.0774657 |                 -0.203366  |        42 |       58 |      0 | 0.232397  | False                   |
| rob_unseen_delta_nmse       | EHHO-VC                | MO-BDA-EHHO-VC |                   -9.78243e-06 |               1869   |   0.0240993 |                 -0.259802  |        41 |       59 |      0 | 0.0963971 | False                   |
| rob_unseen_delta_nmse       | BEHHO-VC-Calibrated    | MO-BDA-EHHO-VC |                   -7.89341e-06 |               2063.5 |   0.112559  |                 -0.182772  |        44 |       56 |      0 | 0.232397  | False                   |
| rob_unseen_delta_nmse       | BDA-EHHO-VC-Calibrated | MO-BDA-EHHO-VC |                   -2.6986e-06  |               2098   |   0.142059  |                 -0.169109  |        43 |       57 |      0 | 0.232397  | False                   |
| rob_allfamilies_delta_nmse  | HHO-VC                 | MO-BDA-EHHO-VC |                   -9.09428e-06 |               2015   |   0.0795082 |                 -0.20198   |        41 |       59 |      0 | 0.318033  | False                   |
| rob_allfamilies_delta_nmse  | EHHO-VC                | MO-BDA-EHHO-VC |                   -5.55912e-06 |               2062   |   0.111396  |                 -0.183366  |        40 |       60 |      0 | 0.334188  | False                   |
| rob_allfamilies_delta_nmse  | BEHHO-VC-Calibrated    | MO-BDA-EHHO-VC |                   -1.83505e-06 |               2363   |   0.577521  |                 -0.0641584 |        49 |       51 |      0 | 0.577521  | False                   |
| rob_allfamilies_delta_nmse  | BDA-EHHO-VC-Calibrated | MO-BDA-EHHO-VC |                   -3.02243e-06 |               2164.5 |   0.215154  |                 -0.142772  |        46 |       54 |      0 | 0.430308  | False                   |

## Interpretation rule

Security conclusions should be supported particularly by NMI and histogram overlap, because they were not optimization objectives. Robustness generalization should be supported primarily by the unseen perturbation aggregate (random block, dropout, bit flip, crop loss), not only by central block erasure, which was included in the MO objective.