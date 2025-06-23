# Pairs-trading-

This project implements a **market-neutral trading strategy** by identifying statistically cointegrated stock pairs and executing trades based on spread mean reversion. The notebook includes full data analysis, pair selection, trading signal generation, and strategy backtesting.

---

## Objective

Identify cointegrated stock pairs from a set of 20 liquid U.S. equities and build a trading strategy that profits from temporary price divergences using a hedge ratio and z-score signals.

---

##  Data Sources

- **Stock Prices**: Daily adjusted close prices from [Yahoo Finance](https://finance.yahoo.com) via the `yfinance` API.
- **Assets Considered**: 20 large-cap stocks including AAPL, MSFT, AMZN, GOOGL, META, NVDA, TSLA, JPM, V, MA, and others.

---

## Methodology

### 1. **Pair Selection**
- Use the **Engle-Granger cointegration test** to evaluate all unique stock pairs.
- Select pairs with a **p-value < 0.05**, indicating a statistically significant long-run relationship.

### 2. **Hedge Ratio Estimation**
- Estimate the hedge ratio (β) using **Ordinary Least Squares (OLS)** regression.

### 3. **Spread & Z-Score Calculation**
- Compute the spread: `Spread = Y - β·X`
- Calculate rolling **z-score** (mean and standard deviation over 30 days).

### 4. **Trading Rules**
- **Go Long** the spread (long Y, short X) when z-score < -1.
- **Go Short** the spread (short Y, long X) when z-score > 1.
- **Exit** positions when |z-score| < 0.5.
- Position signals are forward-filled and applied daily.

### 5. **Backtesting Performance**
- Apply position signals on historical returns.
- Track **PnL** and calculate **cumulative return** over time.
- Key metrics include:
  - Total Return
  - Annualized Sharpe Ratio
  - Number of Trades Executed

---

##  Results & Outputs

- **Top Cointegrated Pairs** (ranked by p-value)
- **Spread & Z-Score Charts** for selected pairs
- **Cumulative Return Plot** of the strategy
- **Performance Summary** (Sharpe Ratio, Trades, Total Return)

---
