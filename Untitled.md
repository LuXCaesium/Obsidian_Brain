---

created: <% tp.file.creation_date() %>

---
tags:: #Statistics 

# Mahalanobis Distance

Is a measure of the distance between a point $P$ and a distribution $D$. It is a multi-dimensional generalisation of the idea of measuring how many standard deviations away $P$ is from the mean of $D$. the distance is zero for $P$ at the mean of $D$ and grows as $P$ moves away from the mean along each principle component axis. If each of these axes are re-scaled to have unit variance, then the Mahalanobis distance corresponds to standard Euclidean distance in the transformed space. Hence, the Mahakabobis distance is:
- unitless
- Scale-invariant
- Takes into account the correlations of the dataset.

## Definition
Given a pronability distribution $Q$ on $\mathbb{R}^N$, with mean $\overrightarrow{\mu} = (\mu_1, \mu_2, \dots, \mu_N)^\intercal$ and a positive-definite covariance matrix $S$, the Mahalanobis distance of a point $\overrightarrow{x} = (x_1, x_2, \dots, \mu_N)^\intercal$