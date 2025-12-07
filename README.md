Time Series Forecasting & Anomaly Detection – Air Quality Dataset
Course: Time Series Analysis

Project Overview

This project analyzes the UCI Air Quality dataset (2004–2005) to perform:
Time series exploration
Seasonal decomposition
Forecasting using SARIMA and Prophet
Anomaly detection using statistical & ML methods
Re-forecasting after anomaly cleaning

Dataset source:
UCI Machine Learning Repository – Air Quality Dataset
https://archive.ics.uci.edu/dataset/360/air+quality

Repository Structure
project-root/
└── data/
    ├── raw/
    │   └── AirQuality.csv
    └── processed/
        └── airquality_cleaned.parquet
└── notebooks/
    ├── 01_data_cleaning_exploration.ipynb
    ├── 02_decomposition.ipynb
    ├── 03_initial_forecasting.ipynb
    ├── 04_anomaly_detection.ipynb
    └── 05_reforecasting_after_cleaning.ipynb
└── slides/
└── README.md
└── requirements.txt

Environment Setup

Install dependencies:
pip install -r requirements.txt


Recommended content for requirements.txt:
pandas
numpy
matplotlib
seaborn
statsmodels
pmdarima
prophet
scikit-learn
scipy

Notebook 01 — Data Cleaning & Exploration

This notebook performs:
Dataset parsing (semicolon-separated CSV)
Fixing European decimal format
Converting -200 sensor failure values → NaN
Datetime creation and indexing
Frequency validation (dataset already hourly)
Missing value analysis (heatmap + percentages)
EDA visualizations
ADF stationarity test
ACF/PACF analysis
Saving cleaned dataset for further modeling

Output File:
data/processed/airquality_cleaned.parquet

Notebook 02 — Time Series Decomposition

This notebook will:
Apply classical decomposition
Apply STL decomposition
Extract trend, seasonality & residuals
Prepare data for forecasting

Notebook 03 — Initial Forecasting

This notebook will:
Split data into train/test
Build SARIMA model
Build Prophet model
Evaluate using RMSE/MAE
Compare SARIMA vs Prophet

Interpretion of results

Notebook 04 — Anomaly Detection

This notebook will include:
Statistical anomalies (Z-score, STL residuals, ARIMA residuals)
Machine learning anomalies (Isolation Forest, LOF)
Deep Learning (LSTM Autoencoder)

Visualization of anomalies on time series

Notebook 05 — Re-Forecasting After Cleaning

This notebook will:
Remove or impute anomalies
Refit SARIMA & Prophet
Compare performance before vs after anomaly cleaning

Project Deliverables
Cleaned dataset
Jupyter Notebooks (EDA → Forecasting → Anomaly Detection)
Slides (Summary of findings)
GitHub repository with full documentation
