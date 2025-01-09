* Informed Search
  * Aim : find optimum (in terms of cost) sequence of actions that move you from start to goal state 
  * State : abstraction of the environment
  * Action : operator that movees from one state to another
    * Cost : associated with each action 

* Tree Search vs Graph Search
  * graph search has extra data structure explored/closed
  * graph search more efficient : prevents cycles 
* A* can use admissible or consistent heuristic
  * Admissible : tree search
  * Consistent : graph search

# Formulating Problems as Searching Trees/Graphs 
* defined search problem consists of : initial state, actions, goal test, path cost
  * implicitly defines state space
Three Types of Paths
* Nonsolution : doesn't find goal (removed in graph search)
* Suboptimal Solution : not the shortest solution from start to goal
  * A* prunes search space and removes suboptimal solutions
* Optimal Solution : shortest solution from start to goal 

Rubik's Cube Problem
* State represented as a matrix
* Successor function : many choices, example pick a side and rotate 90 degrees either direction
* BFS used since the tree is technically infinite since you could keep rotating 90 degrees so DFS wouldn't return 

# Briefly Cover Basics of Uninformed Search 
* BFS good if you don't know the depth of the solution
  * 8-tile problem
  * bad for 8-queen problem because there are only legal solutions at depth 8 (use depth limited algorithm)

* graph search assumes the first time it exapnds a node was the shortest distance to it --> which it needs a consistent heuristic 

# Why we need A*
* Dijkstra's expands nearly everything
  * one of many best first search algorithms 
* A* expands a much smaller amount by realizing other paths are suboptimal
* f(n)=g(n)+h(n) is guaranteed to find shortest path in least amount of time 
