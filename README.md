# 📈 SBI Stock Price Time Series Analysis (June–July 2024)

This project performs exploratory time series analysis on the closing prices of SBI (State Bank of India) stock, retrieved using Yahoo Finance (`SBIN.NS`) for the period from **June 6, 2024 to July 26, 2024**.

---

## 📚 Libraries Used

- `numpy`, `pandas` – For data manipulation
- `matplotlib`, `seaborn` – For visualization
- `yfinance` – To fetch historical stock data
- `statsmodels` – For time series decomposition and stationarity testing
- `scikit-learn` – For potential model evaluation (e.g., R² score)

---

## 🔍 Project Overview

### ✅ Data Download
Historical stock prices are pulled using the `yfinance` library:

```python
sbi = yf.download('SBIN.NS', start="2024-06-06", end="2024-07-26")
rolling_mean = sbi['Close'].rolling(7).mean()
rolling_std = sbi['Close'].rolling(7).std()
result = adfuller(sbi['Close'])
print('ADF Statistic:', result[0])
print('p-value:', result[1])
decompose = seasonal_decompose(sbi['Close'], model='additive', period=7)
