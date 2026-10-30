# Wavelet–Neural Streamflow Forecasting in the Nile Basin

**Hydrology | Time-series forecasting | Environmental data science**

## Overview

An independent modelling study of monthly streamflow forecasting across selected Nile Basin gauging stations in Sudan and South Sudan. The project compares wavelet-assisted neural networks with conventional statistical and machine-learning baselines, including tests of missing-data robustness and cross-station transfer.

## Study Area and Data

The analysis uses monthly discharge records associated with five stations: Khartoum, Sennar, Roseires, Dongola and Malakal.

**Data source:** [Global Runoff Data Centre (GRDC)](https://www.bafg.de/GRDC/EN/Home/homepage_node.html). See the repository's data-access documentation for source and redistribution considerations.

## Methods

- Discrete wavelet decomposition and engineered time-series features
- Naive persistence, ARIMA, multilayer perceptron and random forest baselines
- Forecast evaluation using RMSE, R², NSE and KGE
- Random and contiguous missing-data scenarios, up to 40%
- Forecast horizons of 1, 3, 6 and 12 months
- Within-basin and cross-basin transfer experiments

## Reported Findings

The study reports stronger performance for the wavelet-assisted MLP than the tested baselines in its principal station-level comparisons, with improved robustness under simulated missing observations. Reported transfer results are more favourable within the Blue Nile than between hydrologically distinct basins.

These conclusions describe the experiments in this repository and should not be generalized beyond the datasets and evaluation design without further validation.

## Repository Guide

| Path | Contents |
| --- | --- |
| `notebooks/` | Analysis notebook |
| `figures/` | Study figures |
| `data/` | Data-access documentation and supporting materials |
| `requirements.txt` | Python package requirements |
| `README.md` | Project summary |

## Research Context

The work is motivated by flood preparedness, irrigation planning and water-security challenges in data-scarce environments.

## Author

Shamseldin Abdelrahim
