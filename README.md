# Backpropogation

## Backpropogation (Quadratic Cost Function)
The Backpropogation algorithm program to solve the XOR problem was implemented.
The algorithm used a quadratic cost function E = ||y(t) - t(t)||^2 and natural ordering of input vectors [ [1, 1], [1, -1], [-1, 1], [-1, -1] ].

The transfer function used was the bipolar sigmoid function:-
f(x) = tanh[ x/(2 * x0) ]
f’(x) = [ 0.5 * (1 + f(x)) * (1 - f(x)) ]/x0

The weights and biases were initialized randomly and uniformly with values between -C and C. The learning rate (alpha) was set at 0.2 and the tolerance (T) was set to 0.05.

The run time limit is set to 100,000 epochs to give the algorithm enough chance to converge.

## Backpropogation (Cross Entropy Cost Function)
A new cost function was introduced for the backpropogation algorithm called the Cross Entropy cost function E = -2log(0.5 * |y(t) + t(t)|).

The transfer function used was the bipolar sigmoid function:-
f(x) = tanh[ x/(2 * x0) ]
f’(x) = [ 0.5 * (1 + f(x)) * (1 - f(x)) ]/x0

The weights and biases were initialized randomly and uniformly with values between -C and C. The learning rate (alpha) was set at 0.2 and the tolerance (T) was set to 0.05.

The run time limit is set to 100,000 epochs to give the algorithm enough chance to converge.

## Observations and Inference
For Backpropogation using Quadratic Cost Function, the average number of epochs
needed for convergence decreases as we increase the number of hidden neurons from 2 to 8. But at N1=10, the epochs for convergence drastically decrease. This shows that the network performs better and better as we increase hidden neurons up to a point. After that the performance begins to degrade. This can be because number of hidden neurons beyond a certain limit cause an unneeded amount of complexity in the network leading to more epochs for convergence. Also, the more hidden layers add to the activation values of neurons and make the output closer to 1 (even when the target is 0 or -1).

Hyper parameter testing reveals that, for x0=0.5, the algorithm converges quickly. This is true for almost all learning rates and C values. This tells us that tweaking the transfer function by a small factor of 0.5 will yield us better results. However, if we use a larger factor like x0=1.5, the algorithm will take a long time to converge. So, in conclusion, a factor less than 1 would be ideal in the transfer function. The alpha values provide mixed results for the runs, however, we observe that for C=0.5, there a many non converging runs. This may be due to the fact that smaller weights and biases in magnitude (between -0.5 and 0.5) are not suitable for converging the algorithm. When the C values are 1.0 and 1.5, we get far more converging runs.

The Quadratic Cost Function suffers from learning slowdown. So, we use the Cross Entropy Cost Function and observe that the average number of epochs required for convergence is very less than those of the quadratic algorithm (364 to 104 for a 2-2-1 network). This clearly shows that the Cross Entropy Function speeds up the learning. As we increase the number of hidden neurons from 2 to 10, the average number of epochs decreases drastically. A 2-10-1 network converges after 55 epochs on an average. This shows that the cross entropy algorithm doesn’t suffer from a learning slowdown and in fact, benefits from more neurons in the hidden layer.

The hyper parameter testing results are somewhat similar to the quadratic algorithm. The x0 factor benefits the learning process if it is less than 1 (0.5). But it sort of slows down the learning if it is greater than 1 (1.5). One significant change was that for C=0.5, the algorithm did not converge most of the time. Hence, we can conclude that perhaps the algorithms prefers initial weights and biases higher in magnitude. The learning rate provides good results for all values although a lesser value of alpha (0.1) can be slightly preferred over the other larger values.

### One Neuron in the Hidden Layer
If there is only 1 hidden neuron in the network, then the algorithm fails to converge. The aim of a neural network is to produce decision boundaries that are hyperplanes. These hyper planes separate different classes from one another. When a problem is not linearly separable, hidden layers need to be used to produce more than one decision planes capable of separating the classes.

The XOR problem that we are dealing with is non linearly separable. So a simple
perceptron is not able to solve the problem. That is why we use Backpropogation with a hidden layer to produce a decision boundary capable of classifying the problem.

This works well when we have 2,4,6,8,10 hidden neurons. But when we only have 1
hidden neuron in the hidden layer, the algorithm doesn’t ever converge. The reason for this can be that a single hidden neuron on its own is unable to find a decision boundary capable of solving the problem. A single neuron doesn’t have the desired effect of a hidden layer on the network.

Moreover, the fact that there are 2 input neurons and so a hidden layer with less than 2 neurons is not able to solve this non linearly separable problem. The case might be that the hidden layer needs at least the same number of neurons as the input layer to find a hyperplane capable of classifying the classes.

The other thing might be the fact the the problem as two classes i.e [-1, 1]. So perhaps a single neuron in the hidden layer is unable to solve a problem involving 2 classes.