---
created: 2026-07-09
type: note
status: draft
topic: ML
tags:
  - classification
---

# One-Hot Encoding

**One-Hot Encoding** is a technique used to represent categorical data as numerical vectors, which can be processed by machine learning models. 

---

## Mechanism
For a categorical variable with $N$ unique categories:
1. We construct a binary vector of length $N$.
2. We assign a $1$ at the index corresponding to the specific category, and $0$ at all other indices.

For example, if the categories are `[Cat, Dog, Bird]`:
* `Cat` $\to [1, 0, 0]$
* `Dog` $\to [0, 1, 0]$
* `Bird` $\to [0, 0, 1]$

![[Pasted image 20250909153908.png]]

---

## Use Case in Deep Learning
In multi-class classification tasks, target labels are typically one-hot encoded. This aligns with the output of a [[Softmax]] layer, which outputs a vector of probabilities of length $N$ summing to 1. This representation enables the calculation of [[Cross Entropy#Categorical Cross-Entropy|Categorical Cross-Entropy]] loss.

---
*From* → [[Cross Entropy]]
