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

--- SKIPPED 3 LECTURES WTF ---

RELU Paddle Detctor
* paddle : kernel / filter / weights put over the image
* element wise multiplication, shift kernel afterwards
 * downscales image
  * ceil([(W-K+2P)/S]+1)
  * w = 5, k = 3, p = 0, s = 1 --> 3 x 3 result
 ![image](https://github.com/user-attachments/assets/7a6981fc-4e19-470c-bb13-502c30ea0f24)

RELU : 
* number > bias --> output number
* if net <+ bias --> output 0

flatten RELU outputs to one large vector which is used as inputs to Feedforward layer 

Seeding the Q network : fixed entries in the Q table




