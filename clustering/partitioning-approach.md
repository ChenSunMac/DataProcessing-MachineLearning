# Partitioning Approach

Obtain a single partition of the patterns that optimizes a criterion function

One common criterion is the sum of squared errors between patterns and cluster centroids

It is a tough optimization problem where we have discrete objective function \(different clusters\), and it is not convex.

One solution is to approximate iterative solutions

## K-Means Clustering Algorithm

Most commonly used clustering algorithm in this type, by following the steps

**Init:** Choose K cluster centers $$[m_1,...,m_k]$$ selecting K patterns randomly

1. Distribute patterns among clusters using similarity measure
2. Compute new cluster centers using the current memberships

Repeat Until **convergence**

Convergence can be: 1. No change in centers 2. Minimum decrease in objective function J 3. Minimum reassignment of patterns to new cluster centers

## Comments on K-means

It is very sensitive to initial step 1, the choice of center, the complexity is $$O(t ,k ,n)$$, where t for the number of iterations, k for the initial assign for number of clusters, n for the number of patterns.

* It may find local optimum and may be stuck in a bad solution
* Does not work on categorical data due to use of mean
* Sensitive to outliers

**PROS:**

* Simple
* Fast for low dimensional data

**CONS:**

* Can’t handle non-globular clusters
* Will not identify outliers, Restricted to data which has notion of center
* May converge to a bad solution and produce empty clusters \(only with centroids and no other members\)

## Partitioning Around Medoids \(PAM\)

In order to avoid the outlier effect caused by taking mean as the cluster center \(may not be a real sample data point\), use medoid \(a real sample point\) as the center.

The idea is based on selecting initially a random K medoid, then examining all the patterns to see which should replace existing medoids to improve the objective function. Keep repeating until convergence. Then group the patterns based on the new medoids

Complexity is high $$O(t, k, (n-k)^2)$$.

1、k-medoids的运行速度较慢，计算质心的步骤时间复杂度是O\(n^2\)，因为他必须计算任意两点之间的距离。而k-means只需平均即可。

2、k-medoids对噪声鲁棒性比较好。例：当一个cluster样本点只有少数几个，如（1,1）（1,2）（2,1）（100,100）。其中（100,100）是噪声。如果按照k-means质心大致会处在（1,1）（100,100）中间，这显然不是我们想要的。这时k-medoids就可以避免这种情况，他会在（1,1）（1,2）（2,1）（100,100）中选出一个样本点使cluster的绝对误差最小，计算可知一定会在前三个点中选取。

以上。虽然k-medoids也有优点，但是他只能对小样本起作用，样本一大，他的速度就太慢了，而且当样本多的时候，少数几个噪音对k-means的质心影响也没有想象中的那么重，所以k-means的应用明显比k-medoids多的多

## Fuzzy C-Means \(FCM\)

Algorithm is an extension of k-means and uses squared errors criterion to handle fuzzy membership

Fuzzy C-means has better convergence properties but can still get stuck at local minima

* can be used to produce hard clustering at different levels by thresholding the membership values
* still suffers from some of the limitations of Kmeans \(non-globular shapes, needs to know choice of K,..\)

## Problem with Partitional Approaches

* 
