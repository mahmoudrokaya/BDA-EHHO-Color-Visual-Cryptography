# Group 2 Controlled Validation

- Images: **6**
- Population: **10**
- Common evaluation budget: **100**
- Budget compliance: **PASS**

## Algorithm summary

| algorithm   |   cases |   mean_best_score |   median_best_score |   mean_evaluations |   mean_runtime_s |
|:------------|--------:|------------------:|--------------------:|-------------------:|-----------------:|
| BDA-EHHO-VC |       6 |           5.01963 |             4.99746 |                100 |          5.63444 |
| BEHHO-VC    |       6 |           5.01926 |             4.99722 |                100 |          5.83636 |
| EHHO-VC     |       6 |           5.01949 |             4.99751 |                100 |          5.57862 |
| HHO-VC      |       6 |           5.01926 |             4.9971  |                100 |          5.94608 |

This is a six-image implementation validation, not the final inferential experiment. The same frozen VC objective and the same image-specific random fields are used across algorithms. Final parameter settings will be selected using BSDS500 validation data only.