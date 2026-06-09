 Created : 2025-08-10 17:09
Tags :
Type :
Lecture : #L01
Video : https://www.youtube.com/watch?v=1nqCZqDYPp0

---
# Deep Learning

Representation learning is a set of methods that allows a machine to be fed with raw data and to automatically discover the representations needed for detection or classication. Deep learning methods are representation-learning methods with multiple levels of representation \[...\]

-- LeCun, Y., Bengio, Y., & Hinton, G. (2015). Deep learning. Nature, 521(7553), 436.

---
### Convolution Neural Networks

-   1990s, These were MLP's with locality.
    -   Able to capture feature dependency
    -   And speeds up training
        -   Achieved by weight sharing and pooling.

-   LeNet, 1989 :
    ![](images/paste-12.png)

    -   Consisted of a Convolutional part and MLP part.
        -   The convolutional layers does the feature learning
        -   This is followed by a Fully-Connected MLP which does the classifying.

### Recurrent Neural Networks

Since MLP's are feed-forward, RNN's have a recurrence property, which is backpropagation through time, making it great for sequential data.

![[Pasted image 20250810171050.png]]

- This causes new issues such as vanishing and exploding gradients.
- Solved with LSTM's (Long Short Term Memory).





---
# References


