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

The boosted estimate is given by:

$\hat{F} = \alpha_1 \hat{f}_1 + \dots + \alpha_M \hat{f}_M$

By increasing the weights for observations that were misclassified, the algorithm forces the models of train more heavily for data on which it performed poorly. 

Consider a two-class problem, with output variable $Y \in \{-1, 1 \}$. Given a vector of predictor variables $X$, a classifier $G(X)$ produces a prediction taking one of the two values $\{-1, 1\}$. The error rate on the training sample is 

$$ err = \frac{1}{N} \sum_{i=1}^{N}I(y_i \neq G(x_i))$$

A weak classifier is one whose error rate is only slightly better than a random guess. The purpose of boosting is to apply multiple weak classifiers $G_m(x) = 1, 2, \dots, M$. The predictions from each are then combined through a weighted majority to produce the final prediction:

$$G(x) = \text{sign} (\sum_{m=1}^{M} \alpha_m G_m(x))$$

Here $\alpha_1, \dots, \alpha_M$ are computed by the boosting algorithm. The effect is to give higher influence to the more accurate classifiers in the sequence. 

1. Initialise the observation weights $w_i = \frac{1}{N}$ for $i=1, \dots, N$
2. For $m=1 \text{ to } M$:
	1. Fit a classifier $G_m(x)$ to the training data using weights $w_i$

