---
created: 2026-07-09
type: note
status: draft
topic: ML
tags:
  - nlp
  - rnn
---

# Different Way to Model Text

Text data requires specialized representations to be processed by machine learning models. There are three primary paradigms for modeling text:

---

## 1. Bag-of-Words (BoW)
A classic, tabular approach where text is represented by word counts or frequencies.
- **Limitation**: It is a naive representation because it completely discards word order and grammar, losing the relationships between words.

## 2. 1D Convolutional Neural Networks (CNNs)
Utilizes 1D convolutions over sequence dimensions.
- **Mechanism**: The 1D kernel slides over word embeddings along the temporal dimension to extract local, n-gram-like features.
- **Use Case**: Effective for capturing local text patterns with low computational complexity.

## 3. Transformers
The modern state-of-the-art architecture for natural language processing, replacing recurrence in [[Recurrent Neural Networks|RNNs]] entirely with the **attention mechanism**.

Transformers are typically pre-trained on massive datasets (billions of sentences) using **self-supervised learning**. For example, **BERT** (Bidirectional Encoder Representations from Transformers) is pre-trained using two tasks:
1. **Masked Language Modeling (MLM)**: Randomly masks 15% of input tokens and trains the model to predict them using context from both directions (e.g., *"The cat sat on the [MASK]"* $\to$ *"mat"*).
2. **Next Sentence Prediction (NSP)**: Pairs two sentences and trains the model to predict if the second sentence logically follows the first (useful for natural language inference and question answering).

---
*From* → [[Sequence Modelling]]
