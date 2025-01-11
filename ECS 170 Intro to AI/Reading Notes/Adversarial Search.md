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
* Decisions must consider the opponents possible reponses 
* Minimax Value : utility of being in the corresponding state assuming both players play optimally from there to the end of the game

### Minimax Algorithm 
* Minimax Algorithm : computes the minimax decision from the current state
 * uses simple recursion computation of minimax values of each successor state
 * recursion proceeds down to thel eaves and the minimax values are backed up through the tree as recursion unwinds

### Optimal Decisions in Multiplayer Games 
![image](https://github.com/user-attachments/assets/35184522-497f-4a3f-a1e0-cae6ef5056b0)

* utilize vectors to represent multiple players

![image](https://github.com/user-attachments/assets/06aa780e-f87c-455b-8ccd-352dcd031c92)

* Alliances : formal or informal agreements between agents, arise naturally from optimal strategies 

## Alpha-Beta Pruning
* Alpha-Beta Pruning : returns same moves as minimax but prunes away branches that cannot possibly influence the final decision 

![image](https://github.com/user-attachments/assets/f7de9906-64ca-4d0f-bd76-db2ba29f57ae)

### Move Ordering 
* If moves are evaluated in an ideal order pruning is more effective

![image](https://github.com/user-attachments/assets/b1344b97-e479-49c5-b53f-21336c5ce5b1)

* Killer Moves : best moves, finding them first is called the killer move heuristic
* Transpositions : different permutations of the moves equence that end up in the same position
 * Transposition Table : store resulting position in a hash table the first time it is encountered 

## Imperfect Real-Time Decisions 

### Evaluation Functions 
* Evaluation Function : returns estimate of the expected utility of the game from a given position
 * Features : features of the state considered when calculating evaluation function
  * define categories or equivalence classes of states
  * Expected Value : determined for each category
  * Material Value : approximate value of a piece (chess piece values)
