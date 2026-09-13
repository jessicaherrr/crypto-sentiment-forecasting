# When Does News Sentiment Help Cryptocurrency Return Forecasting?

### A Multi-Phase Study of FinBERT Scope and Recency

This repository contains the final deterministic v3 notebooks and processed experimental outputs for a multi-phase study of whether news sentiment adds incremental predictive value to next-day Bitcoin (BTC) and Ethereum (ETH) return forecasting.

The study compares market-only baselines, simple provider sentiment, general-financial FinBERT sentiment, crypto-specific FinBERT sentiment, temporal recency treatments, and an exploratory reliability-aware dual-scope fusion. The evaluation emphasizes point-in-time data alignment, naive financial benchmarks, five-seed walk-forward testing, forecasting-specific inference, and multiplicity correction.

## Experimental design

| Phase | Added information | Purpose |
|---|---|---|
| 0 | Market only | Financial baseline |
| 1 | General API sentiment | Simple sentiment increment |
| 2 | General FinBERT | Sentiment-representation effect |
| 3 | Crypto-specific FinBERT | Information-scope effect |
| 4 | Short window / recency decay | Temporal ablation |
| 5 | Dual-scope reliability fusion | Exploratory fusion audit |

## Key findings

- Sentiment does **not** universally improve cryptocurrency return forecasting.
- BTC shows its clearest evidence in favor of **general-financial FinBERT** relative to crypto-specific sentiment.
- ETH shows stronger held-out evidence for **crypto-specific sentiment** and, exploratorily, reliability-aware fusion.
- A validation-selected **60-day half-life** improves BTC LSTM held-out MAE by **1.63%**, but the statistical significance does not persist in walk-forward testing.
- Most positive held-out effects shrink in five-seed walk-forward evaluation, highlighting temporal instability.
- The final reproducibility audit passes all canonical-reuse, repeated-method consistency, and metric-to-significance linkage checks.

See [`RESULTS.md`](RESULTS.md) for the numerical summary.

## Repository structure

```text
crypto-sentiment-forecasting/
├── notebooks/        # Final v3 Phase 0-5, audits, and economic backtest
├── outputs/          # Processed predictions, metrics, tests, audits, and phase figures
├── figures/          # Selected manuscript-ready figures
├── docs/             # Data/code availability wording
├── DATA_ACCESS.md    # Raw-data access and redistribution notes
├── RESULTS.md        # Final numerical summary
├── CITATION.cff
└── requirements.txt
```

## Reproducing the analysis

The notebooks were designed for a Google Colab / Google Drive workflow and should be run in this order:

1. `Phase0_HICSS_Revised_v3.ipynb`
2. `Phase1_HICSS_Revised_v3.ipynb`
3. `Phase2_HICSS_Revised_v3.ipynb`
4. `Phase3_HICSS_Revised_v3.ipynb`
5. `Phase4_HICSS_Revised_v3.ipynb`
6. `Phase5_Reliability_Aware_Dual_Scope_Fusion_v3.ipynb`
7. `FinalRevision_Temporal_Alignment_Audit_v3.ipynb`
8. `FinalRevision_Statistical_and_Consistency_Audit_v3.ipynb`
9. `Economic_Backtest_With_Trading_Costs_v3.ipynb`

The notebooks write the final artifacts to `revised_outputs_v3/` in the configured project directory. Raw/provider data must be supplied separately as described in [`DATA_ACCESS.md`](DATA_ACCESS.md).

## Environment

The final rerun used Python 3.13.15 with the principal package versions recorded in `requirements.txt`. Phase-level `environment_manifest.json` files are also retained under `outputs/`.

## Data and code availability

Code and processed experimental outputs are included in this repository. **Raw Alpha Vantage news data are not redistributed** and remain subject to the provider's access and redistribution terms.

Once published, the manuscript statement can read:

> Code and processed experimental outputs are available at https://github.com/<YOUR_GITHUB_USERNAME>/crypto-sentiment-forecasting. Raw Alpha Vantage news data are subject to the provider's redistribution terms.

## Citation

Citation metadata are provided in [`CITATION.cff`](CITATION.cff). Please cite the associated paper when available.
