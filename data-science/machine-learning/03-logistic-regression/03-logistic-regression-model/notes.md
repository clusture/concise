---
title: Logistic Regression Model
topic: Logistic Regression
slug: logistic-regression-model
---

# Logistic Regression Model

We could approach the classification problem ignoring the fact that $y$ is discrete valued, and use linear regression algorithm to try to predict $y$ given $x$. However, it is easy to construct examples where this method performs very poorly. We will look at one of the examples where linear regression performs poorly. Let us look at the example of linear regression to fit a straight line through {tumor size, tumor type} sample set. Here, tumor type is either malignant or benign (non-malignant). 
Let us look at the diagram to visualize : 

![Linear-Regression-Tumor-Plot](./images/linear-regression-for-classification-example.PNG)

Here, The samples are shown as red crosses. And, malignant tumors get 1 and non-malignant ones get 0 in binary classification task as shown on the y-axis. The x-axis represent the tumor sizes and the green line is our hypothesis $h(x)$. To make predictions, we may say that for any given tumor size $x$, if $h(x)$ gets bigger than 0.5 we predict malignant tumor, otherwise we predict benign. Looks like this way we could correctly predict every single training set sample, but now let's change the task a bit.

Intuitively it's clear that all tumors larger certain threshold are malignant. So let's add another sample with a huge tumor size, and run linear regression again:
 
![Linear-Regression-Tumor-Plot](./images/linear-regression-for-classification-not-working-example.PNG)

Now our $h(x) > 0.5$ for malignant doesn't work anymore. To keep making correct predictions we need to change it to $h(x) > 0.2$ or something - but that not how the algorithm should work. We cannot change the hypothesis each time a new sample arrives. Instead, we should learn it off the training set data, and then (using the hypothesis we've learned) make correct predictions for the data we haven't seen before. this explains why linear regression is not the best fit for classification problems. This motivates the new algorithm called logistic regression. Let us discuss the details of logistic regression model.
