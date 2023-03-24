---

created: <% tp.file.creation_date() %>

---
tags:: #MachineLearning #DataScience
# Evaluating Machine Learning Models

Here we will discuss how to evaluate a machine learning model, and in the process answer some of the following questions:

- How well is my model doing ? is it a useful model?
- Will training my model on more data improve its performance?
- Do I need to include more features.

### The train/test/validation split

One problem with the train/test split that is so commonly used in today's machine learning practice is we often want to determine the best parameters for the model whilst training. You could not do this on the test set as 

Usually we often split our data into 70% train and 30% test, however we often want to evaluate the model during training to find the best parameters. We cannot use the test set for this or else we'll end up selecting the parameters that perform best on the test data and hence wont generalise. Hence we define a new *validation* set using a 60%, 20%, 20% train, validation,test split. 

