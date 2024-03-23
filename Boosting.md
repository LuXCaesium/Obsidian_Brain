---
created: 2024-03-23 20:20
tags:
  - DataScience
  - SupervisedLearning
---

# Boosting

Boosting is a general technique to create an ensemble of models. Several variants of the algorithm are most commonly used: *Adaboost*, *gradient boosting* and *stochastic gradient boosting*. The latter being the most general and most widely used. With the right choice of parameters the algorithm can emulate a random forest.


## Adaboost

Here we outline the *Adaboost* algorithm:

1. Initialise $M$, the maximum number of models to be fit. Initialise the observation weights $w_i = \frac{1}{N}$ for $i = 1, \dots, N$ and the ensemble model $\hat{F}_0 = 0$
2. Using the observation weights $w_1, \dots, w_N$ train a model $\hat{f}_m$ that minimises the weighted error $e_m$ defined by summing the weights for the misclassified observations.
3. Add the model to the ensemble $\hat{F}_m = \hat{F}_{m-1} + \alpha \hat{f}_m$ where $\alpha_m = \frac{\log(1-e_m)}{e_m}$
4. Update the weights $w_1, \dots, w_N$ so the weights are increased for misclassified observations. Large values of $\alpha_m$ lead to bigger weights.
5. Increment the model counter $m=m+1$. If $m \leq M$, go to step 2.

Consider a two-class problem, with output variable $Y \in \{-1, 1 \}$. Given a vector of predictor variables $X$, a classifier $G(X)$ produces a 

The boosted estimate is given by:

$\hat{F} = \alpha_1 \hat{f}_1 + \dots + \alpha_M \hat{f}_M$

By increasing the weights for observations that were misclassified, the algorithm forces the models of train more heavily for data on which it performed poorly. 

