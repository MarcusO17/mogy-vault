---
created: 2026-07-09
type: note
status: draft
topic: ML
---

# Understanding Gradient Descent

**Gradient Descent** is an optimization algorithm used to minimize a loss function by iteratively updating model parameters in the opposite direction of the gradient of the loss function with respect to those parameters.

---

## The Core Concept
The gradient of a function $\nabla \mathcal{L}(\mathbf{w}, b)$ is a vector pointing in the direction of the steepest *ascent* at a given point. To find the minimum of the loss function $\mathcal{L}$, we must take steps in the opposite direction (the steepest *descent*):

$$
\mathbf{w} := \mathbf{w} - \eta \nabla_{\mathbf{w}} \mathcal{L}
$$
$$
b := b - \eta \nabla_b \mathcal{L}
$$

where $\eta > 0$ is the learning rate (step size).

---

## Derivation of Gradients (Linear Regression)
Consider a linear regression model with predictions $\hat{y}^{[i]} = \mathbf{w}^\top \mathbf{x}^{[i]} + b$ trained using the Sum of Squared Errors (SSE) loss:

$$
\mathcal{L}(\mathbf{w}, b) = \sum_{i=1}^{n} (\hat{y}^{[i]} - y^{[i]})^2
$$

To update the weight $w_j$ associated with the $j$-th feature, we compute the partial derivative $\frac{\partial \mathcal{L}}{\partial w_j}$ using the chain rule:

$$
\begin{aligned}
\frac{\partial \mathcal{L}}{\partial w_j} &= \frac{\partial}{\partial w_j} \sum_{i=1}^{n} (\hat{y}^{[i]} - y^{[i]})^2 \\
&= \sum_{i=1}^{n} 2(\hat{y}^{[i]} - y^{[i]}) \cdot \frac{\partial}{\partial w_j} (\hat{y}^{[i]} - y^{[i]}) \\
&= \sum_{i=1}^{n} 2(\hat{y}^{[i]} - y^{[i]}) \cdot \frac{\partial}{\partial w_j} (\mathbf{w}^\top \mathbf{x}^{[i]} + b - y^{[i]})
\end{aligned}
$$

Since the derivative of $\mathbf{w}^\top \mathbf{x}^{[i]} = w_1 x_1^{[i]} + \dots + w_j x_j^{[i]} + \dots$ with respect to $w_j$ is simply the feature value $x_j^{[i]}$:

$$
\frac{\partial \mathcal{L}}{\partial w_j} = 2 \sum_{i=1}^{n} (\hat{y}^{[i]} - y^{[i]}) x_j^{[i]}
$$

Similarly, for the bias $b$:

$$
\frac{\partial \mathcal{L}}{\partial b} = 2 \sum_{i=1}^{n} (\hat{y}^{[i]} - y^{[i]})
$$

---

## Comparison of Optimization Modes
* **[[Batch Gradient Descent]]**: Computes the gradient over the entire dataset before making a single update. This produces a smooth, direct trajectory to the minimum but is computationally expensive for large datasets.
* **[[Stochastic Gradient Descent]] (SGD)**: Computes the gradient and updates parameters using a single training example at a time. This results in a noisy, erratic path but is much faster and helps escape local minima.
* **[[Mini-Batch Gradient Descent]]**: Computes gradients over small subsets of the dataset, balancing the speed of SGD with the stability of Batch Gradient Descent.

---
*From* → [[Supervised Learning]]
