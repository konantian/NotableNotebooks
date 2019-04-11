---
title: Lecture 7 Search and Knowledge(1)
tags: [Notebooks/Cmput 496]
created: '2019-04-11T01:59:43.745Z'
modified: '2019-04-11T04:30:10.644Z'
---

# Lecture 7 Search and Knowledge(1)

## Blind search VS Heuristic Search
### Blind search
  * No extra information that helps us search.
  * We assume only that we recognize goal states when we visit them
  * Blind search algorithms:
    * Complete Search(They find the treasure if it is here,and visit each node exactly once)如果存在一条路径到达goal，那么complete search保证可以到达这个goal
      1. Depth-first seardh
      2. Breadth-first search
    * Incomplete search
      3. Random Sampling
  * Blind Treasure Search
    * Algorithms does not matter
    * Shape of state space does not matter

### Heuristic Search
  * Advantage
    1. They help guide the search through a state space
    2. Following heuristic is often much better than blind search
  * Forms of heuristics
    1. State evaluation
    2. Moving ordering in games
    3. Evaluate moves, not states
    4. Reducing branching factor and depth of search
  * When do we need?
    1. Huge state space(可以减少大量搜索时间，不过还远不及perfect)

  * Search methods
    1. Search algorithm
      * Systematically look ahead into the future
    2. Heuristic evaluation
      * How good is a state or an action
    3. Simulation
      * look ahead into the future by sampling sequences of future states

  * Heuristic Evaluation Single Agent Search
    1. h(s) estimates the distance form s to a goal
    2. h(s) = 0 if it is a goal, h(s) > 0 if it is not a goal

  * Heuristic VS Explore(Balance between exploitation and exploration)
    1. Follow heuristic when it works well
    2. Do not trust heurisitc blindly
    3. Use exploration when stuck or heuristic is misleading
    4. Always use some exploration

    
