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

These metrics are rather different as we now predicting in a continuous range.