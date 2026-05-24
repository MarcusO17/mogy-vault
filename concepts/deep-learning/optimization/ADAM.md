Created : 2025-10-22 19:49
Tags :
Type :
Lecture : L12
Video : https://www.youtube.com/watch?v=7RhNXYqDBfU

---
# ADAM
ADAM or Adaptive Moment Estimation is probably the most widely used optimization algorithm in DL as of today.

It's a combination of [[Momentum]] and [[RMSProp]]

**Momentum-like term:**
$$
m_{t} := \alpha \cdot m_{t-1} + (1-\alpha) \cdot \frac{\partial \mathcal{L}}{\partial w_{i,j}}(t)
$$

**RMSProp term:**
$$
r := \beta \cdot MeanSquare(w_{i,j}, t-1) + (1-\beta) \left( \frac{\partial \mathcal{L}}{\partial w_{i,j}(t)} \right)^2
$$

**ADAM update:**
$$
w_{i,j} := w_{i,j} - \eta \frac{m_{t}}{\sqrt{r} + \epsilon}
$$












---
# References


