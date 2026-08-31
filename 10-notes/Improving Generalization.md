---
created: 2026-07-09
type: note
status: draft
topic: ML
tags:
  - dl/training/regularization
  - dl/theory/generalization
---

# Improving Generalization

**Generalization** refers to a model's ability to perform accurately on unseen, real-world data. Improving generalization involves reducing overfitting by managing model capacity, training stability, and data representation.

---

## Techniques to Improve Generalization

### 1. Dataset-Centric Methods
* **Data Volume**: Collecting more training examples.
* **Data Augmentation**: Artificially increasing dataset diversity (e.g., image translations, color jittering).
* **Label Smoothing**: Softening target labels to prevent the model from becoming overly confident.
* **Unlabeled Data**: Leveraging semi-supervised or self-supervised learning.
* **Related Data**: Applying transfer learning or meta-learning from related tasks.

### 2. Architecture Design
* **[[Weight Initialization]]**: Ensuring stable signal propagation from the start (e.g., [[Kaiming He Initialization]] or Xavier initialization).
* **Activation Functions**: Choosing suitable activation functions (e.g., [[ReLU Function]] or non-linear activations).
* **Residual Connections**: Stabilizing gradient flow in very deep networks.
* **Knowledge Distillation**: Transferring knowledge from a large teacher model to a smaller student model.

### 3. Normalization Techniques
* **Input Normalization**: Scaling input features to a standard range.
* **[[Normalization|Batch Normalization (and variants)]]**: Standardizing activations within layers during training.
* **Weight Standardization & Gradient Centralization**: Stabilizing the optimization landscape.

### 4. Training & Optimization
* **[[Adaptive Learning Rate|Adaptive Learning Rates]]**: Dynamically scaling updates per parameter (e.g., [[ADAM]] or [[RMSProp]]).
* **Gradient Clipping**: Preventing exploding gradients by capping update sizes.
* **Auxiliary Losses**: Adding intermediate objectives to guide optimization.

### 5. Explicit Regularization
* **[[L1 L2 Regularization]]**: Penalizing large parameter values using weight decay.
* **[[Early Stopping]]**: Terminating training when validation performance begins to degrade.
* **[[Dropout]]**: Randomly deactivating units during training to prevent co-adaptation.

---
*From* → [[Overfitting and Underfitting]]
