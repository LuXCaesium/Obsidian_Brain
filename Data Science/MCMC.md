---

created: <% tp.file.creation_date() %>

---
tags:: #Statistics #DataScience #BayesianInference

# Monte Carlo Markov Chain (MCMC)

These are a class of algorithms for sampling from a probability distribution. These samples can be used to evaluate an integral over that variable, as its expected value or variance.

## Sampling

Sampling is a way to apporiximately estimate certain characteristics of the whole population by taking a subset of the population. There are various use cases:

- Could be used to approximate intractable sum or integral, and speed up estimation.
- Could be used to approximate the probability distribution and then to impute missing values.

Sampling Techniques:
- Ancestral Sampling
- Inverse Transform Sampling
- Rejection Sampling
- Importance Sampling
- Monte Carlo Sampling
- MCMC Sampling

## Monte Carlo Sampling

It is a technique for sampling from a probability distribution and using those samples to approximate a desired quantity of interest.
In other words, if calculating some quantity has a complex analytical structure, we can simply perform a simulation to generate lots of samples and use them to approximate the quantity. This works provided the samples asymptotically follow the central limit theorem. mathematically speaking:

Say we wish to estimate the following expectation
$s = \int{p(x)f(x)} dx = E_p[f(x)]$

Then using the Monte Carlo method we resort to approximate this integral by averaging over the samples like so
$\hat{s}_{n} = \frac{1}{n}\sum_{i=1}^{n}{f(x^i)}$

Computing this average over a large number of samples will reduce the standard error and provide a reasonably accurate approximation. The one problem with this however is that it assumes that its easy to sample from the probability distribution, which is not always the case. Hence we introduce Markov Chains.

## Markov Chains

Markov Property: *The probability of jumping from one state to the next state depends only on the current state and not on the sequence of previous states that lead to the current.*
Mathematically speaking, this means
$\mathbb{P}(X_{n+1}|X_n=k_n, X_{n-1}=k_{n-1}, \dots, X_1=k_1) = \mathbb{P}(X_{n+1}=k|X_n=k_n)$

Hence, if a process exhibits this property it is known as a **Markov Chain**. A property that makes these chains so desired is the **Stationary Distribution**

### Stationary Distribution
Suppose we have a process of a few states and we have a fixed transition probability **Q** of jumping between states.
We start with some random probability distribution over all states $S_i$ at time step $i$ and estimate the probability distribution over all states at the next time step we multiple it by the transition probability $Q$.
$S_{i+1} = S_iQ$

If we keep doing this, after a while $S$ stops changing, when this state is reached its know as a **stationary distribution**
$S=SQ$

## Markov Chain Monte Carlo (MCMC)

MCMC can be used to sample from any probability distribution. Mostly we use it to sample from the intractable posterior distribution for the purpose of inference. It is often difficult to directly simulate independent observations from the posterior density $f(\theta|y)$. The approach we will follow is that of generating observations from an approximate posterior density and then correcting those observations.