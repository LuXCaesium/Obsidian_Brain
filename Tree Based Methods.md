---
created: 2024-01-21 00:43
tags:
  - DataScience
---

# Tree Based Methods

Decision trees can be applied to both regression and classification problems, here we will discuss both and highlight potential pros & cons.

### Pros and Cons
- Simple and useful for interpretation.
- Typically not competitive wit the best supervised learning approaches in terms of prediction accuracy.
- [[Bagging]], [[Random Forests]] and [[Boosting]] are methods which grow multiple trees and then combined into a single consensus prediction.
- Combing trees often result in improved prediction accuracy, at the expense of interpret-ability. 

## Regression Trees

### Building the Tree
1. divide the predictor space, i.e the set of possible values $X_1, X_2, \dots, X_p$ into $J$ distinct and non-overlapping regions $R_1, R_2, \dots, R_J$
2. For every observation that falls into $R_j$, the mean of the response values for the training observations in $R_j$ is the prediction that is made.

- In theory, the regions could have any shape. But here we choose boxes for ease of interpretation.

 - The goal is to find boxes $R_1, \dots, R_J$ that minimise the RSS (Residual Sum of Squares), given by:
		$$ \sum^{J}_{j=1} \sum_{i \in R_j}(y_i - \hat{y}_{R_j})^2$$
Where $\hat{y}_{R_j}$ is the mean response for the training observations within the $j^{th}$ box.

We take a *top-down*, *greedy* approach as its infeasible to consider every possible partition of the features space into $J$ boxes. *top-down* as we start at the top of the tree successively splitting the space, and *greedy* as we choose the best split at each step, not looking ahead for the best split in consideration of future steps.

1. Select the predictor $X_j$ and the cutpoint $s$ such that splitting the predictor space into regions $\{X | X_j < s\}$ and $\{X | X_j \geq s\}$ leads to greatest reduction in RSS.
2. 