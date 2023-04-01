---

created: <% tp.file.creation_date() %>

---
tags:: #TimeSeries #MachineLearning #DataScience 

# Kernel Methods

These are popular machine learning algorithms allowing for non-linear transformations or decision functions. support vector machines are a famous example.

Kernel methods rely on a kernel function to measure similarity between any pair of inputs. This has the necessary assumption of the kernel method  being positive definite. However, DTW does not satisfy the triangle inequality and hence cannot be used and is an important limitation.

**Global Alignment Kernel**: A true positive-definite kernel for time series, denoted $k_{GA}^{\gamma}$, is defined as the sum of all negatively exponentiated costs over all the possible warping paths:
