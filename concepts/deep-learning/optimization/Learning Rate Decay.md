Created : 2025-10-22 11:01
Tags :
Type :
Lecture : L12
Video : https://www.youtube.com/watch?v=7RhNXYqDBfU

---
# Learning Rate Decay

Because a [[Training a Neural Net#Mini-Batch Mode|Mini-Batch]] is only a small sample of the entire dataset, the calculated loss and **gradients are approximations** of the true values, leading to significant **oscillations** or noise in the parameter updates as the model trains. This noise, while initially helpful for escaping local minima, prevents the model from settling precisely into the global minimum later in training; therefore, the standard solution is to **decay the learning rate** over time, gradually reducing the size of the update steps to **dampen these oscillations** and ensure a smooth, stable convergence.

It's recommended to train once first to see how much the LR should be decayed.

---
## Learning Rate Decay Techniques

### Exponential Decay
$$
\eta_{t} := \eta_{0} \cdot e^{-k \cdot t}
$$
![[Pasted image 20251022115417.png]]

### Halving the Learning Rate
$$
\eta _{t} := \eta_{t-1} / 2
$$

### Inverse Decay
$$
\eta_{t} := \frac{\eta_{0}}{1+ k \cdot t}
$$

![[Pasted image 20251022115727.png]]

---
## Relationship between LR and Batch Size
![[Pasted image 20251022115953.png]]



---
# References


