# Group 1 Real-Image BDA Baseline Validation

- Selected images: **6**
- Population: **10**
- Iterations: **10**
- Budget/channel: **100**

## Selected images

| experiment_id   | dataset                | split      | filename    |   width |   height |
|:----------------|:-----------------------|:-----------|:------------|--------:|---------:|
| IMG_0027        | BSDS500                | validation | 16077.jpg   |     481 |      321 |
| IMG_0087        | BSDS500                | validation | 66053.jpg   |     481 |      321 |
| IMG_0169        | BSDS500                | test       | 183066.jpg  |     481 |      321 |
| IMG_0173        | BSDS500                | test       | 188025.jpg  |     481 |      321 |
| IMG_0305        | USC-SIPI Miscellaneous | classical  | 4.1.05.tiff |     256 |      256 |
| IMG_0313        | USC-SIPI Miscellaneous | classical  | 4.2.07.tiff |     512 |      512 |

## Critical checks

| check                             |   passed |   total | status   |
|:----------------------------------|---------:|--------:|:---------|
| same_spatial_dimensions           |        6 |       6 | PASS     |
| non_expansible_flag               |        6 |       6 | PASS     |
| share1_binary_0_255               |        6 |       6 | PASS     |
| share2_binary_0_255               |        6 |       6 | PASS     |
| xor_reconstruction_exact          |        6 |       6 | PASS     |
| optimized_levels_valid_2_255      |        6 |       6 | PASS     |
| fitness_values_finite             |        6 |       6 | PASS     |
| best_so_far_convergence_monotonic |        6 |       6 | PASS     |
| same_seed_exactly_reproducible    |        6 |       6 | PASS     |

## Reproducibility

- Same-seed exact reproducibility: **6/6**
- Alternate-seed variability: **6/6**

## Runtime

- Mean primary runtime/image: **10.048 s**
- Projected BDA-only time for 214 images × 30 runs at this validation budget: **17.92 h**

## Overall status

**PASS:** 6/6 images passed all critical checks.