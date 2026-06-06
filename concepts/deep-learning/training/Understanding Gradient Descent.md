Created : 2025-08-18 14:05
Tags :
Type :
Lecture : #L05
Video : [L5.6 Understanding Gradient Descent](https://www.youtube.com/watch?v=L4xzybIa-bo&list=PLTKMiZHVd_2KJtIXOW0zFhFfBaJJilH51&index=38)


---
# Understanding Gradient Descent

In terms of [[Linear Regression|Linear Regression]]...

![[Pasted image 20250818143705.png]]

The loss of Linear Regression can be defined as:
$$
\mathcal{L}(\mathbf{w},b) = \sum_{i}(\hat{y}^{[i]}-y^{[i]})^{2}
$$
aka SSE, Sum Squared Error.

![[Pasted image 20250818153843.png]]]

The loss function will look like this with respect to w. (When we move w, how much does the loss change)



![[Pasted image 20250818154059.png]]

![[Pasted image 20250818154037.png]]

---
## Finding the Gradients of LR parameters.
Recap to [[An Iterative Training Algorithm for Linear Regression#Stochastic Gradient Descent|Stochastic Gradient Descent]]

Step 2. requires finding out the gradients of the loss in respect to w and b.
#### Finding $\nabla_{w}\mathcal{L}$

$$
\begin{align}
\frac{ \partial \mathcal{L} }{ \partial w_{j} } &= \frac{ \partial  }{ \partial w_{j} }\sum_{i}(\hat{y}^{[i]}-y^{[i]})^2 \\
 &=   \frac{ \partial  }{ \partial w_{j} }\sum_{i}(\sigma(\mathbf{x}^{[i]T}\mathbf{w})-y^{[i]})^2 \\
 &= \frac{ \partial  }{ \partial w_{j} }\sum_{i}2(\sigma(\mathbf{x}^{[i]T}\mathbf{w})-y^{[i]}) \cdot \frac{ \partial  }{ \partial w_{j} }(\sigma(\mathbf{x}^{[i]T}\mathbf{w})-y^{[i]}) \\
 &= \frac{ \partial  }{ \partial w_{j} }\sum_{i}2(\sigma(\mathbf{x}^{[i]T}\mathbf{w})-y^{[i]}) \cdot  \frac{ \partial  }{ \partial w_{j} }\sigma(\mathbf{x}^{[i]T}\mathbf{w}) \\ \
 \\ 
 & \text{Using Leibniz notation of chain rule }\dots \\
 &\text{Let : } u = (\mathbf{x}^{[i]^T}\mathbf{w})  
 \\ \\

&= \frac{ \partial  }{ \partial w_{j} }\sum_{i}2(\sigma(\mathbf{x}^{[i]T}\mathbf{w})-y^{[i]}) \cdot \frac{ d \sigma }{ d(\mathbf{x}^{[i]^T}\mathbf{w}) } \cdot \frac{ \partial }{ \partial w_{j} } (\mathbf{x}^{[i]^T}\mathbf{w}) \\
 &= \frac{ \partial  }{ \partial w_{j} }\sum_{i}2(\sigma(\mathbf{x}^{[i]T}\mathbf{w})-y^{[i]}) \cdot \frac{ d \sigma }{ d(\mathbf{x}^{[i]^T}\mathbf{w}) }x^{[i]}_{j} \\
&= \frac{ \partial  }{ \partial w_{j} }\sum_{i}2(\sigma(\mathbf{x}^{[i]T}\mathbf{w})-y^{[i]}) x^{[i]}_{j}
\end{align}
$$
---
[[Batch Gradient Descent]] as a Surface Plot

![[Pasted image 20250819104450.png]]

[[Stochastic Gradient Descent]]

![[Pasted image 20250819104506.png]]



---
# References


