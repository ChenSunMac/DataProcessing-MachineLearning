# Partitioning Approach

Obtain a single partition of the patterns that optimizes a criterion function

One common criterion is the sum of squared errors between patterns and cluster centroids


It is a tough optimization problem where we have discrete objective function (different clusters), and it is not convex.

One solution is to approximate iterative solutions



### K-Means Clustering Algorithm

Most commonly used clustering algorithm in this type, by following the steps


**Init:** Choose K cluster centers $$[m_1,...,m_k]$$ selecting K patterns randomly

1. Distribute patterns among clusters using similarity measure
2. Compute new cluster centers using the current memberships

Repeat Until **convergence**

Convergence can be:
1. No change in centers
2. Minimum decrease in objective function J
3. Minimum reassignment of patterns to new cluster centers

### Comments on K-means

It is very sensitive to initial step 1, the choice of center, the complexity is $$O(t ,k ,n)$$, where t for the number of iterations, k for the initial assign for number of clusters, n for the number of patterns.

- It may find local optimum and may be stuck in a bad solution
- Does not work on categorical data due to use of mean
- Sensitive to outliers

**PROS:**

- Simple
- Fast for low dimensional data

**CONS:**
- Can’t handle non-globular clusters
- Will not identify outliers, Restricted to data which has notion of center
- May converge to a bad solution and produce empty clusters (only with centroids and no other members)
