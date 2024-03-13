---
created: 2024-03-13 18:32
tags:
  - BayesianInference
  - Statistics
  - MachineLearning
  - DataScience
---

# Variational Inference

As apposed to [[sampling methods]] Variational Inference formulates inference as an optimisation problem. Sampling-based methods have several important shortcomings:

- Although they are guaranteed to find a globally optimal solution given enough time, its difficult to quantify how close they are to a good solution in practice.
- In order to quickly reach a good solution, MCMC methods require choosing an appropriate sampling technique (i.e [[Metropolis Hastings]]). Choosing this technique can prove very difficult.

## Inference as Optimisation

The main idea of variational inference is to cast inference as a optimisation problem. 

Suppose we are given an intractable probability distribution $p$. Variational techniques try to solve an optimisation problem over a class of tractable distributions $\mathcal{Q}$  to find a $q \in \mathcal{Q}$ that is most similar to $p$. We then query $q$ in order to get an approximate solution. 

Main differences between sampling & variational techniques:

- Unlike sampling methods, variational approaches will almost never find the globally optimal solution. 
- We will always know if they have converged, and even have bounds on the accuracy.
- Variational methods can often scale better in practice.

## Ku