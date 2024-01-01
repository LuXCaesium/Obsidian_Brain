---
created: 2024-01-01 16:53
tags:
  - BayesianInference
  - DataScience
  - MachineLearning
  - SupervisedLearning
---

# Naive Bayes Classifier

Are a family of linear probabilistic classifiers, meaning the features are conditionally independent given the target class.

## Definition:

Given a vector of features $\boldsymbol{x} = (x_1, \dots, x_n)$ we aim to assign probability's to each possible class $C_k$ , $p(C_k | x_1, \dots, x_n)$. Decomposing this using Bayes formula

$p(C_k, \boldsymbol{x}) = \frac{p(C_k)p(\boldsymbol{x} | C_k)}{p(\boldsymbol{x})}$

Using the chain rule, and using the assumptions of conditional independence we arrive at:

$p(C_k | x_1, \dots, x_n) = \frac{1}{Z}p(C_k)\prod^{n}_{i=1}p(x_i | C_k)$

$Z$
