---
created: 2024-03-23 20:20
tags:
  - DataScience
  - SupervisedLearning
---

# Boosting

Boosting is a general technique to create an ensemble of models. Several variants of the algorithm are most commonly used: *Adaboost*, *gradient boosting* and *stochastic gradient boosting*. The latter being the most general and most widely used. With the right choice of parameters the algorithm can emulate a random forest.


## Adaboost

Consider a two-class problem, with output variable $Y \in \{-1, 1 \}$. Given a vector of predictor variables $X$, a classifier $G(X)$ produces a prediction taking one of the two values $\{-1, 1\}$. The error rate on the training sample is 

$$ err = \frac{1}{N} \sum_{i=1}^{N}I(y_i \neq G(x_i))$$

A weak classifier is one whose error rate is only slightly better than a random guess. The purpose of boosting is to apply multiple weak classifiers $G_m(x) = 1, 2, \dots, M$. The predictions from each are then combined through a weighted majority to produce the final prediction:

$$G(x) = \text{sign} (\sum_{m=1}^{M} \alpha_m G_m(x))$$

Here $\alpha_1, \dots, \alpha_M$ are computed by the boosting algorithm. The effect is to give higher influence to the more accurate classifiers in the sequence. 

1. Initialise the observation weights $w_i = \frac{1}{N}$ for $i=1, \dots, N$
2. For $m=1 \text{ to } M$:
	1. Fit a classifier $G_m(x)$ to the training data using weights $w_i$
	2. Compute: $$ err_m = \frac{\sum_{i=1}^{N} w_i I(y_i \neq G_m(x_i))}{\sum_{i=1}^{N}w_i}$$
	3. Compute $\alpha_m = log(\frac{1-err_m}{err_m})$
	4. Set $w_i \leftarrow w_i \exp{[\alpha_m I(y_i \neq G_m(x_i))]}$, $i=1, \dots, N$
3. Output $G(x) = \text{sign}[\sum_{m=1}^{M}\alpha_m G_m(x)]$



