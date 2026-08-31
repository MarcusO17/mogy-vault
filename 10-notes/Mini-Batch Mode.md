---
created: 2026-06-09
type: note
status: draft
topic: ML
tags:
  - optimization
---

# Mini-Batch Mode

*This is the most used training mode* in deep learning so far.

1. Initialize $\textbf{w} := \mathbf{0} \in \mathbb{R}^m, \mathbf{b} := 0$
2. For every training epoch:
	1. For every minibatch of size *k* initiated:
		1. Initialize $\Delta\mathbf{w} := 0, \, \Delta b := 0$
		2. For every $\{\langle \mathbf{x}^{[i]},y^{[i]}\rangle,\dots,\langle\mathbf{x}^{[i+k]},y^{[i+k]}\rangle\} \subset D$ aka *minibatch*.
			1. Compute output (predict/forward pass)
			2. Calculate error (backward)
			3. Update $\Delta \mathbf{w}, \, \Delta b$
		3. Update $\mathbf{w},b$ :
		   $\mathbf{w} := \mathbf{w} + \Delta{w}, \, b := +\Delta b$

Basically it's batch mode done on minibatches.

So why is mini-batch used the most?
- Take advantage of vectorization. The subset can be processed with vectorization allowing more training samples to be fed in with efficiency at the same time.
- Having fewer updates than "[[On-line Mode|on-line]]" mode makes the updates less noisy and more robust.
- makes more updates per epoch than "[[Batch Gradient Descent]]" and is thus faster.
























---
