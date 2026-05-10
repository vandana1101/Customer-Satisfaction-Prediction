# Customer Support Ticket Analysis
### Predicting Customer Satisfaction Rating with Machine Learning

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![LightGBM](https://img.shields.io/badge/LightGBM-95%25_Accuracy-brightgreen)
![Status](https://img.shields.io/badge/Status-Complete-success)

---

## Overview

This project analyzes **8,000 customer support tickets** to predict **Customer Satisfaction Rating (1–5)** using operational metrics such as resolution time, first response time, agent quality, and SLA compliance.

The best model — **LightGBM** — achieves **~95% test accuracy** and **~96% 5-fold cross-validation accuracy**, demonstrating that satisfaction can be reliably predicted from ticket handling behavior alone.

---

## Repository Structure

```
customer-support-satisfaction/
│
├── customerSupport_Tickets.csv                            # Dataset (8,000 tickets, 18 features)
├── Customer_Satisfaction_Prediction_Model.ipynb           # Main analysis notebook
└── README.md                                              # This file
```

---

## Dataset

| Property | Value |
|---|---|
| Rows | 8,000 |
| Features | 17 |
| Target | Customer Satisfaction Rating (1–5) |
| Time period | Jan 2021 – Dec 2023 |

### Feature Descriptions

| Feature | Type | Description |
|---|---|---|
| Ticket ID | int | Unique ticket identifier |
| Customer Age | int | Age of the customer (18–69) |
| Customer Gender | categorical | Male / Female / Other |
| Product Purchased | categorical | Product associated with the ticket |
| Date of Purchase | date | Purchase date (DD-MM-YYYY) |
| Ticket Type | categorical | Billing / Technical / Refund / Product / Cancellation |
| Ticket Priority | categorical | Low / Medium / High / Critical |
| Ticket Channel | categorical | Email / Phone / Chat / Social media |
| Assigned Agent | categorical | Agent ID handling the ticket |
| Agent Quality Score | float | Historical quality score of the agent (1–5) |
| First Response Time (hrs) | float | Hours until first agent response |
| Resolution Time (hrs) | float | Total hours from open to close |
| Num Interactions | int | Number of back-and-forth exchanges |
| SLA Breached | binary | 1 if resolution exceeded priority SLA target |
| Reopened | binary | 1 if the ticket was reopened after closing |
| Resolved First Contact | binary | 1 if resolved in a single interaction |
| Purchase Days Ago | int | Days between purchase and ticket creation |
| **Customer Satisfaction Rating** | **int (1–5)** | **Target variable** |

---

## Methodology

### Feature Engineering
- **Label encoding** of all categorical columns
- **Frequency encoding** — how common each category is in the dataset
- **Target encoding** — mean satisfaction per category (5-fold CV to prevent leakage)
- **Log transforms** on right-skewed time features (`Resolution Time`, `First Response Time`)
- **Threshold indicators** — binary flags for key operational thresholds (e.g. resolved under 4 hrs, response under 2 hrs)
- **Calendar features** from purchase date (month, day of week, year)

### Models Trained
| Model | Test Accuracy |
|---|---|
| Random Forest | ~95% |
| Extra Trees | ~95% |
| XGBoost | ~95% |
| Voting Ensemble | ~95% |
| **LightGBM** | **~95%** |
| **LightGBM 5-Fold CV** | **~96% ± 0.4%** |

---

## Key Findings

> Satisfaction is driven almost entirely by **how the ticket is handled**, not by who the customer is.

1. **Resolution Time** is the strongest predictor — tickets resolved in under 4 hours consistently receive 4–5 star ratings.
2. **SLA Breaches** are the most reliable signal for low ratings; missing the priority target strongly predicts dissatisfaction.
3. **First Response Time** under 30 minutes significantly boosts satisfaction across all ticket types.
4. **Agent Quality Score** has a measurable and consistent effect — better agents produce better outcomes.
5. **Reopened tickets** almost always result in 1–2 star ratings, regardless of how quickly the issue is eventually resolved.
6. **Demographics** (age, gender, product purchased) have negligible predictive power, confirming that satisfaction is a function of service quality, not customer profile.

---

## How to Run

1. Clone the repository
   ```bash
   git clone https://github.com/<your-username>/customer-support-satisfaction.git
   cd customer-support-satisfaction
   ```

2. Install dependencies
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn lightgbm xgboost
   ```

3. Launch the notebook
   ```bash
   jupyter notebook Project02_GitHub.ipynb
   ```

---

## Requirements

```
pandas
numpy
matplotlib
seaborn
scikit-learn
lightgbm
xgboost
jupyter
```

---

## Results

```
LightGBM 5-Fold CV Accuracy : 96.0% ± 0.4%
LightGBM Test Accuracy      : 95.3%

Classification Report (LightGBM):
              precision  recall  f1-score
  Rating 1       0.95    0.97      0.96
  Rating 2       0.95    0.96      0.96
  Rating 3       0.95    0.96      0.96
  Rating 4       0.94    0.93      0.93
  Rating 5       1.00    0.86      0.93
  accuracy                         0.95
```
