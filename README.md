# Comparative Time Series Forecasting of Temperature in the Davao Region, Philippines

A comparative time series analysis of monthly mean surface air temperature in Davao City, Philippines, using statistical forecasting, multivariate time series models, climate indices, and deep learning.

## Project Overview

This project examines historical temperature patterns and forecasts future monthly mean surface air temperature using meteorological variables and large-scale climate indices. It compares univariate statistical forecasting, multivariate time series analysis, and deep learning to evaluate their forecasting performance and investigate the predictive relationships between climate variables and temperature.

The analysis uses historical climate data from NASA POWER and climate indices from NOAA, covering January 1981 through the most recent observation available in the dataset.

## Research Objectives

This project aims to:

1. Analyze historical monthly temperature patterns in Davao City.
2. Examine the relationships between temperature, meteorological variables, and large-scale climate indices.
3. Investigate Granger causality to determine whether past values of climate variables improve temperature prediction.
4. Develop and compare univariate, multivariate, and deep learning forecasting models.
5. Evaluate forecasting accuracy using statistical performance metrics.
6. Generate monthly temperature forecasts for a 12-month horizon.

## Data Sources

- **NASA POWER:** Meteorological observations and derived climate variables.
- **NOAA:** Large-scale climate indices associated with ocean-atmosphere variability.

### Variables

| Variable | Description |
|---|---|
| T2M | Temperature at 2 meters |
| RH2M | Relative humidity at 2 meters |
| PRECTOTCORR | Corrected precipitation |
| PS | Surface pressure |
| ALLSKY_SFC_SW_DWN | All-sky surface shortwave downward radiation |
| NINO34 | Niño 3.4 climate index |
| SOI | Southern Oscillation Index |
| PDO | Pacific Decadal Oscillation |
| DMI | Dipole Mode Index |

## Methodology

### 1. Data Preparation and Exploratory Analysis

The workflow includes data collection, date alignment, missing-value assessment, descriptive statistics, visualization, and time series exploration. Stationarity tests and differencing are used where appropriate to prepare the data for time series modeling.

### 2. Univariate Forecasting

**Seasonal Autoregressive Integrated Moving Average (SARIMA)** models the historical temperature series using its temporal structure and seasonal patterns.

### 3. Multivariate Time Series Analysis

**Vector Autoregression (VAR)** and **Vector Error Correction Model (VECM)** are used to investigate dynamic relationships among temperature and climate variables.

The analysis includes:

- Lag-order selection using information criteria
- Granger causality testing
- Cointegration testing
- Impulse response functions (IRF)
- Forecast error variance decomposition (FEVD)

These methods examine temporal predictive relationships, long-run associations where supported by cointegration, and the modeled responses of variables to shocks.

### 4. Deep Learning

A **Long Short-Term Memory (LSTM)** neural network is used to learn temporal patterns from historical climate data and generate temperature forecasts.

### 5. Forecast Evaluation

The models are compared using forecasting error metrics, including Root Mean Squared Error (RMSE). A seasonal naive forecast provides a baseline for evaluating whether more complex models improve predictive accuracy.

## Granger Causality Analysis

Granger causality testing examines whether past values of a predictor provide additional information for forecasting temperature.

The null hypothesis is:

**H₀:** The predictor does not Granger-cause temperature.

At the 5% significance level:

- **Reject H₀:** Evidence that the predictor provides additional lagged predictive information under the specified test.
- **Fail to reject H₀:** Insufficient evidence to establish additional lagged predictive information.

Granger causality does not establish physical or experimental causation. Pairwise tests also do not control for every other variable in the climate system, so conditional multivariate testing and appropriate diagnostic checks are needed before drawing stronger conclusions.

## Preliminary Forecasting Results

The notebook reports the following RMSE values:

| Model | RMSE (°C) |
|---|---:|
| SARIMA | 0.2638 |
| VECM | 0.3313 |
| Seasonal Naive | 0.3682 |
| LSTM | 0.4042 |

Lower RMSE represents better predictive accuracy on the evaluated data. In the reported comparison, SARIMA achieved the lowest RMSE, followed by VECM, the seasonal naive baseline, and LSTM.

These results apply to the evaluation setup used in the notebook. A fair comparison requires consistent forecast periods, data splits, and preprocessing, with no leakage from future observations.

## Technologies Used

- Python
- Jupyter Notebook
- pandas and NumPy
- Matplotlib and Seaborn
- statsmodels
- scikit-learn
- TensorFlow/Keras
- NASA POWER data services
- NOAA climate data

## Repository Contents

- `Davao_Time_Series_TM2.ipynb` — Main notebook containing data preparation, exploratory analysis, statistical testing, model development, forecasting, and evaluation.

## How to Run

1. Clone this repository:

   ```bash
   git clone https://github.com/JohnAnalytics0315/Time-Series-Analysis.git
   ```

2. Navigate to the project directory:

   ```bash
   cd Time-Series-Analysis
   ```

3. Install the required Python packages:

   ```bash
   pip install pandas numpy matplotlib seaborn statsmodels scikit-learn tensorflow jupyter
   ```

4. Launch Jupyter Notebook:

   ```bash
   jupyter notebook
   ```

5. Open `Davao_Time_Series_TM2.ipynb` and run the cells in sequence.

   If the notebook retrieves data from external services, an internet connection may be required. Review the notebook's data paths and date settings before running it.

## Limitations

- Climate data may contain missing observations and require careful preprocessing.
- Results depend on the selected lag order, model specification, and forecast evaluation period.
- Pairwise Granger causality tests do not establish independent predictive effects after controlling for all other variables.
- Cointegration rank and model residual diagnostics require careful validation.
- LSTM performance depends on the training configuration, sample size, and evaluation design.
- Forecasts represent model-based estimates and are subject to uncertainty.

## Future Improvements

- Apply conditional multivariate Granger causality tests.
- Correct for multiple hypothesis testing.
- Validate lag selection, cointegration rank, and residual assumptions.
- Compare models using rolling-origin or expanding-window evaluation.
- Add prediction intervals and forecast uncertainty analysis.
- Test whether causality-based feature selection improves out-of-sample accuracy.
- Reconcile the dataset's final observation date with the forecast horizon and update saved forecast tables.

## Author

**JohnAnalytics0315**

GitHub: [JohnAnalytics0315](https://github.com/JohnAnalytics0315)

