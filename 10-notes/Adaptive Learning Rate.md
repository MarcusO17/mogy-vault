---
created: 2026-07-09
type: note
status: draft
topic: ML
tags:
  - dl/training/optimizer
---

# Adaptive Learning Rate

Adaptive learning rate methods adjust the step size for individual parameters during training to optimize convergence. 

A classic heuristic-based approach (such as the Delta-Bar-Delta algorithm) assigns a local gain parameter $g_{i,j}$ to each individual weight $w_{i,j}$ to scale the global learning rate $\eta$:

$$
w_{i,j}(t) = w_{i,j}(t-1) - \eta \cdot g_{i,j}(t) \cdot \frac{\partial \mathcal{L}}{\partial w_{i,j}}(t)
$$

### Local Gain Update Heuristics
The local gain is updated at each time step based on the consistency of the gradient direction:

1. **Consistent Direction** (gradient sign remains the same): If the gradient continues to point in the same direction, we increase the learning rate additively to accelerate training:
   $$
   g_{i,j}(t) = g_{i,j}(t-1) + \beta
   $$
2. **Inconsistent Direction** (gradient sign changes): If the gradient changes sign (indicating that the update has overshot a minimum and is oscillating), we decrease the learning rate multiplicatively:
   $$
   g_{i,j}(t) = g_{i,j}(t-1) \cdot (1 - \beta)
   $$

where $\beta$ is a small adjustment hyperparameter (e.g., $0.05$).

Modern adaptive optimizers (such as [[RMSProp]] and [[ADAM]]) build on this concept by using the history of squared gradients to scale the learning rate per-parameter automatically.

*From* → [[Understanding Gradient Descent]]
