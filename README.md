# TSFM_VaR_CEE

Reproduction code for the paper:

**Can Foundation Models Manage Risk? Zero-Shot VaR and ES Forecasting with
Conformal Calibration in CEE Markets**

Siang-Li Jheng, Rahul Tak, Ștefan Găman, Miruna Mazurencu-Marinescu-Pele,
Daniel Traian Pele (corresponding author — danpele@ase.ro)

Bucharest University of Economic Studies · Institute for Economic Forecasting,
Romanian Academy

*Economic Computation and Economic Cybernetics Studies and Research* (ECECSR), 2026.

## Overview

Zero-shot Value-at-Risk (VaR) and Expected Shortfall (ES) forecasting for five
CEE equity indices (BET, WIG20, PX, BUX, SOFIX) and five FX pairs (EUR/RON,
EUR/PLN, EUR/CZK, EUR/HUF, USD/BGN), comparing time-series foundation models
(Chronos-2, TimesFM 2.5, Moirai 2.0) — raw and conformally calibrated — against
econometric baselines (GJR-GARCH, Historical Simulation, ARIMA-Conformal,
LSTM-Conformal) under the Basel traffic-light framework.

Each Quantlet is a self-contained Jupyter notebook that imports shared settings
from `config.py`.

## Repository structure (Quantlets)

| Quantlet | Purpose |
|---|---|
| `VaR_CEE_DataDownload` | Download raw index / FX series |
| `VaR_CEE_DataPipeline` | Clean, align, compute log-returns |
| `VaR_CEE_GJRGARCH` | GJR-GARCH baseline VaR / ES |
| `VaR_CEE_HistoricalSim` | Historical Simulation baseline |
| `VaR_CEE_Chronos` | Chronos-2 zero-shot forecasts |
| `VaR_CEE_TimesFM` | TimesFM zero-shot forecasts |
| `VaR_CEE_Moirai` | Moirai zero-shot forecasts |
| `VaR_CEE_ConformalARIMA` | ARIMA + conformal prediction |
| `VaR_CEE_ConformalLSTM` | LSTM + conformal prediction |
| `VaR_CEE_ConformalFM` | Conformal calibration of TSFMs |
| `VaR_CEE_Backtesting` | Kupiec, Christoffersen, Acerbi-Szekely, Basel zones |
| `VaR_CEE_DMTest` | Diebold-Mariano tests |
| `VaR_CEE_Figures` | All paper figures |

`config.py` — shared paths, market definitions, and parameters used by every
Quantlet (sample 2007-01-01 to 2025-12-31; out-of-sample from 2018-01-01;
rolling window 250 days; VaR levels 1%, 2.5%, 5%; ES level 2.5%; foundation-model
context 512, 1000 samples, 1-step horizon; seed 42).

## How to run

Edit `config.py` if needed, then execute the notebooks in this order:

```bash
jupyter nbconvert --to notebook --execute VaR_CEE_DataDownload/VaR_CEE_DataDownload.ipynb
jupyter nbconvert --to notebook --execute VaR_CEE_DataPipeline/VaR_CEE_DataPipeline.ipynb
jupyter nbconvert --to notebook --execute VaR_CEE_GJRGARCH/VaR_CEE_GJRGARCH.ipynb
jupyter nbconvert --to notebook --execute VaR_CEE_HistoricalSim/VaR_CEE_HistoricalSim.ipynb
jupyter nbconvert --to notebook --execute VaR_CEE_Chronos/VaR_CEE_Chronos.ipynb
jupyter nbconvert --to notebook --execute VaR_CEE_TimesFM/VaR_CEE_TimesFM.ipynb
jupyter nbconvert --to notebook --execute VaR_CEE_Moirai/VaR_CEE_Moirai.ipynb
jupyter nbconvert --to notebook --execute VaR_CEE_ConformalARIMA/VaR_CEE_ConformalARIMA.ipynb
jupyter nbconvert --to notebook --execute VaR_CEE_ConformalLSTM/VaR_CEE_ConformalLSTM.ipynb
jupyter nbconvert --to notebook --execute VaR_CEE_ConformalFM/VaR_CEE_ConformalFM.ipynb
jupyter nbconvert --to notebook --execute VaR_CEE_Backtesting/VaR_CEE_Backtesting.ipynb
jupyter nbconvert --to notebook --execute VaR_CEE_DMTest/VaR_CEE_DMTest.ipynb
jupyter nbconvert --to notebook --execute VaR_CEE_Figures/VaR_CEE_Figures.ipynb
```

Outputs are written to `data/` (`raw`, `processed`, `var_forecasts`,
`backtesting`, `figures`, `stats`).

## Environment

The foundation models require separate environments (Chronos, TimesFM, Moirai
have conflicting dependencies); baselines and analysis run in a common
environment.

> TODO: add `requirements.txt` / environment files and exact package versions.

## Data

Daily equity-index and FX series from Stooq / Yahoo Finance (see
`VaR_CEE_DataDownload` for tickers and retrieval).

## Citation

See [`CITATION.cff`](CITATION.cff).

## License

MIT — see [`LICENSE`](LICENSE).
