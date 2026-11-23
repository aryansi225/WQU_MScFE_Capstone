# Final synthetic and actual-market capstone run

This folder contains the completed fixed synthetic configuration and the actual-market results in [real_market/](real_market/README.md). The canonical executed notebook is `notebooks/capstone_amm_study.ipynb`. Read [the findings assessment](../../paper/capstone_results.md) for the supported and unsupported claims.

Configuration: CPMM and binary LMSR; null-noise, planted nonlinear and external-reference scenarios; three independently sampled source-training repeats; ten independent target paths per mechanism/scenario; 192 events per path; 200 predictive draws; 10/50-swap horizons. Source repeats are evaluated on the same target markets. Models remain small: a 481-parameter MLP and a 769-parameter GRU alongside simple controls.

The complete synthetic-plus-real run completed in **51.46 seconds on CPU**, reusing the saved data. Reproduce it with:

```bash
/workspace/.venv-notebooks/bin/python notebooks/run_study.py --profile final
```

| Artifact | Contents |
| --- | --- |
| `flow.csv` | 1,260 one-step normalized-flow evaluations; all three scenarios retained. |
| `flow_summary.csv` | 42 summaries with target-market SE and source-repeat SD recorded separately. |
| `flow_paired.csv` | 24 paired contrasts of MLP with simple/reference/sequence baselines. |
| `adaptation.csv`, `paired.csv` | 1,980 equal-budget common-suffix evaluations and 30 descriptive paired contrasts. |
| `paths.csv`, `path_paired.csv` | 840 predictive-path evaluations and 16 terminal-CRPS contrasts in the reference-signal scenario. |
| `training_diagnostics.csv` | 126 selected source models, model sizes, sample counts and training-budget diagnostics. |
| `path_ensembles.png` | Preselected first-market MLP/ridge path illustration with predictive intervals. |
| `adaptation_and_calibration.png` | Common-suffix adaptation and observed interval coverage. |
| `protocol.json`, `manifest.json`, `execution.json` | Fixed configuration, seeds, package versions, code/protocol hashes and execution status. |

Path metrics include predictive-mean error, terminal CRPS, coverage/width, a common validation-threshold tail Brier score, downward coordinate-excursion error and measured structural violations. Log-price and log-odds errors are reported separately. The observed zero structural violations are the expected property of the mechanism maps, not evidence of forecasting superiority. Paired intervals are descriptive and are not adjusted for multiple comparisons.

The null scenario is labeled `null_noise` so ordinary CSV readers preserve it as a scenario name. Fixture validation is retained separately in `notebook_results/demo/fixture_pipeline_check/` and labeled `synthetic_fixture`. The actual-market execution is complete: 126,934 reconciled swaps, 26,453 untouched test events, ten test days, 600 path evaluations, and 28 descriptive paired contrasts. The simple reference-gap model has the best one-step point score; neural and synthetic-pretraining superiority are not supported in this window.
