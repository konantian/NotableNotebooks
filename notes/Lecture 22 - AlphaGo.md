---
title: Lecture 22 - AlphaGo
tags: [Notebooks/Cmput 496]
created: '2019-04-13T04:17:45.590Z'
modified: '2019-04-13T05:12:25.854Z'
---

# Lecture 22 - AlphaGo
### Deepmind and AlphaGo
  * Massive advance in playing strength of Go programs
  * Before AlphaGo, programs about 3 levels below best human
  * AlphaGo/Alpha Zero: far surpassed human skill in Go
  * AlphaGo is retired

### AlphaGo Fan
#### Design
  * Search: MCTS, modified UCT combines simulation result and value network evaluation
  * Simulation policy: relatively normal 
    * Uses small, fast network for policy
  * Supervised learning policy network
  * Strong RL policy network, Value network,

#### Rollout policy network
  * Used for simulations in MCTS
  * Designed to be simple and fast
  * Linear softmax of small pattern features
  * Probabilistic move selection
  * Weights trained by RL instead of MM

#### Architecture
  * Networks: SL policy network, RL policy network, RL value network
  * 13-layer deep CNN
  * Small overall design for all three

#### Value network
  * Learn a state evaluation function
  * Given a Go position, computes probability of winning
  * **No search and no simulations**
  * Learn mapping from state s to expected outcome $\mathbb{E}[z]$ of the game
  * Network architecture mostly same as policy nets
  * Value net outputs single number : evaluation of s
  * Policy nets output probability distribution

#### Training pipeline
  * Supervised learning 
    * Rollout policy
    * SL policy network
      * Maximize likelihood of human move
      * Small improvements in accuracy led to large improvements in playing strength
      * MCTS with this network is already much better than all previous Go programs
  * Reinforcement learning
    * RL policy network
      * Learns from self play
      * adjust weights of net to learn from winner of each game
      * Exact same network architecture as SL net
      * keeps a pool of previous networks as opponents to avoid overfitting
    * Value network


