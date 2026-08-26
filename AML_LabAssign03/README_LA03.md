# Applied Machine Learning --- Lab Assignment 3

**Course:** CSAI2017P --- Applied Machine Learning (Lab)\
**Name:** Abhishek Bhatt\
**SAP ID:** 590028847\
**Batch:** B-05

## Objective

To build a time-series regression model for stock price prediction using
daily stock data, generate lag-based features, compare different
train-test splitting strategies, evaluate the model against a naive
baseline, and assess its usefulness for trading decisions.

## A1 --- Load and Describe the Series

The daily stock price history of **RELIANCE.NS** was downloaded using
the `yfinance` library and sorted in chronological order.

  Property       Result
  -------------- -------------
  Ticker         RELIANCE.NS
  Start Date     2021-08-26
  End Date       2026-08-26
  Trading Days   1240

**Observation:**\
The dataset contains daily stock prices of RELIANCE.NS arranged in
chronological order. It covers approximately five years of trading
history with 1240 trading days. Unlike tabular datasets, the order of
rows is important because previous prices are used to predict future
prices.

------------------------------------------------------------------------

## A2 --- Lag Features

Lag features were created using the previous one, two and three closing
prices along with a five-day rolling average. The target variable was
defined as the next day's closing price.

**Observation:**\
Lag features capture information from previous trading days, while the
rolling mean summarizes recent price movements. The first few rows
contain missing values because sufficient historical data is unavailable
for lag calculations, so these rows were removed before model training.

------------------------------------------------------------------------

## A3 --- Naive Baseline

The persistence baseline predicts that tomorrow's closing price will be
equal to today's closing price.

  Metric                        Value
  -------- --------------------------
  MAE        *(Update from notebook)*
  RMSE       *(Update from notebook)*

**Observation:**\
The naive baseline provides a simple benchmark for evaluating
forecasting models. Any machine learning model should achieve lower
prediction error than this baseline to demonstrate that it has learned
meaningful patterns from the historical data.

------------------------------------------------------------------------

## B1 --- Random Split versus Chronological Split

A Random Forest Regressor was trained using two different train-test
splitting strategies.

  Method                  Test MAE
  --------------------- ----------
  Random Split             18.7856
  Chronological Split      19.5120

**Observation:**\
The random split achieved a slightly lower MAE than the chronological
split because shuffling mixes observations from different time periods.
This introduces data leakage and produces an unrealistically optimistic
evaluation. For time-series forecasting, chronological splitting
provides a more reliable estimate of real-world performance.

------------------------------------------------------------------------

## C1 --- Would You Trade on It?

The model's predicted prices were converted into up/down movement
predictions and compared with the actual market direction.

  Metric                    Value
  ---------------------- --------
  Directional Accuracy     56.28%

**Observation:**\
The model correctly predicted the direction of price movement
approximately 56.28% of the time, which is only slightly better than
random guessing. Although the regression error is reasonably low, this
level of directional accuracy is not sufficient for reliable trading
decisions. More informative features and more advanced forecasting
techniques would be required before using the model in practice.

------------------------------------------------------------------------

## Conclusion

This experiment demonstrated how time-series regression differs from
traditional regression problems. Lag features and rolling averages were
used to transform historical stock prices into supervised learning
features. The comparison between random and chronological train-test
splits highlighted the importance of preserving temporal order to avoid
data leakage. Finally, evaluating directional accuracy showed that a
regression model with acceptable prediction error is not necessarily
suitable for making profitable trading decisions.
