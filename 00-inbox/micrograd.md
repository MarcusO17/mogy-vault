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
We wanna find what if we nudge juts $x_i$  
















---
