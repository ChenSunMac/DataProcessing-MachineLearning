# Nonlinear Methods

Linear projections are not able to preserve complex data strucutes, they will fail to capture the intrinsic low simension manifold that has a nonlinear strucure, for example nonlinear curve such as circle or spiral..

### Multidimensional Scaling (MDS)

Focus on preserving the **pairwise distance** between data points.

The discrepancy or error between the distances in the original and projected data is measured using a stress function based on distances.


The discrepancy or error between the distances in the original and projected data is measured using a **stree function** based on distances.

1. Based on square of the differences in distances

$$

\begin{equation}
J = \sum_{i,j}(\|x_i - x_j\| - \|y_i - y_j\|)^2 
\end{equation}

$$

2. Based on fractional error
\begin{equation}
J = \frac{1}{\sum \|x_i - x_j\|} \sum_{i\neq j} \frac{(\|x_i - x_j\| - \|y_i - y_j\|)^2}{\|x_i - x_j\|}
\end{equation}

where (1) focuses on the errors whether the distance are large or small (2) puts more emphasis on very small relative distances.

The MDS Solution objective is to find the y configuration that minimizes the stress function. Can be solved using iterative methods such as gradient-descent or Newton Method.

**Comment on MDS:**
- Slow due to the computational cost
- The use of Euclidean distances may lead to considering point close while they are far on the manifold (consider a S shape would be worse in the case)
- Doesn't model the geometry of the manifold


### Isomap

Isomap tries to preserve the distances along the manifold by using geodesic distance or approximaiton of it. (by following 3 steps)

1. Construct neighbourhood graph
2. Approximate the **geodesic distance** between for all pairs in graph
3. Apply MDS on pairwise distances

**geodesic distance**: number of edges between two nodes in some shortest path in the graph G. 

**Comment on ISOMAP:**
- Captures the geometric properties of the space in which the data resides
- Proof for its convergence
- **Connot handle new/online data** directly (since need to construct graph)
- Computationally demanding (more than MDS)
- May construct erroneous connections in the neighborhood graph (short circuiting)
- May suffer if there is a gap in the manifold or it may miss some of the samples if the manifold has **disconnected components**


### Locally Linear Embedding (LLE)

Models the manifold as a union of linear patches, local properties constructed by writing dthe data points $$x_i$$ as a linear combination of their K(i) nearest neighbors in the high dimension.

Then the lower dimensional points $$y_i$$ are expressed as the same linear combination of their corresponding neighbors K(i) in the low dimension space.


1. Identify the neightbors K(i) of each points $$x_i$$
2. Compute weights vectors $$w_i$$ that best linearly reconstruct $$x_i$$ from its neighbors minimizing reconstruction errors
$$
\begin{equation}
\min_w \sum_{i=1}^n \|x_i - \sum_{j\in k(i)} w_{ij} x_j \|^2 
\end{equation}
$$
s.t. $$\sum_j w_{ij} = 1$$, This can be solved using least squares method
3. Given w find the low dimensional set $y_i$ which is best reconstructed by these weights
$$
\begin{equation}
\min_y \sum_{i} \|y_i - \sum_{j\in k(i)} w_{ij} y_j \|^2 
\end{equation}
$$


**Comment on ISOMAP:**
- More computationally efficient than global methods like ISOMAP
- May be able to represent wider range of manifolds whose local properties are captured by euclidean geometry
- Doesn't provide a direct form that can be applied to new data (no out of sample extension, since need to construct K neighbors)
- No estimate of dimensionality unlike PCA where we have a ratio of variance
- Handles non-uniform sample densities poorly (due to the selection of neighbor, if non-uniform, K is set constant)
- May miss sample sample points if disconnnected through K neighbors.

