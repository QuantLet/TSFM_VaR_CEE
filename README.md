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
CEE equity indices (BET, WIG20, PX, BUX, SOFIX) and five FX pairs, comparing
time-series foundation models (Chronos-2, TimesFM, Moirai) — raw and conformally
calibrated — against econometric baselines (GJR-GARCH, Historical Simulation)
under the Basel traffic-light framework.

## Repository structure (Quantlets)

| Quantlet | Purpose |
|---|---|
| `VaR_CEE_DataDownload`   | Download raw index / FX series |
| `VaR_CEE_DataPipeline`   | Clean, align, compute log-returns |
| `VaR_CEE_GJRGARCH`       | GJR-GARCH baseline VaR / ES |
| `VaR_CEE_HistoricalSim`  | Historical Simulation baseline |
| `VaR_CEE_Chronos`        | Chronos-2 zero-shot forecasts |
| `VaR_CEE_TimesFM`        | TimesFM zero-shot forecasts |
| `VaR_CEE_Moirai`         | Moirai zero-shot forecasts |
| `VaR_CEE_ConformalARIMA` | ARIMA + conformal prediction |
| `VaR_CEE_ConformalLSTM`  | LSTM + conformal prediction |
| `VaR_CEE_ConformalFM`    | Conformal calibration of TSFMs |
| `VaR_CEE_Backtesting`    | Kupiec, Christoffersen, Acerbi–Szekely, Basel zones |
| `VaR_CEE_DMTest`         | Diebold–Mariano tests |
| `VaR_CEE_Figures`        | All paper figures |

## How to run

Global settings (paths, tickers, sample window, confidence levels) live in
`config.py`. Run the Quantlets in the following order:

```bash
```bash
python VaR_CEE_DataDownload VaR_CEE_DataPipeline VaR_CEE_GJRGARCH VaR_CEE_HistoricalSim VaR_CEE_Chronos VaR_CEE_TimesFM VaR_CEE_Moirai VaR_CEE_ConformalARIMA VaR_CEE_ConformalLSTM VaR_CEE_ConformalFM VaR_CEE_Backtesting VaR_CEE_DMTest VaR_CEE_Figures/<script>
```

## Data

Daily equity-index and FX series (see `VaR_CEE_DataDownload` for sources and the
sample period). Intermediate datasets are written to `data/`.

> TODO: add exact sample period, data vendor, and Python/`requirements.txt`.

## Citation

See [`CITATION.cff`](CITATION.cff).

## License

MIT — see [`LICENSE`](LICENSE).
