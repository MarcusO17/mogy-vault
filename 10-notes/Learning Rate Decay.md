---
created: 2026-07-09
type: note
status: draft
topic: ML
---

# Learning Rate Decay

**Learning Rate Decay** (or learning rate scheduling) is a technique used during training where the learning rate $\eta$ is gradually reduced over time. 

---

## Motivation
In [[Mini-Batch Gradient Descent]], gradients are computed on small subsets of the dataset. Because a mini-batch is only a sample, the calculated gradients are approximations of the true gradient. This introduces noise and causes parameter updates to oscillate. 

While this noise can initially help the model escape local minima, it prevents the model from settling precisely into the global minimum later in training. Decaying the learning rate over time reduces step sizes, dampening these oscillations and allowing the model to smoothly converge.

---

## Decay Techniques

### 1. Step Decay / Halving
The learning rate is reduced by a constant factor (e.g., halved) after a fixed number of epochs:
$$
\eta_{t} = \eta_{t-1} \cdot \gamma
$$
where $\gamma$ is a decay factor (e.g., $0.5$).

### 2. Exponential Decay
The learning rate decays exponentially at each epoch or step $t$:
$$
\eta_{t} = \eta_{0} \cdot e^{-k \cdot t}
$$
where $k$ is the decay rate.

### 3. Inverse Decay
The learning rate decays inversely proportional to the time step $t$:
$$
\eta_{t} = \frac{\eta_{0}}{1 + k \cdot t}
$$

---

## Relationship with Batch Size
The optimal learning rate is closely linked to the batch size:
- **Small Batch Size**: Introduces more gradient noise, requiring a smaller learning rate to maintain stability.
- **Large Batch Size**: Yields more accurate, lower-variance gradient estimates, allowing the model to safely use a larger learning rate. 
A common heuristic is the **Linear Scaling Rule**: if you scale the batch size by $B$, the learning rate should also be scaled by $B$ (or $\sqrt{B}$ for square root scaling).

---
*From* → [[Understanding Gradient Descent]]
