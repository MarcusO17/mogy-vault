Created : 2025-10-22 19:43
Tags :
Type :
Lecture : #L12
Video : https://www.youtube.com/watch?v=7RhNXYqDBfU

---
# RMSProp

RMSProp is a unpublished algorithm by Geoff Hinton based on Rprop. It's a type of [[Adaptive Learning Rate]]. RMSProp is very similar to another concept called AdaDelta.

---
## How does RMSProp work?

The primary concept is to divide the learning rate by an exponentially decrease moving average of the squared gradients.
$$ MeanSquare(w_{i,j}, t) := \beta \cdot MeanSquare(w_{i,j}, t-1) + (1-\beta) \left( \frac{\partial \mathcal{L}}{\partial w_{i,j}(t)} \right)^2 $$ 

 * The $MeanSquare(w_{i,j}, t)$ is essentially the moving average of the squared gradient for each weight 

$$ w_{i,j}(t) := w_{i,j}(t) - \eta \cdot \frac{\partial \mathcal{L}}{\partial w_{i,j}(t)} \bigg/ \left( \sqrt{MeanSquare(w_{i,j}, t)} + \epsilon \right) $$








---
# References


