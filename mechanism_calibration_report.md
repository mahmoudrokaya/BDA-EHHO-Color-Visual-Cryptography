# Group 2 Mechanism Calibration

## BEHHO diversity calibration

| variant          |   runs |   mean_score |   median_score |   mean_runtime_s |   mean_injections |   pct_runs_with_injection |   mean_diversity |   mean_final_diversity |   mechanism_penalty |
|:-----------------|-------:|-------------:|---------------:|-----------------:|------------------:|--------------------------:|-----------------:|-----------------------:|--------------------:|
| thr0.70_frac0.30 |     24 |      5.0567  |        5.04298 |          54.1744 |           2.75    |                   62.5    |         0.821819 |               0.812726 |             2.5     |
| thr0.70_frac0.20 |     24 |      5.0568  |        5.043   |          54.3473 |           2.91667 |                   62.5    |         0.818187 |               0.771806 |             2.5     |
| thr0.75_frac0.30 |     24 |      5.05667 |        5.04298 |          54.3315 |           3.95833 |                   66.6667 |         0.822225 |               0.779722 |             6.66667 |
| thr0.75_frac0.20 |     24 |      5.05676 |        5.043   |          53.8669 |           3.79167 |                   66.6667 |         0.826727 |               0.798073 |             6.66667 |
| thr0.80_frac0.20 |     24 |      5.05671 |        5.04305 |          55.3255 |           5.375   |                   79.1667 |         0.826645 |               0.815833 |            19.1667  |
| thr0.80_frac0.30 |     24 |      5.05673 |        5.04306 |          55.3024 |           5.70833 |                   79.1667 |         0.821549 |               0.776823 |            19.1667  |

Mechanism-first recommendation: **thr0.70_frac0.30**.
Its run-level injection rate is **62.50%**.

## Hybrid schedule calibration

| variant        |   runs |   mean_score |   median_score |   mean_runtime_s |   mean_bda_fraction |   mean_bda_proposals |   mean_ehho_proposals |   mechanism_penalty |
|:---------------|-------:|-------------:|---------------:|-----------------:|--------------------:|---------------------:|----------------------:|--------------------:|
| balanced_70_30 |     24 |      5.05663 |        5.04251 |          54.5884 |            0.491042 |              98.2083 |               101.792 |                   0 |
| balanced_65_35 |     24 |      5.05666 |        5.04258 |          56.3751 |            0.49     |              98      |               102     |                   0 |
| balanced_80_20 |     24 |      5.05672 |        5.0427  |          54.518  |            0.488333 |              97.6667 |               102.333 |                   0 |

Mechanism-first recommendation: **balanced_70_30**.
Its mean BDA proposal fraction is **0.491** (EHHO fraction ≈ 0.509).

## Selection principle

The recommended settings are selected first for evidence that the intended mechanism is actually operating, and only then by objective score/runtime. This prevents tuning the mechanisms merely to manufacture a favorable result.

After accepting these settings, rerun the original 12-image pilot with the calibrated BEHHO and calibrated hybrid before proceeding to the larger screen profile.