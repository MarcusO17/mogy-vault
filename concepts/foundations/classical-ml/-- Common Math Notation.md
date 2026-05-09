Created : 2025-08-09 14:51
Tags : #Math #Notations #SupervisedLearning #Vectors #Matrices 
Type : Concept

---
Common Math Notation to keep note of.

Vector – $\vec{X}$

Matrix – $\underline{X}$

Scalar – $\text{X}$


-   **Supervised Learning**
    -   Training Set :
        $$
        \mathscr{D} = \{ \langle \vec{x}^{[i]}, y^{[i]} \rangle, i=1,\ldots,n\}
      $$
        -   whereby:
            -   $\vec{x}$ : feature set in the form of a vector
            -   $y$ : corresponding label

    -   Unknown function : $f(x)=y$
        -   The unknown function represents a natural phenomenon where it's associates the feature vectors with a label.

    -   Hypothesis : $h(x)=\hat{y}$
        -   $\hat{y}$ : predicted label
            -   Can be represented as t or o sometimes.
        -   Basically h(x) is the "model"



    -   Classification : $h: \mathbb{R}^m \rightarrow \mathscr{Y}, \mathscr{Y} = \{1, \ldots, k\}$
        -   whereby:
            -   $\mathbb{R}^m$ : features
            -   $\mathscr{Y}$ : target


    -   Regression : $h : \mathbb{R}^m \rightarrow \mathbb{R}$
        -   $\mathbb{R}^m$ : features
        -   $\mathscr{Y}$ : target

  
Feature Vector –
$$
\vec{X} = \begin{bmatrix}\
x_1 \\
x_2 \\
\vdots \\
x_m
\end{bmatrix}
$$
-   Represents a row in a dataset.

---
# References


