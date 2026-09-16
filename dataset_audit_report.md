# Dataset Audit Report

**Data root:** `D:\48\481\New Papers\BDA_To_HHO_paper\Data`

## 1. Overall Summary

- Total files: **1,139**
- Readable images: **549**
- Unreadable/corrupted image files: **0**
- Total storage: **154.33 MB**
- Dataset hints: **BSDS500**
- Duplicate groups: **15**

## 2. Image Characteristics

- Width: 256–1024 px; mean 434.0; median 481.0
- Height: 256–1024 px; mean 376.3; median 321.0
- Image area: mean 0.161 MP; median 0.154 MP

### Color modes

| mode   |   channels | bit_depth     |   count |   percentage |
|:-------|-----------:|:--------------|--------:|-------------:|
| RGB    |          3 | 8-bit/channel |     519 |        94.54 |
| L      |          1 | 8-bit/channel |      30 |         5.46 |

### Most common dimensions

|   width |   height |   count |   percentage |
|--------:|---------:|--------:|-------------:|
|     481 |      321 |     354 |        64.48 |
|     321 |      481 |     156 |        28.42 |
|     512 |      512 |      22 |         4.01 |
|     256 |      256 |      14 |         2.55 |
|    1024 |     1024 |       3 |         0.55 |

## 3. Dataset Splits

| split       |   image_count |   total_size_mb |   percentage |
|:------------|--------------:|----------------:|-------------:|
| test        |           200 |         14.0611 |        36.43 |
| train       |           200 |         13.8771 |        36.43 |
| val         |           100 |          7.3395 |        18.21 |
| unspecified |            49 |         13.7959 |         8.93 |

## 4. File Extensions

| extension      |   file_count |   total_size_mb |
|:---------------|-------------:|----------------:|
| .mat           |          515 |       23.0059   |
| .jpg           |          505 |       35.5955   |
| .tiff          |           39 |       13.3801   |
| .txt           |           27 |        0.003955 |
| .m             |           16 |        0.029021 |
| .hh            |           11 |        0.099635 |
| .cc            |            9 |        0.069788 |
| .png           |            5 |        0.097974 |
| .db            |            3 |        0.680664 |
| .h             |            2 |        0.008961 |
| [no extension] |            2 |        0.000187 |
| .fig           |            1 |        0.093928 |
| .sh            |            1 |        8.1e-05  |
| .pdf           |            1 |       10.2683   |
| .mexa64        |            1 |        0.1074   |
| .tar           |            1 |       70.8887   |

## 5. Main Data Folders

| folder                             |   total_files |   image_files |   total_size_mb | extensions                            | splits      | dataset_hints             |
|:-----------------------------------|--------------:|--------------:|----------------:|:--------------------------------------|:------------|:--------------------------|
| BSR\BSDS500\data\images\test       |           201 |           200 |          14.727 | .db; .jpg                             | test        | BSDS500                   |
| BSR\BSDS500\data\images\train      |           201 |           200 |          13.884 | .db; .jpg                             | train       | BSDS500                   |
| BSR\BSDS500\data\images\val        |           101 |           100 |           7.347 | .db; .jpg                             | val         | BSDS500                   |
| misc                               |            39 |            39 |          13.38  | .tiff                                 | unspecified | Unknown / custom          |
| BSR\bench\data\images              |             5 |             5 |           0.318 | .jpg                                  | unspecified | Unknown / custom          |
| BSR\bench\data\png                 |             5 |             5 |           0.098 | .png                                  | unspecified | Unknown / custom          |
| BSR\BSDS500\data\groundTruth\test  |           200 |             0 |           8.684 | .mat                                  | test        | BSDS500                   |
| BSR\BSDS500\data\groundTruth\train |           200 |             0 |           8.614 | .mat                                  | train       | BSDS500                   |
| BSR\BSDS500\data\groundTruth\val   |           100 |             0 |           4.318 | .mat                                  | val         | BSDS500                   |
| BSR\bench\source                   |            26 |             0 |           0.179 | .cc; .h; .hh; .m; .sh; [no extension] | unspecified | Unknown / custom          |
| BSR\bench\benchmarks               |            15 |             0 |           0.228 | .fig; .m; .mexa64                     | unspecified | Unknown / custom          |
| BSR\bench\data\test_1              |             8 |             0 |           0.001 | .txt                                  | unspecified | Unknown / custom          |
| BSR\bench\data\test_4              |             8 |             0 |           0.001 | .txt                                  | unspecified | Unknown / custom          |
| BSR\bench\data\groundTruth         |             5 |             0 |           0.191 | .mat                                  | unspecified | Unknown / custom          |
| BSR\bench\data\segs                |             5 |             0 |           0.077 | .mat                                  | unspecified | Unknown / custom          |
| BSR\bench\data\test_5              |             5 |             0 |           0.001 | .txt                                  | unspecified | Unknown / custom          |
| BSR\bench\data\ucm2                |             5 |             0 |           1.12  | .mat                                  | unspecified | Unknown / custom          |
| BSR\bench\data\test_2              |             3 |             0 |           0.001 | .txt                                  | unspecified | Unknown / custom          |
| BSR\bench\data\test_3              |             3 |             0 |           0.001 | .txt                                  | unspecified | Unknown / custom          |
| BSR\bench                          |             2 |             0 |           0.002 | .m                                    | unspecified | BSDS500; Unknown / custom |
| .                                  |             1 |             0 |          70.889 | .tar                                  | unspecified | BSDS500                   |
| BSR\documentation                  |             1 |             0 |          10.268 | .pdf                                  | unspecified | Unknown / custom          |

## 6. Data Quality

- Unreadable/corrupted images: **0**
- Exact duplicate files: **30 files across 15 groups**

## 7. Implications for the VC Experiments

- **519/549** readable images are already RGB; the remainder would require conversion if a uniform RGB protocol is used.
- Use the same fixed image list for BDA-VC, HHO-VC, EHHO-VC, BEHHO-VC, BDA-EHHO-VC, and MO-BDA-EHHO-VC.
- If dimensions vary, explicitly state whether native dimensions are retained or images are resized to a common resolution.
- Exclude exact duplicates from inferential comparisons unless duplication is intentional.
- Report train/validation/test folders for reproducibility even if the optimization study does not train a predictive model.