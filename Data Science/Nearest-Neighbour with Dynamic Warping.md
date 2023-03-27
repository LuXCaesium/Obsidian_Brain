---

created: <% tp.file.creation_date() %>

---
tags:: #TimeSeries #MachineLearning #DataScience #SupervisedLearning

# Nearest Neighbour with Dynamic Time Warping

Nearest-neighbour methods are one of the most intuitive algorithms for supervised learning: the prediction for a new sample is based on the target value of similar samples. A key element of these algorithms is the metric, (Euclidean distance) a popular one is not suitable for time series, due to many reasons:
* It is only defined for two vectors of the same length, where time series of a dataset can vary.
* it compares values at each point in time independently, whereas time series values are correlated.

Dynamic time warping (DTW) is a metric for time series that address both limitations, and is often considered to be the baseline algorithm for time series classification.

## Dynamic Time Warping

Let $X = (x_1, \dots, x_n) \in \mathbb{R}^n$ and $Y = (y_1, \dots, y_m) \in \mathbb{R}^m$ be two time series of length $n$ & $m$ respectively. The cost matrix, $C$ is an $n \times m$ consisting of the cost between each pair of values in both time series:

$\forall i,j \in \{1, \dots, n\} \times \{1, \dots, m\},$ $C_{ij} = f(x_i, y_j)$

where $f$ (local divergence) is a function evaluating the cost between any pair of real numbers; usually the squared difference function:
$\forall x,y \in \mathbb{R}, f(x, y) = (x-y)^2$

A warping path is a sequence $p = (p_1, \dots, p_L)$ such that:

* **Value Condition**: $\forall l \in \{1, \dots,L\},$ $p_l = (i_l, j_l) \in \{1, \dots, n\} \times \{1, \dots, m \}$
* **Boundary Condition**: $p_1 = (1,1)$ and $p_L = (n, m)$
* **Step Condition**: $\forall l \in \{1, \dots, L-1\},$ $p_{l+1} - p_l \in \{(0,1), (1, 0), (1,1)\}$

The cost associated with a warping path, denoted $C_p$, is the sum of the elements of the cost matrix that belong to the warping path:
$C_p(X, Y) = \sum_{l=1}^{L}{C_{i_l, j_l}}$

Then the dynamic time warping score is defined as the minimum cost among all the warping paths:

$DTW(X, Y) = \min_{p \in \mathcal{P}} C_p(X, Y)$

Where $\mathcal{P}$ is the set of warping paths. We use [[Dynamic Programming]] to speed up this computation.

## Limitations & Variants
* The algorithmic complexity is $\mathcal{O}(nm)$
* it is not a distance because it does not satisfy not only the separation property (DTW between two different time series can be zero) or the triangle inequality. so efficient NN search algorithms ([[K-dimensional Tree]] [[Ball Tree]]) cannot be used.
* DTW allows for very large time warps, which may be undesired.
* DTW is not differentiable, making it difficult to use with machine learning algorithms relying on minimising an objective function with [[gradient descent]].

There are several variants which aim to mitigate these issues. The set of warping paths is restricted to the set of warping paths such that all their elements belong to the constraint region. This does reduce complexity, but add the complexity of the constraint region. The [[Sakoe-Chiba Band]]

