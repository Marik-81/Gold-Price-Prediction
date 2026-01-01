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

[cite_start]The final output provides a **365-day forecast** with a Risk-Adjusted 95% Confidence Interval, helping retailers and investors quantify market risk[cite: 120, 168, 173].

---

## 🎯 Objectives
1.  [cite_start]**Data Extraction:** Ethically scrape historical data (2020–2025) from `gold.sa` using reverse-engineering techniques[cite: 135].
2.  [cite_start]**EDA:** Analyze trends and confirm high volatility (IQR: ~66 SAR)[cite: 151].
3.  [cite_start]**Modeling:** Build a time-series model that handles non-stationarity[cite: 156].
4.  [cite_start]**Forecasting:** Generate a 2026 prediction with risk bounds[cite: 175].

---

## 🛠️ Technology Stack
* **Data Handling:** Pandas, Numpy, JSON
* [cite_start]**Web Scraping:** Requests (with ethical delays to avoid throttling) [cite: 139]
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
The data shows a clear upward trend from 2020 to 2025, driven by global economic factors. [cite_start]The market is non-stationary and required differencing ($d=1$)[cite: 144, 159].
### 2. Volatility Clustering
The analysis confirmed that gold volatility is not constant. [cite_start]High-risk periods cluster together, which justified the use of GARCH(1,1) over a simple Random Walk model[cite: 168].
### 3. Final Forecast (2026)
[cite_start]The model predicts the following for the next 365 days[cite: 176]:

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
| **Dynamic Data** | Standard scraping failed. [cite_start]Reverse-engineered network requests to find the JSON endpoint[cite: 137]. |
| **Rate Limiting** | [cite_start]Implemented `time.sleep(7)` to respect server limits and avoid 403 errors[cite: 139]. |
| **Model Flatlining** | Basic ARIMA(0,1,0) failed to capture risk. [cite_start]Integrated GARCH(1,1) to model volatility[cite: 163, 168]. |

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
**Disclaimer:** This project is for educational purposes only. [cite_start]Financial decisions should not be made based solely on this model[cite: 181].
