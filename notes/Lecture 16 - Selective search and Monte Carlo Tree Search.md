---
title: Lecture 16 - Selective search and Monte Carlo Tree Search
tags: [Notebooks/Cmput 496]
created: '2019-03-24T17:01:46.941Z'
modified: '2019-04-12T05:37:41.804Z'
---

# Lecture 16 - Selective search and Monte Carlo Tree Search
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
  ![](https://ws3.sinaimg.cn/large/006tNc79ly1g1yjyqypylj311g0keqco.jpg =400x400)

**Efficient minimax(or negamx)**
  * Does not visit the whole tree, some parts of the tree may be cut(剪枝一些不好的move)
  * Best case: visit only one child for winner(只要能找到一个最好的child就能赢)
  * Need to try all moves for loser(必须探索所有的child来验证lose)
  * Back up result to root node
    * For alphabeta, some back-up values are “good-enough” upper or lower bounds, not exact values
  ![](https://ws3.sinaimg.cn/large/006tNc79ly1g1yjz6dq2tj314a0n2gxc.jpg =400x400)

### Selective Search Solver
**Depth-limited Alphabeta Search**
  * Similiar with alphabeta, prune some bad moves but until the depth limit
  * Backup result to root node
    * Min and Max
  * Selective search, exact evaluation of leaves node(evaluation来自于最后一层可以到达的node)
  * Source of error:
    1. Source of error: heuristic evaluation in leaf nodes
  ![](https://ws4.sinaimg.cn/large/006tNc79ly1g1yjzgw0gfj313a0i611f.jpg =400x400)

**Selective Alphabeta Search with Fixed Time or Node Budget**
  * **Reduce b and d until search fits within budget**

**Selective Alphabeta Search**
  * Does not consider all legal moves of each node, similiar with depth-limited
  * Backup result to root node
    * Min and Max
  * Search “interesting” moves much deeper than others
  * Source of error:
    1. Source of error: heuristic evaluation in leaf nodes
    2. may prune the best move from a node --- **MCTS was the first approach that worked well that keep best move**
  ![](https://ws4.sinaimg.cn/large/006tNc79ly1g1yk011j04j30ze0majzf.jpg =400x400)

**Simulation-Based Player**
  * as Selective Minimax Search
    * Extreme case of selective search
    * Simulation-based player with one simulation per move
    * Branching factor b at root and 1 at all later levels(每层只有一个move候选)
  * Repeated sampling
    * Eventually samples all nodes in the full tree infinitely often
    * With selective policy samples some subtree infinitely often
  * Uniform Random Simulation policy
    * **Selective search**
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

  * Simple VS UCB move selection
    * UCB take average over more simulations for good move
    * UCB take fewer simulations for bad move
    * Simple just average over all simulations
    * UCB selectes move with most-simulated
    * Simple selected move with highest winrate

## Monte Carlo Tree Search
### Model
  1. **Selection** - traverse existing tree using formula such as UCT to select a child in each node
    * Much deeper search for moves with better win rates
    * Run as many iterations of MCTS as you can
    * Then select move to play at root
    * Select child
      * Child with highest number of wins(not stable,有的时候较差的move由于simulation的次数不够，导致胜率比相对更好的move高)
      * Child with most visited
  2. **Expansion** - add nodes to tree
    * Add one node per iteration
    * Paths with strong moves become much deeper than others(有好的move的路径会探索更多，不好的move的路径探索相对更少)
  3. **Simulation** - follow randomized policy to end of game
    * Using any simulation policy, uniform random, rule_based, probabilistic
    * Result can only be 1(win) or 0(lose)
    * Can run more than one simulation from each leaf node
  4. **Backpropagation** - update winrate along path to root
    * Update wins and visit counts along path to root(在到达leaf node以后，更新这条路径上所有的node的count)
    * Flip wins/loses at each step
  5. **Extending Search**
    * Extending search if highest winrate move is different with most visited move
    * If B is really good then it will receives many more simulations soon(好的move会导致更多的visit)
    * If B is is a bad move, it's winrate and upper confidence bound will drop quickly with more simulations(不好的move随着simulation的增加，胜率不断稳定，最终开始下降)


### UCT algorithms Main ideas
  * Combines tree search with simulations
  * Uses results of simulations to guide growth of the game tree
  * Uses UCB-like rule to select "best" child of a tree node
  * Select a good path in the tree to explore/exploit next
  * Stores winrate statistics in each node, used for child selection

### From UCB to UCT
  * UCB: uses **global count** of all simulations N
  * UCT: uses **simulaiton count** of parent $n_p$
  * For root, UCT is identical to UCB(分母都是1，而且只有root一个node)
  $U C T(i)=\hat{\mu}_{i}+C \sqrt{\frac{\log n_p}{n_i}}$


