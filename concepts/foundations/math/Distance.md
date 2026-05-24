Created : 2025-03-26 14:51
Tags : #LinearAlgebra #LinearAlgebra/Vectors
Type :
Lecture : L04
Video : https://www.youtube.com/watch?v=3mjJxu3B0zA

---
# Distance

* The (*Euclidean*) distance between two vectors $a$ and $b$ is: $$\textbf{dist}(a,b)= ||a-b||$$
* $\mathbf{rms}(a-b)$ is the *RMS deviation* between $a$ and $b$
## Feature Distance

* If $x$ and $y$ are feature vectors for two entities, $||x-y||$ is the feature distance.
* If $z_1,\dots , z_m$ is a list of vectors, $z_j$ is the closest neighbour of $x$ if $$||x - z_j|| \le ||x - z_i||, \ \ \ i=1,\dots , m$$
## Document Dissimilarity

* 5 Wikipedia Articles : 'Veterans Day','Memorial Day','Academy Awards','Golden Globe Awards','Super Bowl'.
* Collected word count histograms from each article, which ended up with a dictionary of 4423 words.
* Pairwise distances shown below

|                     | Veterans Day | Memorial Day | Academy Awards | Golden Globe Awards | Super Bowl |
| ------------------- | ------------ | ------------ | -------------- | ------------------- | ---------- |
| Veterans Day        | 0            | 0.095        | 0.130          | 0.153               | 0.170      |
| Memorial Day        | 0.095        | 0            | 0.122          | 0.147               | 0.164      |
| Academy Awards      | 0.130        | 0.122        | 0              | 0.108               | 0.164      |
| Golden Globe Awards | 0.153        | 0.147        | 0.108          | 0                   | 0.181      |
| Super Bowl          | 0.170        | 0.164        | 0.164          | 0.181               | 0          |


* Veterans and Memorial Day are the most similar! Due to them having the least "distance". Followed by the Golden Globes and Academy Awards.
* This is interesting as the word histograms bring no meaning, has no understand of the English language, whatsoever and yet we can agree that these assumptions are right!









---
# References


