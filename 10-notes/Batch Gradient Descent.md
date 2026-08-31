---
created: 2026-07-09
type: note
status: draft
topic: ML
tags:
  - dl/training/optimizer
---

# Batch Gradient Descent

**Batch Gradient Descent** (sometimes referred to as Batch Mode training) is a optimization algorithm variant where the model parameters (weights $\mathbf{w}$ and bias $b$) are updated only after evaluating the loss and gradients over the **entire training dataset**.

### Algorithm

Given a training dataset $\mathscr{D} = \{ \langle \vec{x}^{[i]}, y^{[i]} \rangle \}_{i=1}^{n}$:

1. **Initialization**: Initialize weights $\mathbf{w} := \mathbf{0}$ and bias $b := 0$.
2. **Epoch Loop**: For each epoch:
   1. Initialize update vectors to store accumulated gradients: $\Delta\mathbf{w} := \mathbf{0}$ and $\Delta b := 0$.
   2. **Batch Pass**: For each training example $\langle \vec{x}^{[i]}, y^{[i]} \rangle$ in $\mathscr{D}$:
      - Perform forward pass to compute prediction $\hat{y}^{[i]}$.
      - Perform backward pass to calculate the gradients of the loss with respect to parameters.
      - Accumulate the gradients: $\Delta\mathbf{w} := \Delta\mathbf{w} + \nabla_{\mathbf{w}} \mathcal{L}^{[i]}$ and $\Delta b := \Delta b + \nabla_{b} \mathcal{L}^{[i]}$.
   3. **Parameter Update**: Update the parameters using the accumulated gradients and learning rate $\eta$:
      $$
      \mathbf{w} := \mathbf{w} - \eta \cdot \Delta\mathbf{w}
      $$
      $$
      b := b - \eta \cdot \Delta b
      $$

### Characteristics
- **Update Frequency**: Parameters are updated exactly once per epoch.
- **Gradient Accuracy**: The accumulated update uses the true gradient of the entire dataset loss surface, resulting in a stable and direct path toward the minimum.
- **Computational Cost**: Extremely computationally expensive for large datasets, as a full pass over all data is required to perform a single step.

*From* → [[Understanding Gradient Descent]]
