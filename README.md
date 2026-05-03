# RetailMind

Practicum project for MS Data Science at Regis University.

I built a pipeline that takes any retail sales CSV, figures out which columns are dates/sales/categories on its own, and runs forecasting + regression + anomaly detection without the user needing to rename anything.

## What's in here

- `project-1.ipynb` — the full notebook with all analysis, models, and results
- `walmart_Retail_Data.xlsx` — Walmart transaction data (8,399 rows, 2012-2015)
- `train.csv` / `store.csv` — Rossmann store sales data from Kaggle
- `requirements.txt` — pip dependencies

## What it does

1. **Schema mapping** — fuzzy matches column names so it works on any retail dataset
2. **Cleaning** — removes duplicates, clips outliers, imputes missing values
3. **Forecasting** — Prophet for 12+ months of data, Chronos for shorter datasets, Holt-Winters as comparison
4. **Regression** — compares LightGBM, XGBoost, ExtraTrees, RandomForest and picks the best by MAPE
5. **Anomaly detection** — Isolation Forest flags unusual sales days
6. **Recommendations** — tells you what categories to order more or less of based on momentum

## Results

- Walmart forecast MAPE: 12.65% (Holt-Winters)
- Walmart regression R²: 0.987 (RandomForest)
- Rossmann Prophet MAPE: 14.6%
- Schema mapping: 100% on Walmart, 94% on Rossmann

## How to run

```
pip install -r requirements.txt
jupyter notebook project-1.ipynb
```

The notebook also has a `RetailMind()` function at the end — you can call it on any sales CSV:

```python
RetailMind('your_file.csv')
```

## Datasets

- Walmart: https://www.kaggle.com/datasets/saadabdurrazzaq/walmart-retail-data
- Rossmann: https://www.kaggle.com/competitions/rossmann-store-sales

## Author

Sai Teja Sunku — Regis University, Denver CO
