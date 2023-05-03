---

created: <% tp.file.creation_date() %>

---
tags:: #TimeSeries #DataScience #DataEngineering 

# Handling Missing Values

## Time Series Data
Handling missing values in time series data can be different. As most of the analysis on time series require complete and equidistant time series data points the need for imputation is heavily increased. Due to correlation between adjacent observations we cannot simply drop data points.

There are four common techniques to impute missing values.
1) Last Observation Carried Forward (LOCF)
2) Next Observation Carried Backward (LOCB)
3) Rolling Statistics
4) Interpolation

### 1) Last Observation Carried Forward
The previous non-missing values are carried or copied forward and replaced with the missing values.

```python
df['Forward_Fill'] = df['variable'].ffill()
```

This will fill the missing value with the previous one.

### 2) Next Observation Carried Backward
missing values are replaced with the previous non-missing values.
```python
df['Backward_Fill'] = df['variable'].bfill()
```

### 3) Rolling Statistical

#### Simple Moving Average
$P_t = (P_{t-1}+P_{t-2}+ \dots + P_{t-n})/n$

```python
df['SMA'] = df['variable'].rolling(window=5).mean()
```

#### Weighted Moving Average
$P_t = (N*P_{t-1} + (N-1)*P_{t-2} + (N-2)*P_{t-3}* + \dots + 1*P_{t-n})/(N*(N+1)/2)$
```python
df['WMA'] = df['variable'].rolling(window=5).apply(lambda x: x[::-1].cumsum().sum() * 2 / n / (n+1))
```

#### Exponential (weighted) Moving average
$\hat{Y}_{t+1} = \alpha[Y_t + (1-\alpha)Y_{t-1} + (1-\alpha)^2Y_{t-2} + \dots]$

```python
df['EWA'] = df['variable'].ewm(halflife=4).mean()
```

### 3) Interpolation
These estimate the missing values by assuming a relationship within a range of data points. in rolling statistical techniques where only the previous values were considered, interpolation estimates using past and future known data points.

Methods:
1) Linear: Assumes linear relationship between a range of data points.
2) Spline: Estimates values that minimise overall curvature, thus obtaining a smooth surface passing through input points.
3) time: estimates missing values by focusing more on nearby points than far away.

All the above assume that adjacent points are similar, this is not always the case.
