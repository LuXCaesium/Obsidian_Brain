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
for some constant $C \geq 1$, then accepting or rejecting the sample with a certain probability. 

Idea is to generate uniformly a point $(X, Y)$ under the graph of $Cg$, by first drawing $X \sim g$ and then $Y \sim \mathcal{U}(0, Cg(x))$. If $Y$ lies under the graph of $f$, then we accept $X$ as a sample from $f$. The efficiency is usually $1/C$ (i.e the probability of acceptance).

**Input**: pdf $g$ and constant $c$ s.t $Cg(X) \geq f(x)$ for all $x$
**Output**: RV $X$ distributed according to $f$
found $\leftarrow$ false
while not found do:
	Generate $X$ from g
	Generate $U$ from $\mathcal{U}(0,1)$ indep of $X$
    $Y \leftarrow UCg(X)$
    if $Y \leq f(X)$ then found $\leftarrow$ true

## Resampling

An iid sample $\tau := {x_1, \dots, x_n}$ from some **unknown** cdf $F$ represents our best knowledge of $F$ if we make no further a *priori* assumptions. The best way to repeat the experiment is to resample from the original data by drawing from the empirical cdf $F_n$.

**Input**: Original iid sample $x_1, \dots, x_n$ 
**Output**: iid sample $X_1^*, \dots, X_n^*$ from the empirical cdf
for t=1 to N do
	Draw $U \sim \mathcal{U}(0,1)$
	Set $I \leftarrow \lceil{nU} \rceil$
    Set $X_t^* \leftarrow x_I$

$I$ is drawn uniformly at random from the set $\{1, \dots, n\}$

## Markov Chain Monte Carlo

This is a Monte Carlo sampling technique for (approximately) generating samples from an arbitrary (target) distribution. You run the Markov chain long enough such that the limiting distribution is close to the target, the initial rvs may have a distribution far fro mthe target, so rvs in the *burn-in* period are often discarded. The accpeted random variables for an *approximate* and *dependent* sample from the target distribution.

The two most popular MCMC samplers: **Metropolis Hastings**, **Gibbs**

### Metropolis-Hastings Sampler
Similar to the [[Monte Carlo Sampling#Acceptance-Rejection Method|Acceptance-Rejection Method]] we simulate a trial state, which is then accepted or rejected according to some random mechanism.

Suppose we want to sample from a target pdf $f(\textbf{x})$. The aim is to construct a Markov Chain $\{\textbf{X}_t, t=0,1, \dots\}$ in such a way that its limiting pdf is $f$.