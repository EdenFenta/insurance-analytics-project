# Insurance Analytics Project

## Overview

The Insurance Analytics Project focuses on building a dynamic, risk-based pricing system for AlphaCare Insurance. The goal is to analyze policy and claims data to identify low-risk segments, predict claim severity, and optimize premium pricing using machine learning techniques.

This project leverages exploratory data analysis (EDA), feature engineering, statistical modeling, and predictive analytics to inform data-driven business decisions.

## Project Structure

```
insurance-analytics-project/
│
├─ data/                   # Raw and processed datasets
│   ├─ MachineLearningRating_v3.txt
│   └─ df_model_task1.csv
│
├─ notebooks/              # Jupyter notebooks for analysis and modeling
│   ├─ eda.ipynb
│   ├─ feature_engineering.ipynb
│   ├─ modeling.ipynb
│   └─ models/             # Saved ML models and scalers
│       ├─ scaler_task4.pkl
│       ├─ rfc_claimprob.pkl
│       ├─ best_severity_model_LinearRegression.pkl
│
├─ reports/                # Project reports and blog-style final submission
│
├─ .dvcignore              # DVC ignore rules
├─ .gitignore
├─ README.md
└─ requirements.txt
```

## Data Versioning

This project uses DVC to track large datasets and machine learning models:

```
# Track raw or processed datasets
dvc add data/MachineLearningRating_v3.txt

# Track models
dvc add notebooks/models/best_severity_model_LinearRegression.pkl

# Push data and models to remote storage
dvc push
```

**Note:** Only .dvc files are tracked by Git. Raw data and model binaries are tracked by DVC.

## Key Tasks

### Task 1: Exploratory Data Analysis (EDA)

- Cleaned and inspected raw datasets.
- Generated descriptive statistics, visualizations, and insights.
- Identified missing values and outliers.

### Task 2: Feature Engineering

- Created new features (e.g., vehicle_age, premium_to_suminsured, log-transformed features).
- One-hot encoded categorical variables (Province, Gender, VehicleType, make).
- Prepared data for modeling.

### Task 3: Claim Probability Model

- Built binary classification models to predict the likelihood of a claim (ClaimFlag).
- Models used: Logistic Regression, Random Forest Classifier, XGBoost (optional).
- Evaluated using accuracy, precision, recall, F1-score, and ROC AUC.

### Task 4: Severity & Premium Prediction

- Predicted claim severity for policies with claims (TotalPremium or log1p_TotalPremium).
- Built regression models: Linear Regression, Random Forest, XGBoost (optional).
- Predicted premium pricing (CalculatedPremiumPerTerm) for all policies.
- Used SHAP for model interpretability to identify the most influential features.

## How to Run

1. **Install dependencies**

   ```
   python -m venv .venv
   source .venv/bin/activate
   pip install -r requirements.txt
   ```

2. **Pull data and models via DVC**

   ```
   dvc pull
   ```

3. **Run notebooks**

   - `eda.ipynb` → Exploratory data analysis
   - `feature_engineering.ipynb` → Feature creation and encoding
   - `modeling.ipynb` → Classification and regression models

## Model Outputs

- **Scaler:** `models/scaler_task4.pkl`
- **Claim probability model:** `models/rfc_claimprob.pkl`
- **Best severity model:** `models/best_severity_model_LinearRegression.pkl` (or RandomForest depending on evaluation)

## Future Work

- Integrate more advanced feature engineering (e.g., interaction terms, temporal features).
- Tune hyperparameters for better model performance.
- Extend to multi-period premium prediction and dynamic pricing updates.
- Deploy models for production-ready pricing and risk assessment.
