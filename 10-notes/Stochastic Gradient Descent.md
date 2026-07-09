---
created: 2026-07-09
type: note
status: draft
topic: ML
---

# Stochastic Gradient Descent

**Stochastic Gradient Descent (SGD)** is an optimization algorithm where model parameters (weights $\mathbf{w}$ and bias $b$) are updated iteratively after evaluating a **single training example** at a time. 

---

## The Algorithm

For a dataset $D = \{\langle \mathbf{x}^{[1]}, y^{[1]} \rangle, \dots, \langle \mathbf{x}^{[n]}, y^{[n]} \rangle\}$, features $m$, and learning rate $\eta$:

1. Initialize parameters (e.g., $\mathbf{w} := \mathbf{0} \in \mathbb{R}^m$, $b := 0$).
2. For each training epoch:
   1. Shuffle the dataset $D$.
   2. For each training example $\langle \mathbf{x}^{[i]}, y^{[i]} \rangle$:
      1. **Forward Pass**: Compute the predicted output $\hat{y}^{[i]} = \sigma(\mathbf{w}^\top \mathbf{x}^{[i]} + b)$ (where $\sigma$ is the activation function).
      2. **Compute Gradients**:
         $$
         g_{w_j} = \frac{\partial \mathcal{L}^{[i]}}{\partial w_j} = - (y^{[i]} - \hat{y}^{[i]}) x_j^{[i]} \quad \text{for } j \in \{1, \dots, m\}
         $$
         $$
         g_b = \frac{\partial \mathcal{L}^{[i]}}{\partial b} = - (y^{[i]} - \hat{y}^{[i]})
         $$
      3. **Update Parameters**:
         $$
         w_j := w_j - \eta \cdot g_{w_j} = w_j + \eta (y^{[i]} - \hat{y}^{[i]}) x_j^{[i]}
         $$
         $$
         b := b - \eta \cdot g_b = b + \eta (y^{[i]} - \hat{y}^{[i]})
         $$

---

## Characteristics of SGD
* **Speed and Frequency**: Updates parameters much more frequently than Batch Gradient Descent. This leads to faster learning progress in early training stages.
* **Noisy Path**: Because each step is computed on a single sample, the gradients are noisy approximations of the true gradient. This causes the loss curve to oscillate heavily.
* **Escaping Local Minima**: The random noise in the updates helps the model jump out of shallow local minima or saddle points that might trap batch gradient descent.
* **Dampening**: To achieve stable convergence at the global minimum, it is usually necessary to apply [[Learning Rate Decay]] to gradually reduce step sizes as training progresses.

---
*From* → [[Understanding Gradient Descent]]
