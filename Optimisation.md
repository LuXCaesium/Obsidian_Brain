---
created: 2024-01-23 21:19
tags:
  - DataScience
---

# Optimisation

Here we discuss the problem of finding a set of inputs to an objective function that results in a maximum or minimum function evaluation. This can take many forms, from logistic regression to machine learning [[neural Networks]]. 

We divide this topic into two sections, those dealing with *Continuous* variables or those dealing with *Discrete* variables.

## Continuous Optimisation

### Differentiable Function

Optimisation is significantly easier if the gradient of the objective function can be calculated, and hence we have a range of optimisation algorithms:

#### Bracketing Algorithms

- Intended for single variable problems, where the optima exists within a specific range.
- Efficiently navigate the known range and locate the optima
- Assume only a single optima is present.

Examples:
[[Fibonacci Search]]
[[Golden Section Search]]
[[Bisection Method]]
#### Local Descent Algorithms

- Intended for multi variable problems, and a single global optima.
#### First-Order Algorithms

#### Second-Order Algorithms



