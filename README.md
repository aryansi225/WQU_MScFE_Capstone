# Compact capstone submission

The code submission is two self-contained notebooks. No `amm_sim` package or production application is required.

1. Extract this bundle and use the extracted `capstone/` folder as the working directory. In Colab, upload/unzip the bundle and change the runtime working directory to that folder before executing the notebook.
2. Run `notebooks/capstone_amm_study.ipynb` top to bottom. The included frozen real dataset requires no API key or internet access for data acquisition. Install the libraries in `notebooks/requirements.txt` if the runtime lacks them; Colab normally supplies the scientific stack. All models run on CPU.
3. The main notebook contains the complete synthetic/real forecasting, adaptation and path experiments. Results and package versions are exported under `notebook_results/final/`.
4. `notebooks/prepare_real_data.ipynb` documents the complete source query and reconstruction. With acquisition disabled, it runs offline fixture checks. To collect a fresh copy, choose a NEW data directory, set `AMM_ACQUIRE=1`, and provide `AMM_RPC_URL` through the environment. In Colab, a saved secret must first be read using `google.colab.userdata.get` and assigned to that environment variable. Never place credentials in notebook source or outputs.

The compact bundle includes the cleaned inputs and their original frozen checksums, reconciliation, query ledger and data card. Large raw responses, block metadata, price archives and the SQLite restart cache remain outside this compact bundle. A separate raw-source archive accompanies it. To regenerate sources, use a new directory rather than the compact input directory: the original complete checksum list deliberately references raw files omitted here.

Read `paper/capstone_results.md` for the evidence and claim limits. `paper/real_data_protocol.md` and the local pre-evaluation hash record document the fixed protocol; this is an internal freeze record, not a claim of public preregistration. Notebook execution was validated in fresh local Jupyter kernels; an actual Google Colab execution has not been performed. The completed capstone writeup is included under `paper/report/`, with its PDF and editable LaTeX source ZIP. Author/group/date fields are intentionally dummy values in the source ZIP's `metadata.tex`. The presentation remains separate.

A standalone reproduction from this bundle folder passed in a fresh local kernel in 49.5 seconds, without the project package or credentials. All 15 evidence CSV tables and the protocol reproduced byte for byte. See `reproduction_report.json`.
