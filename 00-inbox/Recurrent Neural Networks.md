Created : 2025-11-28 20:27
Tags :
Type :
Lecture : #L15
Video : https://www.youtube.com/watch?v=q5YxK17tRm0

---
# Recurrent Neural Networks

To be exact, sequence modelling with RNNs.

So how do we know that we are sequence modelling? One is through the X-axis, and one is through the y-axis. 

When they are on the x-axis, or usually represented by the rows. The data usually needs to remain at it's position, or relative position within a certain window as the location of it relative to the other points convey meaning.

But sequences can also be ordered by the features/ y-axis. MLP's regard features as independent. 

It shows that sequence truly matters (duhh).

![[Pasted image 20251128205445.png]]


---
## Applications of Sequence Modelling

1. Working with Text
2. Working with Speech Recognition
3. Language Translation
4. Stock Market Prediction
5. DNA Modelling.
---
## Backpropagation Through Time

![[Pasted image 20251206155015.png]]


There are 3 weight matrices in a **single-hidden** layer RNN.
$$
\mathbf{W_{h} = [W_{hh};W_{hx}]}
$$
So how do we compute the net-input which has 2 matrices?

For the 2nd iteration, the hidden layer computes this.
Net-Input :
$$
\mathbf{z}_{h}^{\langle t \rangle} = \mathbf{W}_{hh}\mathbf{x}^{\langle t \rangle} + \mathbf{b}_{h}
$$
Activation :
$$
\mathbf{h}^{\langle t \rangle} = \sigma_h \big( \mathbf{z}_h^{\langle t \rangle} \big)
$$


The output of the 2nd iteration is calculated through.
Net Input :
$$
\mathbf{z}_y^{\langle t \rangle} = \mathbf{W}_{yh} \mathbf{h}^{\langle t \rangle} + \mathbf{b}_y
$$
Output :
$$
\mathbf{y}^{\langle t \rangle} = \sigma_y \big( \mathbf{z}_y^{\langle t \rangle} \big)
$$

**What about loss?**
It really depends on the task of sequence modelling that is being performed.



---
# References


