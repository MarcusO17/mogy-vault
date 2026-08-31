---
created: 2026-07-09
type: note
status: draft
topic: ML
tags:
  - dl/training/normalization
---

# Normalization

**Normalization** in deep learning refers to techniques that scale inputs or hidden activations to a standard distribution. This stabilizes training, prevents vanishing or exploding gradients, and accelerates convergence.

---

## 1. Input Normalization
Standardizes the input features (e.g., using z-score standardization or min-max scaling) before feeding them to the network.
- **Why**: If input features have vastly different scales, the loss landscape becomes elongated. Gradient descent will optimize slowly as updates oscillate. Normalizing features creates a symmetric, rounder loss landscape, allowing for faster convergence.
- **Limitation**: Input normalization only stabilizes the first hidden layer. As activations propagate deeper, their distributions shift again.

---

## 2. Batch Normalization (BatchNorm)
Developed by Sergey Ioffe and Christian Szegedy in 2015, **Batch Normalization** normalizes the net inputs (activations before the activation function) of hidden layers across each mini-batch.

### How it Works
For a mini-batch of size $n$, and a neuron's net inputs $z_j^{[1]}, \dots, z_j^{[n]}$:

1. **Calculate Mini-Batch Mean**:
   $$
   \mu_j = \frac{1}{n} \sum_{i=1}^{n} z_j^{[i]}
   $$
2. **Calculate Mini-Batch Variance**:
   $$
   \sigma_j^2 = \frac{1}{n} \sum_{i=1}^{n} (z_j^{[i]} - \mu_j)^2
   $$
3. **Normalize**:
   $$
   \hat{z}_j^{[i]} = \frac{z_j^{[i]} - \mu_j}{\sqrt{\sigma_j^2 + \epsilon}}
   $$
   *(where $\epsilon$ is a small constant to prevent division by zero)*
4. **Scale and Shift**:
   $$
   \tilde{z}_j^{[i]} = \gamma_j \hat{z}_j^{[i]} + \beta_j
   $$
   where $\gamma_j$ (scale) and $\beta_j$ (shift) are learnable parameters updated via backpropagation. This allows the network to restore the original representation capacity if normalizing the activations degrades performance.

---

## PyTorch Implementation
In PyTorch, BatchNorm is implemented using `nn.BatchNorm1d` (for MLPs) or `nn.BatchNorm2d` (for CNNs). It is typically applied **pre-activation** (after the linear layer and before the activation function):

```python
import torch.nn as nn

model = nn.Sequential(
    # Bias is set to False because BatchNorm's beta parameter acts as a bias
    nn.Linear(input_dim, hidden_dim, bias=False),
    nn.BatchNorm1d(hidden_dim),
    nn.ReLU(),
    nn.Linear(hidden_dim, output_dim)
)
```

---

## Why BatchNorm Works
* **Original Theory (Internal Covariate Shift)**: The creators hypothesized that BatchNorm reduces "Internal Covariate Shift" (the continuous shifting of activation distributions as previous layers update).
* **Smoother Loss Landscape (Modern Consensus)**: A 2018 study by Santurkar et al. demonstrated that BatchNorm's success is unrelated to covariate shift. Instead, it significantly **smooths the optimization landscape**. This smoothing makes gradients more predictable and stable, allowing for much larger learning rates $\eta$ and faster convergence.

---
*From* → [[Improving Generalization]]
