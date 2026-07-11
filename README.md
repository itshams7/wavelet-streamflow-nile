# Wavelet-Neural Network Streamflow Forecasting: Nile Basin, Sudan & South Sudan

Monthly discharge forecasting using wavelet-decomposed neural networks (WA-MLP), benchmarked against Naive, ARIMA, raw MLP, and Random Forest models across five long-record GRDC gauging stations on the Blue Nile and White Nile.

This project was developed as an independent research study in support of a graduate application to McGill University's Integrated Water Resources Management (IWRM) program, and is methodologically aligned with wavelet-hydrology approaches developed by Dr. Jan Adamowski and colleagues.

## Stations

| Station | River | Country | Record Period (approx.) |
|---|---|---|---|
| Khartoum | Blue Nile | Sudan | 1900s-1980s |
| Sennar | Blue Nile | Sudan | 1900s-1980s |
| Roseires | Blue Nile | Sudan | 1900s-1980s |
| Dongola | Main Nile | Sudan | 1900s-1980s |
| Malakal | White Nile | South Sudan | 1900s-1980s |

Data: monthly discharge records from the Global Runoff Data Centre (GRDC). See data/DATA_ACCESS.md for how to obtain the raw files.

## Methods

- Signal decomposition: Discrete Wavelet Transform (PyWavelets) decomposing each discharge series into approximation (trend) and detail (high-frequency) sub-signals, used as engineered inputs to the forecasting models.
- Models: Naive persistence, ARIMA (statsmodels), raw-input MLP, wavelet-input MLP (scikit-learn MLPRegressor), and Random Forest (RandomForestRegressor) benchmark.
- Evaluation: RMSE, R-squared, Nash-Sutcliffe Efficiency (NSE), Kling-Gupta Efficiency (KGE), and Wilcoxon signed-rank tests for paired-model significance.
- Robustness testing: random dropout and contiguous block-gap missing-data scenarios (0-40%).
- Multi-horizon forecasting: 1, 3, 6, and 12-month-ahead evaluation.
- Transfer learning: same-basin (Blue Nile to Blue Nile) and cross-basin (Blue Nile to White Nile) generalization tests.

## Key Findings

1. Wavelet-MLP outperforms all baselines at all 5 stations across all 4 metrics.
2. Wavelet-MLP is substantially more stable than raw MLP under both random and contiguous missing-data gaps.
3. Wavelet benefit tracks basin hydrology: the Blue Nile (26-31% high-frequency energy) sees a larger boost than the buffered White Nile (~92% trend energy, Lake Victoria/Sudd-regulated), where the signal is already smooth.
4. Random Forest benefits from wavelet inputs at 4 of 5 stations - the wavelet advantage is more consistent for neural networks than tree ensembles.
5. Wilcoxon signed-rank tests confirm the wavelet-MLP improvement is statistically significant at all 5 stations (p < 0.05; p ~ 0 at 4 stations, p = 0.011 at Malakal).
6. The wavelet advantage is strongest at short forecast horizons (1-3 months) and narrows at longer horizons, with a slight reversal at Malakal at 12 months.
7. Transfer learning succeeds within-basin (Blue Nile to unseen Khartoum, NSE = 0.98) but fails across basins (Blue Nile to Malakal, NSE = 0.11-0.19), consistent with hydrological expectations, though wavelet inputs still outperform raw inputs even in the failure case.

## Repository Structure

notebooks folder - Analysis notebooks (Colab-developed)
figures folder - All 10 output figures (fig0-fig9)
data folder - GRDC data-access notes
results folder - Metric tables, significance test outputs
requirements.txt
README.md

## Figures

| # | Description |
|---|---|
| fig0 | Example wavelet decomposition |
| fig1 | Hydrograph overview, all stations |
| fig2 | Baseline model comparison (Naive/ARIMA/MLP/WA-MLP) |
| fig3 | Wavelet energy distribution by station |
| fig4 | Missing-data robustness (random + block-gap) |
| fig5 | Multi-horizon forecast performance |
| fig6 | Transfer learning results |
| fig7 | Random Forest comparison |
| fig8 | Statistical significance table |
| fig9 | Study area map |

## Data Source

Discharge data from the Global Runoff Data Centre (GRDC), Koblenz, Germany: https://www.bafg.de/GRDC/EN/Home/homepage_node.html

## Author

Shamseldin Abdelrahim - developed as an independent research study motivated by water security challenges facing communities across the Nile Basin, where reliable streamflow forecasting directly supports flood preparedness, irrigation planning, and drought resilience in data-scarce regions.

## License

Code: MIT License. GRDC data subject to GRDC's own data policy/terms of use - see the GRDC portal for redistribution rules before including raw data files in this repository.
