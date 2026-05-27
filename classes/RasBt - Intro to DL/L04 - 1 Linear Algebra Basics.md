# Basic Math Notation of Key Data Structures

## Scalars
- aka rank-0 tensor
- $x \in \mathbb{R}$
- for e.g, $x = 1.23$

>[!info]-
> ps. $\mathbb{R}$ represents the set of all REAL numbers

## Vector
- aka rank-1 tensor
- $x \in \mathbb{R}^n$
- For this course we shall be assuming that, 
	- $x \in \mathbb{R}^{n \times 1}$
- $$x = \begin{bmatrix} x_{1} \\ x_{2} \\ x_{3} \\ \vdots \\ x_{n} \end{bmatrix}$$
- and that would make $x^T = \begin{bmatrix} x_{1} & x_{2} & x_{3} \dots & x_{n} \end{bmatrix}$, where $x^T \in \mathbb{R}^{1\times n}$

## Matrix
-  rank-2 tensor
- $X \in \mathbb{R}^{m \times n}$
- 
  $$
  	\mathbf{X} = \begin{bmatrix} x_{1,1} & x_{1,2} & \cdots & x_{1,n} \\ x_{2,1} & x_{2,2} & \cdots & x_{2,n} \\ \vdots & \vdots & \ddots & \vdots \\ x_{m,1} & x_{m,2} & \cdots & x_{m,n} \end{bmatrix}
  $$
- We will be using $\mathbf{X}$ as a convention to denote the *DESIGN MATRIX* which is the matrix containing the training examples and inputs (features)