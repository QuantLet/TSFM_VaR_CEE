<div style="margin: 0; padding: 0; text-align: center; border: none;">
<a href="https://quantlet.com" target="_blank" style="text-decoration: none; border: none;">
<img src="https://github.com/StefanGam/test-repo/blob/main/quantlet_design.png?raw=true" alt="Header Image" width="100%" style="margin: 0; padding: 0; display: block; border: none;" />
</a>
</div>

```
Name of Quantlet: VaR_CEE_DMTest

Published in: Can Foundation Models Manage Risk? Zero-Shot VaR and ES Forecasting with Conformal Calibration in CEE Markets

Description: Performs pairwise Diebold-Mariano tests using asymmetric tick (quantile) loss at the 1% VaR level across all 10 models and 10 CEE series. Pools tick losses across series, computes DM statistics with Harvey et al. small-sample correction, and produces a p-value heatmap with significance annotations.

Keywords: Diebold-Mariano test, forecast comparison, tick loss, quantile loss, Value-at-Risk, predictive accuracy, heatmap, hypothesis testing, CEE markets

Author: Daniel Traian Pele

Submitted: 23 April 2026

Datafile: ../data/var_forecasts/*.csv

Input: VaR forecast CSV files for all 10 models and 10 series, each containing columns date, y_true, var_01

Output: dm_tick_loss_1pct.csv (45 pairwise comparisons with DM statistics, p-values, significance flags), fig10_dm_heatmap.png

Example: Computes DM statistic comparing TimesFM-2.5 vs GJR-GARCH tick loss pooled across all CEE series, tests at 1%, 5%, 10% significance

```
