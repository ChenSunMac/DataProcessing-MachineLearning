# Linear Classification

For a **linear** binary classificaiton problem ($$y \in \{-1, 1\}$$):
$$
a(x) = sign (w^Tx)
$$
essentialy created a linear mapping based on the inner product between weight and the input features, and the resulted sign reflect the classfication result. (bias can be included by dummy feature 1).


##### Classification loss

**Classification Accuracy:** $$ \frac{1}{n} \sum_{i=1}^{n} [a(x_i) = y_i]$$, where the bracket $$[P]$$ is Iversion bracket, which equals to 1 when the inner statement P is true, otherwise 0.

- Not differentiable -> hard to be optimized
- Does not assess model confidence level

**Softmax transform:** We can compute the class score (as an interpretation of the probablity distributions) by:
$$
z = (w^T_1x, ..., w^T_Kx) \rightarrow \sigma(z) = (\frac{e^{z_1}}{\sum_{k=1}{K}e^{z_k}}, ..., \frac{e^{z_K}}{\sum_{k=1}{K}e^{z_k}})
$$
where in total of K classes, $$\sigma(z)$$ is normalized and all the componnent are positive and the sum is 1 (similar to probability distribution).

Note that the target values for class probabilities is $$p = ([y=1], ..., y=[K])$$, we can use the **similarity  between p and $$\sigma(z)$$** as loss function, one way to measure the similarity is cross-entropy:

