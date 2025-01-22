## Assignment 1 
* What to change in graph search?
  * "dumber" heuristic is faster to compute
  * bidirectional search
    * replace goal test with check to see whether the frontiers of two searches intersect (finds legal path, not optimal)
      * need to figure out termination criterion for optimal path
    * makes assumption shorest path from S->G same as G->S, is this the case of exponential cost function?
  * more efficient data structures

Game Classifications 
* information
  * perfect : all information related to the state of the game available to all players
  * imperfect
* state transition function
  * deterministic : applying action i in state j will always get you to the same new state
  * chance

Game Theory Perspective Requirements (requirements to turn something into a game)
* turn taking
* two player
* zero-sum : extent of a player's loss is the extent of the other's win
* perfect information
* player is rational

Algorithm Contingency Plan : minimize maximum loss
* Computing Nash Equilibirum

* Max : maximizes lower bound
* Min : minimizes upper bound
* Nash Equilibrium : result if both Max and Min play optimally
 * Composite Functions : Max(Min(values))
Recursive Algorithm
![image](https://github.com/user-attachments/assets/bcb05479-40e8-4ae4-912f-e5d6af4db62e)

Informed vs Adversarial Search Differences
* informed can wokr on a graph but min-max only on a tree
* weights are on edges for informed and nodes for adversarial: sattes have payoffs 
* aim : informed typically solves the shortest path problem but adversarial minimizing maximum loss

Most games can't explore bottom of the search tree so we implement depth limited search 
* Need an evaluation function to determine how good a state is (heuristic, not admissible)

Evaluation Function Types
* Attach values to pieces or locations
 * chess pieces
* Estimate number of ways to win/lose
Function needs to be accurate, fast, easy to order
 * order tree in way so ordering of nodes is strictly monotonically increasing/decreasing

Properties of Minimax Search
* Complete : finite tree
* Optimal against an opponent
* Time Complexity : O(b<sup>m</sup>)
* Space Complexity : O(bm) (depth-first exploration)
reasonable games exact solution infeasable : chess b = 35 and m = 100

## Alpha Beta Pruning 
Not an approximation algorithm, will calculate the exact nash equilibrium in less iterations 

Two interpretations to algorithm
* efficient computation of nash equilibrium via pruning state space
* pruning state space by exlpoiting that both players are rational
 * most optimal move needs to be explored first to maximize amount of pruning

![image](https://github.com/user-attachments/assets/2ffd136e-0993-42dd-a5f3-515d6290db53)
Same as mini-max except two changes 
* maintain alpha/beta (lower/upper bounds on NE) value for each node
* test for irrational behavior




