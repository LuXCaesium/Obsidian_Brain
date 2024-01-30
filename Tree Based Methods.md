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
2. Repeat the above, but instead split one of the two previously defined regions.
3. We continue this process until we reach a defined stopping criterion. Say until no region contains more than 5 observations.

### Pruning a Tree
The above process is likely to cause [[Overfitting]]. A smaller tree, with fewer splits might leaf to lower variance and better interpretation at the cost of a little bias.

An alternative is to grow the tree so long as the decrease in the RSS due to each split exceeds some *high* threshold. This results in smaller trees, but is too *short-sighted*: a worthless early slit might be followed by a very good split. This is a problem with the *greedy* aspect.

To improve we grow a large tree $T_0$, and then *prune* it back in order to obtain a *subtree*. We use *Cost complexity pruning*, or *weakest link pruning* to do this.

Consider a sequence of trees indexed by tuning parameter $\alpha > 0$. For each $\alpha$ there corresponds a subtree $T \subset T_0$ such that:

$$\sum_{m=1}^{|T|} \sum_{x_i \in R_m} (y_i - \hat{y}_{R_m})^2 + \alpha|T|$$

is as small as possible. $|T|$ indicates the number of terminal node of the tree $T$, $R_m$ is the rectangle of the mth terminal node, and $\hat{y}_{R_m}$ is the mean of the training observations in $R_m$.

Over all the terminal nodes in tree T, we take the RSS of the region $R_m$ of the terminal node $m$.
The tuning parameter $\alpha$ controls a trade-off between the subtree's complexity and its fit to the training data.
Select the optimal $\hat{\alpha}$ using cross-validation.

### Summary: Tree Algorithm
In culmination of the previous discussion we end up with the following algorithm to build the most optimal tree.

1. Use recursive binary splitting to grow a large tree on training data, stopping when each terminal node has fewer than some minimum number of observations.
2. Apply cost complexity pruning to obtain a sequence of best subtrees, as a function of $\alpha$.
3. Use K-fold cross-validation to choose $\alpha$. For each $k=1, \dots, K$:
	1. Repeat steps 1, 2 on the $\frac{K-1}{K}$ th fraction of the training data, excluding $kth$ fold
	2. Evaluate mean squared prediction error on the data in the kth fold, as a function of $\alpha$
	3. Average the results, and pick $\alpha$ to minimise average error.
4. Return subtree from step 2 that corresponds to the chosen value of $\alpha$.
