---
created: 2026-07-09
type: note
status: draft
topic: ML
---

# Distance

In machine learning and linear algebra, **distance** measures the geometric separation between two vectors. It is a fundamental metric used to assess similarity or dissimilarity between data points.

---

## Euclidean Distance
The **Euclidean distance** between two $n$-dimensional vectors $\mathbf{a}$ and $\mathbf{b}$ is defined as the [[Norm#Euclidean Norm|Euclidean norm]] of their difference:

$$
\textbf{dist}(\mathbf{a}, \mathbf{b}) = \|\mathbf{a} - \mathbf{b}\| = \sqrt{\sum_{i=1}^{n} (a_i - b_i)^2}
$$

A related metric is the **Root-Mean-Square (RMS) deviation**, which is the RMS value of the difference vector: $\mathbf{rms}(\mathbf{a} - \mathbf{b})$.

---

## Applications

### 1. Feature Distance and Nearest Neighbors
If $\mathbf{x}$ and $\mathbf{y}$ are feature vectors representing two entities, then $\|\mathbf{x} - \mathbf{y}\|$ represents their **feature distance**. 
Given a query vector $\mathbf{x}$ and a set of candidate vectors $\{\mathbf{z}_1, \dots, \mathbf{z}_m\}$, the **closest neighbor** $\mathbf{z}_j$ is the vector that minimizes this feature distance:
$$
\|\mathbf{x} - \mathbf{z}_j\| \le \|\mathbf{x} - \mathbf{z}_i\| \quad \forall i=1,\dots,m
$$

### 2. Document Dissimilarity
Vector distance can be used to compare text documents. By representing documents as word count histograms (vectors where each element corresponds to the frequency of a word in a vocabulary), the Euclidean distance between these vectors correlates with semantic dissimilarity.

For example, comparing the word counts of Wikipedia articles:
- Articles with similar topics (e.g., *Veterans Day* and *Memorial Day*) have a small Euclidean distance.
- Articles with unrelated topics (e.g., *Veterans Day* and *Super Bowl*) have a larger Euclidean distance.

Even without understanding grammar or semantics, simple distance metrics on bag-of-words vectors can capture meaningful relationships.

---
*From* → [[Vectors]]
