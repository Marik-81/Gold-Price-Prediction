# 📈 Gold Price Prediction in KSA [2020-2026]
### Time-Series Forecasting using Hybrid ARIMA-GARCH Model

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![Status](https://img.shields.io/badge/Status-Completed-success)
![License](https://img.shields.io/badge/License-MIT-green)

[📄 Read Full Documentation](FD-OS(Gold-Portfolio.v2).pdf)
## 📋 Project Overview
This project predicts the daily price of **24K Gold (per Gram)** in Saudi Arabia (KSA) for the year **2026**.

Gold prices are inherently non-stationary and exhibit "volatility clustering" (periods of high risk followed by calm). Standard models like Linear Regression or simple ARIMA fail to capture this changing risk. This project solves that problem by implementing a **Hybrid ARIMA-GARCH** model:
* **ARIMA:** Models the trend (mean).
* **GARCH:** Models the volatility (variance/risk).

The final output provides a **365-day forecast** with a Risk-Adjusted 95% Confidence Interval, helping retailers and investors quantify market risk.

---

## 🎯 Objectives
1.  **Data Extraction:** Ethically scrape historical data (2020–2025) from `gold.sa` using reverse-engineering techniques.
2.  **EDA:** Analyze trends and confirm high volatility (IQR: ~66 SAR).
3.  **Modeling:** Build a time-series model that handles non-stationarity.
4.  **Forecasting:** Generate a 2026 prediction with risk bounds.

---

## 🛠️ Technology Stack
* **Data Handling:** Pandas, Numpy, JSON
* **Web Scraping:** Requests (with ethical delays to avoid throttling) 
* **Modeling:** `statsmodels` (ARIMA), `arch` (GARCH)
* **Visualization:** Matplotlib, Seaborn

---

## 📂 Repository Structure
* `01_Gold_Extraction.ipynb`: Scrapes data from gold.sa and saves it to CSV.
* `02_Exploratory_Data_Analysis.ipynb`: Visualizes trends and volatility.
* `03_Model_Prediction.ipynb`: Builds the ARIMA-GARCH model and generates the 2026 forecast.
* `gold_sa_historical_data_2020_onwards.csv`: The historical dataset used for training.

---

## 📊 Key Results

### 1. Trend Analysis
The data shows a clear upward trend from 2020 to 2025, driven by global economic factors. The market is non-stationary and required differencing ($d=1$).
### 2. Volatility Clustering
The analysis confirmed that gold volatility is not constant. High-risk periods cluster together, which justified the use of GARCH(1,1) over a simple Random Walk model.
### 3. Final Forecast (2026)
The model predicts the following for the next 365 days:

| Metric | Value | Interpretation |
| :--- | :--- | :--- |
| **Prediction Horizon** | 365 Days | Full year 2026 forecast |
| **Avg. Predicted Price** | **525.49 SAR/g** | Expected Mean Price |
| **Lower Bound (95%)** | 438.01 SAR/g | Best-Case / Low-Risk Scenario |
| **Upper Bound (95%)** | 612.96 SAR/g | Worst-Case / High-Risk Scenario |

---

## ⚠️ Challenges & Solutions
| Challenge | Solution |
| :--- | :--- |
| **Dynamic Data** | Standard scraping failed. Reverse-engineered network requests to find the JSON endpoint. |
| **Rate Limiting** | Implemented `time.sleep(7)` to respect server limits and avoid 403 errors. |
| **Model Flatlining** | Basic ARIMA(0,1,0) failed to capture risk. Integrated GARCH(1,1) to model volatility. |

---

## ⚙️ How to Run
1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/YourUsername/Gold-Price-Prediction-KSA.git](https://github.com/YourUsername/Gold-Price-Prediction-KSA.git)
    ```
2.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
3.  **Run the Notebooks:**
    Start Jupyter Notebook and run the files in order: `01` -> `02` -> `03`.

---

## 📄 License & Disclaimer
**Data Source:** [Gold.sa](https://gold.sa)
**Disclaimer:** This project is for educational purposes only. Financial decisions should not be made based solely on this model.
