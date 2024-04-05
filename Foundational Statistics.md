---
created: 2024-04-05 18:42
tags:
  - Statistics
---

# Foundational Statistics

**Random Experiment:** an experiment whose outcome cannot be determined in advance.

These experiments are modelled as triplets $(\Omega, \mathcal{H}, \mathbb{P})$ where:
- **Sample Space:** $\Omega$ is the set of all possible outcomes of the experiment.
- **Events:** $\mathcal{H}$ is the collection of all subsets of $\Omega$ to which a probability can be assigned. An **Event Space** is thus a subset of $\Omega$.
- **Probability Measure:**  $\mathbb{P}$ is a function assigning to each event $A \in \mathcal{A}$ a number $\mathbb{P}[A]$ between 0 and 1, indicating the degree of belief that the event will occur.

Any probability measure must satisfy the **Kolmogorov Axioms:**
1. $\mathbb{P}[A] \geq 0$ for every event $A$.
2. $\mathbb{P}[\Omega] = 1$
3. For any sequence $A_1, A_2, \dots$ of events, $$\mathbb{P}[\cup_i A_i] \leq \sum_{i} \mathbb{P}[A_i]$$ With strict equality whenever the events are disjoint, in this case its called the *Sum Rule*

If events are allowed to overlap, then the above is called the *Union Bound*.

When the sample space is *countable* then its easy to specify a probability measure. $$\mathbb{P}[A] = \sum_{i:a_i \in A}{p_i} \text{ for all } A \subseteq \Omega$$
Here the collection of events $\mathcal{H}$ can be taken equal to the collection of all subsets of $\Omega$. This is a **discrete probability space**.

## Random Variables & Probability Distributions

Random variables represent numerical measurements of the experiment. Mathematically this is defined as:

**Random Variable:** $X$ is a function from $\Omega$ to $\mathbb{R}$ such that sets of the form $\{a < X \leq b\} = \{\omega \in \Omega: a < X(\omega) \leq b\}$ are events (and thus can be assigned a probability). In other words the probability that $X$ takes on a value in a measurable set $S \subseteq E$ is written: $$P(X \in S) = P(\{\omega \in \Omega | X(\omega) \in S\})$$

All probabilities can be computed from a random variables CDF:
**Cumulative Distribution Function:** $F(X) = \mathbb{P}[X \leq x] \text{ for } x \in \mathbb{R}$

For 




 