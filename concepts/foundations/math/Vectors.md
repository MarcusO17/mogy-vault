Created : 2025-02-24 20:57
Tags : #LinearAlgebra #LinearAlgebra/Vectors
Concepts :
Lecture : L04
Video : https://www.youtube.com/watch?v=3mjJxu3B0zA

---
# Vectors
* A vector is an ordered list of numbers
* Written as :
$$\left[\begin{matrix} 4 \\ 5 \\ 6.93 \\ -1.7\end{matrix}\right]$$
 * Denoted as:
$$
\textbf{a}, \vec{a}
$$
 * $\text{i}$th element of an n-vector $\vec{a}$ is denoted as $\vec{a}_i$
 * i is known as the index
 * for a n-vector,  indexes can run from i =1 to i = n , $i=1...n$

---
#### *Block Vectors*
* Let vectors b, c and d are vectors with sizes m,n,p.
* The **stacked vector** or concatenation of b,c,d is denoted as:
$$
a = \left[\begin{matrix} b \\ c\\ d \end{matrix}\right]
$$
* This is also called as a **block vector**, with (block) entries b,c,d.
* a has a size of $m + n + p$.
$$
a = (b_1,b_2,\dots,b_m,c_1,c_2,\dots,c_n,d_1,d_2,\dots,d_p)
$$
---
#### *Zero, ones and unit Vectors*
* n-vectors with all entries 0 is known as $0_n$ or $0$.
* n-vectors with all entries 1 is known as $1_n$ or $1$.
*  a unit vector has one 1 and the others 0
___
#### Sparsity
* **a vector is sparse if many of its entries are 0**
* $\textbf{nnz}(x)$ is number of entries that are nonzero
	* stands for number of non-zero
___
## Examples
* color : (R,G,B)
* cash flow : $x_i$ is payment in period i to us
* audio : $x_i$ is the acoustic pressure at sample time i,
---
## Vector Addition
* summing vectors can be denoted as, $a + b$
* To get sum, add corresponding elements.
$$
\left[\begin{matrix} 0 \\ 7 \\ 3 \end{matrix}\right] + \left[\begin{matrix} 1 \\ 4 \\ 7 \end{matrix}\right] = \left[\begin{matrix} 1 \\ 11 \\ 10 \end{matrix}\right]
$$
* Same as subtraction.
#### Properties of Vector Additions
* Commutative : $a +b = b + a$
* Associative : $(a+b)+c = a+ (b+c) \iff (a+b+c)$

## **Scalar-Vector** Multiplication
* scalar $\beta$ and n-vector $a$  can be multiplied.
$$
\beta a = (\beta a_1,\dots,\beta a_n)
$$
* Denoted as, $\beta a$
* Example :
$$
(-2)\left[\begin{matrix} 1 \\ 9 \\ 6 \end{matrix}\right] = \left[\begin{matrix}-2 \\ -18 \\ -12\end{matrix}\right]
$$
#### Properties of scalar-vector multiplication
Let $a$ be any n-vector;
$\beta$ and $\gamma$ are any real number.

* Associative :  $(\beta \gamma)a = \beta (\gamma a)$
* Left distributive : $(\beta + \gamma)a = \beta a + \gamma a$
* Right distributive: $\beta(a+b)=\beta a+ \beta b$
___
#### Linear Combinations

* Given vectors $a_1,\dots,a_m$ and scalars $\beta_1,\dots,\beta_m$
$$
\beta_1a_1+\dots+\beta_ma_m
$$
	$\dots\dots \text{is known as a linear combination of vectors}$


* Certain linear combinations have special names assigned to them.
	* In a case, where; $\beta_i \ge 0$ and $\sum\beta_i = 1$
	* This is known as a weighted average...

* A identity: for any $n$-vector b and identity $e$;
$$
b = b_1e_1 + \dots + b_ne_n
$$
	* E.g. 
	$$
	\begin{align}
	\text{Let b} &=\left[\begin{matrix}9 \\ -4\end{matrix}\right] \\ \\
	b &= 9e_1 + -4e_2 \\ \\
	b &= 9\left[\begin{matrix}1 \\ 0\end{matrix}\right] + -4\left[\begin{matrix}0 \\ 1\end{matrix}\right] \\\\
	b &= \left[\begin{matrix}9 \\ 0\end{matrix}\right] + \left[\begin{matrix}0 \\ -4\end{matrix}\right] \\\\
	b &=\left[\begin{matrix}9 \\ -4\end{matrix}\right]
	\end{align}
	$$

---

#### Dot Product
* Let a and b be $n$-vectors ...
$$
a^Tb =a_1b_1+a_2b_2+\dots+a_nb_n
$$
* Also known as the inner product 
* Other notations :
$$
\langle a,b \rangle, \langle a|b\rangle, (a,b), a \cdot b
$$
* Example :
 $$
 \left[\begin{matrix} -1 \\ 2 \\ 2\end{matrix}\right]^T\left[\begin{matrix} 5 \\3 \\ -1\end{matrix}\right] = (-1)(5) + (2)(3) + (2)(-1) = -1
$$

##### Properties of Inner Product
1. $a^Tb = b^Ta$
2. $(\gamma a)^Tb = \gamma(a^Tb)$
3. $(a+b)^Tc = a^Tc + b^Tc$
   
* Things can get pretty complicated when they are combined
$$
(a+b)^T(c+d) = a^Tc + a^Td + b^Tc + b^Td
$$
###### Examples 
* $e^T_ia = a^i$
	* $\text{Let a = (2,1,-5) and e = (0,1,0)}$
	* $e^T_2a = 1$
* $\textbf{1}^Ta = a_1 + \dots + a_n$
	* Sum of all entries as 1 * every element of a and adding them together.
* $a^Ta = a^2_1 + \dots + a^2_n$
	* Sum of squares.
___

* $w$ is a weight vector and $f$ is a feature vector ; $w^Tf$ is score.
* $p$ is a vector of prices and $q$ is a vector of quantities; $p^Tq$ is the total cost.

---
#### Complexity
* Computer's store real numbers in a *floating-point format*
* Mathematical operations on these numbers are then known as *floating-point operation* / **FLOP**
* Complexity of an operation is the 
$$
\text{Total Flops Needed}
$$
##### Examples
* $x+y$ needs $n$ additions ; so $n$ flops.
* $x^Ty$ needs $n$ multiplications, which is $n-1$ additions so; $2n-1$ flops.
* Much less when $x$ or $y$ is *[[#Sparsity |sparse]]*


