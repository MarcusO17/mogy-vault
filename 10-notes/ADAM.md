---
created: 2026-07-09
type: note
status: draft
topic: ML
tags:
  - dl/training/optimizer
---

# ADAM

**Adam** (Adaptive Moment Estimation) is a widely used optimization algorithm in deep learning that combines the concepts of [[Momentum]] and [[RMSProp]].

It maintains moving averages of both the gradients (first moment) and the squared gradients (second raw moment):

1. **First Moment (Momentum-like term)**:
   $$
   m_t = \beta_1 m_{t-1} + (1 - \beta_1) g_t
   $$
   where $g_t$ is the gradient $\frac{\partial \mathcal{L}}{\partial w}$ at time step $t$, and $\beta_1$ is the exponential decay rate for the first moment estimate (typically $0.9$).

2. **Second Moment (RMSProp-like term)**:
   $$
   v_t = \beta_2 v_{t-1} + (1 - \beta_2) g_t^2
   $$
   where $\beta_2$ is the exponential decay rate for the second raw moment estimate (typically $0.999$).

### Bias Correction
Because $m_t$ and $v_t$ are initialized as vectors of zeros, they are biased toward zero, especially during initial steps when decay rates are close to $1$. To correct this, bias-corrected estimators are computed:
$$
\hat{m}_t = \frac{m_t}{1 - \beta_1^t} \quad \text{and} \quad \hat{v}_t = \frac{v_t}{1 - \beta_2^t}
$$

### Parameter Update
Parameters are updated using the bias-corrected moments:
$$
w_{t} := w_{t} - \frac{\eta}{\sqrt{\hat{v}_t} + \epsilon} \hat{m}_t
$$
where $\eta$ is the learning rate and $\epsilon$ is a small constant (e.g., $10^{-8}$) to prevent division by zero.

*From* → [[Momentum]], [[RMSProp]]
