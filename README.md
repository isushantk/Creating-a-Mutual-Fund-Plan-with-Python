# 📈 Mutual Fund Portfolio Creator

**Create an optimized mutual fund portfolio from Nifty 50 stocks using Python.** Analyzes historical data to select high-ROI, low-volatility stocks for long-term investment.

[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Plotly](https://img.shields.io/badge/Plotly-239120?style=for-the-badge&logo=plotly&logoColor=white)](https://plotly.com/python/)

## ✨ Features

- **Data Analysis**: Nifty 50 historical closing prices
- **Smart Selection**: High ROI + Low Volatility stocks
- **Risk Management**: Inverse volatility portfolio weighting
- **Future Projections**: SIP returns for 1-10 years
- **Interactive Charts**: Plotly visualizations

## 🎯 Selected Portfolio

| Stock          | ROI (%) | Allocation (%) |
|----------------|---------|----------------|
| ICICIBANK.NS  | 13.48   | 6.93           |
| INDUSINDBK.NS | 7.16    | 7.44           |
| JSWSTEEL.NS   | 7.02    | 15.99          |
| AXISBANK.NS   | 6.59    | 9.22           |
| HDFCBANK.NS   | 6.32    | 8.93           |
| SUNPHARMA.NS  | 5.63    | 7.26           |
| KOTAKBANK.NS  | 5.47    | 7.66           |
| CIPLA.NS      | 4.85    | 8.48           |
| NTPC.NS       | 4.36    | 28.08          |

## 💰 Expected Returns (₹5000/month SIP)

| Period | Future Value |
|--------|--------------|
| 1 Year | ₹62,000      |
| 3 Years| ₹210,000     |
| 5 Years| ₹370,000     |
| 10 Years| ₹860,000    |

## 🚀 Quick Start

Clone repository
git clone [https://github.com/isushantk/Creating-a-Mutual-Fund-Plan-with-Python]
cd mutual-fund-python

Install dependencies
pip install -r requirements.txt

Download dataset & run
python mutual_fund_analysis.py

## 📁 Project Structure
mutual-fund-python/
├── README.md # This file
├── mutual_fund_analysis.py # Main analysis script
├── nifty50_closing_prices.csv # Dataset
├── requirements.txt # Dependencies
└── outputs/ # Generated charts
├── stock_trends.html
├── risk_comparison.html
└── sip_projection.html


## 📋 Step-by-Step Methodology

### 1. Data Loading & Cleaning
import pandas as pd
data = pd.read_csv("nifty50_closing_prices.csv")
data['Date'] = pd.to_datetime(data['Date'])
data.fillna(method='ffill', inplace=True)

### 2. Calculate Key Metrics
- **Volatility**: Standard deviation of closing prices
- **Growth Rate**: Average daily % change
- **ROI**: `(Final Price - Initial Price) / Initial Price × 100`

### 3. Stock Selection Criteria
High ROI (> median ROI) AND Low Volatility (< median volatility)

### 4. Portfolio Allocation
Weight = 1/Volatility (normalized)
Lower risk = Higher allocation
### 5. SIP Future Value Formula
FV = P × [((1 + r/n)^(n×t) - 1) / (r/n)] × (1 + r/n)
P = Monthly investment, r = ROI, n = 12, t = years

## 📊 Visualizations Generated

1. **All Stocks Trend** - Price movements over time
2. **Risk Comparison** - Mutual Fund vs Growth Stocks
3. **ROI Comparison** - Portfolio vs High-growth stocks
4. **SIP Projection** - Future value over 1-10 years

## 🛠️ Requirements

pandas==2.1.4
plotly==5.17.0
numpy==1.24.3


## 📥 Dataset

**Nifty 50 Closing Prices** (Aug 2024 - present)
- 51 stocks × daily data
- Download: [nifty50_closing_prices.csv](https://drive.google.com/file/d/1AQui5tPCNinqRBkHErIFzPauqf_hAP-h/view?usp=sharing)

## 🔬 Complete Code Preview
Core Analysis
all_companies = data.columns[1:]
roi = ((data[all_companies].iloc[-1] - data[all_companies].iloc) /
data[all_companies].iloc) * 100
volatility = data[all_companies].std()

Select optimal stocks
selected = roi[(roi > roi.median()) & (volatility < volatility.median())]

Investment weights
weights = (1/volatility[selected.index]) / (1/volatility[selected.index]).sum()

print("Portfolio Allocation:\n", weights.sort_values(ascending=False))





