---
created: 2026-07-09
type: note
status: draft
topic: ML
---

# Loss Functions

A **Loss Function** (or cost/objective function) is a mathematical function that quantifies the difference between a model's predictions and the true target values. During training, optimization algorithms (such as gradient descent) adjust the model's parameters to **minimize** this loss.

---

## Loss vs. Cost Function
* **Loss Function ($\mathcal{L}$)**: Evaluates the error on a single training instance (e.g., $\mathcal{L}(y^{[i]}, \hat{y}^{[i]})$).
* **Cost Function ($J$)**: Evaluates the average error across the entire training dataset (e.g., $J(\mathbf{w}, b) = \frac{1}{n} \sum_{i=1}^n \mathcal{L}(y^{[i]}, \hat{y}^{[i]})$).

---

## Common Loss Functions

### 1. Regression Loss Functions
* **Mean Squared Error (MSE)**: Penalizes larger errors quadratically, making it sensitive to outliers. Used in [[Linear Regression]].
  $$
  \text{MSE} = \frac{1}{n} \sum_{i=1}^{n} (y^{[i]} - \hat{y}^{[i]})^2
  $$
* **Mean Absolute Error (MAE)**: Penalizes errors linearly, making it more robust to outliers.
  $$
  \text{MAE} = \frac{1}{n} \sum_{i=1}^{n} |y^{[i]} - \hat{y}^{[i]}|
  $$

### 2. Classification Loss Functions
* **Binary Cross-Entropy (BCE)**: Used for binary classification tasks. Measures the divergence between predicted probabilities and binary labels. Used in [[Logistic Regression]].
  $$
  \text{BCE} = -\frac{1}{n} \sum_{i=1}^{n} \left[ y^{[i]} \log(\hat{y}^{[i]}) + (1 - y^{[i]}) \log(1 - \hat{y}^{[i]}) \right]
  $$
* **Categorical Cross-Entropy (CCE)**: Used for multi-class classification tasks with one-hot encoded targets. Used in conjunction with [[Softmax]] activations.
  $$
  \text{CCE} = -\frac{1}{n} \sum_{i=1}^{n} \sum_{j=1}^{K} y_j^{[i]} \log(a_j^{[i]})
  $$

---
*From* → [[Supervised Learning]]
