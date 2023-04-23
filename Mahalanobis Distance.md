---

created: <% tp.file.creation_date() %>

---
tags:: #Statistics 

# Mahalanobis Distance

Is a measure of the distance between a point $P$ and a distribution $D$. It is a multi-dimensional generalisation of the idea of measuring how many standard deviations away $P$ is from the mean of $D$. the distance is zero for $P$ at the mean of $D$ and grows as $P$ moves away from the mean along each principle component axis. If each of these axes are re-scaled to have unit variance, then the Mahalanobis distance corresponds to standard Euclidean distance in the transformed space (i.e there is no correlation between variables). Hence, the Mahalabobis distance is:
- unitless
- Scale-invariant 
- Takes into account the correlations of the dataset.

![[Mahalanobis.png]]
Hence the covariance matrix will fit a distribution better as it indicates how variables variate together. This *green* perimeter is a confidence ellipsoid which is specified by the distribution of the data.

---
## Definition
Given a pronability distribution $Q$ on $\mathbb{R}^N$, with mean $\overrightarrow{\mu} = (\mu_1, \mu_2, \dots, \mu_N)^\intercal$ and a positive-definite covariance matrix $S$, the Mahalanobis distance of a point $\overrightarrow{x} = (x_1, x_2, \dots, x_N)^\intercal$ from $Q$ is

$d_M(\overrightarrow{x}, Q) = \sqrt{(\overrightarrow{x} - \overrightarrow{\mu})^\intercal S^{-1}(\overrightarrow{x} - \overrightarrow{\mu})}$

Given two points $\overrightarrow{x}$ and $\overrightarrow{y}$ in $\mathbb{R}^N$, the mahalanobis distance between them with respect to $Q$ is

$d_M(\overrightarrow{x}, \overrightarrow{y}; Q) = \sqrt{(\overrightarrow{x} - \overrightarrow{y})^\intercal S^{-1}(\overrightarrow{x} - \overrightarrow{y})}$
Which means $d_M(\overrightarrow{x}, Q) = d_M(\overrightarrow{x}, \overrightarrow{\mu}; Q)$

Since $S$ is positive-definite, so is $S^{-1}$, thus the square roots are always defined.

---
## Relationship to [[Principle Component Analysis]]

## Relationship to [[Hotelling's T-squared distribution]]

Assuming $X \sim \mathcal{N}(\boldsymbol{\mu}, \boldsymbol{\Sigma})$ is a multivariate normal with known mean $\mu$ and variance $\Sigma$. $(\textbf{X} - \boldsymbol{\mu}) \boldsymbol{\Sigma}^{-1} (\textbf{X} - \boldsymbol{\mu})$ (which is the Mahalanobis distance squared) follows a Chi squared distribution with $p$ degrees of freedom.

However, if we estimate $\Sigma$ from n samples, we denote it as $\textbf{S}$, which follows a Wishart distribution with n degrees of freedom. Then 
$(\textbf{X} - \boldsymbol{\mu}) \textbf{S}^{-1} (\textbf{X} - \boldsymbol{\mu})$ follows a Hotelling's T-squared distribution with $p$ and $n$ degrees of freedom.

They have different contexts of usage, however they are asymptotically similar.



