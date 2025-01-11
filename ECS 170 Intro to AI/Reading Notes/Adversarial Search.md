# Adversarial Search 

## Games 
* Multiagent Environments : each agent needs to consider the actions of other agents and how they affect its own welfare
  * Contingencies : introduced by unpredictability of other agents
* Competitive Environments : agent's goals are in conflict
* Games : adversarial search problems
* Game Theory : branch of economics that views any multiagent environment as a game provided that the impact of each agent on the others is significant regardless of whether the agents are cooperative or competitive
* Zero-Sum Games (perfect information) : deterministic, turn taking, two player (chess)
  * Total payoff to all players is the same for every instance of teh game
  * Adversarial : one winning means the other loses
* Pruning : ignore portions of search tree that make no difference to the final choice
* Evaluation Functions : approximate the true utility of a state without doing a complete search
* Imperfect Information : not all information available to agent
* Initial State : specifies how the game is set up
* Transition Model : defines result of a move
* Terminal Test : true when game is over
* Terminal States : state when game has ended
* Utility Function : final numeric value for a game that ends in terminal state s for a player p
* Game Tree : initial state, actions, and results define game tree
  * tree where nodes are game states and edges are moves
* Search tree : tree superimposed on the ull game tree and examines enough nodes to allow a player to determine what move to make 

## Optimal Decisions in Games 

### Minimax Algorithm 

### Optimal Decisions in Multiplayer Games 

## Alpha-Beta Pruning

### Move Ordering 

## Imperfect Real-Time Decisions 

### Evaluation Functions 
