# Completed actual-market evidence

Data: Ethereum mainnet Uniswap v2 USDC/WETH, January 1–February 25, 2024. Of 129,289 swaps, 126,934 (98.18%) match the declared exact ordinary maximum-output transition. The test period has 26,453 events over ten calendar days. Three training repeats share all observations and test origins. The primary neural model does not improve on strong simple controls; synthetic pretraining with the declared bias adapter does not save fitting labels. See [the evidence assessment](../../../paper/capstone_results.md).

| File | Contents |
| --- | --- |
| `split.json` | Whole-block time boundaries, UTC dates, available/used sample counts and deterministic sample hashes. |
| `flow.csv` | 30 full-information/AMM-only model evaluations over all test events. |
| `daily_flow.csv` | 300 daily evaluations used for dependence-aware paired comparisons. |
| `flow_summary.csv` | Ten model summaries; `source_sd` is across-training-seed SD, not an independent-market SE. |
| `adaptation.csv` | 1,290 daily rows across common target budgets; available and actually fitted labels are separate fields. |
| `paths.csv` | 600 ensemble evaluations at common daily origins over 10/50 swaps; 200 draws each. |
| `paired.csv` | 28 primary/secondary descriptive paired calendar-block intervals. Negative differences favor the challenger. |
| `training_diagnostics.csv` | 66 real fitting records, parameter counts, sample budgets and checkpoint diagnostics. |
| `adaptation_and_calibration.png` | All declared adaptation budgets and empirical terminal coverage. |
| `path_ensembles.png` | First eligible test origin/first declared training seed, MLP and ridge; no trajectory selection by performance. |

CRPS/widths are in log-price coordinates; flow RMSE is signed gross input divided by the input-side pre-swap reserve. All path rows have zero measured structural violations, shared by every estimator using the mechanism map. The ten days and three-day bootstrap blocks provide limited temporal evidence. Forecast, calibration and transfer performance remain distinct from structural validity. The parent manifest contains exact versions, input/code/protocol hashes and execution status.
