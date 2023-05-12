---

created: <% tp.file.creation_date() %>

---
tags:: #TimeSeries #MachineLearning #DataScience 

# Time Series

A time series is simply a series of data points order in time. Time is often an independent variable and the goal is usually to make a forecast for the future. There are four main components of a time series, and each one will be discussed in terms of analysis.
- trend
- seasonality
- cycles
- residuals

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
$(X_t, \dots, X_{t_k}) \stackrel{\mathcal{D}}{=} (X_{t_1+h}, \dots, x_{t_k+h})$ $\forall t_1, \dots, t_k$ and $h \in \mathbb{Z}$
essentially the time series has the same distribution over all time points.

A sequence is **weakly stationary**, or **second order stationary** if
- $\mathbb{E}(X_t) = \mu$
- $cov(X_t, X_{t+k}) = \gamma_k$
where $\mu$ is constant and $\gamma_k$ is independent of $t$.

If we have a time series that is not stationary, there are various transformations we can apply to make them so.

#### Tests for stationarity
There are several techniques to tets for stationarity. 

- **Augmented Dickey-Fuller**
	- Essentially its tests the null hypothesis that a unit root is present in an autoregressive (AR) time series model.

- **Kwiatkowski-Phillips-Schmidt-Shin**
	- Testing a null hypothesis that an observable time series is stationary around a deterministic trend against the alternative of a unit root.

### Converting Non-Stationary into Stationary
There are three methods available for this conversion:

#### Detrending
It involves the removal of trend effects from the given dataset and showing only the differences in values from the trend. It always allows cyclical patters to be identified.

#### Differencing
We do this to remove the series dependence on time and stabilise the mean of the time series, so trend and seasonality are reduced during this transformation.
$Y_t = Y_t - Y_{t-1}$

- Note that we can difference as many time as we wish.

#### Transformation
There are three methods for this.
- Power Transform
- Square Root
- Log Transform

The most common is the log transform.


## Limitations of Time Series Analysis
- Similar to other models, missing values are not supported.
- The data points must be linear in their relationship.
- Data transformations are mandatory
- Models mostly work on Uni-variate data.

## Classification

[[Nearest-Neighbour with Dynamic Warping]]
[[kernel Methods]]


