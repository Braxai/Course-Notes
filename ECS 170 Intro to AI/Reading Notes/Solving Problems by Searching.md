* Problem-Solving Agent
  * Atomic Representations : states of the world considered as wholes with no internal structure
* Goal-Based (Planning) Agent : use factored or structured representations
* Uninformed Search : algorithm given no information about the problem other than definition
* Informed Search : algorithm given guidance on where to look for solutions 

# Prolem Solving Agents
* Goal : set of world states
  * Goal Formulation : based on current situation and agent's performance
* Problem Formulation : process of deciding what actions and states to consider given a goal
* Unknown Environment : no additional information for agent, must take action at random
* Assumptions about the Environment 
  * Observable : agent knows the current state
  * Discrete : finite actions to choose at any given state
  * Known : agent knows which states are reached by each action
  * Deterministic : each action has exactly one outcome 
* Search : process of looking for a sequence of actions that reaches the goal
  * Solution : action sequence that achieves goal returned by search
  * Execution : actions found by search are carried out
  * Formulate, search, execute
* Open-Loop System : ignoring precepts breaks the loop between agent and environment

![image](https://github.com/user-attachments/assets/427927bf-f485-4e44-b99f-72d26d396dc1)

## Well Defined Problems and Solutions 
* Problem
  * Initial State
  * Actions Available to agent
    * Action is applicable in s if it can be done from state s
  * Transition Model : description of what each action does
  * State Space : implicitly defined by inital state, actions, and transition model
    * Forms a graph : directed network in which nodes are states and links between nodes are actions
    * Path : sequence of states connected by sequence of actions
  * Goal Test : determines whether a given state is a goal state
  * Path Cost : Function that assigns a numeric cost to each path  

## Formulating Problems 
* Abstractino : process of removing detail from a representation 

# Example Problems 
* Toy Problem : illustrates varius problem solving methods given concise, exact description
* Real-World Problem : meaningful solutions people care about 

## Toy Problems 
* Vacuum World
![image](https://github.com/user-attachments/assets/651d1fb0-d744-4a05-9976-a9766ead214a)
![image](https://github.com/user-attachments/assets/bcfc2dac-9a55-4ca2-9bef- (153b6e903463)

* 8-Puzzle : sliding-block puzzle (NP-Complete)
![image](https://github.com/user-attachments/assets/89016c19-5558-4f3e-a797-77d041423b28)

* 8-Queens : place 8 queens on chessboard so none are attacked by the others
![image](https://github.com/user-attachments/assets/07ba3e7b-8b88-45f6-a267-a091cd0c4c50)
* Incremental Formulation : operators augment the state description starting with an empty state
* Complete-State Formulation : start with all 8 queens on the board and move them around

## Real World Problems 
* Route Finding Problem : defined in terms of specificed locations and transitions along links between them
* Airline Travel Problem
![image](https://github.com/user-attachments/assets/a629a711-8b81-404c-be13-d5c97f12bb78)
* Touring Problems : route-finding problems but all nodes must be visited by the time the goal node is reached
  * Traveling Salesperson Problem : each city (node) must be visited exactly once - find the shortest tour
* VSLI Layout Problem : positinoing millions of components and connections on a chip to minimize area, circuit delays, stray capacitances and maximize manufacturing yield
  * Cell Layout : primitive components of the circuit are grouped into cells each with recognized function
  * Channel Routing : find specific route for each wire through the caps between cells
* Robot Navigation : route-finding problem with a continuous space of movement and an infiite set of possible actions and states
* Automatic Assembly Sequencing : aim to find an order to assemble parts of some object and if the wrong order is chosen there is no way to add a part later without undoing work already done 

# Searching for Solutions 
* Search Tree : possible action sequences starting at the initial state
  * Nodes : states
  * Branches : actions 
* Expand current state by applying each legal action to generate new set of states
* Frontier (Open List) : set of all leaf nodes available for expansion 
  * Leaf Node : node with no children
* Search Strategy : how a search algorithm chooses which state to expand next
* Repeated State : commonly generateed by loopy paths
* Redundant Paths : exist whenever there is more than one way to get from one state to another
  * No reason to keep more than one path to any given state if only concerned about reaching the goal

![image](https://github.com/user-attachments/assets/399e4d3e-e8c0-4b1f-a2f3-262a00a6cd52)

![image](https://github.com/user-attachments/assets/9e186048-453f-48e8-9186-70d27cc4d7eb)

* Rectangular grid Route Finding : each state has four successors so a search tree of depth d that includes repeated states has 4<sup>d</sup> leaves
* Explored Set (Closed List) : search algorithm data structure that remembers every expanded node
  * Discard newly generated nodes that match a node in the explored set

![image](https://github.com/user-attachments/assets/a72737eb-d157-40a5-b20d-e8ceb02e1ae0)

## Infrastructure for Search Algorithms 
* Structure contains four components
  * n.STATE : the state in the state space to which the node corresponds
  * n.PARENT : the node in the search tree that generated this node
  * n.ACTION : the action that was applied to the parent to generate the node
  * n.PATH-COST : the cost, traditinoally denoted by g(n), of the path from the initial state to the node, as indicated by the parent pointers
 
![image](https://github.com/user-attachments/assets/302cbe4c-8a00-4a4d-9fa9-92f1f050f29f)

Funciton CHILD-NODE takes a parent node and an action and returns the resulting child node 

![image](https://github.com/user-attachments/assets/5c390eaa-5335-4217-8192-03564f0b52e7)

* Frontier stored in a queue that has functions empty, pop, and insert
  * Queue : FIFO
  * Stack : LIFO
  * Priority Queue : pops element with highest priority
 
## Measuring Problem-Solving Performance 
* Completeness : is the algorithm guaranteed to find a solution when there is one?
* Optimally : does the strategy find the optimal solution?
* Time Complexity : how long does it take to find a solution?
* Space Complexity : how much memory is needed to perform the search

* Complexity expressed in terms of three quantities
  * b (branching factor) : maximum number of successors of any node
  * d (depth) : depth of shallowest goal node (number of steps along the path from the root
  * m : maximum length of any path in the state space
* Search Cost : typically depends on time complexity but can also include a term for memory usage
* Total Cost : combines search cost and path cost of the solution found 
