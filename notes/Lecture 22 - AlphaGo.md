---
title: Lecture 22 - AlphaGo
tags: [Notebooks/Cmput 496]
created: '2019-04-13T04:17:45.590Z'
modified: '2019-04-13T22:34:22.379Z'
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
      * **Exact same network architecture as SL net**
      * keeps a pool of previous networks as opponents to avoid overfitting
      * No search, only one call to network
      * Play move by sampling from $p_p$
    * Value network
      * Value net computes a function $v_{\theta}(s)$
      * Input state s and output a single real number
      * Training: minimize squared error between value net prediction and true game outcome
      $\text { Squared error }=\sum_{i}\left(v_{\theta}\left(s_{i}\right)-z_{i}\right)^{2}$
      * Training data:
        1. Randomly sample one single state s from each game
        2. Label s with the outcome z of the game
        3. Learn the value net by trying to predict z i from s
    
#### MCTS in AlphaGo Fan
  * Neural nets used as in-tree knowledge
    * Policy net guides tree search
    * Vallue net helps evaluate leaf nodes
  * Maximize Q + u
    * Winrate Q is exploitation term
    * u is exploration term
    * Decay by $u=C \frac{P}{1+N}$
    * Exploration constant C

#### Computing V($s_L$)
  * Value estimate V($s_L$) of leaf nodes $s_L$
  * V($s_L$) is weighted average of two different evaluations
  * $v_{\theta}\left(s_{L}\right)=$ Value network evaluation of $s_L$
  * $z_L=$ win/loss result of single simulation from $s_L$
  * Combined by $V\left(s_{L}\right)=(1-\lambda) v_{\theta}\left(s_{L}\right)+\lambda z_{L}$
    * $\lambda=0.5$ equal weight

#### SL vs RL policy network in MCTS 
  * Search with RL policy was too narrow
  * Quality of other candidate moves not as good as in SL network
  * SL net worked better in MCTS, even though it is much weaker in move prediction
  * SL net gave a better set of good moves to search, not just a single strong move
  * This problem is already solved in Alphago Zero

#### Summary
  * AlphagoFan : MCTS + neural networks for knowledge
  * Policy net for biasing in-tree move selection
  * Value net plus simulations for evaluating leaf nodes in tree
  


