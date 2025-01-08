* Problem-Solving Agent
  * Atomic Representations : states of the world considered as wholes with no internal structure
* Goal-Based (Planning) Agent : use factored or structured representations
* Uninformed Search : algorithm given no information about the problem other than definition
* Informed Search : algorithm given guidance on where to look for solutions 

# Prolem Solving Agents
* Goal : set of world states
  * Goal Formulation : based on current situation and agent's performance
* Problem Formulation : process of decidin what actions and states to consider given a goal
* Unkown Environment : no additional information for agent, must take action at random
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
* Complete-State Formulation : start with all 8 queens on the board and move them aroudn

## Real World Problems 
* Route Finding Problen : defined in terms of specificed locations and transitions laong links between them
* Airline Travel Problem
![image](https://github.com/user-attachments/assets/a629a711-8b81-404c-be13-d5c97f12bb78)
* Touring Problems : route-finding problems but all nodes must be visited by the time the goal node is reached
  * Traveling Salesperson Problem : each city (node) must be visited exactly once - find the shortest tour
* VSLI Layout Problem : positinoing millinos of components and connections on a chip to minimize area, circuit delays, stray capacitances and maximize manufacturing yield
  * Cell Layout : primitive components of the circuit are grouped into cells each with recognized function
  * Channel Routing : find specific route for each wire through the caps between cells
* Robot Navigation : route-finding problem with a continuous space of movement and an infiite set of possible actions and states
* Automatic Assembly Sequencing : aim to find an order to assemble partsof some object and if the wrong order is chosen there is no way to add a part later without undoing work already done 

# Searching for Solutions 
* Search Tree : posible actions seuqneces starting at the initial state
  * Nodes : states
  * Branches : actions 
* Expand current state by applying each legal action to generate new set of states
* Frontier (Open List) : set of all leaf nodes available for expansion 
  * Leaf Node : node with no children
* PAGE 75
