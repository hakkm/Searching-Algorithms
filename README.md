> [!NOTE]
> This is a note for the course [CS50's Introduction to Artificial Intelligence with Python, Lecture 0: Search](https://www.youtube.com/watch?v=WbzNRTTrX0g).
# Solving Search Problems 

## Terminology

- **Agent**: Entity that perceives its environment and acts upon that environment. i.e. a robot, a computer program, etc.
- **State**: A configuration of the agent and its environment. i.e. the robot's location and its battery level, the chess board and the pieces on it, etc.
- **Initial State**: The state in which the agent begins.
- **Actions**: Choices that can be made in a state. i.e. moving left, moving right, etc. 
    - **ACTIONS(s)**: The set of actions that can be executed in state s.
- **Transition Model**: A description of what state results from performing any applicable action in any state. i.e. if the agent is in state s and performs action a, the agent will transition to state s'.
    - **RESULT(s, a)**: The state resulting from performing action a in state s.
- **State Space**: The set of all states reachable from the initial state by any sequence of actions.
- **Goal Test**: Way to determine if a given state is a goal state.
- **Path Cost**: Numerical cost associated with a given path. i.e. the number of steps taken, the amount of time elapsed, etc.

### Problem Formulation

- **Initial State**: Where the agent begins.
- **Actions**: Choices that can be made in a state.
- **Transition Model**: A description of what state results from performing any applicable action in any state.
- **Goal Test**: Way to determine if a given state is a goal state.
- **Path Cost**: Numerical cost associated with a given path.

### Solution 

- **Solution**: A sequence of actions that leads from the initial state to a goal state.
- **Optimal Solution**: A solution that has the lowest path cost among all solutions.

### Node 

To package up all of this information together, we'll use a **node**. A node consists of:

- A state
- A parent node (the node that generated this node)
- An action (the action applied to the parent to get this node)
- A path cost (the cost to reach this node)

## Approach

What is a frontier? A frontier is a data structure that stores all of the paths that we have yet to explore.
- Start with a frontier that contains the initial state 
- Repeat:
    - If the frontier is empty, then no solution
    - Remove a node from the frontier
    - If node contains goal state, return the solution
    - Expand node, add resulting nodes to the frontier

Problem: Arrow in both directions means that we can go back and forth between the two states. How do we avoid going back and forth between two states?
Solution: **Explored Set**. An explored set is a set of states that we have visited. If a state is in the explored set, we will not visit it again.

## Revised Approach

- Start with a frontier that contains the initial state 
- Start with an empty explored set
- Repeat:
    - If the frontier is empty, then no solution 
    - Remove a node from the frontier
    - If node contains goal state, return the solution 
    - Add the state to the explored set 
    - Expand node, add resulting nodes to the frontier if they aren't already in the frontier or the explored set

Problem: How do we decide which node to remove from the frontier?
Solution: Treate the frontier as a Stack or Queue. **Stack**: Last In First Out (LIFO), This version of the algorithm is called **Depth-first search**. **Queue**: First In First Out (FIFO), This version of the algorithm is called **Breadth-first search**.

## Types of Search Algorithms
### Uninformed Search 
Search strategies that use no problem-specific knowledge.

### Informed Search 
Search strategies that use problem-specific knowledge to find solutions more efficiently.

#### Greedy Best-First Search 
Search algorithm that expands the node that is closest to the goal, as estimated by a heuristic function h(n).

What is a heuristic function? A heuristic function, h(n), provides an estimate of the cost from any node n to the goal.

#### A* Search 
Search algorithm that expands node with lowest value of g(n) + h(n). 

g(n) =  is the cost to reach the node.
h(n) = is the estimated cost to the goal from node n.
f(n) = g(n) + h(n)




