Created : 2025-08-15 19:06
Tags :
Type :
Lecture : #L05 
Video : [L5.2 Relation Between Perceptron and Linear Regression](https://www.youtube.com/watch?v=4JB1j8eIGzI&list=PLTKMiZHVd_2KJtIXOW0zFhFfBaJJilH51&index=34) 

---
# Relation Between Perceptron and Linear Regression

- Unlike the [[The Perceptron|perceptron]], the activation function is the [[Identity Function|activation function]] where $\sigma(x) = x$
- The output is a real number $\hat{y} \in \mathbb{R}$


# (Least-Squares) LR

Using statistics, the weights of Linear Regression can be calculated using the least-squares method. $$\mathbf{w} = (\mathbf{X}^\top \mathbf{X})^{-1}\mathbf{X}^\top  y$$
* Generally, this is the best method for linear regression
* However, for larger datasets, and non-convex loss functions, an equation like this won't work and a iterative approach would be much better.

---

---
# References


