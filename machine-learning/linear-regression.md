# Linear Regression

A set of data are with the samples $$(x_i, y_i)$$ where the $$x_i$$ is input vector with feature as $$x_i = (x_{i1}, x_{i2}, ... x_{id})$$ and $$y$$ is the target output. For the regression task, the target output usually is real number $$y \in \mathbb R$$ .

We can tell weather x and y exist linear/nonlinear statistical relation by observing the Correlation where

$$
Cor (X, Y) = \frac{Cov(X,Y)}{S_XS_Y},~ Cov = \frac{1}{l-1} \sum_{i=1}^{l}(x_i - \bar x) (y_i - \bar y)
$$
and the $$S_X, S_Y$$ are the estimates of standard deviations for X observations and Y observations respectively.

**Linear relation:** If Cor(Y,X) is close to 1, it means that we have a positive linear relation (The slop is positive). If Cor(Y,X) is close to -1, it means that we have a negative linear relation.

**Non-linear relation:** If Cor(Y,X) is close to zero, it means that
we do not have any linear relation.

```
# example of the correlation calculation
import pandas as pd
import numpy as np
import scipy

X = np.linspace(-5,5,100)
Y = X**2 + 2* np.random.rand(100)
scipy.stats.pearsonr(X,Y) # would output a correlation close to 0
```



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

#### **Training a Model:** 

We try to fit the model to the training data by minimizing the loss, that is, to find a set of weights w, such that minimize the $$L(w)$$, the exact solution can be obtained as 

$$
w = (X^TX)^{-1} X^Ty
$$
Note that inverting a matrix is hard for high-dimensional data!



