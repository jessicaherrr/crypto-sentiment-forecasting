# When Does News Sentiment Help Cryptocurrency Return Forecasting?

### A Multi-Phase Study of FinBERT Scope and Recency

This repository contains the final notebooks and processed experimental outputs for a multi-phase study of whether news sentiment adds incremental predictive value to next-day Bitcoin (BTC) and Ethereum (ETH) return forecasting.

The study compares market-only baselines, simple provider sentiment, general-news FinBERT sentiment, crypto-specific FinBERT sentiment, temporal recency treatments, and an exploratory reliability-based fusion of general and crypto news.

The evaluation emphasizes point-in-time data alignment, explicit financial benchmarks, five-seed walk-forward testing, forecasting-specific inference, multiple-comparison correction, and reproducibility across experimental phases.

## Experimental Design

| Phase | Added Information | Purpose |
|---|---|---|
| 0 | Market only | Financial baseline |
| 1 | General API sentiment | Simple sentiment increment |
| 2 | General-news FinBERT | Sentiment representation effect |
| 3 | Crypto-specific FinBERT | Information scope effect |
| 4 | Short window / recency decay | Temporal ablation |
| 5 | Dual-scope reliability fusion | Exploratory fusion audit |

## Key Findings

- News sentiment does **not** universally improve cryptocurrency return forecasting.
- For BTC LSTM, **general-news FinBERT** outperforms crypto-specific FinBERT in the held-out sample, reducing MAE by **2.49%**.
- For ETH LSTM, the ordering reverses: **crypto-specific FinBERT** reduces MAE by **3.84%** relative to general-news FinBERT.
- In Phase 4, validation selects a **30-day half-life** for exponential recency weighting.
- Within Phase 4, BTC performs best with a **7-day short window**, improving held-out MAE by **1.13%** relative to the Phase 3 reference.
- ETH performs best with the **combined short-window and decay treatment**, improving held-out MAE by **2.36%**.
- Neither Phase 4 improvement survives Holm correction, and both gains become much smaller in walk-forward evaluation.
- Reliability fusion improves ETH held-out MAE by **5.32%** relative to general-news FinBERT, although its incremental advantage is not statistically robust across time.
- The final reproducibility audit passes all **28 canonical reuse checks**, **78 repeated-method consistency checks**, and **112 metric-to-significance linkage checks**.

## Detailed Results

For the complete phase-by-phase numerical results, prediction figures, statistical tests, walk-forward robustness analysis, provider-shift diagnostics, and economic backtest, see:

**[View the full experimental results and figures →](RESULTS.md)**

## Repository Structure

```text
crypto-sentiment-forecasting/
├── notebooks/        # Final Phase 0-5 notebooks and audit notebooks
├── outputs/          # Processed predictions, metrics, tests, audits, and figures
├── DATA_ACCESS.md    # Raw-data access and redistribution notes
├── RESULTS.md        # Detailed results and figures
├── requirements.txt
└── README.md
```

## Reproducing the Analysis

The notebooks were developed for a Google Colab / Google Drive workflow.

The main experimental sequence is:

1. `Phase0.ipynb`
2. `Phase1.ipynb`
3. `Phase2.ipynb`
4. `Phase3.ipynb`
5. `Phase4.ipynb`
6. `Phase5.ipynb`

Additional notebooks reproduce the no-news audit, temporal-alignment checks, statistical and consistency checks, economic backtest, and manuscript figures.

The final artifacts are written to:

```text
revised_outputs_v4/
```

Raw provider data must be supplied separately as described in [`DATA_ACCESS.md`](DATA_ACCESS.md).

## Evaluation Framework

The primary forecasting metrics are:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R-squared
- Directional accuracy

Financial benchmarks include a zero-return random walk and ARIMA specifications selected using validation data.

Forecast comparisons use:

- Diebold-Mariano tests with Newey-West HAC variance
- Paired two-sided Wilcoxon signed-rank tests
- Holm correction for multiple comparisons
- Five-seed expanding-window walk-forward evaluation

The final analysis also includes an economic sanity check using long/short sign rules under multiple transaction-cost assumptions.

## Data and Temporal Alignment

The forecasting target is next-day log return.

News is assigned to day `t` using exact UTC publication timestamps over:

```text
[t 00:00 UTC, (t+1) 00:00 UTC)
```

The forecast is formed after day `t` is complete and predicts the return from `t` to `t+1`.

All news phases use Alpha Vantage so that general-news and crypto-specific sentiment can be compared without changing the news provider.

The final cleaned news corpora contain:

- General financial news: **1,356,714 articles**
- BTC-specific news: **61,389 articles**
- ETH-specific news: **41,374 articles**

The no-news audit finds:

- General news: **0 no-news days**
- BTC-specific news: **0 no-news days**
- ETH-specific news: **2 no-news days (0.13%)**

## Main Result Interpretation

The strongest result is not that sentiment always improves forecasting.

Instead, the evidence suggests that the usefulness of sentiment depends on:

- the asset,
- the information scope,
- the forecasting architecture,
- the temporal treatment,
- and the market regime.

For BTC, broad financial sentiment is more useful than crypto-specific sentiment in the held-out comparison.

For ETH, crypto-specific sentiment performs better than general-news sentiment.

These information-scope effects remain directionally consistent in walk-forward evaluation, but their magnitudes become smaller and their multiplicity-adjusted significance disappears.

The Phase 4 temporal ablation shows that shorter or more recent histories can help in selected settings, but there is no robust general advantage from exponential decay.

The Phase 5 reliability fusion is exploratory. It improves ETH held-out MAE relative to general-news FinBERT, but its additional advantage over crypto-specific sentiment is modest and does not remain statistically robust across time.

## Reproducibility

The final pipeline uses deterministic LSTM execution and canonical prediction reuse across phases.

The final consistency audit reports:

- **28 / 28** canonical prediction reuse checks passed
- **78 / 78** repeated-method consistency checks passed
- **112 / 112** metric-to-significance linkage checks passed

These controls ensure that repeated method labels refer to the same prediction artifacts and that significance tests are linked to the exact prediction series used to compute the reported forecast losses.

Some provenance fields in processed outputs may retain legacy paths from earlier validated runs because later phases reuse frozen canonical predictions rather than retraining identical baselines. Numerical predictions and final metrics are unchanged, and the final consistency audits pass.

## Economic Backtest

The economic backtest is included as a secondary robustness check rather than the primary objective of the study.

It evaluates prespecified long/short sign rules under one-way transaction costs of:

- 0 basis points
- 5 basis points
- 10 basis points
- 20 basis points
- 50 basis points

Reported diagnostics include cumulative return, Sharpe ratio, maximum drawdown, and turnover.

Some model specifications produce positive realized performance under selected cost assumptions, but block-bootstrap confidence intervals for mean return relative to cash include zero. Forecast-error improvements therefore should not be interpreted as statistically established trading profitability.

## Environment

The principal Python package versions used for the final workflow are recorded in `requirements.txt`.

Phase-level environment manifests are also retained under `outputs/` where applicable.

## Data and Code Availability

Code and processed experimental outputs are included in this repository.

**Raw Alpha Vantage news data are not redistributed** and remain subject to the provider's access and redistribution terms.

Processed outputs are provided for reproducibility and inspection of the reported experiments.

## Paper

The associated manuscript is:

**When Does News Sentiment Help Cryptocurrency Return Forecasting? A Multi-Phase Study of FinBERT Scope and Recency**

The manuscript studies the conditions under which financial news sentiment contributes incremental information to next-day BTC and ETH return forecasting, with particular emphasis on information scope, temporal robustness, benchmark choice, and reproducibility.

## Citation

Citation metadata are provided in [`CITATION.cff`](CITATION.cff).

Please cite the associated paper when available.
