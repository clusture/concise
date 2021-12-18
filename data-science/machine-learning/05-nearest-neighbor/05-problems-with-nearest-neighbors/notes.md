---
title: Problems with Nearest Neighbors
topic: Nearest Neighbors
slug: problems-nearest-neighbors
---

# Problems with Nearest Neighbors

The nearest neighbor learning algorithms are simple supervised learning algorithms. They do not make any assumptions on the data. Hence, they can be used for nonlinear data. However, they suffer from few problems. The following are some of the problems while using nearest neighbors :

1. The nearest neighbor algorithms require high storage.
2. The nearest neighbor algorithms prediction rate is slow.
3. If the training data is small they may not work well, If the training data is large they would be slow as they need to store all the data.
4. k-NN algorithms have the drawback that occurs while using the basic "majority voting" classification when the class distribution is skewed. That is, examples of a more frequent class tend to dominate the prediction of the new example, because they tend to be common among the k nearest neighbors due to their large number.
5. Choice of "k" in k-NN is a crucial parameter. The larger the value of "k", the more accurate the prediction is, but at the same time decision might be skewed towards majority class. For the smaller the value of "k", the less accurate and noisy the prediction is.
