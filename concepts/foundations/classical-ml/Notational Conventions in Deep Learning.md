Created : 2025-08-14 16:54
Tags :
Type :
Lecture : #L4
Video : https://www.youtube.com/watch?v=4pnoymfFiYM&list=PLTKMiZHVd_2KJtIXOW0zFhFfBaJJilH51

---
# Notational Conventions in Deep Learning

- Quick Recap
	The results from a forward pass/Inference in a perceptron is $$\textbf{x}^\top\textbf{w} + b = z$$ where:
		- x is the feature vector
			- x can be $\textbf{x} \in \mathbb{R}^{n\times{1}}$
			- x is transposed ($^\top$) as x is a columnar vector 
				- $\begin{bmatrix}x_1 \\x_2 \\\vdots \\x_m\end{bmatrix} \rightarrow [x_1,x_2,\dots,x_n]$ where $x^\top \in \mathbb{R}^{1\times{n}}$
				- 
		- w is the weight vector $\textbf{w} \in \mathbb{R}^{n\times{1}}$
		- b is the bias (usually $b \in \mathbb{R}$)

Our input matrix is also known as the design matrix. Denoted as $\textbf{X}$.

## Inference

Later on as we perform inference, we would generally have 1 $\vec{x}$ feature vector going through a forward pass through multiple

If we have n training examples,
	$$ \textbf{X}\textbf{w} + b = \textbf{z}$$
	where:
		- $\textbf{X} \in \mathbb{R}^{n\times{m}}$
			- n is usually the number of examples, and m, is the number of features.
		- $\textbf{w}\in\mathbb{R}^{m\times{1}}$
		- b $\in 1$
		- $\textbf{z} \in \mathbb{R}^{n\times{1}}$







---
# References


