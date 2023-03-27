---

created: <% tp.file.creation_date() %>

---
tags:: #TimeSeries #MachineLearning #DataScience #SupervisedLearning

# Nearest Neighbour with Dynamic Time Warping

Nearest-neighbour methods are one of the most intuitive algorithms for supervised learning: the prediction for a new sample is based on the target value of similar samples. A key element of these algorithms is the metric, (Euclidean distance) a popular one is not suitable for time series, due to many reasons:
* It is only defined for two vectors of the same length, where time series of a dataset can vary.
* it compares values at each point in time independently, whereas time series values are correlated.

Dynamic time warping (DTW) is a metric for time series that address both limitations, and is often considered to be the baseline algorithm for time series classification.

## Dynamic Time Warping

Let $X = (x_1, \dots, x_n) \in \mathbb{R}^n$ and $Y = (y_1, \dots, y_m) \in \mathbb{R}^m$ be two time series of length $n$ & $m$ respectively. The cost matrix, $C$ is an $n \times m$ consisting of the cost between each pair of values in both time series:


