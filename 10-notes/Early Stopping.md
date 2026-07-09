---
created: 2026-07-09
type: note
status: draft
topic: ML
---

# Early Stopping

**Early Stopping** is a regularization technique that stops the training process of a model before the specified number of epochs is reached, specifically when the model's performance on a validation set begins to degrade.

---

## Mechanism
To implement early stopping, the dataset is split into training, validation, and test sets:
1. **Training Pass**: The model is optimized using the training set.
2. **Validation Monitoring**: After each epoch, the loss (or accuracy) is evaluated on the validation set.
3. **Termination Condition**: While the training loss continues to decrease, the validation loss will typically decrease to a minimum and then begin to rise (indicating that the model is starting to overfit). Training is stopped at this inflection point (the point of lowest validation loss).

![[Pasted image 20251011155752.png]]

---

## Modern Status
While early stopping is a simple and intuitive way to prevent overfitting, it is less commonly used as the primary regularization method in modern deep learning. This is because:
* Modern architectures use more effective regularization techniques (such as [[Dropout]], batch normalization, and weight decay).
* Larger datasets and advanced optimizers reduce the tendency to overfit early in the training process.
* It requires saving model checkpoints throughout training to restore the weights of the best performing epoch.

---
*From* → [[Regularization]]
