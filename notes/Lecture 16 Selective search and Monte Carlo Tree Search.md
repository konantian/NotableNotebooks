---
title: Lecture 16 Selective search and Monte Carlo Tree Search
tags: [Notebooks/Cmput 496]
created: '2019-03-24T17:01:46.941Z'
modified: '2019-03-24T17:57:07.730Z'
---

# Lecture 16 Selective search and Monte Carlo Tree Search
## Exact Search, Selective Search, and Simulations
### Exact Search Solver
**Naive Minimax (or Negamax)**
  * Explores the whole tree(所有的node都会被探索)
  * Backup result to root node
    * minimax: Minimum over children at min nodes, maximum at max nodes
    * negamax: max(a,b) = -min(-a,-b)
  * Terminal nodes are true end-of-game
  * Use only exact scores at terminal nodes for evaluation
  * Result is proven correct
  ![Naive Minimax](@attachment/cmput496/naive_minimax.png)

**Efficient minimax(or negamx)**
  * Does not visit the whole tree, some parts of the tree may be cut(剪枝一些不好的move)
  * Best case: visit only one child for winner(只要能找到一个最好的child就能赢)
  * Need to try all moves for loser(必须探索所有的child来验证lose)
  * Back up result to root node
    * For alphabeta, some back-up values are “good-enough” upper or lower bounds, not exact values
  ![Naive Minimax](@attachment/cmput496/efficient_minimax.png)

### Selective Search Solver
**Depth-limited Alphabeta Search**
  * Similiar with alphabeta, prune some bad moves but until the depth limit
  * Backup result to root node
    * Min and Max
  * Selective search, exact evaluation of leaves node(evaluation来自于最后一层可以到达的node)
  * Source of error:
    1. Source of error: heuristic evaluation in leaf nodes
  ![Naive Minimax](@attachment/cmput496/depth_limit.png)

**Selective Alphabeta Search with Fixed Time or Node Budget**
  * Reduce b and d until search fits within budget

**Selective Alphabeta Search**
  * Does not consider all legal moves of each node, similiar with depth-limited
  * Backup result to root node
    * Min and Max
  * Search “interesting” moves much deeper than others
  * Source of error:
    1. Source of error: heuristic evaluation in leaf nodes
    2. may prune the best move from a node 
  ![Naive Minimax](@attachment/cmput496/selective_alphabeta.png)

**Simulation-Based Player**
  * as Selective Minimax Search**
    * Extreme case of selective search
    * Simulation-based player with one simulation per move
    * Branching factor b at root and 1 at all later levels(每层只有一个move候选)
  * Repeated sampling
    * Eventually samples all nodes in the full tree infinitely often
    * With selective policy samples some subtree infinitely often
  * Uniform Random Simulation policy
    * Eventually all nodes will be visited
    * Backup result to root node
      * Max at root only
      * Average over all simulations
    * Source of error:
      1. bias, average may be far from min, max(更多sample无法减少bias)
      2. variance, large uncertainty with small number samples(更多sample可以减少variance)
  * Non-unifrom simulation policy
      * Visit all nodes except subtree below moves that are never selected
      * Backup result to the root node
        * 1-ply max + average over simulations, same with uniform random
      * Average over better samples may be closer to min, max
      * Source of errors
        1. can miss totally by hard-pruning all good moves
    


