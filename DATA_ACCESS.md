# Data Access

## Market data

The study uses daily BTC, ETH, S&P 500, and VIX market series. The forecasting notebooks expect the prepared market-data files in the local project data directory. Market data can be reconstructed from the public market-data sources described in the manuscript.

## News data

News was obtained from Alpha Vantage and processed into general-financial and asset-specific BTC/ETH sentiment corpora. Raw Alpha Vantage news records are not included in this repository because redistribution may be restricted by provider terms.

To rerun news-dependent phases, users must obtain their own authorized Alpha Vantage data and prepare the expected files referenced in the notebooks, including general and asset-specific FinBERT-scored article files.

## What is included

The `outputs/` directory contains derived experimental artifacts such as predictions, metrics, significance tests, audit tables, configuration manifests, and figures. It does not contain raw article text.
