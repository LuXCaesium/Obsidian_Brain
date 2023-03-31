---

created: <% tp.file.creation_date() %>

---
tags:: #Statistics 

# Copula

A copula is a multivariate cumulative distribution function for which the marginal probability distribution of each variable is uniform on the interval $[0, 1]$. They are used to describe/model the dependence between random variables. 

## Mathematical Definition

Consider a random vector $(X_1, X_2, \dots, X_d)$. Suppose its marginals are continuous (i.e $F_i(x)=Pr[X_i \leq x]$ are continuous functions). Applying the probability integral transform ($Y := F_X(X)$ has standard uniform distribution for RV $X$ of continuous distribution and CDF $F_X$), the random vector
$(U_1, U_2, \dots, U_d) = (F_1(X_1), F_2(X_2), \dots, F_d(X_d))$
has marginals that are uniformly distributed on the interval $[0, 1]$.

The copula of $(X_1, X_2, \dots, X_d)$ is defined as the joint cumulative distribution function of $(U_1, U_2, \dots, U_d)$:
$C(u_1, u_2, \dots, u_d) = Pr[U_1 \leq u_1]$
