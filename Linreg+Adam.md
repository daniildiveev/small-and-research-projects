### Preamble

Linear regression is one the easiest models of machine learning(both for understanding and coding).

The optimization algortihm used in Linear Regression called Gradient Descent is quite computationally easy, but it has a lot weaknesses. It cannot be used for Deep learning, since its learning rate is not dynamical, and it can simply stop in local minimum, not the global one, etc.

The gradient descent logic in general looks something like that:

![image](https://user-images.githubusercontent.com/69817199/127409962-7465e097-a9ab-4d00-9a4d-60b389c15506.png)

Where `a` is learning rate and `dL/dw` derivative is gradient. That is the rule of updating weights in gradient descent.

Adam optimizer is used for deep learning, it finds the minimum more efficently, and it can overcome local minimums easily using `m` and `v` params. Besides that, its learning rate changes dynamically. 

Here is the formulas for updating weights in Adam:

![image](https://user-images.githubusercontent.com/69817199/127485737-7a0806f5-560b-4543-9565-444e744c1331.png)

So why not to try using Adam in training Linear Regression and see what is actually better in this case: GD or Adam Optimizer.

### Creating data

To create data, i used `random` library and came with idea to create it in this way: 

```Python
import random

n_samples = 500
x_train = [random.randint(i, (i+random.randint(0,100))) + random.randint(0,100) for i in range(n_samples)]
y_train = [random.randint(i, (i+random.randint(0,100))) + random.randint(0,100) for i in range(n_samples)]
```
So then, when i then ran `plt.scatter` i saw something like that: 


