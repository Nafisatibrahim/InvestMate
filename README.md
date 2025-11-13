# InvestMate
Machine Learning based stocks ranking using XGBoost

# 📘 InvestMate Dataset — Data Dictionary

This document describes every column in the InvestMate machine learning dataset.
It includes price data, technical indicators, fundamental indicators, and target
variables used for stock prediction and ranking.

---

## 🟦 1. Identifier Columns

| Column | Type | Description |
|--------|------|-------------|
| **Date** | datetime | Trading day (YYYY-MM-DD). Daily frequency. |
| **Ticker** | string | Stock ticker symbol (e.g., AAPL, MSFT, TSLA). |

---

## 🟧 2. Price Data (OHLCV)

| Column | Type | Description |
|--------|------|-------------|
| **Open** | float | Price at market open. |
| **High** | float | Highest price during the trading day. |
| **Low** | float | Lowest price during the trading day. |
| **Close** | float | Final trading price of the day. |
| **Adj Close** | float | Adjusted close price after corporate actions (splits/dividends). |
| **Volume** | float | Number of shares traded during the day. |

---

## 🟩 3. Technical Indicators

### Momentum & Returns
| Column | Type | Description |
|--------|------|-------------|
| **Return_1d** | float | 1-day return: `(Close_t - Close_(t-1)) / Close_(t-1)` |

### Moving Averages
| Column | Type | Description |
|--------|------|-------------|
| **MA10** | float | 10-day simple moving average. |
| **MA20** | float | 20-day simple moving average. |
| **MA50** | float | 50-day simple moving average. |

### Volatility
| Column | Type | Description |
|--------|------|-------------|
| **Volatility20** | float | 20-day rolling standard deviation of returns. |

### RSI (Relative Strength Index)
| Column | Type | Description |
|--------|------|-------------|
| **RSI14** | float | 14-day RSI, measures momentum and overbought/oversold levels. |

### MACD (Trend Indicator)
| Column | Type | Description |
|--------|------|-------------|
| **MACD** | float | Difference between 12-day and 26-day EMAs. |
| **MACD_Signal** | float | 9-day EMA of MACD, used as a signal line. |

### Bollinger Bands
| Column | Type | Description |
|--------|------|-------------|
| **BB_Middle** | float | 20-day moving average (middle band). |
| **BB_Upper** | float | Upper band = MA20 + 2×std. |
| **BB_Lower** | float | Lower band = MA20 - 2×std. |

### Volume-Based Indicator
| Column | Type | Description |
|--------|------|-------------|
| **OBV** | float | On-Balance Volume (cumulative): `sign(Return) * Volume`. |

---

## 🟨 4. Target Variables (Prediction Objectives)

| Column | Type | Description |
|--------|------|-------------|
| **Close_Future** | float | Close price shifted −5 days (future price). |
| **Target_Return** | float | Future return: `(Close_Future - Close) / Close`. |
| **Target_UpDown** | int (0/1) | 1 if Target_Return > 0 (price expected to rise). |

These are used for:
- **Regression** (predicting future returns)
- **Classification** (predicting up/down movement)

---

## 🟪 5. Fundamental Indicators (Per Ticker)

### Company Descriptors
| Column | Type | Description |
|--------|------|-------------|
| **sector** | string/encoded | Company sector (e.g., Technology). |
| **industry** | string/encoded | Industry classification (e.g., Semiconductors). |

### Valuation Metrics
| Column | Type | Description |
|--------|------|-------------|
| **marketCap** | float | Total market value of the company. |
| **enterpriseValue** | float | MarketCap + debt − cash (better valuation metric). |
| **trailingPE** | float | Price-to-earnings ratio (last 12 months). |
| **forwardPE** | float | Forward-looking P/E based on analyst forecasts. |
| **priceToBook** | float | Price-to-book value ratio. |
| **bookValue** | float | Book value per share. |

### Earnings & Profitability
| Column | Type | Description |
|--------|------|-------------|
| **trailingEps** | float | Earnings per share (last 12 months). |
| **returnOnEquity** | float | ROE = Net income / Shareholder equity. |
| **returnOnAssets** | float | ROA = Net income / Total assets. |
| **profitMargins** | float | Net profit margin. |
| **operatingMargins** | float | Operating margin. |
| **grossProfits** | float | Total gross profit. |

### Cash Flow Metrics
| Column | Type | Description |
|--------|------|-------------|
| **freeCashflow** | float | Free cash flow available after expenses. |

### Growth Metrics
| Column | Type | Description |
|--------|------|-------------|
| **revenueGrowth** | float | Year-over-year revenue growth. |
| **earningsGrowth** | float | Year-over-year earnings growth. |
| **revenueQuarterlyGrowth** | float | Quarter-over-quarter revenue growth. |

### Risk & Financial Health
| Column | Type | Description |
|--------|------|-------------|
| **debtToEquity** | float | Debt-to-equity ratio. |
| **currentRatio** | float | Current assets ÷ current liabilities. |
| **quickRatio** | float | Short-term liquidity ratio. |
| **beta** | float | Volatility relative to the overall market. |

### Dividends & Analyst Targets
| Column | Type | Description |
|--------|------|-------------|
| **dividendYield** | float | Dividend yield as a percentage. |
| **targetMeanPrice** | float | Analyst average target price. |

---

# Summary

Dataset now includes:

- **6 raw price features**
- **14 technical indicators**
- **3 target variables**
- **24 fundamental financial indicators**
- **49 total features**



