---
created: <% tp.file.creation_date() %>
tags:
  - BayesianInference
  - DataScience
  - Statistics
---

# Monte Carlo Sampling

## Generating Random Numbers

At the heart of Monte Carlo is a *random number generator*: producing a stream of uniform random numbers such as:

$U_1, U_2, \dots \sim_{iid} \mathcal{U}(0,1)$

One of the most popular random number generators is the *multiple-recursive generator* of order $k$, which generates a sequence of integers via the linear recurrence:

$$X_t = (a_1X_{t-1} + \dots + a_kX_{t-k})\mod m$$
This is initialised by specifying $k$ seeds $X_0, \dots, X_{k-1}$. Setting $U_t = \frac{X_t}{m}$ gives you a stream of random numbers between $(0,1)$

## Simulating Random Variables
Simulating a RV $X$ from an arbitrary distribution is as follows:

1. Simulate uniform random numbers $U_1, \dots, U_k$ on $(0, 1)$ for some $k=1, 2, \dots$
2. 2. Return $X=g(U_1, U_2, \dots, U_k)$ where $g$ is some real valued function. 

Two of the most useful general procedures for generating random variables are *inverse-transform* methods and the *acceptance - rejection* method.

### Inverse-Transform Method
Let $X$ be a random variable with cdf $F$. Let $F^{-1}$ denote the inverse of $F$ and $U \sim \mathcal{U}(0,1)$ then,
$$\mathbb{P}[F^{-1}(U) \leq x] = \mathbb{P}[\mathcal{U} \leq F(x)]=F(x)$$
so the algorithm follows as:
**Input**: Cumulative distribution function $F$
**Output**: Random variable $X$ distributed according to $F$
1. Generate $U$ from $\mathcal{U}(0,1)$
2. $X \leftarrow F^{-1}(U)$

### Acceptance-Rejection Method

This is used when trying to sample from *difficult* pdfs $f(x)$ by generating instead an *easy* pdf $g(x)$ satisfying $f(x) \leq Cg(x)$
for some constant $C \geq 1$, then accepting or rejecting the sample with a certain probability. Idea is to generate uniformly a point $(X, Y) under the graph of $Cg$, by first drawing $X \sim g$ and then $Y \sim \mathcal{U}(0, Cg(x))$. If $X$ lies under the graph of $f$, then we accept it. The efficiency is usually $1/C$ (i.e the probability of acceptance).
