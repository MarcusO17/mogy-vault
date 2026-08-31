---
created: 2026-07-09
type: note
status: draft
topic: linear-algebra
---

# Norm

In linear algebra, a **norm** is a function that measures the "size" or length of a vector. 

---

## Euclidean Norm
The most common norm is the **Euclidean norm** ($L_2$ norm) of an $n$-vector $\mathbf{x}$, denoted as $\|\mathbf{x}\|$:

$$
\|\mathbf{x}\| = \sqrt{x_1^2 + x_2^2 + \dots + x_n^2} = \sqrt{\mathbf{x}^\top \mathbf{x}}
$$

### Mathematical Properties
For any vectors $\mathbf{x}$ and $\mathbf{y}$, and any scalar $\beta$:
1. **Non-negativity**: $\|\mathbf{x}\| \ge 0$
2. **Definiteness**: $\|\mathbf{x}\| = 0$ if and only if $\mathbf{x} = \mathbf{0}$
3. **Homogeneity**: $\|\beta \mathbf{x}\| = |\beta| \|\mathbf{x}\|$ (scaling a vector scales its norm proportionally)
4. **Triangle Inequality**: $\|\mathbf{x} + \mathbf{y}\| \le \|\mathbf{x}\| + \|\mathbf{y}\|$

---

## Root-Mean-Square (RMS) Value
The **mean-square** value of an $n$-vector $\mathbf{x}$ is the average of its squared entries:
$$
\text{mean-square}(\mathbf{x}) = \frac{\sum_{i=1}^n x_i^2}{n} = \frac{\|\mathbf{x}\|^2}{n}
$$

The **Root-Mean-Square (RMS)** value is the square root of the mean-square value:
$$
\mathbf{rms}(\mathbf{x}) = \sqrt{\frac{x_1^2 + \dots + x_n^2}{n}} = \frac{\|\mathbf{x}\|}{\sqrt{n}}
$$
- The RMS value represents the "typical" absolute value of the vector's entries (e.g., $\mathbf{rms}(\mathbf{1}) = 1$, independent of the vector's length $n$).
- It is useful for comparing the magnitude of vectors of different lengths.

---

## Norm of Block Vectors
For a concatenated or **block vector** formed by stacking sub-vectors $\mathbf{a}$, $\mathbf{b}$, and $\mathbf{c}$:

$$
\left\|\begin{bmatrix} \mathbf{a} \\ \mathbf{b} \\ \mathbf{c} \end{bmatrix}\right\| = \sqrt{\|\mathbf{a}\|^2 + \|\mathbf{b}\|^2 + \|\mathbf{c}\|^2}
$$

---
*From* → [[Vectors]]
