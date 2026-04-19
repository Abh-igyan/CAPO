# CAPO: Cross-Asset Portfolio Optimization 📈
### Systematic Risk Parity with Regime-Switching Overlay

[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![Quant Finance](https://img.shields.io/badge/Domain-Quantitative%20Finance-gold.svg)](#)

## 📌 Project Overview
This repository contains the full model implementation for **Arbitrage Arena 2026**. The goal is to construct a diversified, systematic portfolio across Equities, Crypto, Indices, and Commodities that maintains a high Sharpe Ratio and minimizes Max Drawdown during market stress events.

### The Strategy: Risk Parity + Regime Switch
Unlike traditional mean-variance optimization (which often over-allocates to low-volatility assets), this model uses **Risk Parity** to ensure each asset contributes equally to the total portfolio risk. We overlay a **Regime-Switching indicator** based on NASDAQ volatility to dynamically de-risk during "Stress" regimes.

<img width="1020" height="545" alt="image" src="https://github.com/user-attachments/assets/872c6d74-fd04-4e8e-b455-14b75e54f484" />

---

## 🛠️ Model Architecture

### 1. Risk Contribution Formula
The marginal risk contribution of asset $i$ is defined as:
$$\sigma_i(w) = \frac{w_i \cdot (\Sigma w)_i}{\sqrt{w^T \Sigma w}}$$
Where:
- $w$: Weight vector
- $\Sigma$: Covariance matrix of log returns

### 2. Regime Classification
The model classifies market states using a **Rolling Volatility Threshold**:
- **Stable (Regime 1):** $\text{Vol}_{\text{nasdaq}} < 1.5 \times \text{Median Volatility}$
- **Stress (Regime 0):** $\text{Vol}_{\text{nasdaq}} \geq 1.5 \times \text{Median Volatility}$

---

## 📊 Key Features
- **Data Preprocessing:** Robust handling of multi-asset OHLCV data, log-return normalization, and forward-filling for asynchronous market holidays.
- **Feature Engineering:** RSI-based overbought filters, 50/200-day SMA crossovers, and rolling correlation matrices.
- **Risk Management:** Dynamic position sizing and volatility targeting to survive "Flash Crashes."

---

## 📈 Performance Metrics (Mandatory Evaluation)
| Metric | Result |
| :--- | :--- |
| **Annualized Sharpe Ratio** | 0.470994 |
| **Max Drawdown** | -32.2% |
| **Sortino Ratio** | 0.648199 |
| **Volatility (Annualized)** | 0.207771 |

---

## 🚀 Getting Started

### Prerequisites
```bash
pip install pandas numpy matplotlib seaborn scipy
```
# 📝 Post-Mortem & Conclusion
## ✅ What Worked
### Resilience: The model successfully survived the 2022 tech drawdown and the crypto-winter by dynamically scaling down exposure to BTC and ETH.

### Diversification: Correlation heatmaps confirmed that Gold and Silver acted as effective hedges when Equities were under stress.

### Stability: The Rolling 12-Month Sharpe Ratio remained remarkably consistent compared to a pure S&P 500 benchmark.

## ⚠️ Limitations & Improvements

### Correlation Convergence: In black-swan events, cross-asset correlations often converge to 1.0, reducing the effectiveness of Risk Parity.

### Future Work: Integrating Ledoit-Wolf Shrinkage for the covariance matrix to reduce noise and incorporating Conditional Value at Risk (CVaR) to better manage tail-risk.

## 🚀 Getting Started
### Prerequisites
Usage
### Clone the repo: ```git clone https://github.com/Abh-igyan/CAPO.git```

### Open the notebook: ```jupyter notebook CAPO.ipynb```

### Ensure your local ARBITRARY data folder is populated with the competition-provided .csv files.

## 📂 Repository Structure
### CAPO.ipynb: Full implementation, from EDA to Backtesting.

### Historical OHLCV datasets.

### 👨‍💻 Author

#### Abhigyan Tiwari
#### B.Tech CSE (2nd Year) | Quant Finance Enthusiast | Competitive Programming | ML/DL
