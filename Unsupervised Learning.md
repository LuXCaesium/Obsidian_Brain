---
created: 2024-06-15 13:22
tags:
  - UnsupervisedLearning
  - Statistics
  - DataScience
---
# Unsupervised Learning

In contrast to the supervised case, where a *response* variable $y$ is explained by an explanatory vector $x$, in unsupervised learning there is no response variable. So instead the overall goal is to extract useful information & patterns from the data. We ultimately aim to learn about the underlying probability distribution of the data.

## Risk and Loss

Suppose we want to learn the unknown pdf $f$ of $\boldsymbol{X}$ based on an outcome $\tau = \{ \boldsymbol{x}_1, \dots, \boldsymbol{x}_n \}$ of the training data $\mathcal{T} := \{ \boldsymbol{X}_1, \dots, \boldsymbol{X}_n \}$.  In a similar vein to [[Supervised Learning]], we wish to find a function $g$, which is now probability density that best approximates the pdf $f$ in terms of minimising a risk:

$$\mathcal{l}(g) := \mathbb{E}(Loss(f(\boldsymbol{X}), g(\boldsymbol{X})))$$

