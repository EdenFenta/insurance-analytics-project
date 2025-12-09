# Dataset Preparation for Machine Learning

## Input Data

The dataset used in this task originates from:

- `data/df_model_task1.csv`

This file was produced after completing data cleaning, handling missing values, and conducting exploratory analysis in Task 1 and Task 2.

### Key Columns Relevant to Task 3

- **TotalPremium**
- **TotalClaims**
- **SumInsured**
- **CalculatedPremiumPerTerm**
- **RegistrationYear**
- **VehicleType**
- **make**
- **Gender**
- **Province**
- **Vehicle Characteristics** (Cylinders, NumberOfDoors, CustomValueEstimate)

## Target Variable Engineering

To identify whether a policyholder submitted at least one claim, a binary target variable was created:

- **ClaimFlag = 1** → customer has ≥1 claim
- **ClaimFlag = 0** → customer has no claims

This helps the ML model distinguish low-risk and high-risk policyholders, which is the core business objective for targeted premium reduction.

## Feature Selection

The following features were selected as inputs for modeling due to relevance, stability, and predictive potential:

### Category Variables
- **Vehicle Characteristics**: SumInsured, CalculatedPremiumPerTerm, RegistrationYear, Cylinders, NumberOfDoors, CustomValueEstimate
- **Customer & Policy Indicators**: Province, Gender, VehicleType, make
- **Financial Variables**: TotalPremium

### Target Variable
- ClaimFlag

Text-heavy or high-cardinality fields (e.g., raw descriptions) were excluded to avoid noise and unnecessary dimensionality.

## Categorical Encoding

Categorical fields (Province, Gender, VehicleType, make) were converted using:

- One-Hot Encoding with `drop_first=True`

This prevents multicollinearity and prepares the dataset for algorithms that only accept numerical input.

## Output Dataset

The final ML-ready dataset was saved to:

- `data/processed/ml_dataset.csv`

This file contains:

- Only numerical fields
- Encoded categorical features
- The engineered ClaimFlag target variable
- No missing values
- All features aligned for model training

## DVC Tracking

The final dataset was added to Data Version Control (DVC) for reproducibility:

```
dvc add data/processed/ml_dataset.csv
```

This ensures that:

- The dataset version is fixed
- Changes are traceable
- Model training in Task 4 can fully reproduce results