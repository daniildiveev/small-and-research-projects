# Small and Research projects by sexozavr

Here i will publish some of my 'one-day' projects.

In this file i am going to write some description on every project. 

## Linear regression fitting using Adam optimizer

Linear regression is one the easiest models of machine learning(both for understanding and coding).

The optimization algortihm used in Linear Regression called Gradient Descent is quite computationally easy, but it has a lot weaknesses. It cannot be used for Deep learning, since its learning rate is not dynamical, and it can simply stop in local minimum, not the global one, etc.

The gradient descent logic in general looks something like that:

![image](https://user-images.githubusercontent.com/69817199/127409962-7465e097-a9ab-4d00-9a4d-60b389c15506.png)

Where `a` is learning rate and `dL/dw` derivative is gradient. That is the rule of updating weights in gradient descent.

Adam optimizer is used for deep learning, it finds the minimum more efficently, and it can overcome local minimums easily using `m` and `v` params. Besides that, its learning rate changes dynamically. 

Here is the formulas for updating weights in Adam:

![image](https://user-images.githubusercontent.com/69817199/127413614-e05d7953-7c3d-415b-a946-0657c0f6b90e.png)

