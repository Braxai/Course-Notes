Divisive Cost Function 
* self.cost_function = lambda h0, h1: (1 + math.pow(h0-h1,2))
  * problem : going up and down costs the same

A* implemented correctly will give the same answer as Dijkstras

Dijkstras = A* with h(n) = 0

Admissible Heuristic must always be positive 

* Best Admissible Heuristic : h(n) = h*(n) where h*(n) is the true value of going from node to goal state
* Worst Admissible Heuristic : Dijkstra h(n) = 0
    * Want to be underestimating but as close to h*(n) as possible

Exponential COst Function
* self.cost_function = lambda h0, h1: math.pow(math.e, h1-h0)
    * cost of going up is more than going down

Use Cases Exercise -- DRAW PICTURES
* Same Height : h<sub>n</sub> = h<sub>g</sub>
    * best possible terrain, use that to determine admissible heuristic 
* Lower Height : h<sub>n</sub> < h<sub>g</sub>
* Greater Height : h<sub>n</sub> > h<sub>g</sub>

If you can't think of admissible heuristic for a use case just use 0

With multiple heuristics for a single use case you can take the max of them to utilize the best one

Given Dijkstras : convert graph search to tree search

How to make A* faster 
* Change data structures
* Bidirectional search
    * run goal to start and start to goal
* Successor Function
    * way points : break into smaller problems 
