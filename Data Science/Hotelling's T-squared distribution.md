---

created: <% tp.file.creation_date() %>

---
tags:: #Statistics 

# Hotelling's T-squared distribution

Is a multivariate probability dsitribution that is tightly related to the [[F distribution]] and is most notable for arising from the underlying Students t-distribution.

This distribution arises in multivariate statistics in undertaking tests of differences between the (multivariate) means of different populations. Where test for uni-variate problems would use the t-test.

## Definition

If the vector $d$ is a Guassian multivariate-distribution with zero mean and unit covariance matrix $N(\textbf{0}_{p}, \textbf{I}_{p,p})$ and $M$ is a $p \times p$ matrix with unit scale and m degrees of freedom with a Wishart distribution $W(\textbf{I}_{p,p}, m)$ then the quadratic form $X$ has a Hotelling distribution:

$X = md^{\intercal}M^{-1}d \sim T^2(p,m)$

Furthermore, if a random variable $X$ has Hotelling's T-squared distribution $X \sim T^2_{p,m}$, then:

$\frac{m-p+1}{pm}X \sim F_{p,m-p+1}$

Is the F-distribution with parameters p and m-p+1.
