# Customer Analytics

A small end-to-end demo project that generates a synthetic customer dataset, performs data cleaning and feature engineering, trains classification and regression models, and provides a simple Gradio-based deployment for inference.

This repository is intended for learning and demonstration purposes — it shows a full workflow from data wrangling through model training and lightweight deployment.

## Contents

- `01_DataCleaning.ipynb` — data generation and cleaning steps.
- `02_classification.ipynb` — preprocessing and classification model training; also includes saving of encoders, scaler, and model artifacts.
- `03_Regression.ipynb` — regression model training for predicting monthly spend.
- `04_Deployment.ipynb` — combined Gradio deployment (churn classification + spend regression).
- `cleaned_data` — cleaned data snapshots used by the notebooks.
- `results/` — folder where trained models and preprocessing artifacts are saved:
	- `results/model_XGBoost.joblib` (classification model)
	- `results/model_RF.joblib` (regression model)
	- `results/scaler.joblib` (StandardScaler used for X)

## Notebooks — what to run and in what order

- `01_DataCleaning.ipynb`: Run to generate or inspect the cleaned dataset. Produces `cleaned_data*.csv` files used downstream.
- `02_classification.ipynb`: Run the preprocessing and classification training cells. Important: this notebook creates a dictionary named `encoders` (mapping categorical column name → fitted LabelEncoder) and saves it to `results/label_encoders.joblib` when you run the final save-artifacts cell. If you plan to use `04_Deployment.ipynb`, re-run preprocessing and the save cell so `results/label_encoders.joblib` exists.
- `03_Regression.ipynb`: Run the regression training cells. Save the trained regressor into `results/model_RF.joblib` (or the filename referenced in the deployment notebook).
- `04_Deployment.ipynb`: This notebook builds a combined Gradio app (classification + regression). Before running the deployment cell:
	- Ensure the `results/` directory contains the model/scaler/encoders with the expected filenames.
	- If you just installed Gradio, restart the kernel and re-run the deployment cell so Gradio is importable in the session.