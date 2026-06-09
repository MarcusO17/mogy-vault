---
created: 2026-06-09
type: note
status: draft
---
---

# Batch Mode

Following...
## **General Learning Principle**

$$Let: \quad D=(\langle\mathbf{x}^{[1]},y^{[1]}\rangle,\langle\mathbf{x}^{[2]},y^{[2]}\rangle,\dots,\langle\mathbf{x}^{[n]},y^{[n]}\rangle) \in (\mathbb{R}^m \times{\{ 0,1 \})^n}$$

1. Initialize $\textbf{w} := \mathbf{0} \in \mathbb{R}^m, \mathbf{b} := 0$
2. For every training epoch:
	1. Initialize $\Delta\mathbf{w} := 0, \, \Delta b := 0$
	2. For every $\langle \mathbf{x}^{[i]},y^{[i]}\rangle \in\ D$
		1. Compute output (predict/forward pass)
		2. Calculate error (backward)
		3. Update $\Delta \mathbf{w}, \, \Delta b$
	3. Update $\mathbf{w},b$ :
	   $\mathbf{w} := \mathbf{w} + \Delta{w}, \, b := +\Delta b$

   TLDR, we update weights and biases after every BATCH which in this case is the WHOLE training set, $l$, instead of every data point.
   
- We collect what's to be updated, some information before we update.
	- We can see the batch mode initialises $\Delta \mathbf{w} := 0$ and $\Delta b := 0$
		- $\Delta \mathbf{w}$ is not Difference! but just a placeholder to store what's to be updated to the weights.
	-  The results from the backprop, are fed into the placeholder weight vector and biases ($\Delta \mathbf{w} := 0$ and $\Delta b := 0$)
- The original $\mathbf{w}, \, b$ are updated **ONLY AFTER EVERY TRAINING EPOCH























---
