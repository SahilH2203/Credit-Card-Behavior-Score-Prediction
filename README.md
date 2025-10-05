# Credit-Card-Behavior-Score-Prediction

# Credit Card Default Prediction

## 📌 Project Overview

Credit cards provide convenient short-term credit, but also carry the risk of customer default. This project develops a binary classification model to **predict whether a customer will default in the next billing cycle** based on historical behavioral and financial data.

By identifying high-risk customers early, financial institutions can reduce potential losses, improve decision-making, and strengthen credit risk management.

**Target variable:**

* `next_month_default = 1` → Customer defaults next month
* `next_month_default = 0` → No default

---

## 🎯 Objective

* Build a robust predictive model for credit card default.
* Prioritize identifying defaulters (high recall) over avoiding false positives.
* Ensure financial interpretability by engineering meaningful behavioral features.

---

## 📂 Repository Structure

```
project-name/
├── data/                # Train/test datasets (or sample data if large)
├── notebooks/           # Jupyter notebook(s) with full code
├── reports/             # Final project report and figures
├── requirements.txt     # Python dependencies
├── README.md            # Documentation
```

---

## 🔎 Data and Preprocessing

* **Dataset:** 25,247 rows × 27 columns (demographics, credit limit, bill amounts, payment history).
* Steps performed:

  * Dropped `Customer_ID` and duplicates.
  * Imputed missing `age` values with median.
  * Fixed invalid categorical values in `education` and `marriage`.
  * Log-transformed skewed features like `LIMIT_BAL`.

---

## 📊 Exploratory Data Analysis (EDA)

Key findings:

* Defaulters show **higher payment delays** (PAY_0 to PAY_4).
* **Lower credit limits** were associated with higher defaults.
* **Financial behavior indicators** such as repayment ratios and credit utilization strongly influenced default risk.

---

## 🛠️ Feature Engineering

Engineered features to capture financial behavior:

* `credit_utilization` → Bill amount ÷ Credit limit
* `delay_months` → Count of delayed months
* `repayment_ratio` → Total payments ÷ Total bills
* `avg_delay` → Average payment delay
* `delinquency_streak` → Longest streak of delayed months

---

## 🤖 Model Building

Models trained:

* Logistic Regression
* Random Forest
* LightGBM
* **XGBoost (best performer)**

**Class imbalance** handled using **SMOTE**.
**Threshold tuning** (0.11) emphasized recall and F2 score.

---

## 📈 Model Performance

| Model               | Precision (1) | Recall (1) | F1 Score | F2 Score | AUC  |
| ------------------- | ------------- | ---------- | -------- | -------- | ---- |
| Logistic Regression | 0.40          | 0.64       | 0.49     | 0.57     | –    |
| Random Forest       | 0.27          | 0.84       | 0.41     | 0.59     | 0.75 |
| LightGBM            | 0.33          | 0.76       | 0.46     | 0.61     | 0.77 |
| **XGBoost** (best)  | 0.28          | **0.86**   | 0.42     | **0.61** | 0.76 |

👉 **XGBoost** was selected as the final model due to its **high F2 score (0.607) and recall**, aligning with the business goal of minimizing losses from missed defaulters.

---

## 🚀 How to Run

1. Clone the repository:

   ```bash
   git clone https://github.com/username/project-name.git
   cd project-name
   ```

2. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. Open the Jupyter notebook:

   ```bash
   jupyter notebook notebooks/project_notebook.ipynb
   ```

---

## 📜 Conclusion

* Developed a predictive model for **credit card default risk**.
* Created **financially meaningful features** improving interpretability.
* Addressed **class imbalance** using SMOTE.
* Tuned classification thresholds to prioritize recall.
* **XGBoost emerged as the best model**, helping financial institutions proactively manage risk.

---

## 🛠️ Technologies Used

* Python (Pandas, NumPy, Matplotlib, Seaborn)
* Scikit-learn
* XGBoost, LightGBM, Random Forest
* Jupyter Notebook
* SMOTE (Imbalanced-learn)

---

## 📑 Report

The full detailed analysis, methodology, and findings are available in [`reports/final_report.pdf`](reports/final_report.pdf).

---
