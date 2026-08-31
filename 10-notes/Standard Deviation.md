---
created: 2026-07-09
type: note
status: draft
topic: [statistics, linear-algebra]
---

# Standard Deviation

In statistics and linear algebra, the **standard deviation** of a vector measures the typical amount by which its entries deviate from their average value.

---

## Definitions

For an $n$-vector $\mathbf{x}$:

### 1. Vector Average (Mean)
The average value $\mu$ of the entries in $\mathbf{x}$ is computed as:
$$
\mathbf{avg}(\mathbf{x}) = \mu = \frac{\mathbf{1}^\top \mathbf{x}}{n} = \frac{1}{n} \sum_{i=1}^n x_i
$$

### 2. De-meaned Vector
The **de-meaned** vector $\tilde{\mathbf{x}}$ is obtained by subtracting the average value from each entry:
$$
\tilde{\mathbf{x}} = \mathbf{x} - \mathbf{avg}(\mathbf{x})\mathbf{1}
$$
By construction, the average of a de-meaned vector is always zero: $\mathbf{avg}(\tilde{\mathbf{x}}) = 0$.

### 3. Standard Deviation
The standard deviation $\sigma$ is defined as the root-mean-square ([[Norm#Root-Mean-Square (RMS) Value|RMS]]) value of the de-meaned vector $\tilde{\mathbf{x}}$:
$$
\mathbf{std}(\mathbf{x}) = \sigma = \mathbf{rms}(\tilde{\mathbf{x}}) = \frac{\|\mathbf{x} - \mathbf{avg}(\mathbf{x})\mathbf{1}\|}{\sqrt{n}}
$$

---

## Properties
* **Typical Deviation**: A standard deviation of $\sigma$ means the entries of $\mathbf{x}$ typically lie within the interval $[\mu - \sigma, \mu + \sigma]$.
* **Zero Standard Deviation**: $\mathbf{std}(\mathbf{x}) = 0$ if and only if all entries in $\mathbf{x}$ are equal (i.e., $\mathbf{x} = \alpha \mathbf{1}$ for some scalar $\alpha$).

---

## Mathematical Identity (RMS vs. Std vs. Avg)
For any vector $\mathbf{x}$, its total RMS value can be decomposed into its average and standard deviation:

$$
\mathbf{rms}(\mathbf{x})^2 = \mathbf{avg}(\mathbf{x})^2 + \mathbf{std}(\mathbf{x})^2
$$

### Proof
Using the definitions of standard deviation and de-meaned vector:
$$
\begin{aligned}
\mathbf{std}(\mathbf{x})^2 &= \frac{1}{n} \sum_{i=1}^{n} (x_i - \mu)^2 \\
&= \frac{1}{n} \sum_{i=1}^{n} (x_i^2 - 2\mu x_i + \mu^2) \\
&= \left(\frac{1}{n} \sum_{i=1}^{n} x_i^2\right) - 2\mu \left(\frac{1}{n} \sum_{i=1}^{n} x_i\right) + \left(\frac{1}{n} \sum_{i=1}^{n} \mu^2\right) \\
&= \mathbf{rms}(\mathbf{x})^2 - 2\mu^2 + \mu^2 \\
&= \mathbf{rms}(\mathbf{x})^2 - \mathbf{avg}(\mathbf{x})^2
\end{aligned}
$$
Rearranging terms yields:
$$
\mathbf{rms}(\mathbf{x})^2 = \mathbf{avg}(\mathbf{x})^2 + \mathbf{std}(\mathbf{x})^2
$$

---
*From* → [[Vectors]]
