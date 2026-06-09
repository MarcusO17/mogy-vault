Created : 2025-10-01 11:17
Tags :
Type :
Lecture : #L10
Video : https://www.youtube.com/watch?v=Va4K-wYh_p8

---
# Overfitting and Underfitting

![[Pasted image 20251001130059.png]]

[[Overfitting]] is the issue when the model memorises the details in the training set, which is only specific to the training set but doesn't generalise to the test set.  ^8967bc

The model capacity can represent the number of parameters. We can see that the **Training Error** decreases as we have more parameters/capacity increases. Well that makes good sense, more weights/biases / layers (wider...) are able to capture the dataset's features better to a point it's "moulded" around it.

The **Generalization Error** will increase as the Model is too fixated on the train set features.


![[Pasted image 20251001200656.png]]

[[Bias-Variance Decomposition|Variance and Bias]], Underfitting shows low variance and high bias as we are far away from the real target and those predictions are very consistent with each other. Because the model is too simple, it fails to learn the true underlying patterns in the data, leading to a systematic error (high bias), but it also means the model's output doesn't change much regardless of the specific training data it sees (low variance).


---
# References


