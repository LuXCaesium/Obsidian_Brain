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

$Z = p(\boldsymbol{x}) = \sum_{k}p(c_k)p(\boldsymbol{x} | C_k)$ is a scaling factor and is constant for known feature values.

From the probability model, we wish to apply a decision rule to construct a classifier. A common one being minimising the probability of miss-classification. The *Bayes Classifier* is a function assigning $\hat{y} = C_k$

$\hat{y} = argmax_{k \in \{1, \dots, K \}}p(C_k)\prod^{n}_{i=1}p(x_i | C_k)$

## Types of Classifier:

### Multinomial Naive Bayes:

Mostly used for document classification. i.e whether a document belongs to the category of sports, politics, technology etc. The features/predictors used by the classifier are the frequency of the words present in the document.

### Bernoulli Naive Bayes:

Similar to multinomial, except the predictors are boolean. For example if a word occurs in the text or not.

### Gaussian Naive Bayes:

When predictors take continuous values, we assume they are sampled from a Gaussian distribution. 