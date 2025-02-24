Types of Machine Learning 
* Supervised : supervision in the form of annotations on objects/instances
  * Object prediction
  * labeled training set
* Unsupervised : given just instances and no annotations what can be learned?
  * auto encoder 
* Reinforcement Learning : differences is the settings and what we learn from (environment) not human annotations
  * learning to control an agent to behave optimally/rationally in an environment
 
Limitations 
* Not good at dealing with things that don't fit into the patterns they are trained on
  * objective function
* trying to learn crystallized intelligence : good at a specific task
 
Types of Human Intelligence
* Crystallized Intelligence
  * task specific knowledge
  * use skills, knowledge, experience from long term memory
  * increases throughout life
* Fluid Intelligence
  * general knowledge
  * adapt solve novel problems independent of past knowledge
  * knowledge that transcends tasks
  * increases in adulthood but declines in later years
 
![image](https://github.com/user-attachments/assets/fdc75d99-85db-401d-9803-899d68de2c0e)

* Policy Learning : learning a mapping from state to action
* Can use supervised learning to teach a machine a policy
  * policy gradient learning
  * two main limitations
    * cannot exceed human potential if learning from a human
    * a person has to annotate everything 
* Instead we try to learn a VALUE for each state, measures how much reward we will get for being in that state
* v value is a measure of how much REWARD for being in a state
  * value learning makes a strong assumption
    * need knowledge of state transition operator 
  * c.f. right with pendulum/flight simulator
* reinforcement learning is scary
  * teach machine an optimal policy even though it knows nothing about the environment it begins with with no human expertise

### Q Learning 
* Q learning associates a value for each state/action combination
  * do argmax over current state and choose that action
* Least restrictive but has two core disadvantages
* Q and V learning require access to a cheap simulator to practice in

Addressing the Credit Assignment Problem
* Environment often gives zero reward for performing an action in a state
  * challenge to figure out how to get into good states that eventually yield a reward

Reward Function

![image](https://github.com/user-attachments/assets/2c67ce0d-6e1b-4247-bb0b-17cd284c1ab2)

* Finite Horizon : reward is sum of future awards up to a finite horizon
  * simple computationally
* Average : average rewards up to a point in the future
  *  hard to deal with, can't sensibly choose between small reward soon and large reward very far in the future
* Infinite Discounted : weighted average
  * easier for proving theorems

 * Inverted Pendulum : finite horizon
 * Flying a plane level : average

Q learning algorithm 
* optimal
* anytime algorithm : the more time it's given the better it is

Environment modelled as two functions 
* reward function
* state transition function
  * absorbing state : defines training episode end
 
Q(s,a) <-- r + gamma * argmaxQ(s', a') 

Two Limitations 
* waste time until series of actions is found that produces a reward
  * seed Q-Table with apriori knowledge
* exploration vs exploitation problem : always exploiting a series of actions that yields a reward rather than exploring alternative actinos that could yield higher rewards
  * choose best action (per q tables) most of the time, with a (decreasingly) small chance randomly choose an action

Q Learning modelled by reward and state transition function
* Incorrect assumption : assumes the two functions are nondeterministic
* can be resolved by tracking an overall mean calculated based on the previous mean and the new number

