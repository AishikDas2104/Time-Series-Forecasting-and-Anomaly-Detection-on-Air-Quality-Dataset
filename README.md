# Time Series Forecasting and Anomaly Detection on Air Quality Data

## Course
Time Series Analysis (Master’s in Artificial Intelligence)

## Project Overview
This project focuses on end-to-end time series analysis using an air quality dataset. The workflow includes data cleaning, exploratory analysis, decomposition, forecasting, anomaly detection, and re-forecasting after anomaly handling.

The objective is to understand temporal patterns in air quality data, build forecasting models, detect anomalies caused by sensor failures or extreme events, and evaluate how anomaly handling impacts forecasting performance.

The project strictly follows the course requirements and emphasizes reproducibility, interpretability, and real-world applicability.

---

## Dataset
**Air Quality Dataset (UCI Machine Learning Repository)**  
- Time span: March 2004 – April 2005  
- Frequency: Hourly  
- Variables:  
  - Gas concentrations (CO, NO₂, NOx, Benzene)  
  - Sensor measurements  
  - Temperature, Relative Humidity, Absolute Humidity  

Dataset source:  
https://archive.ics.uci.edu/dataset/360/air+quality

---

## Repository Structure
project-root/
│
├── data/
│ ├── raw/
│ │ └── AirQuality.csv
│ └── processed/
│ ├── airquality_cleaned.parquet
│ ├── airquality_with_stl.parquet
│ └── model_comparison.csv
│
├── notebooks/
│ ├── 01_data_cleaning_exploration.ipynb
│ ├── 02_decomposition.ipynb
│ ├── 03_initial_forecasting.ipynb
│ ├── 04_anomaly_detection.ipynb
│ └── 05_reforecasting_after_cleaning.ipynb
│
├── README.md
└── requirements.txt

---

## Methodology

### 1. Data Cleaning and Exploration
- Parsed semicolon-separated raw data with European decimal format.
- Converted sentinel values (-200) to missing values.
- Created a unified datetime index.
- Verified data frequency (already hourly).
- Conducted missing value analysis and exploratory visualizations.
- Performed stationarity tests (ADF) and ACF/PACF analysis.

### 2. Decomposition
- Applied classical seasonal decomposition.
- Applied STL decomposition to robustly extract trend, seasonality, and residuals.
- Stored STL residuals for anomaly detection.

### 3. Forecasting
- Built an ARIMA model using seasonal differencing (lag = 24) to handle daily seasonality efficiently.
- Built a Prophet model with explicit seasonality handling.
- Evaluated models using RMSE and MAE.
- Compared models to highlight trade-offs between short-term accuracy and robustness to large deviations.

### 4. Anomaly Detection
- Detected anomalies using:
  - Statistical method: Z-score on STL residuals
  - Machine Learning method: Isolation Forest
- Combined multiple detectors to improve anomaly reliability.

### 5. Re-Forecasting After Cleaning
- Removed detected anomalies from the time series.
- Re-trained forecasting models.
- Compared forecasting performance before and after anomaly handling.

---

## Key Findings
- The dataset exhibits strong daily seasonality and autocorrelation.
- ARIMA with seasonal differencing provides better average accuracy (lower MAE).
- Prophet is more robust to large deviations (lower RMSE).
- Anomaly removal improves forecasting stability and reduces extreme errors.
- Data quality has a significant impact on forecasting performance.

---

## How to Run the Project

1. Clone the repository:
   git clone <repository-url>
   cd project-root
   
2. Install dependencies:
   pip install -r requirements.txt

3. Run notebooks in the following order:
   01_data_cleaning_exploration.ipynb
   02_decomposition.ipynb
   03_initial_forecasting.ipynb
   04_anomaly_detection.ipynb
   05_reforecasting_after_cleaning.ipynb
