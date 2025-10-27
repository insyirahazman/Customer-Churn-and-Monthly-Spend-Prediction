# Customer Churn and Monthly Spend Prediction

This repository is an end-to-end demo for synthetic customer analytics: data cleaning, feature engineering, training of classification and regression models, and a simple Gradio-based deployment for inference.

## Project layout

- `01_DataCleaning.ipynb` — data generation and cleaning.
- `02_classification.ipynb` — preprocessing, feature encoding, model training (classification), and saving artifacts.
- `03_Regression.ipynb` — regression training for monthly spend.
- `04_Deployment.ipynb` — Gradio app combining churn classification and spend regression.
- `cleaned_data_classification.csv`, `cleaned_data_regression.csv` — cleaned datasets used by notebooks.
- `results/` — directory for saved artifacts (models, encoders, scaler). Example filenames used across notebooks:
  - `results/model_RF_class.joblib` — classification model
  - `results/model_RF_reg.joblib` — regression model
  - `results/scaler.joblib` — StandardScaler / normalization object for classification model

## Contributors

This project was completed by:

- Nur Insyirah Iman Mohd Azman
- Nurul Eirda Nurina Abd Halim
- Hamizah Hasnan
- Fatin Nur Aisyah Zainal

## Feature improvements
1) Class imbalance (classification)
	- Simple resampling: try SMOTE (oversampling minority), RandomOverSampler, or ADASYN for balanced training.
	- Under-sampling: RandomUnderSampler or cluster-based under-sampling if dataset is large.
	- Class weights: many classifiers accept a `class_weight` parameter (e.g., `class_weight='balanced'`) to penalize errors on minority class.
	- Loss-level approaches: use focal loss (for neural nets) or customized training objective to focus the model on hard examples.
	- Evaluation: prefer precision/recall, F1, and PR AUC over accuracy. Report class-wise metrics and confusion matrices.

2) Robust evaluation and thresholding
	- Use cross-validation with stratification (StratifiedKFold) to get stable performance estimates.
	- Calibrate predicted probabilities (CalibratedClassifierCV) if probability estimates are used for thresholding.