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

- **True Positives**: When you correctly predict an observation belongs to a class.
- **True Negatives**: When you correctly predict an observation does not belong to a class.
- **False Positives**: When you wrongly predict an observation belongs to a class.
- **False Negatives**: When you wrongly predict an observation does not belong to a class.

You often plot these results in a confusion matrix, and use the following metrics to evaluate the performance of the model.

**Accuracy**: the percentage of correct predictions for the test data.

$$
\textrm{accuracy} = \frac{\textrm{correct predictions}}{\textrm{all predictions}}
$$






