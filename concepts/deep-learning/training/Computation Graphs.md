Created : 2025-08-24 10:42
Tags :
Type :
Lecture : L06
Video : https://www.youtube.com/watch?v=j1-r1vO2a_o

---
# Computation Graphs

Computation Graphs are graphs done in PyTorch of calculations.
There are two types of graphs:
- forward(): which constructs the graphs
- backward(): which computes the gradients

It is helpful to think neural networks as computational graphs.

---
Let a activation function be:

![[Pasted image 20250824104401.png]]

[[ReLU Function|ReLU]]/ Rectified Linear Unit

$$\sigma'(z)= \begin{cases}
0  & \text{if } z <0 \\
1  & \text{if } z > 0 \\
DNE  & \text{if }z = 0
\end{cases}$$
But for ML and DL , it is more convenient to say
$$
\sigma'(z)= \begin{cases}
0  &\text{if } z \le 0 \\
z  &  \text{if } z > 0
\end{cases}
$$

An example of a computation graph with ReLU is:

![[Pasted image 20250824105458.png]]


So the backward() of the graph would be something like

![[Pasted image 20250824105755.png]]

We can find out many things using the Chain Rule.
For ex.

$$
\frac{ \partial a }{ \partial b } =  \frac{ \partial v }{ \partial b } \cdot \frac{da}{dv}
$$
OR
$$
\frac{ \partial a }{ \partial w } = \frac{ \partial u }{ \partial w } \cdot \frac{ \partial v }{ \partial a } \cdot \frac{da}{dv}
$$

### Computing the Graph

Let $x = 3$ in the graph ...

$$
\begin{align}
u = wx\, &/ \, u = 6 \\
v = u+b \,  &/ \,  v=7 \\
a = relu(v) \,  &/ \, a = 7 \\
\end{align}
$$
$$
\begin{align}
\frac{ \partial a }{ \partial b } &= \frac{ \partial v }{ \partial b } \cdot \frac{ d a }{ d v }   \\
\frac{ \partial a }{ \partial b } &=\frac{ \partial v }{ \partial b } \cdot 1 \\
\frac{ \partial a }{ \partial b }  &= 1
\end{align}
$$

AND 
$$
\begin{align}
\frac{ \partial a }{ \partial w } &= \frac{ \partial u }{ \partial w } \cdot \frac{ \partial a }{ \partial u } \cdot \frac{da}{dv}  \\
\frac{ \partial a }{ \partial w } &= 3 \times{1}\times {1} \\
\frac{ \partial a }{ \partial w } &= 3
\end{align}
$$


---
# References


