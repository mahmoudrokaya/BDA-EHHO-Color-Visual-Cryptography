# BDA-VC Baseline Fidelity Audit

**Primary reference DOI:** `10.1080/1206212X.2020.1859244`

## Executive conclusion

The Group-1 implementation is structurally close to the published BDA-VC method, and its share-generation and XOR-reconstruction rules match the reference algorithm. However, one material implementation deviation and several source-paper ambiguities must be resolved before the BDA implementation is frozen as the comparative baseline.

**Required correction:** the current Python BDA optimizes R, G and B in separate optimizer runs. The reference method and supplied MATLAB implementation maintain XR, XG and XB inside the same BDA iteration loop. A joint three-channel BDA baseline should therefore replace the sequential-channel implementation before HHO comparisons.

The audit also shows that the low reconstructed-image PSNR observed in the initial validation must not automatically be interpreted as baseline failure. The reference paper explicitly uses low PSNR between the original image and individual shares as an encryption-quality objective. Reconstruction fidelity and share secrecy are conceptually different measurements and must be reported separately in the new work.

## Fidelity matrix

| id   | component                  | importance             | implementation_status   | implementation_evidence                                                                                                                                           |
|:-----|:---------------------------|:-----------------------|:------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| R01  | VC threshold               | critical               | MATCH                   | generate_rgb_shares produces exactly Share 1 and Share 2.                                                                                                         |
| R02  | Color decomposition        | critical               | REVIEW                  | RGB module explicitly separates three channels without resizing.                                                                                                  |
| R03  | Histogram                  | critical               | MATCH                   | Share-generation module builds a 256-bin channel histogram.                                                                                                       |
| R04  | Decision variables         | critical               | MATCH                   | Encoding uses 8 bits per channel; RGB solution is 24 bits.                                                                                                        |
| R05  | Optimization objective     | critical               | ADAPTATION              | Implements mean[PSNR + |CC|] across both shares. Paper does not uniquely specify share aggregation and says ideal CC is zero.                                     |
| R06  | BDA structure              | critical               | DEVIATION               | Current Python g1_07 optimizes R/G/B channels sequentially with separate optimizer streams; supplied/reference MATLAB BDA updates XR/XG/XB within one joint loop. |
| R07  | Reference iteration count  | benchmark-reproduction | CONFIGURABLE            | g1_07 supports max_iterations; real-image validation intentionally used 10 iterations, while paper benchmark states 1000.                                         |
| R08  | Grouping                   | critical               | MATCH_WITH_TIE_RULE     | Uses cumulative histogram targets and unique boundaries; exact equal population may be impossible for tied intensities.                                           |
| R09  | Probability                | critical               | MATCH                   | Probability derives from group index divided by effective_groups-1.                                                                                               |
| R10  | Share generation when r<P  | critical               | MATCH                   | For r<P, implementation assigns (0,0) below P/2 and (255,255) otherwise.                                                                                          |
| R11  | Share generation when r>=P | critical               | MATCH                   | For r>=P, implementation uses split P+(1-P)/2 and assigns (0,255)/(255,0).                                                                                        |
| R12  | Final color shares         | critical               | MATCH                   | R/G/B channel shares are stacked into final RGB shares.                                                                                                           |
| R13  | Pixel expansion            | critical               | MATCH                   | No pixel expansion; real-image validation verifies identical dimensions.                                                                                          |
| R14  | Decryption                 | critical               | MATCH                   | Reconstruction uses bitwise XOR.                                                                                                                                  |
| R15  | BDA binary update          | critical               | MATCH                   | BDA implementation uses the V3 transfer and probabilistic bit flips.                                                                                              |

## Reference-paper ambiguities that affect reproducibility

### A01. Fitness aggregation across two shares

The paper states fitness(PSNR + CC) from original-vs-share comparisons, but does not uniquely specify whether Share 1, Share 2, their sum, mean, minimum, or another aggregation is used.

**Impact on our implementation:** Current Python implementation uses the mean across Share 1 and Share 2.

### A02. Signed versus absolute correlation

The paper says minimize CC and later says ideal CC is zero. Direct minimization of signed Pearson CC could reward strongly negative correlations, which conflicts with the stated zero-correlation security goal.

**Impact on our implementation:** Current Python implementation minimizes |CC|.

### A03. NX range includes invalid group counts

The paper describes XR/XG/XB as 8-bit values ranging 0-255, but share generation uses P=k/(NX-1); NX=0 or NX=1 is mathematically invalid as a number of histogram groups.

**Impact on our implementation:** Current executable implementation clamps decoded NX to [2,255].

### A04. PSNR/MSE interpretation in performance section

The paper treats low PSNR as desirable encryption quality for original-vs-share comparison, but nearby prose also discusses recovered-image quality. Its reported PSNR and MSE values are not mutually consistent under the standard 8-bit PSNR formula.

**Impact on our implementation:** Do not interpret low original-vs-share PSNR as reconstructed-image PSNR. Keep secrecy and reconstruction metrics separate in the new study.

### A05. Grouping and tied histogram intensities

The paper requires equal numbers of pixels per group, but identical intensity values cannot always be split into strictly equal histogram regions without splitting an intensity bin.

**Impact on our implementation:** Current implementation uses deterministic cumulative-histogram quantile boundaries; group populations are therefore approximately equal when ties occur.

## Numerical consistency audit of reported PSNR/MSE

Using the standard 8-bit PSNR definition, none of the PSNR/MSE pairs transcribed from the reference paper's Table 4 are mutually consistent. This does not invalidate the VC scheme, but it means those pairs should not be used as exact numeric reproduction targets without clarification from original code or authors.

| image    |   reported_psnr_db |   reported_mse |   psnr_from_reported_mse_standard_formula |   mse_implied_by_reported_psnr_standard_formula | reported_pair_consistent_standard_8bit_psnr   |
|:---------|-------------------:|---------------:|------------------------------------------:|------------------------------------------------:|:----------------------------------------------|
| Lena     |             7.4121 |         5.4721 |                                   40.7493 |                                         11799.7 | False                                         |
| Jet      |             6.1177 |         4.3311 |                                   41.7648 |                                         15896.8 | False                                         |
| Barbara  |             7.3681 |         5.0011 |                                   41.1401 |                                         11919.8 | False                                         |
| Sailboat |             6.1315 |         4.1121 |                                   41.9902 |                                         15846.4 | False                                         |

**Inconsistent reported pairs under the standard formula:** 4/4.

## Real-image implementation evidence

- Real images audited: **6**
- Images passing all critical software checks: **6/6**
- Same-seed exact reproducibility: **6/6**
- Mean reconstructed-image PSNR in the diagnostic run: **3.4148 dB**.

## Actions before Group 2

1. Replace the sequential-channel Python BDA with a **joint R/G/B BDA loop** matching the supplied MATLAB structure.
2. Preserve the exact probabilistic share-generation rules already implemented.
3. Keep the executable NX bound [2,255] and document it as a necessary interpretation of an internally inconsistent source range.
4. Run a **fitness sensitivity audit** comparing signed CC vs |CC| and Share-1/Share-2 aggregation choices on the six real images.
5. Keep a strict distinction between **share secrecy metrics** (original vs individual share) and **reconstruction quality metrics** (original vs recovered image).
6. Do not use the reference paper's Table-4 PSNR/MSE pairs as exact reproduction targets unless their normalization is clarified.
7. After the corrected joint BDA passes the same real-image checks, freeze it as the BDA-VC baseline and only then implement HHO/EHHO.

## Audit status

**CONDITIONAL PASS — correction required before optimizer comparison.**