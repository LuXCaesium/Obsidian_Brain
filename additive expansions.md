---
created: 2024-03-23 21:23
tags:
  - Statistics
---

# Additive Expansions

In reality it is unlikely that the true function $f(X)$ is actually linear in $X$. In regression problems $f(X) = \mathbb{E}(Y | X)$ will typically be non-linear and non-additive in $X$. So being able to represent $f(X)$ in a linear way is usually a very convenient approximation. Why ?

- A linear model is easy to interpret.
- it is the first-order Taylor approximation of $f(X)$.
- With $N$ small and/or $p$ large, a linear model may not be able to fit the data without overfitting.
- In classification problems, a linear, Bayes-optimal decision boundary implies that some monotone transformation of $Pr(Y=1 | X)$ is linear in $X$.