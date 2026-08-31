---
created: 2026-07-09
type: note
status: draft
topic: ML
tags:
  - linear-models
  - classification
---

# Logistic Regression

**Logistic Regression** is a fundamental supervised learning model used for binary classification. It maps input features to a probability value between $0$ and $1$, which is then thresholded to predict a binary class label $\hat{y} \in \{0, 1\}$.

---

## Model Architecture
Logistic regression is visually similar to [[ADALINE]], but instead of using an identity function, it applies the **logistic sigmoid function** to the net input $z$:

$$
z = \mathbf{w}^\top \mathbf{x} + b
$$
$$
h(\mathbf{x}) = \sigma(z) = \frac{1}{1 + e^{-z}}
$$

The predicted probability $h(\mathbf{x}) = P(y=1 \mid \mathbf{x})$ is converted into a class label $\hat{y}$ using a decision threshold (typically $0.5$):

$$
\hat{y} = \begin{cases} 
1 & \text{if } h(\mathbf{x}) \ge 0.5 \iff z \ge 0 \\ 
0 & \text{if } h(\mathbf{x}) < 0.5 \iff z < 0 
\end{cases}
$$

---

## Loss Function: Negative Log-Likelihood (BCE)

The labels follow a **Bernoulli distribution**:
$$
P(y \mid \mathbf{x}) = h(\mathbf{x})^y (1 - h(\mathbf{x}))^{1-y}
$$

To find the optimal weights $\mathbf{w}$ and bias $b$, we use **Maximum Likelihood Estimation** (MLE) to maximize the joint probability across all $n$ training instances:
$$
P(\mathbf{y} \mid \mathbf{X}) = \prod_{i=1}^{n} P(y^{[i]} \mid \mathbf{x}^{[i]})
$$

To transform this into a numerically stable minimization problem for gradient descent, we negate the function and take its logarithm (transforming the product into a sum). This yields the **Negative Log-Likelihood (NLL)** loss, which is mathematically identical to [[Cross Entropy#Binary Cross-Entropy|Binary Cross-Entropy]]:

$$
\mathcal{L}(\mathbf{w}, b) = -\sum_{i=1}^{n} \left[ y^{[i]} \log(h(\mathbf{x}^{[i]})) + (1 - y^{[i]}) \log(1 - h(\mathbf{x}^{[i]})) \right]
$$

Using the log-likelihood prevents **numerical underflow** that would occur when multiplying many small probability values together.

---

## Gradient and Saturation
The gradient of the loss with respect to weight $w_j$ is calculated using the chain rule:

$$
\frac{\partial \mathcal{L}}{\partial w_j} = \frac{\partial \mathcal{L}}{\partial h(\mathbf{x})} \cdot \frac{\partial h(\mathbf{x})}{\partial z} \cdot \frac{\partial z}{\partial w_j}
$$

### Sigmoid Saturation & Vanishing Gradients
A key limitation of sigmoid-based activations is **saturation**. When the net input $z$ is very large or very small, the sigmoid output sits on a plateau where the derivative $\sigma'(z) = \sigma(z)(1 - \sigma(z))$ approaches $0$. 

During backpropagation, this near-zero derivative causes the overall gradient to vanish, meaning the weights stop updating and learning stalls. This is the origin of the [[Vanishing Gradients]] problem in deep networks.

---
*From* → [[Supervised Learning]]
