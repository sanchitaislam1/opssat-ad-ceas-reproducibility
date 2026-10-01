# Reproduction status

## Authoritative manuscript outputs

The authoritative CSV files preserve the values reported in the final manuscript. They are separated from regenerated outputs so that software-version differences are not silently presented as historical results.

## Verified items

- Final Random Forest confusion matrix: TN=414, FP=2, FN=12, TP=101.
- The six-model table, feature-group ablation table, and channel-generalization table are preserved in `results/authoritative_*.csv`.
- The final representation comparison is preserved in `results/representation_results.csv`.
- The final expanded-feature comparison is preserved in `results/expanded_feature_results.csv`.
- The training-only five-fold screening summary is preserved in `results/expanded_feature_cv_results.csv`.
- Permutation importance is preserved in `results/permutation_importance.csv`; it is descriptive and was not used for model selection.

## Limitations

The original software environment was not archived, so fresh execution may differ for some learners. Regenerated outputs from the available local environment are retained separately where available.

The original raw-CNN/fusion checkpoint was not retained. `src/07_raw_cnn.py` is a clean reimplementation and should not be described as byte-for-byte reproduction of the original neural run.

The raw benchmark dataset is intentionally excluded from this archive. Users should obtain it from Zenodo DOI 10.5281/zenodo.15108715.

## Important provenance rule

Do not replace the authoritative manuscript tables with newly regenerated values solely because they differ numerically. Any such difference should be documented and investigated first.
