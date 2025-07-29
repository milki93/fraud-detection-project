# 🛡️ Fraud Detection System for E-commerce and Banking

This project addresses the challenge of detecting fraudulent financial transactions using supervised machine learning and interpretable AI techniques. We combined multiple datasets (e-commerce, credit card, IP address geolocation) to build predictive models and explain their decisions using SHAP.

---

## 📊 Data Sources

- **Fraud_Data.csv** – Online transaction logs with timestamps, device/browser info, and fraud labels.
- **creditcard.csv** – PCA-anonymized bank card transactions labeled as fraud or not.
- **IpAddress_to_Country.csv** – Maps IP ranges to country codes, used for geolocation enrichment.

---

# Installation & Setup

### Clone the repository:
```bash
git clone https://github.com/milki93/fraud-detection-project.git
cd fraud-detection-project
```

### Install project dependencies:

```bash
pip install -r requirements.txt
```

---

## 🧹 Data Preparation & Feature Engineering

The following steps were applied to clean and enrich the data:

- Converted timestamp columns to datetime objects
- Engineered time-based features:
  - `hour_of_day`, `day_of_week`
  - `time_since_signup` in seconds
- Mapped IP addresses to countries using external IP range data
- Aggregated transactions per user to derive:
  - `txn_count` (number of transactions per user)
- One-hot encoded categorical variables
- Imbalanced data handled using **SMOTE** to balance the number of fraud and non-fraud samples

---

## 🎯 Model Development
### Models Trained

- **Logistic Regression** – Used as a baseline model
- **Random Forest** – Achieved the best performance 
- **XGBoost** – Balanced performance and interpretability,

### Evaluation Metrics

- **F1 Score**
- **Precision-Recall AUC**
- **Confusion Matrix**

SMOTE resampling was applied before training to ensure the models had enough fraudulent examples to learn from.

---

## 🔮 Model Explainability with SHAP

To interpret and validate the decisions of our best-performing models (XGBoost and Logistic Regression), we applied SHAP (Shapley Additive exPlanations).

### Global Explanation – SHAP Summary Plot

- Top predictors across models included:
  - `time_since_signup`: Short durations are often suspicious
  - `txn_count`: High frequency of purchases in a short time can indicate fraud
  - `purchase_value` and `country_CN`: Specific regions and high amounts showed higher SHAP impact
- The SHAP beeswarm plots visualized how each feature contributes to predictions across all samples.

### Local Explanation – SHAP Waterfall Plot

- For individual predictions, waterfall plots showed:
  - Whether each feature pushed the prediction toward fraud or not
  - Feature values that triggered high fraud risk (e.g., low signup-to-purchase time)

SHAP CSVs were also saved to allow deeper numerical interpretation of both global and local drivers.

---

## 📈 Results Summary

| Model              | F1 Score | PR-AUC | Notes                                  |
|-------------------|----------|--------|----------------------------------------|
| Logistic Regression | Medium   | Medium | Good baseline, interpretable           |
| Random Forest      | High     | High   | Best performance but not SHAP-compatible |
| XGBoost            | High     | High   | Best balance of performance + SHAP     |

---


