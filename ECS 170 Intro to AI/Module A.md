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

* graph search assumes the first time it expands a node was the shortest distance to it --> which it needs a consistent heuristic 

# Why we need A*
* Dijkstra's expands nearly everything (optimal but inefficient) 
  * one of many best first search algorithms 
* A* expands a much smaller amount by realizing other paths are suboptimal
* f(n)=g(n)+h(n) is guaranteed to find shortest path in least amount of time 

# Infomred Search A* Algorithm 
* f(n) = g(n) + h(n)
  * h(n) admissible and must never over-estimate the true cost of going from n to the goal state
    * goal state h(n) = 0
* Graph search assuming the first time a state is visited it must be the shortest path to that state

# Inventing Admissible Heuristics (3 Ways) 
* Want admissible heuristic to be as large as possible

Idea 1 : consider geometry of the problem to create the heuristic 

Idea 2 : 
* Original game : lists constraints/rules for environment
* Relaxed game : relax constraints/rules to create a simpler game
  * cost function for relaxed game is an admissible heuristic for the original version
    * why? constraints add cost, relaxing them will create an alternative cost function that will be less

8-puzzle game 
* relax the rules and come up with heuristics, take the max 

* Consistent Heuristic
 * Obeys triangular inequality
  * Admissible heuristic h is consistent (satisfies monotone restriction) if for every node N and every sucessor N' of N: h(N) <= c(N,N') + h(N')
   * shortest path to goal state is the direct path

# Performance Guarantees for A* 
* Optimality of A* : n is on the optimal path
 * Terminology
  * f* is the cost of the optimal solution path
  * f* <= f(n) because the heuristic is admissible
 * All good states have h(n) = 0
 * Proof by Contradiction
<img width="469" alt="image" src="https://github.com/user-attachments/assets/489499dd-15a3-4d68-8532-faa1952bb10f" />
* Optimally Efficient : does enough work to find global optimum but no more unecessary work
 * expands no node with f(n) > f*
* Best admissible heuristic under-estimates the least
 * heuristic that dominates another is guaranteed to do less work 

# Data Strcuture Guarantees when using A*, why?
* Consistent heuristic guaranteed to be admissible
* A* double edged sword : for most problems the size of open-fringe will be exponential to path cost
 * shortest path problem is intractable

g(n) - The *actual* cost of going from the start state to state n
h(n) - The under-estimate of the cost of going from state n to the goal state.

h*(n) - The *actual* cost of going from state n to the goal state, hence h(n) <= h*(n)
c(n,n') - The actual cost of going from state n to n', note this is the incremental cost
f(n) = g(n) + h(n) - the cost of going from the start state to state n and then the under-estimate of going from n to the goal state
f*/C* the optimum cost of going from the start state to the goal state.
