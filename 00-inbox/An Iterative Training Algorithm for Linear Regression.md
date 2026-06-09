---
title: An Iterative Training Algorithm for Linear Regression
course: rasbt-Introduction to Deep Learning
lecture: L5.3
date:
tags:
  - "#L05"
---

# An Iterative Training Algorithm for Linear Regression

To naively train a linear regression model, We could start by initializing the parameters to 0 or (any random small value) then.
- Every $k$ rounds/ epoch:
	- Analyze what effect a change of parameter has on the loss of the model
	- Change the weight/bias (parameters) a little bit in the direction which improves the performance (minimizes loss)
	- Repeat this small step until the loss does not further decrease.

This is rather similar to the [[The Perceptron#Perceptron Learning Algorithm|perceptron learning algorithm]], we utilize [[Stochastic Gradient Descent]]

### Stochastic Gradient Descent

1. Initialize $\mathbf{w} := \mathbf{0} \in \mathbb{R}^m, \, \mathbf{b} := 0$
2. For every training epoch: 
	1. For every $\langle \mathbf{x}^{[i]},y^{[i]}\rangle \in D$
		1. $\hat{y}^{[i]} := \sigma(\mathbf{x}^{[i]T}\mathbf{w}+b)$
		2. $\nabla_\mathbf{w}\mathcal{L} = ( y^{[i]} - \hat{y}^{[i]})\mathbf{x}^{[i]}$
		   $\nabla_b \mathcal{L} = y^{[i]} - \hat{y}^{[i]}$
		3. $\mathbf{w} := \mathbf{w} + \eta \times{(-\nabla_{\mathbf{w}}\mathcal{L})}$
		   $b := b + \eta \times{(-\nabla_b\mathcal{L})}$

 * $\nabla_\mathbf{w}\mathcal{L}$ means the gradient of the loss with respect to the weight … then for bias etc.
 * $\eta$ means the learning rate.
 * So at first glance, we can see the weights and bias are assigned 0 and it appears to be a Online mode method.
 * For each training example
	 * We run a forward pass, alike the perceptron. 
		 * The $\sigma$ / activation function is an identity function in the case of Linear Regression
	* The gradients of the loss respect to the weights and bias are then calculated 
	* The weight vector and bias are updated by using the learning rate as a "nudge factor" which is multiplied by the negative gradient.
	
##### Non-Vectorized Stochastic Gradient Descent

To help with visualization and reference later on. This is the non-vectorized version.

1. Initialize $\mathbf{w} := \mathbf{0} \in \mathbb{R}^m, \, \mathbf{b} := 0$
2. For every training epoch:
	1. For every $\langle \mathbf{x}^{[i]},y^{[i]}\rangle \in D$
		1. $\hat{y}^{[i]} := \sigma(\mathbf{x}^{[i]T}\mathbf{w}+b)$
	2. For weight $j$ in $\{1,\dots,m\}$
		1. $\frac{\partial\mathcal{L}}{\partial w_j} = (y^{[i]} - \hat{y}^{[i]})x^{[i]}_j$
		2. $w_j := w_j + \eta \times{(-\frac{\partial \mathcal{L}}{\partial w_j})}$
	3. $\quad \frac{\partial \mathcal{L}}{\partial b} = (y^{[i]} - \hat{y}^{[i]})$
	    $\quad b := b + \eta \times{(-\frac{\partial \mathcal{L}}{\partial w_j})}$










## Notes




## Questions


---
## Related
- [[]]

## References
