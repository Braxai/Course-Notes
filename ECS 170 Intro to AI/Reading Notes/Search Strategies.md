## Uninformed Search Strategies 
* Uninformed Search (blind search) : strategies have no additional information about state sbeyong that provided in the problem definition.
* Informed Search (heuristic search) : strategies that know whether one non-goal state is more promissing than another

### Breadth-First Search 
* BFS : root node expanded then all sucessors of root expanded, then their successors and so on.
    * Shallowest unexpanded node chosen
    * Queue for frontier
![image](https://github.com/user-attachments/assets/6743134e-60cd-412f-95e8-ee9fb864bc37)

### Uniform-Cost Search (Dijkstras)
* Expand node n with lowest path cost g(n)
    * Priority Queue for frontier 
    * If all step costs are the same UCS is the same as BFS
![image](https://github.com/user-attachments/assets/44cae31e-87e0-493f-8298-c81f23d74e64)

### Depth-First Search
* Expands deepest node in frontier
    * Stack for frontier
* Backtracking Search : only one successor generated at a time rather than all successors
    * partially expanded nodes remember which successor to generate next
    * Memory saving

### Depth-Limited Search 
* DFS with predetermined depth limit l
    * solves DFS Problem in infinite state spaces 
![image](https://github.com/user-attachments/assets/9580e217-5e5f-478c-8118-8798e433e1eb)
* Diamater of state space : number of steps to reach any node from any other node, good choice for limiting depth if known

### Iterative Deepening Depth-First Search 
* DFS that finds the best depth limit by gradually increasing the limit from 0 up until a goal is found
![image](https://github.com/user-attachments/assets/20be2977-b1fd-40a5-a56b-c15fa14e1d6c)
* Preferred uninformed search method when the search space is large and the depth of the solution is not known
* Iterative Lengthening Search : UCS using increasing path-cost limits
    * substantial overhead compared to UCS

### Bidirectional Search
* Run two simultaneous searched : one forward from the initial state and the other backward from the goal hoping the two searches meet in the middle
    * Replaces goal test with check to see if the frontiers of the two searches intersect, if they do a solution has been found
* Requires method for computing predecessors
    * predecessors of a state x are all the states that have x as a successor 

### C0mparing Uninformed Search Strategies 
![image](https://github.com/user-attachments/assets/abe92cc6-65e0-4d55-a5d4-7cbc21d168a0)

## Informed (Heuristic) Search Strategies 
### Greedy Best-First Search 

### A* Search: Minimizing the Total Estimated Solution Cost 

### Memory-Bounded Heuristic Search 

### Learning to Search Better 

## Heuristic Functions 

### The Effect of Heuristic Accuracy on Performance 

### Generating Admissible Heuristics from Relaxed Problems 

### Generating Admissible Heuristics from Subproblems: Patern Databases 

### Learning HEuristics from Experience 

