---

created: <% tp.file.creation_date() %>

---
tags:: #TimeSeries #MachineLearning #DataScience 

# Convert Time Series into a Supervised Learning Problem

Before machine learning can be used, time series forecasting problems must be re-framed as supervised learning problems. From a sequence to pairs of input and output sequences.

### Time Series vs Supervised Learning

A time series is a sequence of numbers that are ordered by a time index. whilst a supervised learning problem is comprised of input patters X and output patters y, such that an algorithm can learn the function mapping X to y.

### Pandas ```shift()``` function
Given a dataframe, the `shift()` function can be used to create copies of columns that are pushed forward (rows of NaN values added to the front) or pulled back (rows of NaN values added to the end). This is the required behaviour to create columns of lag observations as well as columns of forecast observations for a time series dataset.

```python
import pandas as pd
df = pd.DataFrame()
df['t'] = [x for x in range(10)]
print(df)
```

|     | t   |
| --- | --- |
| 0   | 0   |
| 1   | 1   |
| 2   | 2   |
| 3   | 3   |
| 4   | 4   |
| 5   | 5   |
| 6   | 6   |
| 7   | 7   |
| 8   | 8   |
| 9   | 9   |

We can shift all the observations down by one time step by inserting one new row at the top.
```python
import pandas as pd
df = pd.DataFrame()
df['t'] = [x for x in range(10)]
df['t+1'] = df['t'].shift(-1)
```

### `series_to_supervised()` Function

This function will take a univariate or multivariate time series and frames it as a supervised learning dataset. The input arguments are as follows:
- data: Sequence of observations as a list or 2D Numpy array.
- n_in: number of lag observations as input X.
- n_out: Number of observations as output y.
- dropnan: Boolean whether to drop rows with Nan values. Defaults to True.

