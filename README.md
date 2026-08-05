# 🛒 Store Sales Forecasting using LightGBM

A complete end-to-end machine learning pipeline for forecasting daily retail sales using the Corporación Favorita Grocery Sales dataset.

This project demonstrates a production-style time series forecasting workflow, including data preparation, exploratory data analysis, feature engineering, model development, recursive forecasting, and competition submission.

---

## 📌 Project Overview

Retail sales forecasting is challenging due to seasonality, promotions, holidays, changing customer demand, and external economic factors.

This project builds a recursive forecasting pipeline using **LightGBM** and extensive time-series feature engineering to predict daily sales for every store-product combination.

Key highlights:

- End-to-end forecasting pipeline
- Chronological train-validation split
- Recursive multi-step forecasting
- Advanced feature engineering
- Business rule based post-processing
- Kaggle competition submission

---

## 📂 Project Structure

```
Store-Sales-Forecasting/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│   ├── 01_data_preparation.ipynb
│   ├── 02_exploratory_data_analysis.ipynb
│   ├── 03_feature_engineering.ipynb
│   ├── 04_modeling.ipynb
│   └── 05_recursive_forecasting.ipynb
│
├── outputs/
│   ├── figures/
│   ├── reports/
│   └── submission/
│
├── src/
│
├── requirements.txt
├── .gitignore
└── README.md
```

---

# 📖 Workflow

## 1. Data Preparation

- Loaded all competition datasets
- Restored missing calendar dates
- Interpolated missing oil prices
- Cleaned transaction data
- Prepared datasets for downstream analysis

---

## 2. Exploratory Data Analysis

Performed detailed analysis of:

- Sales distribution
- Time series behaviour
- Seasonality
- Trend decomposition (STL)
- Promotions
- Transactions
- Oil prices
- Holiday effects
- Store characteristics
- Correlation analysis

---

## 3. Feature Engineering

Created rich time-series features including:

### Calendar Features

- Day of week
- Month
- Week of year
- Day of year
- Weekend flag

### Cyclical Encoding

- Sine/Cosine transformations

### Lag Features

- 1–7 day lags
- Weekly lags
- Monthly lags
- Annual lags

### Rolling Statistics

- 7-day
- 14-day
- 28-day
- 364-day moving averages

### External Features

- Promotions
- Oil prices
- Store metadata
- Transactions
- Holiday indicators

---

## 4. Model Development

Model:

- LightGBM Regressor

Validation strategy:

- Chronological train-validation split

Evaluation metric:

- Root Mean Squared Logarithmic Error (RMSLE)

Hyperparameters were optimized using early stopping before training the final production models.

---

## 5. Recursive Forecasting

Unlike one-step prediction, future lag values are unavailable during inference.

A recursive forecasting pipeline was developed that:

- predicts one day at a time
- updates lag features using previous predictions
- updates rolling averages
- applies business rules (Zero Rule)
- generates forecasts for the complete competition horizon

---

# 📊 Results

### Validation

Evaluation Metric:

- Kaggle Score: 0.39172

Best validation approach:

- Two production models trained on recent historical periods
- Recursive forecasting validation
- Zero-rule post processing

### Competition Output

- Recursive multi-step forecasting
- Kaggle submission generated successfully

---

# 🛠 Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-Learn
- LightGBM
- Statsmodels

---

# 🚀 Running the Project

Clone the repository

```bash
git clone https://github.com/yourusername/Store-Sales-Forecasting.git
```

Install dependencies

```bash
pip install -r requirements.txt
```

Run the notebooks sequentially:

```
01_data_preparation.ipynb

↓

02_exploratory_data_analysis.ipynb

↓

03_feature_engineering.ipynb

↓

04_modeling.ipynb

↓

05_recursive_forecasting.ipynb
```

---

# 📈 Future Improvements

Potential extensions include:

- Hyperparameter optimization using Optuna
- Feature importance analysis with SHAP
- Model stacking and ensembling
- TimeSeries cross-validation
- Experiment tracking using MLflow
- Modular Python package under `src/`

---

# 📚 Dataset

Corporación Favorita Grocery Sales Forecasting

https://www.kaggle.com/competitions/store-sales-time-series-forecasting

---

## 👤 Author

**Navdeeshwar Suman**

MBA Candidate | IIM Tiruchirappalli

B.Tech | NIT Hamirpur

Interested in Machine Learning, Data Science, Analytics and Product Management.