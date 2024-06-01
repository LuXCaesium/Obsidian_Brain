---
created: 2024-06-01 22:10
tags:
  - BayesianInference
  - DataScience
  - Statistics
---

# Gibbs Sampler

In essence the **Gibbs Sampler** uses a somewhat different methodology than the [[Metropolis-Hastings Sampler]] and is useful for generating n-dimensional random vectors. One at a time we update each component of the random vector, by sampling them from conditional pdfs. Which has the advantage the conditional pdfs can be easier to sample from than marginalising by integrating over the joint distributions.

Suppose we wish to sample a random vector $\mathbf{X} = [X_1, X_2, \dots, X_n]^{\top}$ according to target pdf $f(\boldsymbol{x})$. Let $f(x_i | x_1, \dots, x_{i-1}, x_{i+1}, \dots, x_n)$ represent the condition pdf of the i-th component $X_i$.

**Input:** Initial point $X_0$, sample size $N$ and target pdf f.
**Output:** $\boldsymbol{X}_1, \dots, \boldsymbol{X}_N$ approximately distributed according to f.

for $t=0$ to $N-1$ do:
	Draw $Y_1$ from the conditional pdf $f(y_1| X_{t,2}, \dots, X_{t,n})$
		for $i=2$ to $n$ do:
			Draw $Y_i$ from the conditional pdf $f(y_i|Y_1, \dots, Y_{i-1}, X_{t, i+1}, \dots, X_{t,n})$
		$\boldsymbol{X}_{t+1} \leftarrow \boldsymbol{Y}$

The above is what we call a *systematic gibbs sampler* as the components are updated in a fixed order. There are many variants of this. 





