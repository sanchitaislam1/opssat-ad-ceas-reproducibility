# Experiment configuration

## Tabular models

All tabular experiments use the official `train` field for the fixed train/test split, the 18 benchmark features, `random_state=42`, and class-balanced weighting where supported.

- Logistic Regression: `StandardScaler`, `class_weight="balanced"`, `max_iter=5000`.
- SVM-RBF: `StandardScaler`, RBF kernel, `class_weight="balanced"`, `probability=True` for probability-based ranking metrics; classification uses the decision-function threshold 0.
- Random Forest: 500 trees, `class_weight="balanced"`, `n_jobs=-1`.
- Extra Trees: 500 trees, `class_weight="balanced"`, `n_jobs=-1`.
- HistGradientBoosting: `max_iter=200`, default remaining parameters, `random_state=42`.
- XGBoost: 300 estimators, `max_depth=5`, `learning_rate=0.05`, `subsample=0.9`, `colsample_bytree=0.9`, binary-logistic objective, log-loss evaluation, `random_state=42`.

Random Forest, Extra Trees, HistGradientBoosting, and XGBoost use a 0.5 probability threshold for classification. ROC-AUC and PR-AUC are computed from continuous model scores.

## Feature ablation and importance

Feature-group ablation uses Extra Trees with 500 trees, class-balanced weighting, and `random_state=42`. Permutation importance uses the held-out test set, F1 scoring, 20 repeats, and `random_state=42`; it is descriptive and is not used for model selection.

## Channel-shift analysis

Leave-one-channel-out analysis uses Extra Trees with the same configuration. A held-out test channel is included when it has at least 30 test segments and both classes are represented. The model is trained on all training channels except the held-out channel.

## Expanded-feature screening

The screening experiment uses a stratified five-fold cross-validation split with `shuffle=True` and `random_state=42`, with a 500-tree class-balanced Random Forest.

## Raw CNN / fusion

The original neural-model checkpoint and complete machine-readable architecture configuration were not retained. `src/07_raw_cnn.py` is therefore explicitly a clean reimplementation scaffold rather than an exact reconstruction. The manuscript reports the original exploratory results separately from the reproducible tabular experiments.

## Reproducibility note

Exact numerical values for some learners can vary slightly with library versions. The manuscript's authoritative result tables are retained separately from regenerated outputs, and the package records the fixed seed and model settings used for the tabular analyses.

## Expanded spectral descriptors

Spectral descriptors are computed from the raw segment amplitude without prior standardization. After excluding the DC bin, the lower quartile of frequency bins is used for low-frequency power and the upper quartile for high-frequency power; the high-to-low ratio is their quotient.

HistGradientBoosting and XGBoost use no class weighting in the documented protocol.
