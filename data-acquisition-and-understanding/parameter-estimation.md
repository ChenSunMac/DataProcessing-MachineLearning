# Parameter Estimation

**Descriptive Analysis** that seek to describe and summarize the data, the available samples. We can not in general use it for interpretation of unobserved data.

**Inferential Analysis** can describe measures over the popilation of data, that is observed and unobserved.

比如，算sample mean, mean is correct for just the sample as it is descriptive of the samples.

It can only be an estimate of the mean of population that has a slight variation of the sample in the interential analysis.

## Parameter Estimation

可以从sample 数据里面算出来 **Expectation:** for a discrete random variable, the expected value is

$$
\begin{equation}
E(x) = \sum_{i=1}^n x_i p(x_i)
\end{equation}
$$

We define the parameter or statistic of the data to be

$$
\begin{equation}
\theta = g(x_1, x_2, ..., x_n)
\end{equation}
$$

We don't know $$\theta$$, so we estimate it and call the estimate $$\hat\theta$$

### Unbiased Estimators

If the expected value of the estimate equals the actual valueof the parameter thenthe estimator is called unbiased otherwise bias is the difference.

$$
\begin{equation}
Bias(\hat \theta) = E(\hat \theta) - \theta
\end{equation}
$$

For example, we can estimate the mean of data by proposed estimator _sample mean_: \(suppose Bernoulli distribution where $$\theta = P$$\)

$$
\begin{equation}
Bias(\hat \theta) = E(\hat \theta) - \theta = E(\frac{1}{n} \sum_{i=1}^n x_i) - \theta = 0
\end{equation}
$$

which is unbiased.

We can also follow the same line to find out that the sample variance is biased.

**Variance** : $$V(\hat\theta) = E(\hat \theta - E(\hat \theta))^2$$

### Mean Squeared Error \(MSE\)

**MSE** is one effective measure of the combination of bias and variance

$$MSE(\hat \theta)= E(\hat \theta - \theta)^2 = B^2(\hat\theta) + V(\hat \theta)$$

**RMSE** gives a better sense of the magnitude of the error

If the estimator $\theta$ is unbiased, then MSE = Variance

## Reducing Bias

We can attempt to reduce the bias by resampling and K-Cross Validation

### Resampling

Jackknife Estimate, or so-called leave-one-out resampling:

The estimate is obtained by omitting one sample \(i\) from the data sample set.

$$
\begin{equation}
\hat\theta_{(i)} = \hat \mu_{(i)} = \frac{\sum_{j\neq i}^n x_j}{n} 
\end{equation}
$$

Then take the mean of theses as the overall parameter

$$
\begin{equation}
\hat \theta = \frac{\sum_{j=1}^n \hat\theta_{(j)}}{n}
\end{equation}
$$

### K-Cross Validation

More generally to the Kackknife estimate, we can leave out multiple samples: 1. Splict the data into K equal sized parts 2. For l = 1, 2, ... K

* leave part l out and build estimator on K-1 data points
  1. Combine results into K statstics

If K = n then this is just leave-one-out validation.

To summarize, there is a bias-variance trade-off associated with the choice of k in k-fold cross-validation. Typically, given these considerations, one performs k-fold cross-validation using k = 5 or k = 10, as these values have been shown empirically to yield test error rate estimates that suffer neither from excessively high bias nor from very high variance.

## Maximum Likelihood Estimation \(MLE\)

Assumes that the samples are from a specific distribution with unknown parameters.

Likelihood is the probability that the samples observed come from the given distribution. $$L(\theta|X) = p(X|\theta)$$

We can estimate the paramter $\theta$ by maximizing the likelihood function.

Given a known _distribution function $f\(x\_i, \theta\)$_

Given a _sample data $x = {x\_1, x\_2, ... , x\_n}$_

The likelihood can be formulated as

$$
\begin{equation}
L(\theta|x_1, ..., x_n) = \prod_{i=1}^{n}f(x_i|\theta)
\end{equation}
$$

MLE = the value of prameter $\theta$ that maximizrs likelihood L is the estimate, can be obtained by finding the derivative of the log-liklihood with respect to the parameter $\theta$ and queating the resulting formula to zero.

**NOTE:** This analytical MLE method requires full data that we can solve the equation exactly.

## Expectation Maximization \(EM\)

If we have missing data, we can use EM to solve for the incomplete data. 可以用作数据填充，fill out the missing data

**Pros:** Easy to implement, compared to using model fit solutions which often required gradients

**Cons:** Slow to converge, might find local maxima, senesitive to initial guess, bad in high dimensions.

1. **Estimation**: calculate a value for the missing data
2. **Maximization**: use the data and new values of the missing data to find new estimates using MLE

Repeat steps 1 and 2 until convergence.

