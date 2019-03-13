# Linear Regression

A set of data are with the samples $$(x_i, y_i)$$ where the $$x_i$$ is input vector with feature as $$x_i = (x_{i1}, x_{i2}, ... x_{id})$$ and $$y$$ is the target output. For the regression task, the target output usually is real number $$y \in \mathbb R$$ .

#### **Linear Model:** 

propose the hypothesis on the input and output that trying to fit a linear relationship between them.

$$
h(x) = w_1x_1 + w_2 x_2 + ...+ w_dx_d + b
$$

where the weight terms are coefficient of the model and bias b is a unknown constant we need to solve, so in total there will be d+1 parameters. We can also make it even simple that assume a fake feature that always be 1, then the bias can be viewed as a weight as well, that is $$h(x) = w^Tx$$ .

For a group of $$l$$ sample inputs \(aka a test data set\) X, we can rewrite the hypothesis in vector form as 

$$
h(X) = Xw, ~~X = \begin{bmatrix}
    x_{11} & x_{12}   & \dots  & x_{1d} & 1 \\
    x_{21} & x_{22}  & \dots  & x_{2d}  & 1\\
    \vdots & \vdots & \ddots & \vdots   & \vdots \\
    x_{l1} & x_{l2} &   \dots  & x_{ld} & 1
\end{bmatrix}
$$

#### **Loss Function:** 

How to measure the model quality, how do we know the resulting model fits not only the training data but also the data outside of our sampling regime.

**Mean Squared Error \(MAE\):** 

$$
L(w) = \frac{1}{l} \sum_{i=1}^{l} (w^Tx_i - y_i)^2 = \frac{1}{l}\| Xw - y \|^2
$$



