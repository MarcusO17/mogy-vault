---
created: 2026-07-09
type: note
status: draft
topic: ML
tags:
  - rnn
  - nlp
---

# Sequence Modelling

**Sequence Modelling** refers to the task of predicting or generating sequences of data, where the relative order and position of data points (such as words in a sentence, audio frames in speech, or stock prices over time) convey critical meaning.

---

## Types of Sequence Modelling Tasks

Sequence tasks are classified based on the relationship between the input sequence length $T_x$ and output sequence length $T_y$:

### 1. Many-to-One
The input is a sequence, but the output is a single, fixed-size vector.
- **Example**: Sentiment Analysis (inputting a sentence of words and outputting a single sentiment score or class).
- ![[Pasted image 20251202150504.png]]

### 2. One-to-Many
The input is a single static vector, but the output is a sequence.
- **Example**: Image Captioning (inputting a single image vector and outputting a sequence of words describing the image).
- ![[Pasted image 20251202150548.png]]

### 3. Many-to-Many
Both the inputs and outputs are sequences. This can be:
- **Synchronous (Direct)**: The output at each step corresponds to the input at that step (e.g., Video Captioning or POS tagging).
- **Asynchronous (Delayed/Seq2Seq)**: The input sequence is processed fully before the output sequence is generated (e.g., Machine Translation).
- ![[Pasted image 20251202150959.png]]

---
*From* → [[Supervised Learning]]
