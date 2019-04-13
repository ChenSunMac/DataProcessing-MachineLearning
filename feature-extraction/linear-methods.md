# Linear Methods

### Principal Component Analysis (PCA)

A way to linearly transform a set of d-dimensional vector $x_1, x_2, ..., x_n$ into another set of m-dimensional vectors

The main idea is that high information corresponds to high variance, the direction of max variance is parallel to the eigenvector, corresponding to the largest eigenvalue of the covariance matrix of the sample matrix A. 


Let $R = A^TA$ be the covariance matrix of $A$ where A is normalized by substracting mean, R is symmetric positive definite it eigenvlues are real and positive. Now we apply an orthogonal transformation to R to diagonalize it:
$$
\begin{equation}
CRC^T = \Lambda_d
\end{equation}
$$

The sorted eigenvalues of R $\lambda_1 \ge \lambda_2...\ge \lambda_d \ge 0$ 

*Note:* we can choose $m$ by 
$$
\begin{equation}
r_m = \frac{\sum_{i=1}^m \lambda_i }{\sum_{i=1}^d \lambda_i} \ge \tau  
\end{equation}
$$
e.g. choosing $\tau = 0.95$ will ensures that 95% of the variance is retained in the new space.

*Note:* Covariance matrix $R = A^TA$ is $d\times d$ matrix which make the computation too complex, we can use singular value decomposition instead.

##### Singular Value Decomposition
The matrix A can be decomposed using SVD $A_{n\times d} = USV^T$ where
- U is a $n\times d$ matrix of orthonomal columns $U^TU = I$
- V is a $n\times d$ matrix of orthonomal columns $V^TV = I$
- S is a $d\times d$ diagonal matrix of singular values

SVD can be used to obtain PCA, Now $R = A^TA = VS^2V^T$


- PCA is *optimal* in the sense of minimize sum of square of errors. It mainly rotates the coordinates to find new axes that have the max variance.

- The PCA may not be the best for discriminating between classes. 




