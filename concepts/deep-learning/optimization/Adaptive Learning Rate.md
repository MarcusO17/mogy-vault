Created : 2025-10-22 19:35
Tags :
Type :
Lecture : L12
Video : https://www.youtube.com/watch?v=7RhNXYqDBfU

---
# Adaptive Learning Rate

With adaptive learning rate, we should,
* decrease learning if the gradient changes it's direction
* increase learning if the gradient stays consistent

---
## How can we do that?

1. Define a local gain *(g)* for each weight. $$
\Delta w_{i,j} = \eta \cdot g_{i,j} \cdot \frac{ \partial \mathcal{L} }{ \partial w_{i,j} } 
$$
2. If gradient is consistent : $$g_{i,j}(t) := g_{i,j}(t-1) + \beta$$ else : $$g_{i,j}(t) := g_{i,j}(t-1) \cdot (1 - \beta)$$










---
# References


