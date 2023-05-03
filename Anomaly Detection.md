---

created: <% tp.file.creation_date() %>

---
tags:: #TimeSeries #MachineLearning #DataScience #Unsupervised


# Unsupervised Anomaly Detection on Time Series

## Probability Based Approaches
Using a **Z-score** is one of the most straightforward approaches. It stands for the number of standard deviations an observation is from the mean of the distribution. It assumes the each feature fits a normal distribution. note that when estimating these score you should take into account the several factors that affect the pattern.

Note: *Z-scores* can be used as inputs for other anomaly detection models as well.

**Quartiles-based** solutions are similar to the **z-score** except the take into account the median instead of the mean, but it all depends on the distribution of the data as to which you choose.

**Elliptic Envelope** is another option for outlier detection, which fits a multivariate gaussian distribution to the data. However, it might not perform well with high dimensional data.

Drawbacks:
- It assumes that features fit a normal distribution.
- It ignores correlations between features


## Forecasting Based Approaches
A prediction is performed with a forecasting model for the next time period and if forecasting value is out of the confidence interval, the sample is flagged as an anomaly.

Common models: [[LSTM]] [[ARIMA]]

- Can often just apply these forecasting models to a time series without feature engineering.
- Estimating confidence intervals is not a trivial or easy task.
- Accuracy of forecasting model has a direct effect on the success of the anomaly detection.
- You can evaluate the accuracy of the forecasting model as in supervised learning.

[[Prophet]] is a forecasting algorithm designed for time series developed by Facebook.


## Neural Network Based Approaches
## Clustering Based Approaches
## Proximity Based Approaches
## Tree Based Approaches
## Dimension Reduction Based Approaches

## General Guidance
- Before starting ask the following questions:
	- How much data do we have retroactivly?
	- Univariate or multivariate data ?
	- What is the frequency we want to perform anomaly detection?

- Do we have multiple items? i.e different wind turbines etc.
	- We want to avoid designing seperate models.
	- Selecting correct features is more functional than focusing on different models.
	- Determine the patterns of each item, considering properties of the time. Extract deviation from their patterns (like z-scores) and feed the models with these features. a [[multi head neural network]] is an advanced model here.

-