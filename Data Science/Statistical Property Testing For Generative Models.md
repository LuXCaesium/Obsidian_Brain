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

Let $G$ be a generative model that outputs data points $\boldsymbol{x} \in \mathbb{R}^d$ based on a distribution $p_{G}(.)$; we abuse the notation $\boldsymbol{x} \sim G$. e.g $\boldsymbol{x}$ could represent images, text or other types of data. For some generative models, the generated samples could be dependent on a prompt $\boldsymbol{c} \in \mathbb{R}^d$ (e.g t)
