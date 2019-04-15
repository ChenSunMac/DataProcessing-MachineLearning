# Density Based Classifiers

The classification problem can be described statistically estimating $$p(y=1|x=x_i)$$. 

A bayes classifier can formulate as:

$$
\begin{equation}
P(y=c_k| x=x_i) = \frac{P(x=x_i|y=c_k) P(y=c_k)}{P(x=x_i)}
\end{equation}
$$
where the decision boundary is $$P(y=1| x=x_i) = P(y=0| x=x_i)$$



- The prior : $$P(y=c_k) $$种类的分布
- The likelihood : $$ P(x=x_i|y=c_k)$$
These two distribution need to know in order to solve the classfication problem.




### Naive Bayesian Classifier
基础思想：对于给出的待分类项，求解在此项出现的条件下各个类别出现的概率，哪个最大，就认为此待分类项属于哪个类别。算法步骤如下：

1、找到一个已知分类的待分类项集合，这个集合叫做训练样本集。

2、统计得到在各类别下各个特征属性的条件概率估计 likelihood，即 $$ P(x=x_i|y=c_k)$$ 

因为分母对于所有类别为常数，要找概率最大的类别，我们只要找到分子最大的就行。又因为**假设**各特征属性是条件独立的


### Linear Discriminant Analysis (LDA)
Assume the **likelihood** follow the Gaussian Distribution instead of calculate from training data statistics



### Parzen Window Density Estimation
由给定样本集合求解随机变量的分布密度函数问题是概率统计学的基本问题之一。解决这一问题的方法包括参数估计和非参数估计。


Parzen window density estimation is another name for kernel density estimation. It is a nonparametric method for estimating continuous density function from the data.


Imagine that you have some datapoints $$D: x_1,...,x_n$$ that come from common unknown, presumably continuous, distribution f. You are interested in estimating the distribution given your data. One thing that you could do is simply to look at the empirical distribution and treat it as a sample equivalent of the true distribution. However if your data is continuous, then most probably you would see each xi point appear only once in the dataset, so based on this, you would conclude that your data comes from an uniform distribution since each of the values have equal probability. Hopefully, you can do better then this: you can pack your data in some number of equally-spaced intervals and count the values that fall into each interval. This method would be based on estimating the histogram. Unfortunately, with histogram you end up with some number of bins, rather then with continuous distribution, so it's only a rough approximation.


Kernel density estimation is the third alternative. The main idea is that you approximate f by a mixture of continuous distributions K (using your notation ϕ), called kernels, that are centered at xi datapoints and have scale (bandwidth) equal to h:
$$
\begin{equation}
f_h(x|D) = \frac{1}{nh} \sum_{i=1}^n K(\frac{x-x_i}{h})
\end{equation}
$$


Saying this in plain English, what you assume in here is that the observed points xi are just a sample and follow some distribution f to be estimated. Since the distribution is continuous, we assume that there is some unknown but nonzero density around the near neighborhood of xi points (the neighborhood is defined by parameter h) and we use kernels K to account for it. The more points is in some neighborhood, the more density is accumulated around this region and so, the higher the overall density of fh^. The resulting function fh^ can be now evaluated for any point x (without subscript) to obtain density estimate for it, this is how we obtained function fh^(x) that is an approximation of unknown density function f(x).
