---
created: 2026-07-09
type: note
status: draft
topic: ML
tags:
  - regularization
---

# Regularization

**Regularization** refers to a set of techniques used in machine learning to prevent overfitting by constraining or reducing a model's capacity to fit noise in the training data. This helps improve the model's ability to generalize to unseen test data.

In the context of deep learning, regularization is typically achieved by adding a penalty term to the loss function, modifying the training procedure, or constraining the parameter space.

### Common Regularization Methods
* **Weight Penalties**: Adding a penalty to the loss function based on the magnitude of the model parameters (e.g., [[L1 L2 Regularization]]).
* **Noise Injection**: Deactivating random neurons during training to prevent co-adaptation (e.g., [[Dropout]]).
* **Early Termination**: Stopping training when validation performance begins to worsen, preventing the model from over-optimizing on the training set (e.g., [[Early Stopping]]).

---
*From* → [[Improving Generalization]]
