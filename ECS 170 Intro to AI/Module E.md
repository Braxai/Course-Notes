## Deep Learning with an Emphasis on Convolutional Neural Networks and RL 

Why replace Q-table with Q-network
* gigantic state space too large to model and update q-table

Convolutional Neural Networks
* convolutional layers : look for properties/features they can reason about
* feedforward layers : reasoning
* innovation is to do these simultaneously

How we teach DL
* deep learner is complex composite function (parameters of functions are weights on edges)
  * learning is performed by comparing the expected vs actual output
  * if they are same, weights aren't changed otherwise they are changed via back propagation (gradient descent)
 
* Domain : input
* Range : output

Q Network
* domain : state
* range : actions
* update : train it with expected value and actual result

Feedforward Layers : part of network that do reasoning 
* perceptron : simplest type of FF unit
  * makes a decision on each point in the instance space
  * decision boundary defines the boundary/transition from predicting -1 to predicting +1
  * decision boudnary for perceptron is linear
    * decisionboundary orthogonal to weight vector
      * y intercept is -w0

