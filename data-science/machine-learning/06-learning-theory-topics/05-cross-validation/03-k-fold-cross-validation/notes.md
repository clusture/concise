---
title: k-Fold Cross-Validation
topic: Cross Validation
slug: k-fold-cross-validation
---

# k-Fold Cross-Validation

In k-fold cross-validation or k-fold cross-validation, we take the following steps :
1. Randomly split the dataset $S$ into $k$ disjoint subsets $S_{1}, \dots, S_{k}$ into roughly equal parts.
2. For each model $\mathcal{M}_i$, evaluate :
    * For each subset $S_{j}$ of $S_{1}, \dots, S_{k}$:
        * Train the model $\mathcal{M}_i$ on the $S_{1}, \dots,S_{j-1},S_{j+1},\dots, S_{k}$ set to get the hypothesis $h_{ij}$.
        * Test the model on the $S_{j}$ set to get the error $\hat \epsilon_{S_j}(h_{ij})$.
    * Estimated generalization error of the model $\mathcal{M}_i$ is given by the average of the errors $\hat \epsilon_{S_j}(h_{ij})$'s (over all $j$'s).
3. Select the model $\mathcal{M}_i$ with the lowest estimated generalization error, and retrain the model on entire training set $S$.
4. The resulting model is the final model.

A typical choice for the number of folds to use here would be $k = 10$.
While the fraction of data held out each time is now $1/k$ much smaller
than before. This procedure may also be more computationally expensive
than hold-out cross validation, since we now need train to each model k
times. Also, since we're holding out one training example at a time, this method is also called **leave-one-out cross validation**.