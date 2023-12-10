## Gradient descent algorithm
$$
w = w - \alpha \frac{\partial}{\partial w} J(w,b)
$$

$$
b = b - \alpha \frac{\partial}{\partial b} J(w,b)
$$

> $\alpha$ is learning rate. it controls the step size of taking hilldown

> $\alpha \frac{d}{dw} J(w)$ is to control how big step next time


1. Repeat untl convergence.

2. We need to update both of them **simultaneously**.

In summary, if we want to ensure a linear regression model(ensure $w$ and $b$). It means we need to make the cost function minimized. 

The problem turn into ensure where our derivative equals or near the zero. Therefore, we need a way to automatically adjust $w$ and $b$ every time(or every iterate) to make the cost function close to 0. And this way is the gradient descent algorithm.

