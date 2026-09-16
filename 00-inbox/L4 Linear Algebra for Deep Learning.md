---
created: 2026-09-16
type: note
status: draft
---
---

# L4 Linear Algebra for Deep Learning

 
## Tensor
A Tensor is a generalization of the concepts of scalar's, vector's and matrices
### Scalar
aka rank-0 tensor, 
 $x \in \mathbb{R}$ , (X is a real number, $x=1.23$)

### Vector
a rank-1 tensor, like a container of real values
* $\mathbf{x} \in \mathbb{R}^{n \times 1}$
* The $\times 1$ on the dim of the vector kinda makes in upright, we can imagine it like a matrices with 1 column, this is to ease the many different deep learning computations
* With that, we then will represent $$\mathbf{x}^T = \begin{bmatrix}
x_1 \quad x_2 \quad \dots  \quad x_n
\end{bmatrix}, \text{where } \mathbf{x}^T \in \mathbb{R}^{1 \times n}$$
### Matrix 
a rank-2 tensor
$$\mathbf{X} \in \mathbb{R}^{m \times n}$$
e.g.,

$$
\mathbf{X} = \begin{bmatrix}
x_{1,1}  &  x_{1,2}  & \dots  & x_{1,n} \\
x_{2,1} & x_{2,2}  &  \dots  & x_{2,n}  \\
\vdots  & \vdots & \ddots & \vdots \\
x_{m,1}  &  x{m,2}  & \dots  &  x_{m,n}
\end{bmatrix}
$$

We will often use ${}\mathbf{X}{}$ as a special convention to refer to the **design matrix**. Which is the matrix which contains all the training examples and the features (input).

The dims of the design matrix will assume the structure ${}\mathbf{X} \in \mathbb{R}^{n \times m}{}$

because ${}n{}$ is often used to refer to the number of examples in a dataset, like number of rows. (Ironic as in the matrix it's a column)

$$
\mathbf{X} = \begin{bmatrix}
x_{1}  &  x_{1,2}  & \dots  & x_{1,n} \\
x_{2,1} & x_{2,2}  &  \dots  & x_{2,n}  \\
\vdots  & \vdots & \ddots & \vdots \\
x_{m,1}  &  x{m,2}  & \dots  &  x_{m,n}
\end{bmatrix}
$$




















---
