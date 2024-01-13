---
created: <% tp.file.creation_date() %>
tags:
  - Statistics
  - MachineLearning
---
source: [Paper](https://openreview.net/pdf?id=xmY_plRB15j)
# Statistical Property Testing For Generative Models

Here we look at a framework to statistically test whether the output from a [[Generative Model]] satisfies some property with a given confidence interval.

## Methodology

Let $G$ be a generative model that outputs data points $\boldsymbol{x} \in \mathbb{R}^d$ based on a distribution $p_{G}(.)$; we abuse the notation $\boldsymbol{x} \sim G$. e.g $\boldsymbol{x}$ could represent images, text or other types of data. For some generative models, the generated samples could be dependent on a prompt $\boldsymbol{c} \in \mathbb{R}^d$ (e.g text to image), and in that case we have $\boldsymbol{x} \sim G(\boldsymbol{c})$ and the data $\boldsymbol{x}$ following the distribution $p_G(.|\boldsymbol{c})$.

Let $\phi: \mathbb{R}^d \rightarrow \{0, 1\}$ be a property that we want to verify. Imagine this to be a function whereby, upon an input $\boldsymbol{x}$, returns the output 1 (if the property is satisfied) or ) if not. In practice, $\phi$ can be implemented by human inspection or a model that classifies whether its input $\boldsymbol{x}$ satisfies the property or not.

We want to test whether the hypothesis that $G$ outputs data that satisfies the property with sufficiently high probability. For this, we formulate the (null) hypothesis $H_0 = \{p \geq p_0\}$, where $p = P_{\boldsymbol{x} \sim G}[\phi(\boldsymbol{x}) = 1]$ is the probability that $G's$ output satisfies the property, and $p_0$ is the lower bound that we want to achieve. We want to then show that $H_0$ holds with sufficiently high probability and can derive the following using [[Hoeffding's inequality]]

