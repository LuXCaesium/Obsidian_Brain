---
created: 2024-06-15 13:22
tags:
  - UnsupervisedLearning
  - Statistics
  - DataScience
---
# Unsupervised Learning

In contrast to the supervised case, where a *response* variable $y$ is explained by an explanatory vector $x$, in unsupervised learning there is no response variable. So instead the overall goal is to extract useful information & patterns from the data. We ultimately aim to learn about the underlying probability distribution of the data.

## Risk and Loss

Suppose we want to learn the unknown pdf $f$ of $\boldsymbol{X}$ based on an outcome $\tau = \{ \boldsymbol{x}_1, \dots, \boldsymbol{x}_n \}$ of the training data $\mathcal{T} := \{ \boldsymbol{X}_1, \dots, \boldsymbol{X}_n \}$.  In a similar vein to [[Supervised Learning]], we wish to find a function $g$, which is now probability density that best approximates the pdf $f$ in terms of minimising a risk:

$$\mathcal{l}(g) := \mathbb{E} \text{Loss}(f(\boldsymbol{X}), g(\boldsymbol{X}))$$
Where $\text{Loss}$ is some loss function, for example the **Kullback-leibler risk** 

$$\mathcal{l}(g) := \mathbb{E}\ln\frac{f(\boldsymbol{X})}{g(\boldsymbol{X})} = \mathbb{E}\ln f(\boldsymbol{X}) - \mathbb{E}\ln g(\boldsymbol{X})$$


If $\mathcal{G}$ is a class of functions containing f, then minimising the above will yield the correct minimiser of $f$. Since the term $\mathbb{E}\ln f(\boldsymbol{X})$ does not contain $g$ then it plays no role in the minimisation. So by removing this term, we obtain the **Cross-Entropy risk**:

$$\mathcal{l}(g) := - \mathbb{E}\ln g(\boldsymbol{X}) = - \int f(\boldsymbol{x}) \ln g(\boldsymbol{x}) \,d\boldsymbol{x}$$
Minimising this is often infeasible so we aim to minimise the **Cross-Entropy training loss**:
$$\mathcal{l}_{\tau}(g) := \frac{1}{n} \sum_{i=1}^{n} \text{Loss}(f(\boldsymbol{x}_i), g(\boldsymbol{x}_i)) = - \frac{1}{n}\sum_{i=1}^{n} \ln g(\boldsymbol{x}_i)$$
