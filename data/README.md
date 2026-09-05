# Data

This repository does not distribute the raw news corpus.

## Market Data

Market variables were obtained from Yahoo Finance using `yfinance`.

Main assets and external market indicators:
- Bitcoin (`BTC-USD`)
- Ethereum (`ETH-USD`)
- S&P 500 (`^GSPC`)
- CBOE Volatility Index (`^VIX`)

## News Data

General financial news and cryptocurrency-specific news were obtained from Alpha Vantage.

Raw Alpha Vantage articles are not included because of data-provider licensing considerations and file-size constraints.

The analysis notebooks document duplicate removal, automated recap exclusion, FinBERT feature construction, daily sentiment aggregation, and chronological alignment with next-day returns.

## Asset Selection

The main analysis uses Bitcoin and Ethereum. Solana was excluded from the primary analysis after a pre-modeling coverage audit found limited publisher diversity relative to BTC and ETH. The exclusion was based on data quality and representativeness rather than model performance.
