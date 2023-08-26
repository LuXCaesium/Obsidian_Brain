---

created: <% tp.file.creation_date() %>

---
tags:: #QuantileRegression #DataScience #Statistics 

# Quantile Regression

In Linear regression, we aim to estimate the conditional mean of the response variable using Ordinary Least Squares, however in Quantile Regression we use a pinball loss function to calculate the conditional median (or any other quantile) of the response variable. Note that, estimating the conditional mean is rather robust to outliers.

## Quantile of a Random Variable
Let $Y$ be a real valued random variable with CDF $F_Y(y) = P(Y \leq y)$. The $\tau^{th}$ quantile of $Y$ is given by 

$$q_Y(\tau) = F^{-1}_Y(\tau) = \inf\{y:F_Y(y) \geq \tau\}$$
Where $\tau \in (0,1)$.

Given the mean absolute error loss for the conditional median ($F^{-1}_Y(0.5|X=x)$) is $l(y,\hat{y}) = |y-\hat{y}|$ we generalise this for any quantile $\tau$ defining a loss function we call the *Pinball Loss*:

$$l_\tau(y, \hat{y}) = \left{ t$$

