# Medical Cost Prediction in the United States
## DSC 241 – Statistical Models | Winter 2026 Final Project
**Authors:** Dave Melkani & Eric Ness

---
###### This repository contains the final project for **DSC 241: Statistical Models (Winter 2026)**. The objective is to effectively predict individual medical insurance charges from demographic and health attributes, and to interpret the results using a progression of statistical models.
---
## Problem Statement
> *How do we effectively predict individual medical insurance charges from demographics and health attributes, and how do we interpret these results?*
---
## Dataset
The dataset contains **1,338 data points** (1,337 after removing one duplicate) for health insurance policyholders across **7 variables** with three measurement types:
| Type | Variables |
|------|-----------|
| **Continuous** | Age, BMI, Charges |
| **Binary** | Sex (`female`: 0, `male`: 1), Smoker (`no`: 0, `yes`: 1) |
| **Categorical** | Region (`northeast`: 0, `northwest`: 1, `southeast`: 2, `southwest`: 3), Children |
---
## Modeling Approach
Models were applied sequentially, with each successive model relaxing one or more structural assumptions — representing a clear tradeoff between **interpretability** and **flexibility**:
1. **Baseline OLS** — Linear regression on raw features as a transparent baseline
2. **Log-Linear OLS** — Log-transforms charges and adds interaction terms (e.g., `smoker×BMI`, `smoker×obese`) to address skewness and capture nonlinear effects
3. **Linear Mixed-Effects (LME)** — Treats region as a random intercept to account for geographic heterogeneity via partial pooling
4. **Random Forest (Ensemble Learning)** — Non-parametric, fully flexible ensemble that automatically captures high-order interactions
---
## Results
- **Baseline OLS** predictions were off by an average of ~42% of actual charges (MAPE = 42.24%)
- Each successive model improved predictive accuracy over the last
- **Random Forest** (tuned to 44 trees via loss curve) delivered the best overall performance (R² = 0.897, RMSE = $4,348)
- The **smoker–BMI interaction** was the single most important feature (28.4% importance), with smoking and obesity together compounding costs far beyond what either factor does alone
- A bucket evaluation classified data into cost percentile ranges (Low: 0–50th, Mid: 51–80th, High: 81–100th) — RF showed high classification accuracy across all buckets, none falling below 85%
---
## Conclusions
- The progression from OLS → Log-Linear → LME → Random Forest consistently improved predictive performance
- Relaxing structural assumptions comes at the cost of interpretability
- **Smoking status** is the dominant predictor, with smokers incurring roughly four times the charges of non-smokers; this effect is significantly amplified in combination with obesity
- Age contributes a consistent moderate positive effect, while sex, region, and number of children are statistically present but practically minor
---
## Future Work
- Incorporate additional features such as pre-existing conditions and claims history to reduce prediction error, especially for high-cost outliers
- Apply one-hot encoding for the region variable (rather than ordinal encoding) to remove the implicit false ranking
- Use a consistent train/test split across all models to enable fair out-of-sample comparison
---
## Goal
To demonstrate rigorous statistical reasoning, clear communication, and proper application of statistical modeling techniques in a real-world medical cost prediction context.
---

###### The data for this project comes from https://www.kaggle.com/datasets/mirichoi0218/insurance/data
