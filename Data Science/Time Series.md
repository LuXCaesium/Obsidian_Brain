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

- $cov(X_t, X_{t+k})  =\gamma_k$ where the sequence $\{\gamma_k, k \in \mathbb{Z}\}$ is called the *autocovariance function.*

- $\rho_k = \frac{\gamma_k}{\gamma_0} = corr(X_t, X_{t+k})$ and call $\{\rho_k, k \in \mathbb{z}\}$ the *autocorrelation function* (ACF)

### Seasonality
This refers to periodic fluctuations. For example electricity consumption is high during the day and low during the night.

Looking at the autocorrelation plot will highlight any seasonality in the data. You would expect high correlation at certain periodic points in the series.

### Stationarity
Is a very important characteristic of time series, with many algorithms being dependent upon it. A time series is stationary if has constant mean and variance, and covariance is independent of time. Formally:

A sequence $\{X_t, t \in \mathbb{Z}\}$ is **strongly stationary** or **strictly stationary** if
$(X_t, \dots, X_{t_k}) \stackrel{\mathcal{D}}{=} (X_{t_1+h}, \dots, x_{t_k+h})$
$ \all t_1, \dots, t_k$

If we have a time series that is not stationary, there are various transformations we can apply to make them so.

## Classification

[[Nearest-Neighbour with Dynamic Warping]]
[[kernel Methods]]


