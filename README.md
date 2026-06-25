# Medical Insurance Cost Prediction

## Project Overview

This project analyzes medical insurance charges and builds a regression workflow to estimate expected insurance cost. The target variable is `charges`, which is continuous, so this notebook uses multiple linear regression and regularized regression techniques.

The notebook is designed as a transparent analytics report. It explains the cost patterns in the data, compares regression approaches, checks residual behavior, and reviews subgroup error so the model is not treated as a black box.

## Problem Definition

Insurance providers and analysts often need to estimate expected charges based on customer attributes. A useful model should identify major cost drivers, provide interpretable predictions, and expose where prediction error is higher.

The key questions are:

- Which attributes are most associated with higher insurance charges?
- Is smoking status more important than age, BMI, or region?
- Are the numeric predictors affected by severe multicollinearity?
- Which regression approach performs best on the holdout set?
- Does model error differ across important customer groups?

## Dataset

The notebook uses the local CSV:

```text
data/raw/insurance.csv
```

The dataset contains:

- Age
- Sex
- BMI
- Number of children
- Smoking status
- Region
- Insurance charges

## What Is Covered

- Dataset loading from a local CSV
- Data quality and duplicate-row audit
- Descriptive statistics for customer attributes and charges
- Target distribution review for raw and log-transformed charges
- Exploratory visual analytics for age, BMI, smoking status, and risk groups
- Median-charge heatmap by age band and BMI category
- Statistical tests for numeric and categorical cost differences
- Correlation and VIF review for multicollinearity
- VADER sentiment applicability audit
- Multiple linear regression
- Ridge regression and Lasso regression
- Log-target Ridge regression for skewed charges
- MAE, RMSE, and R-squared evaluation
- Actual-vs-predicted and residual diagnostics
- Subgroup error review by smoker status and region
- Coefficient interpretation for model transparency

## Key Findings

- Insurance charges are strongly right-skewed, so mean values alone can be misleading.
- Smoking status is the clearest and strongest visible cost driver.
- Age and BMI are also important, especially when analyzed alongside smoking status.
- Sex and region are included for completeness, but they do not dominate the cost story in this dataset.
- The base numeric predictors do not show severe multicollinearity.
- Regression is appropriate here because the target is continuous.
- VADER sentiment analysis is not applicable because the dataset has no patient notes, reviews, or free-text fields.

## Solution Approach

The solution uses a regression-focused analytics pipeline:

1. Clean the data and remove duplicates.
2. Study the distribution of charges and apply a log target for comparison.
3. Explore cost patterns by smoking, age, BMI, and customer segment.
4. Use statistical tests to identify meaningful relationships.
5. Check multicollinearity using correlation and VIF.
6. Train multiple linear regression, Ridge, Lasso, and log-target Ridge models.
7. Compare models using MAE, RMSE, and R-squared.
8. Review residuals and subgroup errors to understand where predictions are weaker.

## Results Summary

The regression analysis confirms that smoking status is the dominant cost signal. Age and BMI provide additional predictive value, while regularized models help stabilize the regression workflow. The diagnostic plots show that high-cost cases are harder to predict, which is typical for skewed medical-cost data.

## Business Solution

This model can support insurance analytics by estimating expected charges and explaining major cost drivers. It can be useful for educational analysis, cost forecasting, and baseline underwriting research.

It should not be used as a production pricing system without:

- Richer historical claims data
- Regulatory and actuarial review
- Fairness and bias testing
- Out-of-time validation
- Strong governance around sensitive attributes

## Repository Structure

```text
data/raw/
  insurance.csv
notebooks/
  04_insurance_claim_prediction.ipynb
outputs/figures/
  Exported charts from the notebook
requirements.txt
README.md
```

## How to Run

```bash
pip install -r requirements.txt
jupyter notebook notebooks/04_insurance_claim_prediction.ipynb
```

## Conclusion

Medical insurance charges are driven most clearly by smoking status, with age and BMI adding important context. A transparent regression workflow is the right solution for this task because the outcome is continuous and the findings need to be explainable.
