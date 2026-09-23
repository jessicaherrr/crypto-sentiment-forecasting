# Data Access

This repository contains the code and processed experimental outputs used in the study. Raw news data are not redistributed because they remain subject to the original provider's access and redistribution terms.

## Market Data

Daily market data are obtained through **Yahoo Finance** for:

- Bitcoin (BTC)
- Ethereum (ETH)
- S&P 500
- CBOE Volatility Index (VIX)

The study uses daily observations from **April 2022 through August 2026**, with April 2022 used as a warm-up period for feature construction. The main forecasting sample begins on May 1, 2022.

Market variables used in the forecasting pipeline include cryptocurrency returns, lagged returns, RSI, rolling volatility, volume-based features, intraday range, S&P 500 returns, and VIX changes.

Market data are not included as raw source files in this repository. They can be reconstructed from Yahoo Finance using the data-preparation logic in the notebooks.

## News Data

News data are obtained from **Alpha Vantage**.

All news phases use the same provider so that changes in forecasting performance between general and crypto-specific sentiment are not confounded by a change in news provider.

Three cleaned news corpora are used:

| News corpus | Final article count |
|---|---:|
| General financial news | 1,356,714 |
| BTC-specific news | 61,389 |
| ETH-specific news | 41,374 |

Before daily aggregation, duplicate articles are removed using provider article IDs or matching normalized titles, sources, and UTC publication dates. Identified automated MarketWatch recap articles are excluded, while regular editorial articles are retained.

News is aligned using exact UTC publication timestamps. Articles published during

```text
[t 00:00 UTC, (t+1) 00:00 UTC)
