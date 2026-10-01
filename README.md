# OPSSAT-AD Final Reproducibility Package

**Manuscript:** *Machine Learning for CubeSat Telemetry Anomaly Detection: A Reproducible Comparison of Handcrafted and Raw-Signal Representations on OPSSAT-AD*

**Author:** Sanchita Islam  
**Affiliation:** Heritage Institute of Technology, Kolkata, India

## Purpose

This package is the submission-version reproducibility archive prepared for the CEAS Space Journal manuscript. It contains the study-specific analysis scripts, experiment configuration, authoritative result tables, regenerated tabular outputs, representation-comparison summaries, and publication figures.

The package intentionally does **not** redistribute the OPSSAT-AD benchmark dataset. Obtain the public benchmark data from the official Zenodo record:

https://doi.org/10.5281/zenodo.15108715

The official benchmark code is maintained by KP Labs:

https://github.com/kplabs-pl/OPS-SAT-AD

## Important reproducibility statement

The `results/authoritative_*.csv` files preserve the numerical tables reported in the manuscript's final historical experiment. They are the authoritative source for the manuscript's reported values.

The tabular scripts implement the documented analysis protocol. Because the original software environment was not archived, fresh execution can produce version-dependent differences for some learners and exploratory analyses. Such regenerated outputs are retained separately and are not silently substituted for the authoritative manuscript results.

The original raw-CNN/fusion checkpoint was not retained. `src/07_raw_cnn.py` is therefore a clean reimplementation of the described exploratory raw-sequence experiment, not a byte-for-byte reconstruction of the original neural training run. The manuscript discloses this limitation.

## Final headline results

Random Forest using the 18 benchmark features:

- Accuracy: 0.9735
- Precision: 0.9806
- Recall: 0.8938
- F1: 0.9352
- MCC: 0.9202
- ROC-AUC: 0.9875
- PR-AUC: 0.9675
- Confusion matrix: TN=414, FP=2, FN=12, TP=101

Exploratory representation comparison:

- Raw 1D-CNN: F1=0.9099
- Raw+18 fusion: F1=0.9129
- Expanded 32-feature RF: F1=0.9187

These are descriptive comparisons; the manuscript does not claim a new state-of-the-art method.

## Directory structure

```text
.
├── README.md
├── CONFIGURATION.md
├── REPRODUCTION_STATUS.md
├── LICENSE_NOTE.txt
├── requirements.txt
├── src/
│   ├── common.py
│   ├── 01_data_audit.py
│   ├── 02_model_comparison.py
│   ├── 03_feature_ablation.py
│   ├── 04_feature_importance.py
│   ├── 05_channel_generalization.py
│   ├── 06_expanded_features.py
│   ├── 07_raw_cnn.py
│   └── 08_generate_figures.py
├── results/
│   ├── authoritative_model_results.csv
│   ├── authoritative_ablation_results.csv
│   ├── authoritative_channel_results.csv
│   ├── representation_results.csv
│   ├── expanded_feature_results.csv
│   ├── expanded_feature_cv_results.csv
│   ├── permutation_importance.csv
│   ├── model_comparison_reproduced.csv
│   ├── feature_ablation_reproduced.csv
│   └── channel_generalization_reproduced.csv
└── figures/
    ├── fig_model_comparison.png
    ├── fig_feature_ablation.png
    ├── fig_channel_robustness.png
    └── fig_representation_comparison.png
```

## Dataset and data handling

The raw OPSSAT-AD dataset is not included. The experiments use the official machine-readable train/test designation. Derived feature tables used in the analysis are not redistributed here.

## Citation

Please cite the OPSSAT-AD benchmark paper and dataset when using this package:

Ruszczak, B., Kotowski, K., Evans, D., & Nalepa, J. *The OPS-SAT benchmark for detecting anomalies in satellite telemetry*. Scientific Data, 12, 710 (2025). DOI: 10.1038/s41597-025-05035-3.

Ruszczak, B., Kotowski, K., Evans, D., & Nalepa, J. *OPSSAT-AD - anomaly detection dataset for satellite telemetry*. Zenodo, v2 (2025). DOI: 10.5281/zenodo.15108715.
