---
noteId: "e00617d070a011f19ec49d9bd6d884a1"
tags: []

---

# Insurance Claim Amount Prediction and Regression Analytics

This repository contains a completed analytics notebook for predicting medical insurance charges. This task is treated as a regression problem because the target variable, `charges`, is continuous.

## What This Notebook Covers

- Dataset loading from a local CSV
- Data quality and duplicate-row audit
- Descriptive statistics for charges and customer attributes
- Exploratory visual analytics for charges, age, BMI, smoking status, and risk segments
- Statistical tests for numeric and categorical cost differences
- Correlation and VIF review for multicollinearity
- VADER sentiment applicability audit
- Multiple linear regression
- Ridge and Lasso regularization
- Log-target Ridge regression for skewed charges
- MAE, RMSE, and R-squared evaluation
- Residual diagnostics and subgroup error review
- Coefficient interpretation for model transparency

## Main Result

Smoking status is the clearest driver of insurance charges in this dataset. Age and BMI are also important, but their cost patterns are much easier to understand when smoking status is shown separately.

## Important Note

This notebook is a transparent baseline for analytics practice, not a production insurance-pricing model. Real insurance modeling would require richer claims history, regulatory review, fairness testing, and out-of-time validation.

## How to Run

```bash
pip install -r requirements.txt
jupyter notebook notebooks/04_insurance_claim_prediction.ipynb
```

The notebook expects this file:

```text
data/raw/insurance.csv
```

Exported charts are saved in `outputs/figures/`.
