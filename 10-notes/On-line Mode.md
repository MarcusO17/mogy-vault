---
created: 2026-06-09
type: note
status: draft
topic: ML
tags:
  - dl/training/optimizer
---

# On-line Mode

## **General Learning Principle**

$$Let: \quad D=(\langle\mathbf{x}^{[1]},y^{[1]}\rangle,\langle\mathbf{x}^{[2]},y^{[2]}\rangle,\dots,\langle\mathbf{x}^{[n]},y^{[n]}\rangle) \in (\mathbb{R}^m \times{\{ 0,1 \})^n}$$

1. Initialize $\textbf{w} := \mathbf{0} \in \mathbb{R}^m, \mathbf{b} := 0$
2. For every training epoch:
	1. For every $\langle \mathbf{x}^{[i]},y^{[i]}\rangle \in\ D$
		1. Compute output (predict/forward pass)
		2. Calculate error (backward)
		3. Update $\vec{w},b$

Online Mode essentially shows that the model weights are update after **each training data point**.

Usually the dataset is shuffled prior to each epoch to prevent cycles. This is part of [[Stochastic Gradient Descent||SGD]] best practices.

> [!NOTE]- Side Note
> 1. := means "assigned", So both weight and biases are assigned zero vector and zero.

So we can see that it's rather similar to the [[The Perceptron#Perceptron Learning Algorithm||Perceptron Learning Algorithm]] Making the Perceptron learning an "On-line" mode method!! But it is important to know that other neural nets are also On-Line.






















---
