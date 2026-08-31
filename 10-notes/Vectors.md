---
created: 2026-07-09
type: note
status: draft
topic: linear-algebra
---

# Vectors

In linear algebra and machine learning, a **vector** is an ordered list of numbers, typically represented as a column vector:

$$
\mathbf{x} = \begin{bmatrix} x_1 \\ x_2 \\ \vdots \\ x_n \end{bmatrix} \in \mathbb{R}^n
$$

---

## Special Vectors
* **Zero Vector ($\mathbf{0}$)**: A vector where all entries are zero.
* **Ones Vector ($\mathbf{1}$)**: A vector where all entries are one.
* **Unit Vector ($\mathbf{e}_i$)**: A vector where the $i$-th entry is one, and all other entries are zero.
* **Sparse Vector**: A vector where most entries are zero. The function $\mathbf{nnz}(\mathbf{x})$ returns the number of non-zero entries in $\mathbf{x}$.

---

## Vector Operations

### 1. Addition & Subtraction
Vectors of the same dimension can be added or subtracted element-wise:
$$
\mathbf{x} + \mathbf{y} = \begin{bmatrix} x_1 + y_1 \\ \vdots \\ x_n + y_n \end{bmatrix}
$$
* **Properties**: Commutative ($\mathbf{x} + \mathbf{y} = \mathbf{y} + \mathbf{x}$) and Associative ($(\mathbf{x} + \mathbf{y}) + \mathbf{z} = \mathbf{x} + (\mathbf{y} + \mathbf{z})$).

### 2. Scalar-Vector Multiplication
Multiplying a vector by a scalar scales each element:
$$
\beta \mathbf{x} = \begin{bmatrix} \beta x_1 \\ \vdots \\ \beta x_n \end{bmatrix}
$$
* **Properties**: Left distributive ($(\beta + \gamma)\mathbf{x} = \beta \mathbf{x} + \gamma \mathbf{x}$) and Right distributive ($\beta(\mathbf{x} + \mathbf{y}) = \beta \mathbf{x} + \beta \mathbf{y}$).

---

## Dot Product (Inner Product)
The dot product of two $n$-vectors $\mathbf{a}$ and $\mathbf{b}$ is a scalar computed by summing the products of their corresponding entries:

$$
\mathbf{a}^\top \mathbf{b} = \sum_{i=1}^{n} a_i b_i = a_1 b_1 + a_2 b_2 + \dots + a_n b_n
$$

### Properties
1. **Symmetric**: $\mathbf{a}^\top \mathbf{b} = \mathbf{b}^\top \mathbf{a}$
2. **Linearity**: $(\gamma \mathbf{a})^\top \mathbf{b} = \gamma (\mathbf{a}^\top \mathbf{b})$
3. **Distributive**: $(\mathbf{a} + \mathbf{b})^\top \mathbf{c} = \mathbf{a}^\top \mathbf{c} + \mathbf{b}^\top \mathbf{c}$

### Special Dot Products
* **Element Extraction**: $\mathbf{e}_i^\top \mathbf{a} = a_i$
* **Summing Elements**: $\mathbf{1}^\top \mathbf{a} = \sum_{i=1}^{n} a_i$
* **Sum of Squares**: $\mathbf{a}^\top \mathbf{a} = \sum_{i=1}^{n} a_i^2 = \|\mathbf{a}\|^2$ (the squared [[Norm|Euclidean norm]])

---

## Stacked (Block) Vectors
Concatenating vectors $\mathbf{b} \in \mathbb{R}^m$, $\mathbf{c} \in \mathbb{R}^n$, and $\mathbf{d} \in \mathbb{R}^p$ results in a block vector $\mathbf{a}$ of size $m+n+p$:
$$
\mathbf{a} = \begin{bmatrix} \mathbf{b} \\ \mathbf{c} \\ \mathbf{d} \end{bmatrix}
$$

---

## FLOP Complexity
The computational complexity of vector operations is measured in Floating-Point Operations (FLOPs):
* **Addition ($\mathbf{x} + \mathbf{y}$)**: Requires $n$ additions ($n$ FLOPs).
* **Dot Product ($\mathbf{x}^\top \mathbf{y}$)**: Requires $n$ multiplications and $n-1$ additions ($2n-1$ FLOPs). (Complexity is lower if either vector is sparse).

---
*From* → [[Notational Conventions in Deep Learning]]
