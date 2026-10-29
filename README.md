# Customer Churn – Data Cleaning

Cleaned a raw customer churn dataset (605 rows) into an analysis-ready file (600 rows) using Python and Pandas.

## Files
- `data_cleaning.ipynb` – Jupyter Notebook with the full cleaning workflow and documented decisions
- `customer_churn_clean.csv` – cleaned dataset

## Cleaning decisions

| Issue | Rows | Decision | Reason |
|---|---|---|---|
| Exact duplicate records | 5 | Dropped | CustomerID must be unique |
| `TotalChargesINR` = "unknown" | 10 | Filled with MonthlyCharges × Tenure (0 if tenure is 0) | Actual vs. estimated ratio is about 0.98 on all complete rows |
| `MonthlyChargesINR` outliers | 7 | Divided by 12 and flagged | Annual amounts entered as monthly; ÷12 matches the plan price range |
| `Region` missing | 13 | Filled with "Unknown" | No reliable way to infer it; avoids biasing regional analysis |
| Column names and data types | all | snake_case names, numeric types fixed, `auto_pay` as True/False, added `churn_flag` (1 = churned) | Consistency for analysis |

## Result
- 605 rows → 600 rows
- 0 missing values, 0 duplicates
- All validation checks pass

## Tools
Python, Pandas, NumPy, Jupyter Notebook
