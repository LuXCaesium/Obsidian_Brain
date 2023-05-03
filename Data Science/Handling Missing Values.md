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
