Created : 2025-03-05 13:37
Tags : #LinearAlgebra #LinearAlgebra/Vectors
Concepts : 
Lecture : #L04
Video : https://www.youtube.com/watch?v=3mjJxu3B0zA

---
## Linear Functions

* Denoted as $f : \mathbf{R}^n \rightarrow \mathbf{R}$ 
	* means that $f$ is a function.====
	* $\mathbf{R}^n$ takes in an $n$-vector
	* and spits out $\mathbf{R}$, a real number.
* Aka, *scalar-value function*

* This function $f$ satisfies the *superposition property* if,
  $$
	f(\alpha x + \beta y) = \alpha f(x)+ \beta f(y)
	$$
	holds for all numbers $\alpha,\beta$ and all $n$-vectors $x,y$
	
> [!tip]- Superposition Property
>The superposition property states that the result does not change if linear combination is formed before applying the function or after. ^fd277f
* A function which satisfies *superposition* is **linear**

#### Examples
* An example of a linear function is the [[Vectors#Dot Product |inner function]]!
$$
f(x) = a^Tx = a_1x_1 + a_2x_2 + \dots + a_nx_n
$$
* [[#^fd277f | Superposition]] Proof :
$$
\begin{align}
f(\alpha x + \beta y) &= a^T(\alpha x + \beta y)\\
&= a^T(\alpha x) + a^T (\beta y) \\
&=  \alpha(a^Tx) + \beta (a^Ty) \\
&= \alpha f(x)+ \beta f(y)
\end{align} 
$$
___
## Affine Functions
* A function that is linear + a constant is known as a affine function.
* Usually represented by $f(x) =  a^Tx + b$, where a is a $n$-vector and $b$ is a scalar.
* An affine function is also defined by a superposition type equation:
  $$
	f(\alpha x+\beta y) = \alpha f(x)+\beta f(y)
	$$
	holds for all $\alpha, \beta$ with $\alpha + \beta = 1$, and all $n$-vectors $x,y$
---
## Taylor Approximation

* Let $f : \mathbf{R}^n \rightarrow \mathbf{R}$
* The *first-order Taylor Approximation of f, near point z*:$$
\hat{f}(x) = f(z) + \frac{\partial f}{\partial x_1} (z)(x_1-z_1) + \dots + \frac{\partial f}{\partial x_n}(z)(x_n -z_n)
$$
* $\hat{f}$ is an affine function of x
* We can rewrite using the [[Vectors#Dot Product |inner product]] as:$$
	\hat{f}(x) = f(z) + \nabla f(z)^T(x-z)
	$$
	where $n$-vector $\nabla f(z)$ is the gradient of $f$ at $z$,
	$$ \nabla f(z) = \left(\frac{\partial f}{\partial x_1}(z),\dots ,\frac{\partial f}{\partial x_n}(z)\right)$$
---
## Regression model
* Regression model is an affine function. $$ \hat{y} =x^T\beta + v$$


















