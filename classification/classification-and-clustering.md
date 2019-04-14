# Classification & Clustering

Classificaiton is a learning method that uses training samples with known class labels to learn how to assign the samples into their proper classes. This learning can be used to label test sampels with unknown labels.

Classification can be facilitated if the features of samples in the same class share characteristics trhat discriminate them from other classes. It can be seen as the discrete form of prediction.

- Supervised, Domain sensitive
- Easy to evaluate
- Examples: Bayesian, KNN, SVM, Decision trees

Clustering is more descriptive, where given inputs without label, the output is categorical clustering. 
- Unsupervised
- Notion of similarity
- Hard to evaluate
- Examples: K-Means, Fuzzy C-means, Hierarchical


### Classification Definition
Given a dataset $$X= \{x_1, ..., x_n\}$$ where each data point $$x_i \in X$$ contains F features denoted $$x_{i,f}$$ and given a set of classes $$C = \{c_1, ... c_k\}$$

The classification problem is to define a mapping $$\delta(x_i) : X \rightarrow C$$

The classes are preddefined, nonoverlapping and partition the entire set of datapoints



