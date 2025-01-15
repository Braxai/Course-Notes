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

Game Theory Perspective Requirements 
* turn taking
* two player
* zero-sum : extent of a player's loss is the extent of the other's win
* perfect information
* player is rational

Algorithm Contingency Plan : minimize maximum loss
* Computing Nash Equilibirum
