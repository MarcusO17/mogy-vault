Created : 2025-08-15 13:43
Tags :
Type :
Lecture : #L05 
Video : 

---
# Training a Neural Net

### **General Learning Principle**

$$Let: \quad D=(\langle\mathbf{x}^{[1]},y^{[1]}\rangle,\langle\mathbf{x}^{[2]},y^{[2]}\rangle,\dots,\langle\mathbf{x}^{[n]},y^{[n]}\rangle) \in (\mathbb{R}^m \times{\{ 0,1 \})^n}$$

### "On-line" mode

1. Initialize $\textbf{w} := \mathbf{0} \in \mathbb{R}^m, \mathbf{b} := 0$
2. For every training epoch:
	1. For every $\langle \mathbf{x}^{[i]},y^{[i]}\rangle \in\ D$
		1. Compute output (predict/forward pass)
		2. Calculate error (backward)
		3. Update $\vec{w},b$

Usually the dataset is shuffled prior to each epoch to prevent cycles. This is part of [[Stochastic Gradient Descent|SGD]] best practices.

> [!NOTE]- Side Note
> 1. := means "assigned", So both weight and biases are assigned zero vector and zero.

So we can see that it's rather similar to the ![[The Perceptron#Perceptron Learning Algorithm]] 
Making the [[The Perceptron|Perceptron]] learning an "On-line" mode method!! But it is important to know that other neural nets are also On-Line.

### Batch Mode

1. Initialize $\textbf{w} := \mathbf{0} \in \mathbb{R}^m, \mathbf{b} := 0$
2. For every training epoch:
	1. Initialize $\Delta\mathbf{w} := 0, \, \Delta b := 0$
	2. For every $\langle \mathbf{x}^{[i]},y^{[i]}\rangle \in\ D$
		1. Compute output (predict/forward pass)
		2. Calculate error (backward)
		3. Update $\Delta \mathbf{w}, \, \Delta b$
	3. Update $\mathbf{w},b$ :
	   $\mathbf{w} := \mathbf{w} + \Delta{w}, \, b := +\Delta b$

- We collect what's to be updated, some information before we update.
	- We can see the batch mode initialises $\Delta \mathbf{w} := 0$ and $\Delta b := 0$
		- $\Delta \mathbf{w}$ is not Difference! but just a placeholder to store what's to be updated to the weights.
	-  The results from the backprop, are fed into the placeholder weight vector and biases ($\Delta \mathbf{w} := 0$ and $\Delta b := 0$)
- The original $\mathbf{w}, \, b$ are updated **ONLY AFTER EVERY TRAINING EPOCH
---
### Mini-Batch Mode

*This is the most used training mode*

1. Initialize $\textbf{w} := \mathbf{0} \in \mathbb{R}^m, \mathbf{b} := 0$
2. For every training epoch:
	1. For every minibatch of size *k*:
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
- Having fewer updates than "on-line" mode makes the updates less noisy and more robust.
- makes more updates per epoch than "batch" and is thus faster.










---
# References


