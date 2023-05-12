---

created: <% tp.file.creation_date() %>

---
tags:: #TimeSeries #MachineLearning #DataScience 

# Time Series

A time series is simply a series of data points order in time. Time is often an independent variable and the goal is usually to make a forecast for the future.

## General analysis
There are many aspects that come into play when dealing with time series.
- Is it **stationary?**
- Is there **seasonality?**
- Is the target variable **autocorrelated?**

### Autocorrelation
Informally, autocorrelation is the similarity between observations as a function of the time lag between them. Formally:

$cov(X_t, X_{t+k})  =\gamma_k$ where the sequence $\{\gamma_k, k \in \mathbb{Z}\}$ is called the *autocovariance function.*



## Classification

[[Nearest-Neighbour with Dynamic Warping]]
[[kernel Methods]]


