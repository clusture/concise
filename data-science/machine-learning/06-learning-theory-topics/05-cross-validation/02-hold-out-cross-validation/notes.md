---
title: Hold-out Cross-Validation
topic: Cross Validation
slug: hold-out-cross-validation
---

# Hold-out Cross-Validation

In hold-out cross-validation or simple cross-validation, we take the following steps :
1. Randomly split the dataset $S$ into two subsets $S_{train}$ and $S_{cv}$ into rougly 70-30 ratio. $S_{cv}$ is called the hold-out cross-validation set.
2. Train the model $\mathcal{M}_i$ in on the $S_{train}$ set to get the hypothesis $h_i$.
3. Select and output hypothesis $h_i$ that has the smallest error $\hat \epsilon_{S_{cv}}(h_i)$ on hold-out cross-validation set. Here, $\hat \epsilon_{S_{cv}}(h)$ denotes the empirical error of the model $h$ on the hold-out cross-validation set.

The above procedure results in better model, as with the testing on a set of examples $S_{cv}$ that the models were not trained on, we obtain a better estimate of each hypothesis $h_i$'s true generalization error.

We can then pick the one with the smallest estimated generalization error. Usually, somewhere between 1/4 − 1/3 of the data is used in the hold out cross validation set, and 30% is a typical choice.

The disadvantage of using hold-out cross-validation is that it is wasting 30% of the data. This is because the model is trained only on the 70% of the data, and the remaining 30% of the data is used for cross-validation it does not have any effect on the model. Especially, when the dataset size is very small, we can not afford to waste the data. Let us look at another type of cross-validation called **k-fold cross-validation** that addressed this problem.