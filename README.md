# Autoregressive-and-Moving-Average-Time-Series-Model
## 🌟 Overview

This project is a **complete time series analysis and modeling pipeline** developed in Python. It analyzes IoT sensor readings collected hourly over a year to uncover trends, evaluate stationarity, build forecasting models, and benchmark them against synthetic baselines.

## 🎯 Objectives

- Explore patterns in time series data.
- Test for stationarity and seasonality.
- Decompose the series into interpretable components.
- Compare with white noise and random walk baselines.
- Fit statistical models (Moving Average and AutoRegression).
- Evaluate model accuracy with quantitative metrics.

## 🗂️ Repository Structure

```
src/
├── Engine.py                  # Orchestrator script
└── ML_Pipeline/
    ├── Preprocess.py          # Data cleaning and resampling
    ├── EDA.py                 # Decomposition plots
    ├── Stationarity.py        # ADF & KPSS tests
    ├── acf.py                 # Autocorrelation visualization
    ├── pacf.py                # Partial autocorrelation visualization
    ├── WhiteNoise.py          # White noise generator
    ├── RandomWalk.py          # Random walk generator
    ├── MA_model.py            # Moving Average model fitting
    ├── Autoregressor.py       # AutoRegression model fitting
    └── autocovariance.py      # Covariance matrix computation

notebooks/
└── TS workbook.ipynb          # Interactive exploration notebook

output/
├── acf.png
├── pacf.png
├── components.png
├── IOT_Sensor_Reading_plot.png
├── Diff_IOT_Sensor_Reading_plot.png
├── white_noise.png
├── random_walk.png
├── MA_Model.png
├── AR_Model.png
└── log.txt                    # Text logs with all statistical results
```

## 🔍 Data Description

- **File:** `Data-Chillers.csv`
- **Frequency:** Hourly readings
- **Date Range:** January 2017 – December 2017
- **Columns:**
  - `time` (timestamps)
  - `IOT_Sensor_Reading` (target variable)
  - `Error_Present`
  - `Sensor_2`
  - `Sensor_Value`

## 🛠️ Workflow and Procedures

Below is a **step-by-step description** of everything this project does:

### 1️⃣ Data Loading and Initial Exploration

- Load the CSV using `pandas`.
- Inspect data types, null values, date ranges, and basic statistics.
- Visualize raw readings.

### 2️⃣ Preprocessing

- Convert `time` to datetime.
- Remove unneeded columns.
- Resample to hourly frequency.
- Fill missing values (forward fill for readings).
- Reset index.

### 3️⃣ Exploratory Data Analysis

- Decompose the series into trend, seasonality, and residuals.
- **Plot:** `components.png`

### 4️⃣ Stationarity Testing

**ADF Test:**

- Statistic: **-6.1615**
- p-value: **7.15e-8**
- Conclusion: Stationary.

**KPSS Test:**

- Statistic: **0.8367**
- p-value: **0.01**
- Conclusion: Trend-stationary.

*Interpretation:* Differencing improves stationarity.

**Plots:**

- `IOT_Sensor_Reading_plot.png`
- `Diff_IOT_Sensor_Reading_plot.png`

### 5️⃣ Autocorrelation Analysis

- ACF and PACF generated.
- **Plots:**
  - `acf.png`
  - `pacf.png`

### 6️⃣ Synthetic Baselines

- White noise and random walk generated to visualize random processes.
- **Plots:**
  - `white_noise.png`
  - `random_walk.png`

### 7️⃣ Modeling

**Moving Average Model (MA(1)):**

- RMSE: **0.2581**
- MA coefficient: **0.8047**
- AIC: **250.86**
- **Plot:** `MA_Model.png`

**AutoRegressive Model (AR(1)):**

- Results logged in `log.txt`.
- **Plot:** `AR_Model.png`

### 8️⃣ Covariance Calculation

- Variance computed: **0.1726**

## 🖼️ Outputs

| File                                 | Description                  |
| ------------------------------------ | ---------------------------- |
| `acf.png`                          | Autocorrelation plot         |
| `pacf.png`                         | Partial autocorrelation plot |
| `components.png`                   | Decomposition plot           |
| `IOT_Sensor_Reading_plot.png`      | Raw time series              |
| `Diff_IOT_Sensor_Reading_plot.png` | Differenced series           |
| `white_noise.png`                  | White noise baseline         |
| `random_walk.png`                  | Random walk baseline         |
| `MA_Model.png`                     | MA model fit                 |
| `AR_Model.png`                     | AR model fit                 |
| `log.txt`                          | Model and test results       |

## ✨ Interpretation

- **Seasonality and Trend:** Confirmed by decomposition.
- **Stationarity:** ADF indicates stationarity; KPSS indicates trend-stationarity.
- **Model Fit:** MA(1) and AR(1) effectively capture the data structure.
- **RMSE ~0.26:** Models perform well in-sample.

## 📝 What We Achieved

✅ End-to-end reproducible pipeline.
✅ Clear visualization of trends, seasonality, and randomness.
✅ Quantitative metrics to assess forecasting accuracy.
✅ Modular codebase for further experimentation.
