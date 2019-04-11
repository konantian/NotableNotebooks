---
title: Lecture 5 Sequential decision-making Review
tags: [Notebooks/Cmput 496]
created: '2019-04-10T21:39:58.175Z'
modified: '2019-04-10T22:58:08.635Z'
---

# Lecture 5 Sequential decision-making Review
## Decrease branching factor b
### Use symmetry
  * Symmetries at level 1
    * After cornor or edge: 5 distinct cases
    * After center: 2 distinct cases
  * Most symmetries broken after few moves
  * Good reduction at depth 1 or 2 and symmetry breaks. Almost no reduction deeper in the tree
### DAG
  * Single node for **all equivalent states**
  * Can lead to huge reduction in state space, since the whole subtree below is no longer duplicated
  * Avoid redundant computations
  * Share results of analysis - compute once, re-use often
  ![](https://ws3.sinaimg.cn/large/006tNc79ly1g1yabi7ny8j30cm0neq7o.jpg =150x150)
  * Limitations:
    1. Need memory to store and recognize equivalent states
    2. Some algorithms designed only for trees, not for DAGs
    3. States with different history cannot merge into one node cause not equivalent
    4. Propagating information up towards root could be inefficient, since many paths lead to a same node

  * $b^d$ Model and DAG
    * No longer a constant b for whole DAG
    * Can compute $b_d$ at depth d as:
    ![](https://ws1.sinaimg.cn/large/006tNc79ly1g1yb10gktuj30ic03m3yy.jpg)
    * Checkers: $b\approx2.8$
    * Chess: $b\approx35$
    * Shogi: $b\approx92$

### Decision making
  * We need to look ahead to future states in order to make a good decision now
  * We need to consider sequences of actions, until we reach a terminal state
  * Evaluate different options and choose the best-looking one
