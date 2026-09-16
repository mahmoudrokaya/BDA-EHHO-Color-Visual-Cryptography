# Fitness-Definition Sensitivity Audit

The BDA-VC source paper leaves two fitness details ambiguous: whether correlation is signed or absolute, and how the two shares are aggregated. This audit exhaustively scans color-level counts and quantifies whether those choices change the selected optimum.

## Definitions compared

- Correlation: signed Pearson CC vs |CC|.
- Share aggregation: Share 1 only, Share 2 only, mean of both, or conservative maximum.
- Current default: **mean[PSNR + |CC|] across the two shares**.

## Summary

| correlation_mode   | share_aggregation   |   cases |   same_optimum_rate |   median_abs_NX_difference |   max_abs_NX_difference |
|:-------------------|:--------------------|--------:|--------------------:|---------------------------:|------------------------:|
| abs_cc             | max                 |      18 |            22.2222  |                       13   |                     187 |
| abs_cc             | mean                |      18 |           100       |                        0   |                       0 |
| abs_cc             | share1              |      18 |            22.2222  |                       11   |                     237 |
| abs_cc             | share2              |      18 |            16.6667  |                       11   |                     187 |
| signed_cc          | max                 |      18 |            22.2222  |                       13   |                     180 |
| signed_cc          | mean                |      18 |            55.5556  |                        0   |                     180 |
| signed_cc          | share1              |      18 |             5.55556 |                       19.5 |                     237 |
| signed_cc          | share2              |      18 |            16.6667  |                       11   |                     180 |

## Decision rule

If signed-vs-absolute CC or share aggregation materially changes the optimum, the paper should explicitly disclose the adopted interpretation and include the sensitivity result as a reproducibility note. If differences are small, the current default can be retained as a stable operationalization of the paper's stated goal of low secret-share similarity.