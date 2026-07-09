---
created: 2026-07-09
type: note
status: draft
topic: ML
---

# Linear Regression

**Linear Regression** is a fundamental supervised learning model used to predict a continuous target variable $\hat{y} \in \mathbb{R}$ from input features $\vec{x}$.

### Model Formulation
Unlike [[The Perceptron]], which uses a step function for classification, linear regression uses the **identity function** as its activation function:
$$
h(\vec{x}) = \mathbf{w}^\top \vec{x} + b = \hat{y}
$$


### Parameter Optimization

There are two primary methods for finding the optimal weights $\mathbf{w}$ and bias $b$ that minimize the loss (typically Mean Squared Error):

#### 1. Closed-Form Analytical Solution (Normal Equation)
Using statistics, the exact weights can be computed directly:
$$
\mathbf{w} = (\mathbf{X}^\top \mathbf{X})^{-1}\mathbf{X}^\top \mathbf{y}
$$
- **Pros**: Finds the exact global minimum in a single step without tuning learning rates.
- **Cons**: Calculating the inverse of $\mathbf{X}^\top \mathbf{X}$ has a computational complexity of $O(d^3)$ (where $d$ is the number of features). This is computationally prohibitive for very large datasets and does not generalize to non-convex loss surfaces in deep neural networks.

#### 2. Iterative Solution (Gradient Descent)
For large-scale machine learning, we train the model iteratively using [[Stochastic Gradient Descent]] (SGD):
1. **Initialization**: Initialize weights $\mathbf{w}$ and bias $b$ to zero or small random values.
2. **Analysis**: In each training round (epoch), compute the loss on the dataset and determine how changing the parameters affects the loss (by computing the partial gradients).
3. **Update**: Step the parameters slightly in the negative gradient direction to reduce the loss.
4. **Repeat**: Iterate this process until the loss converges (stops decreasing).

*From* → [[Common Math Notation]]
