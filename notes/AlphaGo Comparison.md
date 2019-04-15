---
title: AlphaGo Comparison
tags: [Notebooks/Cmput 496]
created: '2019-04-15T05:16:06.916Z'
modified: '2019-04-15T05:44:34.263Z'
---

# AlphaGo Comparison
## Alpha Fan
**Search**
   * MCTS(parallel MCTS)
   * Modified UCT combines simulation result and value network evaluation

**Simulations(rollout policy)**
  * uses small,fast network for policy
  * probabilistic move selection
  * weights trained by RL instead of MM
  * Slightly larger patterns features
  * linear softmax of small pattern features
  * designed to be simple and fast

**Supervised learning policy network**
  * DCNN
  * Learns move prediction from master games
  * more data

**Network Architecture**
  * SL policy network(new)
    * Maximize likelihood of human move
    * MCTS with this network is already much better than all previous 
    Go programs
    * learns from labeled game data created by strong RL policy
  * RL policy network
    * learning for training DCNN policy net
    * Learns from self play
    * adjust weights of net to learn from winner of each game
    * keeps a pool of previous networks as opponents to avoid overfitting
  * RL value network(new)
    * state evalution
    * Given position in Go, computes probability of winning
    * No search no simulations
    * Learns mapping from state s to expected outcome of the game
    * Value net outputs single number:evaluation of s
  * Same overall design for three

