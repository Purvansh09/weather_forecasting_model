# 🌦️ Weather Trend Forecasting — Data Science Assessment

* Data Scientist & AI/ML Model**

A complete data science pipeline on the **Global Weather Repository** dataset to forecast weather trends. This project demonstrates data cleaning, exploratory data analysis, anomaly detection, time-series forecasting with multiple models, and unique geospatial/feature-importance analyses.

---

## 📊 Dataset

- **Source**: [Global Weather Repository — Kaggle](https://www.kaggle.com/datasets/nelgiriyewithana/global-weather-repository)
- **Key column**: `last_updated` (datetime)
- **Scale**: 41 features, 130,783 rows of daily worldwide weather data

---

## 🚀 Installation & Quick Start

```bash
git clone https://github.com/<your-username>/weather-trend-forecasting.git
cd weather-trend-forecasting
pip install -r requirements.txt
```

### Run the notebooks

Open Jupyter and run the notebooks **in order**:

```bash
jupyter notebook
```

1. `notebooks/01_data_cleaning.ipynb`
2. `notebooks/02_eda.ipynb`
3. `notebooks/03_anomaly_detection.ipynb`
4. `notebooks/04_forecasting.ipynb`
5. `notebooks/05_unique_analyses.ipynb`

---

## 📁 Project Structure

```
PMA/
│
├── data/
│   ├── GlobalWeatherRepository.csv          # Raw dataset
│   ├── cleaned_weather.csv                  # Cleaned + normalized
│   └── cleaned_weather_unscaled.csv         # Cleaned (original scale)
│
├── notebooks/
│   ├── 01_data_cleaning.ipynb               # Data cleaning & preprocessing
│   ├── 02_eda.ipynb                         # Exploratory data analysis (6+ plots)
│   ├── 03_anomaly_detection.ipynb           # Isolation Forest anomaly detection
│   ├── 04_forecasting.ipynb                 # ARIMA, Prophet, XGBoost, Ensemble
│   └── 05_unique_analyses.ipynb             # Feature importance + spatial map
│
├── src/
│   └── utils.py                             # Shared helper functions
│
├── outputs/
│   ├── figures/                             # All saved plots (.png, .html)
│   ├── models/                              # Serialized models (.pkl)
│   └── model_comparison.csv                 # Model evaluation table
│
├── report/
│   └── weather_forecasting_report.pdf       # Final report
│
├── requirements.txt
└── README.md
```

---

## 📈 Results Summary

| Model | MAE | RMSE | MAPE (%) |
|-------|-----|------|----------|
| ARIMA (2,1,2) | 3.5493 | 3.9109 | 24.81 |
| **Facebook Prophet** | **1.0060** | **1.5798** | **8.17** |
| XGBoost (Lag Features) | 1.2332 | 1.8496 | 9.94 |
| Ensemble (Average) | 1.8674 | 2.3234 | 13.96 |

> **Best Model**: Facebook Prophet achieved the lowest MAE (1.006) and MAPE (8.17%), significantly outperforming ARIMA and performing slightly better than XGBoost on all metrics.

---

## 🔍 Key Analyses

### Data Cleaning
- Zero missing values after median imputation
- IQR-based outlier flagging: 28,134 rows (21.5%) flagged — not dropped
- StandardScaler normalization on 26 numeric features

### EDA (6 Visualizations)
1. Daily global mean temperature trend
2. Precipitation distribution (histogram + KDE)
3. Full correlation heatmap
4. Top 20 countries by average temperature
5. Temperature distribution by continent
6. Wind speed vs. temperature scatter

### Anomaly Detection
- Isolation Forest with 5% contamination rate
- 6,540 anomalies identified (5.0%)
- Top anomalies: extreme temperatures in Kuwait (49.2°C) and Iraq (49.1°C)

### Forecasting
- Three individual models + simple average ensemble
- 80/20 chronological train/test split (539 train / 135 test days)
- Prophet captured yearly seasonality most effectively

### Unique Analyses
- **Feature Importance**: XGBoost gain analysis — top features: humidity, wind speed, UV index, pressure
- **Spatial Analysis**: Interactive Plotly choropleth world map of mean temperature by country

---

## 🎥 Demo Video

> https://www.loom.com/share/c402a1d1e00240c0a35c02ec338ebb67

---

## 📄 License

This project is part of the PM Accelerator assessment program.
