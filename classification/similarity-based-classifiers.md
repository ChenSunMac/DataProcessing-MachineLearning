# Similarity based Classifiers

### K-Nearest Neighbor Classifier

A simple supervised, non-parametric, classification model 
1. For some test datapoint x define a set of K points in training set nearest to x
2. Count how many members of each class are in the nearest neightbors set
3. Return Empirical fraction for each class as a probability 
4. Optionally take highest probability as class label for x


$$
\begin{equation}
p(x=c|x, D, K) = \frac{1}{K} \sum_{i} \in N_K(x,D)I(y_i=c)
\end{equation}
$$

**Comments on KNN**:
- Non-parametric because the number of neighboring points used depends on the data
- Biased towards Classes with more samples
- Sensitive to noise in the data
- Computationally expensive in large dimensions or large K
  + Could compute distance using only some dimensions
  + Remove redundatn points from training set (clustering points)
  + For low dimensions could use search trees to organize training points into independent subsets
  
