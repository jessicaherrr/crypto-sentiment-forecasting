# Paper 1 final consistency checklist

- Require `canonical_prediction_reuse_check.csv`, `repeated_method_consistency_check.csv`, and `metric_significance_consistency_check.csv` to pass before manuscript drafting.
- Copy all reported MAE/RMSE/R2/DA values from `paper1_results_registry.csv`.
- Copy inferential p-values from `paper1_significance_registry.csv`; identify raw vs Holm-adjusted values explicitly.
- Use DM-HAC as the primary forecast-loss comparison and two-sided Wilcoxon as the nonparametric robustness check.
- Do not compare classification accuracy values from prior literature numerically with this study's regression MAE/RMSE/R2.
- State the UTC news window, forecast origin, and close-to-close target interval explicitly.
- Report the validation-selected Phase 4 decay half-life/rate exactly as stored in `selected_decay_rate.json`.
- Use five-seed walk-forward summaries, not the legacy seed-42-only result.
- Keep Phase 5 exploratory and brief; report the provider-volume sensitivity audit.
- Regenerate final figures from final CSV outputs; do not transcribe intermediate console numbers.
