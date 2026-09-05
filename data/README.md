# Data

This repository does not distribute the raw news corpus.

## Market Data

Market data were obtained from Yahoo Finance using `yfinance`. Features were constructed from cryptocurrency prices, trading volume, and broader market indicators.

To reduce multicollinearity, Variance Inflation Factor (VIF) screening was performed using the training period only, with a threshold of 5.

The final common feature set includes:

- Log return
- 1-day, 3-day, and 5-day lagged returns
- Relative Strength Index (RSI)
- 20-day realized volatility
- Daily volume change
- Volume relative to its 5-day moving average
- Intraday high-low range
- S&P 500 return
- VIX change

## News Data

General financial news and cryptocurrency-specific news were obtained from Alpha Vantage.

Raw Alpha Vantage articles are not included because of data-provider licensing and file-size constraints.

The analysis pipeline includes:

- Duplicate removal
- Exclusion of identified automated market-recap articles
- FinBERT sentiment feature construction
- Daily sentiment aggregation
- Chronological alignment of day-t information with day-(t+1) returns

## Asset Selection

The main analysis focuses on Bitcoin (BTC) and Ethereum (ETH).

Solana (SOL) was evaluated during a pre-modeling news-coverage audit but was excluded from the primary analysis because its historical news corpus showed substantially lower publisher diversity than BTC and ETH.

This decision was based on data quality and representativeness before model evaluation, rather than forecasting performance.
