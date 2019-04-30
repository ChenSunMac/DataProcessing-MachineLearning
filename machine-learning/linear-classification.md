# Linear Classification

For a **linear** binary classificaiton problem \($$y \in \{-1, 1\}$$\):

$$
a(x) = sign (w^Tx)
$$

essentialy created a linear mapping based on the inner product between weight and the input features, and the resulted sign reflect the classfication result. \(bias can be included by dummy feature 1\).

$$
a(x; w) = \langle w, x \rangle
$$

$$
P( y=1 \; \big| \; x, \, w) = \dfrac{1}{1 + \exp(- \langle w, x \rangle)} = \sigma(\langle w, x \rangle)
$$

```python
def probability(X, w):
    """
    Given input features and weights
    return predicted probabilities of y==1 given x, P(y=1|x), see description above

    Don't forget to use expand(X) function (where necessary) in this and subsequent functions.

    :param X: feature matrix X of shape [n_samples,6] (expanded)
    :param w: weight vector w of shape [6] for each of the expanded features
    :returns: an array of predicted probabilities in [0,1] interval.
    """

    # TODO:<your code here>
    X_expanded = expand(X)
    logit = X_expanded.dot(w)
    prob = 1.0 / (1.0 + np.exp(-logit))
    return prob
```

## Classification loss

**Classification Accuracy:** $$\frac{1}{n} \sum_{i=1}^{n} [a(x_i) = y_i]$$, where the bracket $$[P]$$ is Iversion bracket, which equals to 1 when the inner statement P is true, otherwise 0.

* Not differentiable -&gt; hard to be optimized
* Does not assess model confidence level

**Softmax transform:** We can compute the class score \(as an interpretation of the probablity distributions\) by:

$$
z = (w^T_1x, ..., w^T_Kx) \rightarrow \sigma(z) = (\frac{e^{z_1}}{\sum_{k=1}{K}e^{z_k}}, ..., \frac{e^{z_K}}{\sum_{k=1}{K}e^{z_k}})
$$

where in total of K classes, $$\sigma(z)$$ is normalized and all the componnent are positive and the sum is 1 \(similar to probability distribution\).

Note that the target values for class probabilities is $$p = ([y=1], ..., y=[K])$$, we can use the **similarity between p and** $$\sigma(z)$$ as loss function, one way to measure the similarity is cross-entropy:

$$
L(w) =  - {1 \over \ell} \sum_{i=1}^\ell \left[ {y_i \cdot log P(y_i \, | \, x_i,w) + (1-y_i) \cdot log (1-P(y_i\, | \, x_i,w))}\right]
$$

```python
def compute_loss(X, y, w):
    """
    Given feature matrix X [n_samples,6], target vector [n_samples] of 1/0,
    and weight vector w [6], compute scalar loss function using formula above.
    """
    # TODO:<your code here>
    prob = probability(X,w)
    loss = - 1.0/X.shape[0] * np.sum(y * np.log(prob) + (1-y) * np.log(1.0 - prob))
    return loss
```

The gradient can be calculated in the following way:

```python
def compute_grad(X, y, w):
    """
    Given feature matrix X [n_samples,6], target vector [n_samples] of 1/0,
    and weight vector w [6], compute vector [6] of derivatives of L over each weights.
    """

    # TODO<your code here>
    prob = probability(X,w)
    grad = -1.0 / X.shape[0] * np.sum((y - prob)[:,None] * X, axis = 0)
    return grad
```

