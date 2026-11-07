# Experimental Protocol — Credit Card Fraud Detection

## 1. Problem formulation

The objective is to detect fraudulent credit card transactions using machine learning techniques.

The problem is characterized by a highly imbalanced dataset, with fraudulent transactions representing a very small proportion of observations.

We compare supervised and unsupervised approaches.

## 2. Dataset and preprocessing

- Dataset: Kaggle Credit Card Fraud Detection.
- Cleaned observations: 283,726.
- Features: 30 explanatory variables.
- Target: Class (0 = legitimate, 1 = fraudulent).
- Random state: 42.

Exact duplicate observations were removed before the experimental split. The original dataset was preserved.

No additional observations will be removed without methodological justification.

## 3. Data splitting strategy

A chronological split is used to preserve the temporal order of transactions.

| Dataset | Approximate proportion | Purpose |
| --- | --- | --- |
| Training | 70% | Model fitting |
| Validation | 15% | Hyperparameter and threshold selection |
| Test | 15% | Final evaluation |

The test set remains untouched until the experimental configuration is finalized.

## 4. Models

Four approaches will be evaluated:

1. Baseline: always predicts the majority class (0).
2. Logistic Regression: supervised classification with class weighting.
3. Random Forest: supervised ensemble classification with class weighting.
4. Isolation Forest: unsupervised anomaly detection.

## 5. Preprocessing

For Logistic Regression, numerical features will be standardized using StandardScaler.

The scaler will be fitted exclusively on the training data.

Random Forest and Isolation Forest will use their original numerical inputs without mandatory standardization.

No information from the validation or test sets will be used to fit preprocessing transformations.

## 6. Hyperparameter tuning

Hyperparameters will be selected using the validation set.

Proposed search configurations:

**Logistic Regression**

- C: 0.01, 0.1, 1, 10.
- class_weight: balanced.
- max_iter: 2000.

**Random Forest**

- n_estimators: 200, 300.
- max_depth: None, 10, 20.
- min_samples_leaf: 1, 2, 5.
- class_weight: balanced_subsample.

**Isolation Forest**

- n_estimators: 200, 300.
- Random state: 42.
- Training performed without using training labels.
- Anomaly decision threshold selected using validation data.

## 7. Evaluation metrics

The primary metrics are:

- Precision
- Recall
- F1-score
- PR-AUC, measured using Average Precision.

Accuracy will be reported only as a supplementary metric because of the severe class imbalance.

For supervised models, the classification threshold will be selected on the validation set by maximizing F1-score.

For Isolation Forest, the anomaly score threshold will also be selected using validation labels.

## 8. Final evaluation

After model selection and protocol validation, the selected configurations will be evaluated on the untouched test set.

The final evaluation will include:

- Confusion matrices.
- Precision, Recall and F1-score.
- PR-AUC.
- Error analysis.
- Subgroup performance analysis.
- Feature importance analysis.
- Bootstrap confidence intervals using 1,000 resamples.
- Statistical comparisons between models.

No model or threshold modification will be made based on final test results.

## 9. Reproducibility

- Random state: 42.
- Python and scikit-learn versions will be recorded.
- Experimental configurations and results will be documented.
- Results will be saved in `results/resultats.csv`.

The protocol will be frozen before final test evaluation.
