Created : 2025-03-27 10:27
Tags : #LinearAlgebra #LinearAlgebra/Vectors 
Type : 
Lecture : #L04
Video : https://www.youtube.com/watch?v=3mjJxu3B0zA

---
# Standard Deviation

- for $n$-vector $x, \mathbf{avg}(x) = \mathbf{1}^T x/n$
	- Sum of all entries of x / n
- *de-meaned* vector is $\tilde{x} = x - \mathbf{avg}(x)\mathbf{1}$
	- If we take the mean of the vector and subtract all entries with it, we get the *de-meaned* vector.
	- That would mean $\mathbf{avg}(\tilde{x}) = 0$, as the de-meaned vector has average subtracted.
- *standard deviation* of $x$ is
	- Literally the $\mathbf{rms}(\tilde{x})$
	- $$\mathbf{std}(x) = \mathbf{rms}(x) = \frac{||x-(\mathbf{1}^Tx/n)\mathbf{1}||}{\sqrt{n}}$$
* $\mathbf{std}(x)$ represents the typical amount that $x_i$ varies from it's $\mathbf{avg}(x)$
	* For e.g. if $\mathbf{std}(x)$ = 3, and $\mathbf{avg}(x)$ is 4. We would expect the entries to **USUALLY** fall between 1 and 7, but can go beyond this range.
* When $\mathbf{std}(x) = 0$ only if $x = \alpha\mathbf{1}$ for some $\alpha$
	* All the entries are the same.
* Usually $\mu$ is used for mean while $\sigma$ is used for std. dev


# Exercise
1. Try to proof that: $$rms(x)^2 = avg(x)^2 + std(x)^2$$
2. 









---
# References


