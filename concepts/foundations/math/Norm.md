Created : 2025-03-08 15:04
Tags : #LinearAlgebra #LinearAlgebra/Vectors 
Type : 
Lecture : L04
Video : https://www.youtube.com/watch?v=3mjJxu3B0zA

---
## Norm
* The *Euclidean* norm or norm of an $n$-vector $x$ $$\left\Vert x\right\Vert = \sqrt{x^2_1 + x^2_2 + \dots + x^2_n} = \sqrt{x^Tx}$$
* Used to measure the size of a vector
* reduces to absolute value of $n$ = 1
### Properties
* for any $n$-vectors $x$ and $y$, and any scalar $\beta$
* homogeneity: $||\beta x|| = |\beta| ||x||$
	* If an $n$-vector and scale all of the entries by $\beta$, the norm of the result is the absolute value of $\beta$ multiplied by the norm of $x$
	
* triangle inequality: $||x+y|| \le ||x|| + ||y||$
* nonnegativity : $||x|| \ge 0$
* definiteness : $||x|| = 0 \text{ only if } x = 0$
## RMS Value
* The *mean-square* value of $n$-vector $x$ is $$\frac{x^2_1+\dots+x^2_n}{n} = \frac{||x||^2}{n}$$
* *root-mean-square* value (RMS values) is $$\mathbf{rms}(x) = \sqrt{\frac{x^2_1 + \dots + x^2_n}{n}} = \frac{||x||}{\sqrt{n}}$$
* $\mathbf{rms}(x)$ gives the 'typical' value of $|x_i|$
* e.g., $\mathbf{rms(1)} = 1$ (independent of $n$)
* RMS value useful for comparing sizes of vectors of different lengths.
## Norm of Block Vectors
* Let $a,b,c$ be vectors.
* $||(a,b,c)||^2 = a^T a + b^T b + c^T c = ||a||^2 + ||b||^2 + ||c||^2$
* $||(a,b,c)|| = \sqrt{||a||^2 + ||b||^2 + ||c||^2}=||(||a||,||b||,||c||)||$

