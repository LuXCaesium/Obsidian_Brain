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
