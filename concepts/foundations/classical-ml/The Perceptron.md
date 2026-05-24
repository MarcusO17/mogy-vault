Created : 2025-08-10 17:13
Tags :
Type :
Lecture : L03
Video : https://www.youtube.com/watch?v=cm_wv2QpTgc

---
# The Perceptron

![[Pasted image 20250810171854.png]]

## McCulloch & Pitt's Neuron Model
$$

\sum_{i=1}^{m}{x_iw_i} = Z

$$
## Frank Rosenblatt's Perceptron
$$

f_\theta\left(\sum_{i=1}^{m}x_iw_i\right) = \hat{y}

$$
## Single Layer Neural Networks

$$

\sigma\left(\sum_{i=1}^{m}x_iw_i+b\right) = \sigma\left(\vec{x}^T\vec{w}+b\right) = \hat{y}

$$

$$

\sigma(z) = \begin{cases}  0, & z \leq 0 \\ 1, & z > 0    \end{cases}

$$

$$

b = -\theta

$$

  

## Perceptron Learning Algorithm


Let :
$$

\mathscr{D} = \left(\langle\vec{w}^{[1]},y^{[1]}\rangle,\langle\vec{w}^{[2]},y^{[2]}\rangle,\dots,\langle\vec{w}^{[n]},y^{[n]}\rangle\right) \in \left(\mathbb{R}^m \times \{0,1\}\right)^{n}

$$
1.  Initialise $\vec{w}$ := $0^{m}$
2.  For every training epoch:
    I.  For every $\langle\vec{x}^{[i]},y^{[i]}\rangle\in\mathscr{D}$:
        a.  $\hat{y}^{[i]} := \sigma{(\vec{w}^{[i]T}\vec{w})}$ 
        b.  err := $(y^{[i]}-\hat{y}^{[i]})$
        c.  $\vec{w} := \vec{w} +err \times \vec{x}^{[i]}$









---
# References


