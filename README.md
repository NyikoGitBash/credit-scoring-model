# Credit Scoring Model

## Overview
This project implements a credit scoring model to assess the risk associated with lending to customers. The model estimates the Expected Loss (EL) using the formula:

EL = PD x LGD x EAD

where:
- **Probability of Default (PD)** is estimated using a Logistic Regression model.
- **Loss Given Default (LGD)** and **Exposure at Default (EAD)** are modeled using Beta distributions.
- Continuous features are grouped using Weight of Evidence (WOE) encoding.

## Methodology
### 1. Probability of Default (PD)
- Uses a **Logistic Regression** model to estimate the likelihood of a customer defaulting.
- Predictor variables are transformed using **Weight of Evidence (WOE)** to improve interpretability and model performance.
- Model performance is evaluated using **AUC-ROC** and **KS statistic**.

### 2. Loss Given Default (LGD)
- Modeled using a **Beta distribution** since LGD values range between 0 and 1.
- Maximum Likelihood Estimation (MLE) is used to estimate distribution parameters.

### 3. Exposure at Default (EAD)
- Also modeled using a **Beta distribution**, assuming EAD is a fraction of the total credit limit.
- Distribution parameters are estimated using historical data.

## Feature Engineering
- **Categorical Variables:** Encoded using WOE.
- **Continuous Variables:** Binned and transformed using WOE.
- **Missing Values:** Handled using mean/mode imputation or separate missing value indicators.

## Model Training & Evaluation
1. **Train-Test Split**: Data is split into training (70%) and testing (30%) sets.
2. **Performance Metrics**:
   - **PD Model**: AUC-ROC, KS Statistic, Brier Score.
   - **LGD & EAD Models**: Log-likelihood, RMSE, and calibration plots.
3. **Validation**: Out-of-Time (OOT) validation ensures robustness.

## Installation & Usage
### Prerequisites
- Python 3.8+
- Libraries: `pandas`, `numpy`, `scikit-learn`, `scipy`, `statsmodels`, `matplotlib`

## Future Enhancements
- Implement XGBoost for PD modeling.
- Extend EAD modeling with additional risk factors.
- Deploy a real-time scoring API.

## Authors
- **Nyiko**

## License
This project is licensed under the MIT License.

