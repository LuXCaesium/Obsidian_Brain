---

created: <% tp.file.creation_date() %>

---
tags:: #TimeSeries #MachineLearning #DataScience 

# Kernel Methods

These are popular machine learning algorithms allowing for non-linear transformations or decision functions. support vector machines are a famous example.

Kernel methods rely on a kernel function to measure similarity between any pair of inputs. This has the necessary assumption of the kernel method  being positive definite. However, DTW does not satisfy the triangle inequality and hence cannot be used and is an important limitation.

**Global Alignment Kernel**: A true positive-definite kernel for time series, denoted $k_{GA}^{\gamma}$, is defined as the sum of all negatively exponentiated costs over all the possible warping paths:
$k_{GA}^{\gamma} = \sum_{p \in \mathcal{P}}\exp \left( -\frac{C_p(X,Y)}{\gamma} \right)$

Where $C_p$ is the cost associated with the warping path $p$, $\mathcal{P}$ the set of all warping paths, and $\gamma > 0$ is a smoothing parameter. This is not a true kernel for every local divergence $f$. However it can be proven that if $\frac{1}{1+exp(f)}$ is a positive definite kernel, then $k_{GA}^{\gamma}$ is a kernel. This kernel has the sample computational complexity as DTW $\mathcal{O}(nm)$, and has been shown to provide better performance that other kernels based on DTW.