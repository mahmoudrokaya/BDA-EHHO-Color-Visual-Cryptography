# Group 3 — Robustness Validation

## Candidate statistics

| candidate            |   global_min |   global_max |   global_span |   global_std |   normalized_iqr |   pct_archives_nonconstant |   median_within_archive_span |   median_within_archive_cv |   pct_monotonic_with_damage_rate |   abs_rho_reconstruction |   abs_rho_security |   abs_rho_complexity |   diagnostic_score |
|:---------------------|-------------:|-------------:|--------------:|-------------:|-----------------:|---------------------------:|-----------------------------:|---------------------------:|---------------------------------:|-------------------------:|-------------------:|---------------------:|-------------------:|
| B1_central_mean      |    0.0578292 |    0.0589518 |   0.00112262  |  0.000204887 |         0.251603 |                        100 |                  0.000296126 |                0.00125329  |                              100 |                0.090396  |          0.0903308 |          0.000650232 |           0.782414 |
| B3_dropout_mean      |    0.0577645 |    0.0590648 |   0.00130037  |  0.000286236 |         0.334256 |                        100 |                  0.000262304 |                0.000920669 |                              100 |                0.0610768 |          0.0143179 |          0.0899927   |           0.781185 |
| B4_crop_mean         |    0.057632  |    0.0587288 |   0.00109671  |  0.000223896 |         0.310039 |                        100 |                  0.000303683 |                0.00132906  |                              100 |                0.108242  |          0.158495  |          0.0608768   |           0.765692 |
| B2_random_block_mean |    0.0578918 |    0.0588518 |   0.000959982 |  0.000177301 |         0.244378 |                        100 |                  0.000275617 |                0.00112496  |                              100 |                0.257915  |          0.171472  |          0.177319    |           0.740021 |

## Spearman correlations

|                       |   old_f1_reconstruction |   old_f2_security |   old_f4_complexity |   B1_central_mean |   B2_random_block_mean |   B3_dropout_mean |   B4_crop_mean |
|:----------------------|------------------------:|------------------:|--------------------:|------------------:|-----------------------:|------------------:|---------------:|
| old_f1_reconstruction |               1         |        -0.927114  |        -0.570507    |      -0.090396    |              0.257915  |         0.0610768 |     -0.108242  |
| old_f2_security       |              -0.927114  |         1         |         0.416993    |       0.0903308   |             -0.171472  |         0.0143179 |      0.158495  |
| old_f4_complexity     |              -0.570507  |         0.416993  |         1           |       0.000650232 |             -0.177319  |        -0.0899927 |      0.0608768 |
| B1_central_mean       |              -0.090396  |         0.0903308 |         0.000650232 |       1           |              0.467641  |         0.412804  |     -0.108643  |
| B2_random_block_mean  |               0.257915  |        -0.171472  |        -0.177319    |       0.467641    |              1         |         0.626505  |     -0.0438798 |
| B3_dropout_mean       |               0.0610768 |         0.0143179 |        -0.0899927   |       0.412804    |              0.626505  |         1         |     -0.0802938 |
| B4_crop_mean          |              -0.108242  |         0.158495  |         0.0608768   |      -0.108643    |             -0.0438798 |        -0.0802938 |      1         |

## Diagnostic top candidate

**B1_central_mean**

The automatic ranking is diagnostic only. The final robustness objective must also be conceptually appropriate for visual cryptography.

## Redundancy warnings

- No |rho| >= 0.90 redundancy warning.

## Next step

If the top candidate is conceptually acceptable and satisfies the discrimination/redundancy checks, freeze it as f3 and update the multi-objective problem together with the already selected S2 security objective. Then rerun the same 12-image MO validation once before E4.