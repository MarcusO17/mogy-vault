---
created: 2026-07-09
type: note
status: draft
topic: ML
---

# Non-Linear Activation Functions

**Activation Functions** are mathematical formulas applied to the outputs of neural network nodes (net inputs). They determine whether a neuron should fire and to what degree, introducing non-linearity into the network.

Without non-linear activation functions, a multi-layer neural network collapses mathematically into a single linear model, regardless of how many hidden layers are stacked:
* **No hidden layers + Non-linear activation** = Linear decision boundary.
* **Hidden layers + Linear activation** = Linear decision boundary.
* **Hidden layers + Non-linear activation** = Complex, non-linear decision boundary.

---

## Common Activation Functions

### 1. Sigmoid / Logistic Function
Maps real-valued inputs to a probability-like range of $[0, 1]$. Commonly used in binary classification.
$$
\sigma(z) = \frac{1}{1 + e^{-z}}
$$
* **Drawback**: Suffer from the [[Dead Neurons|vanishing gradient]] problem when saturated.
* *See more* → [[Sigmoid Function]]

### 2. Hyperbolic Tangent (Tanh)
Maps inputs to a range of $[-1, 1]$. Because it is zero-centered, it generally yields faster convergence than sigmoid.
$$
\tanh(z) = \frac{e^z - e^{-z}}{e^z + e^{-z}}
$$

### 3. Rectified Linear Unit (ReLU)
The most popular activation function in deep learning. It is computationally simple and efficient:
$$
\text{ReLU}(z) = \max(0, z)
$$
* **Drawback**: Can suffer from the [[Dead Neurons]] problem.
* *See more* → [[ReLU Function]]

### 4. Hard Tanh
A computationally cheaper approximation of the Tanh function, bounded between $[-1, 1]$:
$$
\text{HardTanh}(z) = \max(-1, \min(1, z))
$$

---
*From* → [[MLP]]
