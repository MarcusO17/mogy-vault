---
created: 2026-07-09
type: note
status: draft
topic: ML
tags:
  - dl/training/optimizer
---

# Momentum

**Momentum** is an optimization technique used to accelerate gradient descent by accumulating a velocity vector in the direction of persistent gradients. It dampens oscillations in high-curvature directions and helps the optimizer escape local minima or saddle points.

---

## Mathematical Formulation
Instead of updating parameters solely based on the current gradient, momentum incorporates a moving average of past update steps (velocity):

$$
v_t = \beta \cdot v_{t-1} + \eta \cdot g_t
$$
$$
w_t = w_{t-1} - v_t
$$

where:
- $w_t$ represents the weights at time step $t$.
- $g_t = \frac{\partial \mathcal{L}}{\partial w}$ is the current gradient of the loss with respect to the weights.
- $v_t$ is the velocity vector at time step $t$ (initially $v_0 = \mathbf{0}$).
- $\eta$ is the learning rate.
- $\beta \in [0, 1)$ is the momentum decay coefficient (typically set to $0.9$), which acts as a "friction" factor.

---

## Conceptual Intuition
1. **The Physical Analogy**: Think of a heavy ball rolling down a loss surface. The ball accumulates momentum from gravity (gradients) as it rolls down, helping it roll past small humps (local minima) and cross flat areas (saddle points) faster.
2. **Dampening Oscillations**: In ravines where the surface curves steeply in one direction but gently in another, standard gradient descent oscillates wildly. Momentum averages out these opposing vertical oscillations while building speed in the horizontal direction toward the minimum.

![[Pasted image 20251022153837.png]]

---
*From* → [[Understanding Gradient Descent]]
