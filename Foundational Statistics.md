---
created: 2024-04-05 18:42
tags:
  - Statistics
---

# Foundational Statistics

**Random Experiment:** an experiment whose outcome cannot be determined in advance.

These experiments are modelled as triplets $(\Omega, \mathcal{H}, \mathbb{P})$ where:
- **Sample Space:** $\Omega$ is the set of all possible outcomes of the experiment.
- **Event Space:** $\mathcal{H}$ is the collection of all subsets of $\Omega$ to which a probability can be assigned. i.e all events
- **Probability Measure:**  $\mathbb{P}$ is a function assigning to each event $A \in \mathcal{A}$ a number $\mathbb{P}[A]$ between 0 and 1, indicating the degree of belief that the event will occur.

Any probability measure must satisfy the **Kolmogorov Axioms:**
1. $\mathbb{P}[A] \geq 0$ for every event $A$.
2. $\mathbb{P}[\Omega] = 1$
3. For any sequence $A_1, A_2, \dots$ of events, $$\mathbb{P}[\cup_i A_i] \leq \sum_{i} \mathbb{P}[A_i]$$ With strict equality whenever the events are disjoint.


 