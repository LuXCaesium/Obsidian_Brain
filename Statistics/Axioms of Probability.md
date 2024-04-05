---
created: 2024-04-05 20:40
tags:
  - Statistics
---

# Axioms of Probability

**Probability Space:** $(\Omega, \mathcal{F}, \mathbb{P})$ Where $\Omega$ is a *Sample Space*, $\mathcal{F}$ is a collection of subsets of $\Omega$ and $\mathbb{P}: \mathcal{F} \rightarrow [0, 1]$ is a *Probability Measure*.
$\mathcal{F}$ must satisfy the following:
1. $\emptyset, \Omega \in \mathcal{F}$
2. $A \in \mathcal{F} \Rightarrow A^C \in \mathcal{F}$
3. $A_1, A_2, \dots \in \mathcal{F} \Rightarrow \cup_{i=1}^{\infty}A_i \in \mathcal{F}$

And $\mathbb{P}$ has to satisfy *Kolmogorov's axioms*:
1. $0 \leq \mathbb{P}(A) \geq 1$ for all $A \in \mathcal{F}$
2. $\mathbb{P}(\Omega) = 1$
3. For any countable collection of events which are disjoint ($A_i \cap A_j = \emptyset$ for all $i, j$) we have