# Research-Direction Evidence Report

## Target idea

- **domain:** color visual cryptography
- **threshold_scheme:** (2,2)
- **image_model:** RGB
- **share_generation:** probabilistic binary shares
- **reconstruction:** XOR/digital overlap
- **optimization_role:** color/intensity level determination
- **baseline_optimizer:** Binary Dragonfly Algorithm (BDA)
- **candidate_optimizer:** Harris Hawks Optimization (HHO/Binary HHO)
- **possible_extension:** BDA-HHO hybrid and/or multi-objective optimization
- **desired_properties:** no pixel expansion; high individual-share secrecy; high reconstruction quality; robustness to attacks/noise; low computational cost

## Corpus status

- Papers processed: **100**
- Papers requiring manual review: **65**
- Relevance tiers: **{'METHOD': 81, 'CORE': 16, 'EXCLUDE': 3}**
- HHO papers: **78**
- Binary-HHO papers: **15**
- BDA papers: **8**
- Color visual cryptography papers: **8**
- Papers optimizing color/intensity levels: **1**

## CORE papers

- **Design and implementation of image data sharing through a visual cryptography system with one-time password authentication.** (2026.0) | Threat: VERY_HIGH | Overlap: 66.7% | DOI: 10.1038/s41598-026-58613-9
- **A Narrative Study on Visual Cryptography Techniques for Robust and Secure Image Communication: A Review** (2025.0) | Threat: HIGH | Overlap: 55.6% | DOI: 10.70389/pjs.100156
- **Image Encryption Using Modified Serpent Algorithm and Harris Hawks Optimization** (2025.0) | Threat: HIGH | Overlap: 51.1% | DOI: 10.58346/jowua.2025.i1.009
- **Size-Invariant Visual Cryptography With Improved Perceptual Quality for Grayscale Image** (2020.0) | Threat: LOW | Overlap: 44.4% | DOI: 10.1109/access.2020.3021522
- **A Secure and Verifiable Color Visual Cryptography Scheme with LSB Based Image Steganography** (2021.0) | Threat: LOW | Overlap: 42.2% | DOI: 10.30534/ijatcse/2021/031042021
- **A Tabu Search Algorithm for General Threshold Visual Cryptography Schemes** (2021.0) | Threat: LOW | Overlap: 35.6% | DOI: 10.18280/isi.260310
- **Lossless Recovery Scheme for Grayscale Visual Cryptography Based on Random Grids** (2025.0) | Threat: LOW | Overlap: 35.6% | DOI: 10.52783/jisem.v10i22s.3613
- **Modified Elgamal based Visual Cryptography via Hybrid Optimization Framework** (2024.0) | Threat: LOW | Overlap: 33.3% | DOI: 10.46253/j.mr.v7i1.a5
- **Grouped k-threshold random grid-based visual cryptography scheme** (2025.0) | Threat: LOW | Overlap: 31.1% | DOI: 10.48550/arxiv.2508.05394
- **Image Encryption An Intelligent Approach of Color Visual Cryptography** (2013.0) | Threat: LOW | Overlap: 26.7% | DOI: 10.5120/14442-2601
- **Survey on computational intelligence based image encryption techniques** (2020.0) | Threat: LOW | Overlap: 26.7% | DOI: 10.11591/ijeecs.v19.i3.pp1428-1435
- **Adaptive Particle Swarm Optimization Data Hiding for High Security Secret Image Sharing** (2022.0) | Threat: LOW | Overlap: 26.7% | DOI: 10.32604/csse.2022.022459
- **An Efficient (n, n) Visual Secret Image Sharing using Random Grids with XOR Recovery** (2019.0) | Threat: LOW | Overlap: 22.2% | DOI: 10.5815/ijcnis.2019.11.02
- **A Multi-Layer Visual Cryptography Framework with Adaptive Key Optimization and Kronecker Product-Based Diffusion** (2026.0) | Threat: LOW | Overlap: 22.2% | DOI: 10.18280/ijsse.160514
- **A Robust Visual Cryptography Technique for Photographic Grayscale Images Using Block Optimization and Blind Invisible Watermarking** (2012.0) | Threat: LOW | Overlap: 15.6% | DOI: 10.7763/ijcte.2012.v4.469
- **A Novel Integration of Proximal Policy Optimization, In-Memory Computing and Visual Cryptography for Secure Image Encryption** (2025.0) | Threat: LOW | Overlap: 8.9% | DOI: 10.55248/gengpi.6.0625.22135

## Highest novelty threats

- **VERY_HIGH | overlap 66.7%** — Design and implementation of image data sharing through a visual cryptography system with one-time password authentication. (2026.0); DOI: 10.1038/s41598-026-58613-9
- **HIGH | overlap 55.6%** — A Narrative Study on Visual Cryptography Techniques for Robust and Secure Image Communication: A Review (2025.0); DOI: 10.70389/pjs.100156
- **HIGH | overlap 51.1%** — Image Encryption Using Modified Serpent Algorithm and Harris Hawks Optimization (2025.0); DOI: 10.58346/jowua.2025.i1.009

## Decision rules

1. If a prior paper already combines color visual cryptography, HHO, RGB decomposition, (2,2) shares, color-level optimization, probabilistic share generation, and XOR recovery, then a simple BDA-to-HHO replacement is not a defensible novelty claim.
2. If direct HHO overlap exists but Binary-HHO representation, fitness formulation, security analysis, or evaluation protocol differs, the contribution must be framed around those differences rather than around HHO itself.
3. If a true BDA-HHO hybrid is not directly represented, investigate a principled hybrid mechanism rather than merely calling two optimizers sequentially.
4. Compare any proposed hybrid with standalone BDA, standard HHO, Binary HHO, and additional strong baselines under equal fitness-evaluation budgets.
5. If multi-objective visual cryptography is sparse, consider separate objectives for share secrecy, reconstruction quality, runtime, and robustness instead of an ad-hoc single scalar score.
6. Any paper classified as CORE with HIGH or VERY_HIGH novelty threat must be manually read in full before finalizing the Introduction, Related Work, contribution statement, or experimental design.