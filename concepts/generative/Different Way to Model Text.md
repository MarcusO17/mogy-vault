Created : 2025-11-28 11:54
Tags :
Type :
Lecture : L15
Video : https://www.youtube.com/watch?v=q5YxK17tRm0

---
# Different Way to Model Text

## Bag-Of-Words

A classic approach for Text Classification where there the text is converted to a tabular dataset. 

It's a naïve method as we lose relationship between the words.


## Convolutional Networks

1D CNNs can model text because language is sequential, and convolutions can learn local n-gram-like patterns by sliding over the sequence.

![[Pasted image 20251128115921.png]]


## [[Transformers]]

The modern way to work with text data right now is **Transformers**. Recurrent Neural Networks were already pretty useful and powerful, and people later added an **attention mechanism** on top of them to help the model focus on relevant parts of the sequence. But in 2017, researchers discovered that the **attention mechanism alone works even better without the RNN**, and so they removed recurrence entirely — resulting in the Transformer architecture.

Usually, when people use Transformers, they train them on **billions of sentences**. With such a large dataset, it becomes very beneficial to use **self-supervised learning**, which pairs naturally with the Transformer design.

For example, in **BERT**, there are **two main self-supervised pretraining tasks**:

### **1. Masked Language Modeling (MLM)**

Randomly mask out some tokens in the input (15%) and ask the model to predict the missing words from the surrounding context.

- Example: “The cat sat on the ___.” → predict “mat”  
    This forces the model to learn deep bidirectional understanding of language.
    

### **2. Next Sentence Prediction (NSP)**

Given two sentences, the model predicts whether the second sentence actually follows the first one in the original text.

- Example:
    
    - A: “John went to the store.”
        
    - B: “He bought some milk.” → **IsNext**  
        This helps BERT learn relationships between sentences, useful for tasks like NLI and QA.





---
# References



