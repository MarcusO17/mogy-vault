---
created: 2026-07-09
type: note
status: draft
topic: ML
tags:
  - dl/training/optimizer
---

# RMSProp

**RMSProp** (Root Mean Squared Propagation) is an adaptive learning rate optimization algorithm designed to stabilize and accelerate gradient descent. It was proposed by Geoffrey Hinton in his Coursera lecture.

---

## Mathematical Formulation
RMSProp scales the learning rate for each parameter by dividing it by the square root of the exponentially decaying average of its historical squared gradients:

### 1. Accumulating Squared Gradients (Second Moment)
$$
v_t = \beta \cdot v_{t-1} + (1 - \beta) g_t^2
$$
where:
- $g_t = \frac{\partial \mathcal{L}}{\partial w}$ is the current gradient at time step $t$.
- $v_t$ is the exponentially running average of the squared gradients (moving average).
- $\beta$ is the decay parameter, typically set to $0.9$.

### 2. Parameter Update
$$
w_t = w_{t-1} - \frac{\eta}{\sqrt{v_t} + \epsilon} g_t
$$
where:
- $\eta$ is the global learning rate.
- $\epsilon$ is a small constant (e.g., $10^{-8}$) to prevent division by zero.

---

## Intuition
By dividing the update step by the root mean square of historical gradients:
* Parameters with **large gradients** (which oscillate heavily) will have their updates scaled *down* (divided by a larger $\sqrt{v_t}$).
* Parameters with **small gradients** (which crawl slowly) will have their updates scaled *up* (divided by a smaller $\sqrt{v_t}$), accelerating learning.

RMSProp is very similar to AdaDelta and forms the basis for the second-moment step in the [[ADAM]] optimizer.

---
*From* → [[Adaptive Learning Rate]]
