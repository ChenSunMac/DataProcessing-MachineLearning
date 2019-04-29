A way to find optimum **weight** to minimize loss function.

** Optimization problem:** $$\min_w L(w)$$

## Gradient Descent

Gradient vector: $$\nabla L(w_0)$$, points in the direction of the steepest slope at $w_0$, the function has fastest decrease rate in the direction of negative gradient.

Update until convergence
$$
\begin{equation}
w^t = w^{t-1} - \eta_t \nabla L(w^{t-1}) 
\end{equation}
$$

- Easy to implement and less memory computation compared to analytical solution
- Can be applied to any differentiable loss function

## Stochastic Gradient Descent (with mini-batch gradient descent)

Gradient Descent becomes infeasible for large data problem where the calculation of gradient vector scales as the training data size scales.

In stochastic gradient descent, we randomly select a subset (or even 1) of training examples and we find the gradient vector based on only the subset of examples:

while True:
i = random index between 1 and n
$$
\begin{equation}
w^t = w^{t-1} - \eta_t \nabla L(w^{t-1}; x_i; y_i) 
\end{equation}
$$
Update until convergence

- Leads to very noisy approximation
- Can be used in online setting
- Learning rate $$\eta_t$$ should be chosen very carefully (might not converge)

#### mini-batch gradient descent

while True:
$$i_1,...,i_m$$ = random index between 1 and n
$$
\begin{equation}
g_t = \frac{1}{m} \sum_{j=1}^m \nabla L(w^{t-1}; x_{i_j}; y_{i_j}) 
\end{equation}
$$
$$
\begin{equation}
w^t = w^{t-1} - \eta_t g_t
\end{equation}
$$
Update until convergence

**Note:** The gradient descent is good but suffers the oscillation of gradient, might not converge or even not stable due to the subset of training data.

## Momentum
In order to dampen the oscillation caused by stochastic gradient descent method, we can use momentum 
$$
\begin{eqnarray}
h_t = \alpha h_{t-1} + \eta_t g_t\\
w^t = w^{t-1} - h_t
\end{eqnarray}
$$

where $$h(t)$$ is just a weighted sum of gradient descent from all previous iteration and current iteration. 

- Tends to move in the same direction as on previous steps, 
- $$h_t$$ accumulates values along dimensions where gradients have the same sign
- if $$h_{t-1}$$ and $$g_t$$ are not with the same sign, it dampens the oscillation.

#### Nesterov Momentum
$$
\begin{eqnarray}
h_t = \alpha h_{t-1} + \eta_t \nabla L (w^{t-1} - \alpha h_{t-1}) \\
w^t = w^{t-1} - h_t
\end{eqnarray}
$$

**Note:** The moment methods and gradient descent still need to tune the learning rate parameter and usually the learning rate need to be update during the iteration.

## AdaGrad
Adaptive change the learning rate for the gradient descent method

$$
\begin{eqnarray}
G_j^t = G_j^{t-1} +  g^2_{tj} \\
w^t_j = w_j^{t-1} - \frac{\eta_t}{\sqrt{G_j^t + \epsilon}} g_{tj} 
\end{eqnarray}
$$

where
- $$g_{tj} $$ is the gradient with repect to j-th parameter
- separate learning rates for each dimension
- Suite for sparse data, and the learning rate $$\eta_t = 0.01$$ can be fixed
- BAD: $$G_j^t $$  always increases, lead to early stops. (might not find the optimum)

## RMSProp
AdaGrad with momentum

Adagrad会累加之前所有的梯度平方，而RMSprop仅仅是计算对应的平均值，因此可缓解Adagrad算法学习率下降较快的问题

$$
\begin{eqnarray}
G_j^t = \alpha G_j^{t-1} +  (1-\alpha) g^2_{tj} \\
w^t_j = w_j^{t-1} - \frac{\eta_t}{\sqrt{G_j^t + \epsilon}} g_{tj} 
\end{eqnarray}
$$

added $$\alpha$$ (usually about 0.9) in the gradient update, where the learning rate adapts to latest gradient steps. 
简单来讲，设置全局学习率之后，每次通过，全局学习率逐参数的除以经过衰减系数控制的历史梯度平方和的平方根，使得每个参数的学习率不同。
起到的效果是在参数空间更为平缓的方向，会取得更大的进步（因为平缓，所以历史梯度平方和较小，对应学习下降的幅度较小），并且能够使得陡峭的方向变得平缓，从而加快训练速度。


Similar idea with momentum method

## Adam
Adam(Adaptive Moment Estimation)是另一种自适应学习率的方法。它利用梯度的一阶矩估计和二阶矩估计动态调整每个参数的学习率。Adam的优点主要在于经过偏置校正后，每一次迭代学习率都有个确定范围，使得参数比较平稳。
$$
\begin{eqnarray}
m_j^t = \frac{\beta_1 m_j^{t-1} + (1-\beta_1)g_{tj}}{1- \beta_1^t}\\
v^t_j = \frac{\beta_2 v_j^{t-1} + (1-\beta_2)g^2_{tj}}{1- \beta_2^t}\\
w^t_j = w_j^{t-1} - \frac{\eta_t}{\sqrt{v_j^t + \epsilon}} m^t_{j} 
\end{eqnarray}
$$

Combines momentum and individual learning rates. 

其实就是Momentum+RMSProp的结合，然后再修正其偏差

