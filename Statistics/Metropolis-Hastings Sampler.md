---
created: 2024-06-01 22:09
tags:
  - BayesianInference
  - Statistics
  - DataScience
---

# Metropolis-Hastings Sampler

Similar to the [[Monte Carlo Sampling#Acceptance-Rejection Method|Acceptance-Rejection Method]] we simulate a trial state, which is then accepted or rejected according to some random mechanism.

Suppose we want to sample from a target pdf $f(\textbf{x})$. The aim is to construct a Markov Chain $\{\textbf{X}_t, t=0,1, \dots\}$ in such a way that its limiting pdf is $f$. Suppose the chain is in state $\textbf{x}$ at time t. A transition of the Markov Chain from state $\textbf{x}$ is carried out in two phases:

1. Propose state $\textbf{Y}$ drawn from transition density $q(.|\textbf{x})$
2. This state is accepted as a new state with acceptance probability $$\alpha(\textbf{x}, \textbf{y}) = \min\left\{\frac{f(\textbf{y})q(\textbf{x}|\textbf{y})}{f(\textbf{x})q(\textbf{y}|\textbf{x})}, 1 \right\}$$
