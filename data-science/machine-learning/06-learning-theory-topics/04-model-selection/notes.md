---
title: Model Selection
topic: Learning Theory Topics
slug: model-selection
---

# Model Selection

Model selection correspond to the process of choosing the best model for a given dataset. Model selection is a process that can be applied across :
1. Different types of models (e.g. logistic regression, Naive Bayes, k-NN, etc.)
2. Same type of models configured with different model hyperparameters (e.g. different values of $k$ in an k-NN).,

For example, we may have a dataset for which we are interested in developing a classification or regression predictive model. We do not know beforehand as to which model will perform best on this problem, as it is unknown. Therefore, we fit and evaluate a suite of different models on the problem. Model selection is the process of choosing one of the models as the final model that addresses the problem.

Let us consider the formal setting, where models are given by $\{\mathcal{M}_1, \mathcal{M}_2,\ldots,\mathcal{M}_n\}$. The goal is to find the best model $\mathcal{M}$ that minimizes the loss function.

There are mainly two types of techniques for model selection:
1. Probabilistic model selection
2. Resampling model selection

## Probabilistic Model Selection

Probabilistic measures involve analytically scoring a candidate model using both its performance on the training dataset and the complexity of the model. The score is a probability that the model is the best model.

It is known that training error is optimistically biased, and therefore is not a good basis for choosing a model. The performance can be penalized based on how optimistic the training error is believed to be. This is typically achieved using algorithm-specific methods, often linear, that penalize the score based on the complexity of the model.

## Resampling Model Selection

There are various resampling techniques that can be used to select the best model. Some of the popular resampling techniques are given as follows: 
1. Train/Validation/Test Split
2. Cross Validation
3. Bootstrap

Resampling techniques are popular techniques compared to probabilistic model selection. Let us see how resampling techniques can be used to select the best model.