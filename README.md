Readme ap project · MDCopyETF Trend-Following Strategy
Overview
This project develops and evaluates a rule-based trend-following trading strategy applied to a portfolio of four ETFs. The strategy uses a simple moving average (SMA) rule to determine when to hold each ETF versus move to cash, with the goal of generating strong risk-adjusted returns while keeping drawdowns controlled.
Strategy Summary

Signal: Buy when price is above its SMA; move to cash when price falls below
Optimized SMA Window: 150 days (selected during training)
Portfolio: Equal-weighted across QQQ, SPY, VTI, and SCHG
Transaction Cost: 0.2% applied per trade (commission + slippage)
Initial Capital: $10,000

Data

Source: Yahoo Finance via yfinance
Tickers: QQQ, SPY, VTI, SCHG
Training Period: 2023-01-01 to 2025-04-30
Testing Period: 2025-04-30 to 2026-04-30

Results
Testing Period (Out-of-Sample) — 2025 to 2026
MetricTargetResultPassAnnual Return> 5%19.26%✓Sharpe Ratio> 0.81.60✓Max Drawdown< 50%-6.42%✓
Portfolio grew from $10,000 → $11,917 (+19.17%) during the test period
Training Period — 2023 to 2025
MetricTargetResultPassAnnual Return> 5%18.29%✓Sharpe Ratio> 0.81.27✓Max Drawdown< 50%-10.46%✓
Portfolio grew from $10,000 → $14,740 (+47.40%) during the training period
Project Breakdown
1. Data Collection & Splitting
Historical price data was downloaded for all four ETFs. Indicators were calculated on the full dataset before splitting to avoid boundary issues near the train/test cutoff.
2. Strategy Design
The SMA crossover signal determines market exposure: long when the price is above the moving average, cash otherwise. This keeps the strategy simple and interpretable.
3. Parameter Optimization
Five SMA window lengths (50, 100, 150, 200, 250 days) were tested on the training set. Windows were scored on a combination of Sharpe ratio and annualized return. The 150-day window produced the best training score (3.10).
4. Performance Evaluation
The optimized strategy was applied to the out-of-sample test period and benchmarked against a 200-day SMA strategy and a simple buy-and-hold approach. All three assignment performance targets were met.
Tools & Technologies

Language: Python 3.13
Libraries: pandas, numpy, matplotlib, yfinance
Environment: Jupyter Notebook

Files
FileDescriptionAPproject_cleaned.ipynbFull Jupyter Notebook with code and analysis
How to Run

Clone this repository
Install dependencies:

bash   pip install pandas numpy matplotlib yfinance

Open APproject_cleaned.ipynb in Jupyter and run all cells
