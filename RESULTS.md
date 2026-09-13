# Final v3 Results Summary

This repository corresponds to the deterministic v3 rerun of the study **When Does News Sentiment Help Cryptocurrency Return Forecasting? A Multi-Phase Study of FinBERT Scope and Recency**.

## Main findings

| Result | Held-out evidence | Walk-forward interpretation |
|---|---|---|
| BTC Phase 2 general FinBERT vs. market-only | MAE 0.016615 vs. 0.016727 (0.67% improvement), not Holm-significant | 0.016647 vs. 0.016750; directionally consistent but not significant |
| BTC general vs. crypto-specific FinBERT | 0.016615 vs. 0.017040; Holm-adjusted DM-HAC p = 0.00335 | Same ordering (0.016647 vs. 0.016892), but not significant after Holm correction |
| ETH crypto-specific vs. general FinBERT | 0.023513 vs. 0.024451; 3.84% improvement; Holm-adjusted DM-HAC p = 0.00615 | Same ordering (0.023191 vs. 0.023390), but not significant after Holm correction |
| BTC Phase 4 decay-only vs. Phase 3 reference | 0.016763 vs. 0.017040; 1.63% improvement; Holm-adjusted DM-HAC p = 0.0331 | 0.016731 vs. 0.016892; directionally favorable but not significant |
| ETH Phase 5 reliability fusion vs. general FinBERT | 0.023150 vs. 0.024451; 5.32% improvement; Holm-adjusted DM-HAC p = 0.0105 | Lowest ETH LSTM MAE (0.023086), but no Phase 5 walk-forward comparison survives Holm correction |

## Reproducibility audit

The final v3 pipeline passes:

- 28/28 canonical prediction-reuse checks
- 78/78 repeated-method metric-consistency checks
- 112/112 metric-to-significance linkage checks

The overall conclusion is intentionally conservative: news sentiment provides conditional, asset-dependent, and regime-sensitive incremental information rather than a universal forecasting advantage.
