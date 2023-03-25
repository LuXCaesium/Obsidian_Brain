---

created: <% tp.file.creation_date() %>

---
tags:: #MachineLearning #DataScience
# Evaluating Machine Learning Models

Here we will discuss how to evaluate a machine learning model, and in the process answer some of the following questions:

- How well is my model doing ? is it a useful model?
- Will training my model on more data improve its performance?
- Do I need to include more features.

## The train/test/validation split

One problem with the train/test split that is so commonly used in today's machine learning practice is we often want to determine the best parameters for the model whilst training. You could not do this on the test set as you would have bias toward this set. Instead we define a third split, *Validation* which we use to tune the parameters when training. These splits are usually 60%, 20%, 20%.

## Metrics

### Classification

When performing classification predictions, there's four types of outcomes that could occur.

- **True Positives**: When you predict an observation belongs to a class and it actually does belong to that class.
- **True Negatives**: When you predict an observation does not belong to a class and it actually does not belong to that class.
- **False Positives**: When you predict an observation belongs to a class when in reality it does not.
- **False Negatives**: When you predict an observation does not belong to a class when in fact it does.

You often plot these results in a confusion matrix, and use the following metrics to evaluate the performance of the model.

**Accuracy**: the percentage of correct predictions for the test data.

$$
\textrm{accuracy} = \frac{\textrm{correct predictions}}{\textrm{all predictions}}
$$

**Precision**: fraction of relevant examples (true positives) among all examples predicted to belong in a certain class.

$$
\textrm{precision} = \frac{\textrm{true positives}}{\textrm{true positives} + \textrm{false positives}}
$$

**Recall**: fraction of examples which were predicted to belong to a class w.r.t all examples which truly belong to that class.

$$
\textrm{recall} = \frac{\textrm{true positives}}{\textrm{true positives + false negatives}}
$$


![[Precisionrecall.png]]

If you create a classifier that always predicts that the person does not have a disease (when 1% of the population has the disease), you would have a model that is 99% accurate and 0% useful. In this example recall will ensure that we are not overlooking the people who have the disease, whilst precision ensures that we are not miss-classifying too many people as having the disease when they do not. So it is important to evaluate both the precision and the recall of the model.

**F-Score**: this is a single metric which combines both precision and recall.

$$
F_\beta = (1+\beta^2)\frac{\textrm{precision.recall}}{(\beta^2.\textrm{precision}) + \textrm{recall}}
$$

The $\beta$ parameter allows us to control the trade-off of importance between precision and recall. $\beta <1$ favours precision whilst $\beta > 1$ the recall.

### Regression

These metrics are rather different as we now predicting in a continuous range instead of a discrete number of classes.

**Explained Variance**: compares the variance within the expected outcomes to the variance in the error of our model. This represents the amount of variation in the original dateset that our model is able to explain.

$$
EV(y_{true}, y_{pred}) = 1- \frac{Var(y_{true} - y_{pred})}{y_{true}}
$$
**Mean Squared Error**: is simply the average of squared differences between the predicted output and the true output. Squared error is commonly used as its agnostic to whether the prediction was too high or low.

$$
MSE(y_{true}, y_{pred}) = \frac{1}{n_{samples}}\sum(y_{true} - y_{pred})^2
$$

**R$^2$ coefficient**: Represents the proportion of variance in the outcome that our model is capable of predicting based on its features. (Note how this is equal to the fraction of explained variance)

$$
R^2(y_{true}, y_{pred}) = 1 - \frac{\sum(y_{true} - y_{pred})^2}{\sum(y_{pred} - \bar{y})^2}
$$

$$
\bar{y} = \frac{1}{n_{samples}\sum{y_{true}}}
$$

## Bias vs Variance

**Bias**: when the  pre-impose the structure of a model inhibits its ability to learn, i.e fitting a linear model to explain a exponential relationship. Bias can also be introduced when trying to teach it to perform a task without presenting all the necessary information.

**under-fitting**: When models with high bias pay little attention to the data being presented.

**Variance**:  When we train out model and it learns *too much* from the training data. This causes the model to capture the noise in addition to the signal. So the model will have large fluctuations that does not represent the true trend. This is high **variance**.

**over-fitting**: when the model pays too much attention to the training dataset, and will not generalise to new data.

The best model will fit somewhere in between these two extremes, we want out model to capture all the required data for accurate prediction, but we do not want to over-fit and capture the noise rather than the signal.

**Validation curves**:

These curves allows us to find the *sweet spot* between under-fitting and over-fitting to build a model that generalises well.

A typical validation curve is a plot of the model's error as a function of some model hyper-parameter which controls the models tendency to over-fit the data. This parameter could be anything and usually has significant control over the complexity of the model.

![[Validation_curve.png]]



