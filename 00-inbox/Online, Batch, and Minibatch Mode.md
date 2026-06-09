Created : 2025-08-15 13:43
Tags :
Type :
Lecture : #L05 
Video : https://www.youtube.com/watch?v=b4DXHd3RwqA&list=PLTKMiZHVd_2KJtIXOW0zFhFfBaJJilH51&index=33

---
# Online, Batch, and Minibatch Mode

---
### Mini-Batch Mode

*This is the most used training mode*

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
- Having fewer updates than "on-line" mode makes the updates less noisy and more robust.
- makes more updates per epoch than "batch" and is thus faster.










---
# References


