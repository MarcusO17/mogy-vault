---
created: 2026-06-18
type: note
status: draft
topic: ML
tags:
  - dl/theory/optimization
  - dl/training/optimizer
---

# Non-Convex Loss

In Multilayer Perceptrons, Loss is NO LONGER convex. This is why [[Understanding Gradient Descent|gradient-based optimization]]] can find different solutions. In [[00-inbox/Linear Regression]], [[ADALINE]], [[Logistic Regression]], and [[Softmax|Softmax Regression]] , their loss functions are usually convex, but that is no longer the case with MLPs.

![[Pasted image 20250914123843.png]]

PLUS if we start with random weights, we can reach different local minima, hence it's pretty good practice.

*From* →
