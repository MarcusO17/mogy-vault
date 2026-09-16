---
created: 2026-09-16
type: note
status: draft
---
---

# micrograd

Let's first understand what is a [[derivative]], It is the backbone of all of [[Backpropagation]].

Assume 
$$
	f(x) = 2x^{2} + 3x + 2 
$$Using `matplotlib` we can get a graph that looks like.

![[Pasted image 20260916150832.png|385]]

This is a classic quadratic equation graph. There is always a local minima, which is the "valley" of the graph.

But in this case we are more interested in calculating the slope of the graph. Why?? tbc..

## Measuring the Slope
To measure the slope at a particular point, in this case $x_{0}$. We are able to differentiate a scalar function, in this case $f(x)$ at a certain point ($x_{0}$) as long there is a possible finite limit (meaning as $f'(x_{0} \to 0) \in \mathbb{R}$ ). 

The formula is as follows, 
$$
f'(x_{0}) = \lim_{ h \to 0 } \frac{f(x_{0}+h) - f(x_{0})}{h}
$$


In real mathematics, we will take the limit of $h \to 0$ but in code we shall just take a tiny tiny number, as it will give us a finite (real number) difference approximation.

We can measure the "slopeyness" or the gradient by the given formula. basically
>[!note]
>If i nudge x, how much does y change?



## Measuring the Slope with multiple inputs

We can utilise partial derivatives, basically at all times, we are only allowed to nudge 1 variable hence we target that.

Let's 
$$
f(x_{1},x_{2},\dots, x_{n}
)
$$
We wanna find what if we nudge just $x_i$ , what happens to the rest of the graph? 
>[!question]
>Why don't we nudge all? Partial derivatives only target one. The base intuition is if we were to bake a cake, and we change all the ingredients everytime, we don't fucking know what caused what.

Partial derivatives will come in very useful as we work with ML/DL, $x$ might represent a vector of a training example etc.  And it will become a drilldown process.

The formula to find out a specific variable in affecting the gradient of the slope.

$$
\frac{ \partial f }{ \partial x_{i} }(x_{1},x_{2},\dots,x_{n}) = \lim_{ h \to 0 } \frac{f(x_{1},\dots,x_{i}+h,\dots,x_{n})+f(x_{1},\dots,x_{i},\dots,x_{n})}{h} 
$$

Okay let's put this into picture, let's assume a function $f$,
$$
f(x,y,z) = xy + z
$$
We can find out roughly  how much each variable, $x,y,z$ affects the final output, like in the previously mentioned cake analogy.

1. $x$
   If we take $\frac{ \partial f }{ \partial x }$ the differentiation rules, would then dictate,
   $$
\begin{align}
\frac{df}{dx} &= x^{1-1}y \\
 &= y
\end{align}
   $$
   But if we think about it, If we wanna nudge $x$ , whether $x$ is $5$ or $10$, the only factor that will affect the whole answer is $y$. 

2. $y$
   same as x?
3. $z$
   For z , no matter what we change $z$ to, its directly adding to the final output without any scaling factor, hence the $\frac{df}{dz}=1$


## Understanding *Value*

   Neural Networks, can be viewed as a bunch of perceptrons/ neurons, wired together, to produce an output, in which these neurons often are just mathematical expressions. And they learn through backpropagation, but what is learning, th


















---
