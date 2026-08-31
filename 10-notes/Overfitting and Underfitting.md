---
created: 2026-07-09
type: note
status: draft
topic: ML
tags:
  - dl/theory/generalization
  - dl/training/regularization
---

# Overfitting and Underfitting

**Overfitting** and **Underfitting** are the two main challenges in machine learning that describe how well a model generalizes from its training data to unseen test data.

---

## 1. Underfitting
Underfitting occurs when the model is too simple to capture the underlying patterns in the data.
- **Error**: High training error and high test error.
- **Bias-Variance Perspective**: High bias, low variance. The model has a systematic error (high bias) but is very consistent and insensitive to variations in the training data (low variance).
- **Solution**: Increase model capacity (e.g., add more layers, parameters, or features) or train for more epochs.

---

## 2. Overfitting
Overfitting occurs when the model memorizes the training data's noise and specific details, rather than learning the general underlying relationship.
- **Error**: Low training error but high test (generalization) error.
- **Bias-Variance Perspective**: Low bias, high variance. The model fits the training set extremely well (low bias) but is highly sensitive to the specific training sample it saw, causing predictions to vary wildly on new data (high variance).
- **Visualizing Capacity**: As model capacity (number of parameters/layers) increases, training error decreases, but generalization error eventually begins to rise as the model "molds" too tightly around the training data.

![[Pasted image 20251001130059.png]]

---

## Mitigating Overfitting

### 1. Collecting More Data
Often the most effective way to reduce overfitting. Evaluating model performance across different dataset sizes (using **Learning Curves**) can reveal if more data will continue to help.

![[Pasted image 20251011154258.png]]

### 2. Data Augmentation
Creating new training examples by applying random, label-preserving transformations to existing data (e.g., rotations, cropping, flipping, or PCA color alterations).

![[Pasted image 20251011154508.png]]

### 3. Regularization
Applying techniques to constrain model capacity or training, such as:
* [[L1 L2 Regularization]] (Weight Decay)
* [[Dropout]]
* [[Early Stopping]]

---
*From* → [[Improving Generalization]]
