---
created: 2026-07-09
type: note
status: draft
topic: ML
tags:
  - dl/paradigm/supervised
---

# Supervised Learning

Supervised learning is a machine learning paradigm where a model learns to map input features to output targets based on a dataset of labeled training examples. 

Mathematically, a training dataset is represented as:
$$
\mathscr{D} = \{ \langle \vec{x}^{[i]}, y^{[i]} \rangle, i=1,\ldots,n\}
$$
where each $\vec{x}^{[i]}$ is a feature vector representing the inputs for the $i$-th instance, and $y^{[i]}$ is its corresponding ground-truth label.

The goal is to approximate an unknown function $f(\vec{x}) = y$ that represents the true underlying natural relationship. We construct a model or hypothesis $h(\vec{x}) = \hat{y}$ that produces a prediction $\hat{y}$ (sometimes denoted as $o$ or $t$).

Depending on the nature of the target space $\mathscr{Y}$, supervised learning is divided into:
- **Classification**: The target space is discrete: $h: \mathbb{R}^m \rightarrow \mathscr{Y}$, where $\mathscr{Y} = \{1, \ldots, k\}$.
- **Regression**: The target space is continuous: $h: \mathbb{R}^m \rightarrow \mathbb{R}$.

*From* → [[Common Math Notation]]
