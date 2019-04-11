---
title: Lecture 10 - Search and Knowledge(4)
tags: [Notebooks/Cmput 496]
created: '2019-04-11T04:29:41.303Z'
modified: '2019-04-11T19:03:36.148Z'
---

# Lecture 10 - Search and Knowledge(4)
### Principle Variation(PV)
  * If both players play best moves, they follow a principal variation or PV of the search
  * This is a move sequence with the property that each node in the sequence has a score of m
  * **Still exist** in depth-limited search and heuristic evaluation
  * If both player follow their proof, they will play out a PV
  * Assume both players follow a move sequence S, such that for all nodes along that sequence the minimax score is m: Then there exist two proof trees:
    1. P1 for max
    2. P2 for min

### Minimax Search Enhancements
  1. Hashing to cache search result
    * Store game positions and its search information
  2. Transposition table
  3. Iterative deepening and move ordering
    * Search with depth limit of 1,2,3...
  4. History heuristic
    * Keep track of which moves are effective in causing beta cuts in the search
    * Give a bonus for those moves, try them earlier among all children

### State Spaces of TicTacToe
  1. Tree: estimate is exact at depth 0 ... 5
  2. DAG: No savings at lower levels
  3. Massive saving deeper in DAG

### Sumary
**Heurisitc search**
> Play as well as possible when time limit is given. Most work on MCTS is on heuristic search, play well.

**Solve**
> With unlimited time, eventually find the perfect play minmax solution. 

