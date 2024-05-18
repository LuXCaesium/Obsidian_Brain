---
created: <% tp.file.creation_date() %>
tags:
  - MachineLearning
  - Statistics
  - BayesianInference
  - DataScience
---

# Monte Carlo Methods

*Monte Carlo Simulation* is the generation of random data by means of a computer. The data could arise from many different areas, but the crux of the simulation is to randomly sample from certain probability distributions. You repeat the random experiment many times to obtain a large quantity of data used to answer questions about the model. Main uses:

- **Sampling**: gather information about a random object by observing many realisations. i.e you can use [[MCMC]] to sample from a posterior distribution.
- **Estimation**: You can estimate certain numerical properties related to a simulation model. i.e with multidimensional integrals can be written as the expectation of a random variable, which is approximated by the sample mean. The [[Law of Large Numbers]] says the approximation will converge when the sample is large enough.
- **Optimisation**: Monte Carlo can be used to optimise complicated objective functions. 
