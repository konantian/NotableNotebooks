---
title: Lecture 24 - Alpha Zero Approach
tags: [Notebooks/Cmput 496]
created: '2019-04-14T00:29:54.234Z'
modified: '2019-04-14T19:03:04.088Z'
---

# Lecture 24 - Alpha Zero Approach
#### Alpha Zero Approach
  * Same as in AlphaGo Zero:
    * Two-head deep network, with policy and value heads
    * $(p, v) = f_{\theta}(s)$
    * MCTS for learning from self-play and for playing
  * Difference
    * Learns expected outcome instead of winning probability
    * There is no board symmetries in chess and shoji
    * Learns by continuous updates to a single network, in AlphaGo learned its networks in generations
  * Generalizes work on Go to other classical board games
  * Stronger than other top chess and shogi programs


#### Game theory Background
  * In perfect information games, solving a games includes
    1. Computing its minimax value
    2. Finding a winning strategy
    3. Strategy includes one move at OR nodes, all moves at AND nodes
  * Imperfect information games:
    1. For games with more than two players, there is no analog to minimax value
    2. The most important general concept is the Nash equilibrium
    3. A player's strategy in general needs to be mixed

#### Stragegies
  * Pure strategy: In the same state, always choose the same action
    * needed in complete information games
  * Mix strategy: choose action according to a probability distribution
    * Needed in imperfect information games
    * we want to avoid being predictable and being exploited by the opponent
  * Probabilistic simulation
    * We want to sample from a huge game tree, get better exploration

