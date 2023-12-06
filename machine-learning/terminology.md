# Terminology
> Terminology: Words that can use to talk about machine learning concepts.



Training set: Data used to train the model.

Univariate linear regression: Linear regression with one variable.

Cost function: tell us how well the is doing.

Squared error cost function(the most commonly used one for linear regression):
$$
J(w,b) = \displaystyle \frac{1}{2m}\sum^m_{i=1}(\hat{y}^{(i)} - y^{(i)})^2
$$
> $m$ = number of training examples

> Divide by $2m$ rather than $2$ just beacuse simplify our derivation later.

Gradient descent: a algorithm that used to find the minimized cost function J automatically. The most important algorithm in ML, applied in most models.
## Notation
$x$ = input variable, feature

$y$ = output variable, target variable

$m$ = number of training examples

$(x,y)$ = single training examples

$(x^{(i)},y^{(i)})$ = $i^{th}$ training example

$\hat{y}$ = the prediction output $y$, it is a estimate

$f_{w,b} = wx + b$ = a function that takes x as input and depending on the value of w and b(parameters, coefficients or weights), f will out put some value of a prediction y-hat 

![how to work](./images/how-to-work.png)