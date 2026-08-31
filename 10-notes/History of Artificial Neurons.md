---
created: 2026-07-09
type: note
status: draft
topic: ML
tags:
  - linear-models
---

# History of Artificial Neurons

The development of artificial neural networks progressed through several key milestones in the mid-20th century, before facing a major setback that led to the first "AI Winter."

---

## Key Milestones

### 1. McCulloch-Pitts Neuron (1943)
Developed by Warren McCulloch and Walter Pitts, this was the first mathematical model of a biological neuron.
- **Mechanism**: Takes binary inputs, sums them, and outputs $1$ if the sum exceeds a threshold, otherwise $0$.
- **Capabilities**: Could represent fundamental logical operations like AND, OR, and NOT.
- **Limitation**: It had no learning mechanism; weights and thresholds had to be manually designed.

### 2. Rosenblatt's Perceptron (1957)
Frank Rosenblatt extended the McCulloch-Pitts model by introducing weights and an automatic learning algorithm.
- **Mechanism**: The [[The Perceptron|Perceptron]] updates its weights iteratively based on classification errors using a step function as its activation function.

### 3. Widrow-Hoff ADALINE (1960)
Bernard Widrow and Ted Hoff developed the **ADALINE** (Adaptive Linear Neuron).
- **Mechanism**: Unlike the Perceptron, [[ADALINE]] updates its weights based on the continuous output of a linear activation function before a threshold is applied, utilizing gradient descent to minimize Mean Squared Error (MSE).

---

## The XOR Problem & First AI Winter (1969)
In 1969, Marvin Minsky and Seymour Papert published their book *Perceptrons*, which mathematically proved that single-layer neural networks (like Perceptrons and ADALINEs) are fundamentally limited to linearly separable functions and **cannot solve the XOR problem**.

This critique, showing that neural networks could not solve relatively simple non-linear boundaries, halted major research funding and interest in the field, triggering the **first AI Winter**.

---
*From* → [[Introduction to Deep Learning]]
