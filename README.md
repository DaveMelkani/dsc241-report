# Medical Cost Prediction in the United States
## DSC 241 – Statistical Models | Winter 2026 Final Project

**Authors:** Dave Melkani & Eric Ness
This repository contains the final project for **DSC 241: Statistical Models (Winter 2026)**. The objective is to effectively predict individual medical insurance charges from demographic and health attributes, and to interpret the results using a progression of statistical models.

---

## Problem Statement

> *How do we effectively predict individual medical insurance charges from demographics and health attributes, and how do we interpret these results?*

---

## Dataset

The dataset contains **1,338 data points** for health insurance policyholders across **7 variables** with three measurement types:

| Type | Variables |
|------|-----------|
| **Continuous** | Age, BMI, Charges |
| **Binary** | Sex (`female`: 0, `male`: 1), Smoker (`no`: 0, `yes`: 1) |
| **Categorical** | Region (`northeast`: 0, `northwest`: 1, `southeast`: 2, `southwest`: 3), Children |

---

## Modeling Approach

Models were applied sequentially, with each successive model relaxing one or more structural assumptions — representing a clear tradeoff between **interpretability** and **flexibility**:

1. **Baseline OLS** — Linear regression as a baseline
2. **Log-Linear OLS** — Addresses skewness in the response variable
3. **Linear Mixed-Effects (LME)** — Accounts for grouped/hierarchical structure
4. **Random Forest (Ensemble Learning)** — Non-parametric, fully flexible

---

## Results

- **Baseline OLS** predictions were off by an average of ~42 cents on every dollar of charges
- Each successive model improved predictive accuracy over the last
- **Random Forest** (tuned to 75 trees via loss function) delivered the best overall performance
- **Smoking status** and **BMI** emerged as the dominant cost drivers
- A bucket evaluation classified data into cost percentile ranges (Low: 0–50th, Mid: 51–80th, High: 81–100th) — RF showed very few misclassifications, with minor underestimation at high extremes (expected behavior)

---

## Conclusions

- The progression from OLS → Log-Linear → LME → Random Forest consistently improved predictive performance
- Relaxing structural assumptions comes at the cost of interpretability
- Smoking status and BMI are the dominant predictors of medical insurance charges

---

## Future Work

Incorporating additional features — such as pre-existing conditions and claims history — could further reduce prediction error, especially for high-cost outliers.

---

## Deliverables

- Final presentation slides
- Reproducible analysis code

---

## Goal

To demonstrate rigorous statistical reasoning, clear communication, and proper application of statistical modeling techniques in a real-world medical cost prediction context.