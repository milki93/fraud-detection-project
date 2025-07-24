# 🛡️ Fraud Detection System for E-commerce and Banking

This repository presents an end-to-end machine learning project focused on detecting fraudulent transactions in e-commerce and banking environments. The goal is to create accurate and interpretable models to flag fraudulent activity in real-world financial datasets.

---

## 🌐 Project Objective

Fraudulent transactions pose a significant threat to e-commerce and banking platforms. This project aims to:

- Detect fraud in **e-commerce transactions** using behavioral, device, and geolocation features.
- Detect fraud in **banking (credit card)** transactions using anonymized transactional features.
- Engineer meaningful features from timestamps and user activity.
- Address **severe class imbalance** using techniques like **SMOTE**.
- Build and compare interpretable and powerful models.
- Use **SHAP** for model explainability to understand feature importance.

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

## 📊 Data Sources

- Fraud_Data.csv: E-commerce transactions with timestamp, user, device, browser, and fraud labels.

- creditcard.csv: Bank credit card transactions with anonymized PCA features.

- IpAddress_to_Country.csv: IP ranges mapped to country codes for geolocation enrichment.

---

## 🎯 Model Development

- **Baseline Model:** Logistic Regression
- **Advanced Model:** Random Forest or XGBoost

---

## Evaluation Metrics

- F1-Score
- Precision-Recall AUC (AUC-PR)
- Confusion Matrix

---

## 🔮 Explainability with SHAP

To build trust and provide insights into model predictions, SHAP was used to:

- Generate global feature importance plots
- Visualize local explanations for individual predictions
