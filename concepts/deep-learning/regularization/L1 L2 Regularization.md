Created : 2025-10-11 16:10
Tags :
Type :

---
# L1 L2 Regularization
L1/L2 Regularization focuses on adding a penalty to a network's complexity. 

* L1 Regularization -> LASSO Regression
* L2 Regularization -> Ridge Regression

Basically, these perform weight shrinkages or to penalize complexity.

---
## L2 Regularization

Assume the loss of w,b is calculated using [[Cross Entropy|binary cross entropy]] across the whole dataset.
$$
\begin{align}
\text{Loss}_{\mathbf{w,b}} &= \frac{1}{n} \sum^n_{i=1}\mathcal{L}(y^{[i]},\hat{y}^{[i]}) \\

\end{align}
$$


The $L_{2}\text{-Regularized-Loss}$ would then be calculated as:
$$
\text{Loss}_{\mathbf{w,b}}=\frac{1}{n}\sum^n_{i=1}\mathcal{L}(y^{[i]},\hat{y}^{[i]}) + \frac{\lambda}{n}\sum_{j}w^2_{j}
$$
$\lambda$ here is the regularization strength. Usually 0.01 or 0.1

So we can see, the loss of the result, it adds a penalty based on the squared value of the weights. This forces the model to keep its weights small, which helps prevent overfitting.

>[!help] Larger weights cause overfitting. This means the model is **extremely sensitive** to changes in those specific features, causing it to make predictions based on memorized features from the training data rather than the general pattern

---
### L2 Regularization in MLP

L2 Regularization factor is dependent on the $w^2$ of the respective weight of the feature. So in [[Multilayer Networks]], how can L2 regularization be carried out?
$$
L_{2} \text{-Regularized-Loss} = \frac{1}{n} \sum^n_{i=1}\mathcal{L}(y^{[i]},\hat{y}^{[i]}) + \frac{\lambda}{n} \sum^L_{l=1}\lvert \lvert\mathbf{w}^{(l)}\rvert  \rvert^2_{F} 
$$
where $l$ is the count over layers.

This formula utilises the ***squared Frobenius Norm*** :
$$
\lvert \lvert\mathbf{w}^{(l)}\rvert  \rvert^2_{F} 
$$
which essentially means:

>[!quote]  Take every single weight in the weight matrix for that layer, square it, and then add them all up.

This formula helps us to get the regularization factor across all layers.

---
### L2 with Gradient Descent 

So how does L2 work with [[Gradient Descent]]?

Regular gradient descent:
$$
w_{i,j} := w_{i,j} - \eta \frac{ \partial \mathcal{L} }{ \partial w_{i,j} } 
$$
Gradient Descent with L2 Regularization
$$
w_{i,j} := w_{i,j} - \eta \left( \frac{ \partial \mathcal{L} }{ \partial w_{i,j} } + \frac{2\lambda}{n}w_{i,j}  \right)
$$
---
# References


