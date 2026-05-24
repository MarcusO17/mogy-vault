Created : 2025-10-22 15:37
Tags :
Type :
Lecture : L12
Video : https://www.youtube.com/watch?v=7RhNXYqDBfU

---
# Momentum
In deep learning, momentum learning, is where the convergence is accelerated by dampening oscillations using "velocity".

Unlike regular [[Gradient Descent]], where we move the opposite direction of the gradient. In momentum learning, gradient descent is done by also moving in the 'averaged' direction of the last few updates.

![[Pasted image 20251022153837.png]]



This helps with dampening oscillations, but also helps with escaping local minima traps.

---
### What's Momentum?
$$
\Delta w_{i,j}(t) := \alpha \cdot \Delta w_{i,j}(t - 1) + \eta \cdot \frac{\partial \mathcal{L}}{\partial w_{i,j}}(t)
$$
* $\Delta w_{i,j}(t)$ is often referred to as "$v$", velocity.
*  $\alpha$ is a momentum rate, this is usually 0.9 to 0.999. It's  almost like a "friction" or       "dampening" parameter 
* $\Delta w_{i,j}(t - 1)$ is the velocity from the previous generation. 
* $\eta \cdot \frac{\partial \mathcal{L}}{\partial w_{i,j}}(t)$ which is the regular partial derivative/gradient multiplied by learning rate at current time step $t$.
---

![[Pasted image 20251022155536.png]]



![[Pasted image 20251022155626.png]]


---
# References

https://distill.pub/2017/momentum
