---
created: 2026-07-09
type: note
status: draft
topic: ML
---

# Bias-Variance Decomposition

The **Bias-Variance Decomposition** is a mathematical framework for analyzing the generalization error of a machine learning model. It decomposes the expected prediction error (such as Mean Squared Error) on unseen data into three distinct components: **Bias**, **Variance**, and **Irreducible Error**.

For a true target function $y = f(x) + \epsilon$ (where $E[\epsilon] = 0$ and $\text{Var}(\epsilon) = \sigma^2$), the expected test error at a point $x$ for a model prediction $\hat{y} = \hat{f}(x; \mathscr{D})$ trained on dataset $\mathscr{D}$ is:

$$
E_{\mathscr{D}}\left[ (y - \hat{f}(x; \mathscr{D}))^2 \right] = \text{Bias}[\hat{f}(x)]^2 + \text{Var}[\hat{f}(x)] + \sigma^2
$$

### 1. Bias Term
Bias measures the difference between the expected prediction of the model and the true underlying relationship:
$$
\text{Bias}[\hat{f}(x)] = E_{\mathscr{D}}[\hat{f}(x; \mathscr{D})] - f(x)
$$
- **High Bias**: The model makes strong, incorrect assumptions about the data structure, leading to **underfitting**.

### 2. Variance Term
Variance measures how much the model's predictions fluctuate when trained on different datasets $\mathscr{D}$:
$$
\text{Var}[\hat{f}(x)] = E_{\mathscr{D}}\left[ ( \hat{f}(x; \mathscr{D}) - E_{\mathscr{D}}[\hat{f}(x; \mathscr{D})] )^2 \right]
$$
- **High Variance**: The model is highly sensitive to the specific noise and fluctuations in the training dataset, leading to **overfitting**.

### 3. Irreducible Error ($\sigma^2$)
This represents the inherent noise in the data generating process itself. It cannot be reduced by any model, regardless of complexity.

---
*From* → [[Overfitting and Underfitting]]
