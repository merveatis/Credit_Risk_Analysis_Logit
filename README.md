# Credit_Risk_Analysis_Logit
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/merveatis/Credit_Risk_Analysis_Logit/blob/main/Credit_Risk_Analysis_Logit.ipynb)

# Credit Risk Analysis with Logistic Regression

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/merveatis/Credit_Risk_Analysis_Logit/blob/main/Credit_Risk_Analysis_Logit.ipynb)

This project analyzes **credit risk** using a binary logistic regression model built in Python.  
The goal is to identify how different financial and demographic factors affect the probability of credit approval.

---

## Project Overview

- **Goal:** Determine which customer attributes influence creditworthiness.
- **Dataset:** German Credit Data (800 observations, 26 predictors)
- **Methodology:** Logistic Regression (`statsmodels`)
- **Key Steps:**
  1. Data cleaning and preprocessing  
  2. Mapping symbolic categorical codes (e.g., A32, A34) to descriptive labels  
  3. Dummy variable encoding  
  4. Testing associations between categorical features and the target using **Chi-Square**  
  5. Assessing the strength of relationships with **Cramer’s V** to decide which variables to retain  
  6. Model building with `statsmodels.Logit`  
  7. Statistical significance testing (p-values, LR test)  
  8. Model evaluation (Accuracy, AUC, Confusion Matrix)  
  9. Interpretation of coefficients and odds ratios  

---

## Data Description

The original dataset contained symbolic categorical variables (e.g., A11, A32, A65).  
To make the model interpretable, these codes were manually mapped to descriptive labels before dummy encoding.

| Original Code | Variable | Meaning |
|----------------|-----------|----------|
| A11 | checking_account | little or no balance |
| A12 | checking_account | moderate balance |
| A13 | checking_account | high balance |
| A14 | checking_account | no checking account |
| A30 | credit_history | no credits taken |
| A31 | credit_history | all credits paid back |
| A32 | credit_history | existing credits paid |
| A33 | credit_history | delayed payments |
| A34 | credit_history | critical account / other existing credits |
| A61 | savings_account | little savings |
| A62 | savings_account | moderate savings |
| A63 | savings_account | 500+ savings |
| A64 | savings_account | 1000+ savings |
| A65 | savings_account | unknown savings |

These mappings improve the interpretability of model coefficients and results.

---

## Model Results

| Metric | Value | Interpretation |
|---------|--------|----------------|
| **Pseudo R²** | 0.1999 | Acceptable explanatory power for logistic models |
| **LLR p-value** | < 0.001 | Model is statistically significant ✅ |
| **AUC Score** | 0.80 | Strong ability to distinguish between classes |
| **Accuracy** | 0.74 | Model correctly predicts 74% of outcomes |

### Significant Variables (p < 0.05)
- Duration  
- Credit amount  
- Installment rate  
- Age  
- Checking account (>0, no account)  
- Credit history (critical account/other loans)  
- Savings account (unknown)  
- Installment plans (none)  
- Housing (own)

---

## Interpretation Highlights

- Customers **with a positive checking account balance** are more likely to get credit approval.  
- Those **with no checking account** have a significantly lower chance.  
- **Older customers** tend to have slightly lower approval probability.  
- **Longer duration and higher installment rate** increase approval odds slightly.  
- Unclear or missing savings information negatively impacts approval.  

---

## Technical Details

| Library | Purpose |
|----------|----------|
| `pandas`, `numpy` | Data manipulation |
| `statsmodels` | Econometric modeling & p-value tests |
| `matplotlib` | Visualization |
| `scikit-learn` | Train/test split & metrics |

---

## Next Steps

- Compare this model with **Random Forest** or **XGBoost**  
- Try `class_weight='balanced'` to address class imbalance  
- Visualize results in Power BI or Tableau (e.g., ROC curve, coefficient plot)  

---

##  Author
**Merve Atiş**  
Marmara University – Department of Econometrics  
[GitHub](https://github.com/merveatis)
