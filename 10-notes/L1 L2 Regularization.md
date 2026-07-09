---
created: 2026-07-09
type: note
status: draft
topic: ML
---

# L1 L2 Regularization

**L1 and L2 Regularization** are methods that prevent overfitting by adding a penalty term to the loss function based on the size of the model's weights.

---

## 1. L2 Regularization (Ridge Regression / Weight Decay)
L2 regularization penalizes the sum of the squared weights. The regularized loss is defined as:

$$
\text{Loss}_{\text{reg}} = \frac{1}{n} \sum_{i=1}^{n} \mathcal{L}(y^{[i]}, \hat{y}^{[i]}) + \frac{\lambda}{2n} \sum_{j} w_j^2
$$

where $\lambda \ge 0$ is the regularization strength (hyperparameter), and $n$ is the number of training instances.

### In Multilayer Networks (Frobenius Norm)
For deep networks, the L2 penalty is calculated across all layers $l \in \{1, \dots, L\}$ using the squared **Frobenius norm** of the weight matrices:
$$
\text{Loss}_{\text{reg}} = \frac{1}{n} \sum_{i=1}^{n} \mathcal{L}(y^{[i]}, \hat{y}^{[i]}) + \frac{\lambda}{2n} \sum_{l=1}^{L} \|\mathbf{W}^{(l)}\|_F^2
$$
where $\|\mathbf{W}^{(l)}\|_F^2$ is the sum of the squares of all elements in the weight matrix for layer $l$.

### Effect on Gradient Descent (Weight Decay)
The gradient descent update under L2 regularization becomes:
$$
w_{i,j} := w_{i,j} - \eta \left( \frac{\partial \mathcal{L}}{\partial w_{i,j}} + \frac{\lambda}{n} w_{i,j} \right)
$$
We can rewrite this as:
$$
w_{i,j} := \left(1 - \frac{\eta \lambda}{n}\right) w_{i,j} - \eta \frac{\partial \mathcal{L}}{\partial w_{i,j}}
$$
This demonstrates why L2 regularization is referred to as **weight decay**: at each step, the weights are multiplied by a decay factor $\left(1 - \frac{\eta \lambda}{n}\right)$ before subtracting the gradient step. This prevents weights from growing excessively large, making the model less sensitive to individual feature noise.

---

## 2. L1 Regularization (LASSO)
L1 regularization penalizes the sum of the absolute values of the weights:

$$
\text{Loss}_{\text{reg}} = \frac{1}{n} \sum_{i=1}^{n} \mathcal{L}(y^{[i]}, \hat{y}^{[i]}) + \frac{\lambda}{n} \sum_{j} |w_j|
$$

### Effect of L1
* Unlike L2 which shrinks weights smoothly toward zero, L1 drives weights to be exactly zero.
* This leads to **sparse models**, acting as a form of automatic feature selection by zeroing out unimportant features.

---
*From* → [[Regularization]]
