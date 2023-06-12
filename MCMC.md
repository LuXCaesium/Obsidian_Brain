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
In other words, if calculating some quantity has a complex analytical structure, we can simply perform a simulation to generate lots of samples and use them to approximate the quantity. This works provided the samples asymptotically 