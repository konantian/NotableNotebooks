---
title: Lecture 23 - AlphaGo Zero
tags: [Notebooks/Cmput 496]
created: '2019-04-13T22:42:18.254Z'
modified: '2019-04-14T00:10:31.848Z'
---

# Lecture 23 - AlphaGo Zero

#### Introduction
  * Mastering the game of Go without human knowledge
  * New simplified architecture
  * Learns entirely from self-play
  * No human knowledge beyond the basics such as rules of game
  * New network architecture:
    1. Resnets
    2. combine policy and values nets into one net with two "heads"
  * Strong performance on "one machine"

#### Search
  * Still MCTS
  * Usage
    * Learning(new)
    * Playing
  * Searched is used to improve learning and learning in turn improves search

#### Knowledge
  * All knowledge created by machine learning from self-play
  * Knowledge represented by deep residual neural net
  * combine policy and values nets into one net with two "heads
    * Policy head: learns good moves for the search
    * Value head: Learns evaluation function - probability of winning
  * Both move and position evaluation learned together
  * No more simulations to end of the game
    * MCTS tree growth controlled only by neural net knowledge

#### Resnet
  * Main idea:pass output of previous block directly through
  * Each block learns a "Delta", a small change to previous output
  * Can train really deep nets efficiently
  * In practice learns better than DCNN
  * Two head architecture
  ![](https://ws3.sinaimg.cn/large/006tNc79ly1g21s7tpj6pj30c20asgnr.jpg =150x150)
  $(p, v)=f_{\theta}(s)$, Input Go position s, Network weights $\theta$
  By function $f_{\theta}(s)$, has two outputs(p,v)
    1. policy head: vector of move probabilities p(s,a) for each move a
      * Learns to predict what the search would do
      * How frequently shoudl each move be tried in MCTS
      * Goal:Minimize cross-entropy between Predicted probability of move and Frequency of move as selected by MCTS
      * Cross-entropy: measures how well one probability distribution can predict another
    2. value head: value of s
      * Given a Go position
      * Compute probability of winning
      * Static evaluation function
      * Trained from self-play
      * Goal: minimize squared error between predicted value v and final result z of games

#### MCTS
  * Move selection
    * ![](https://ws1.sinaimg.cn/large/006tNc79ly1g21sk7ahm6j30aa0de75m.jpg =200x200)
    * Value of simulation ending in in-tree state s = value head evalutoin of s
    * No more simulation beyond the tree, no more evaluation component from rollouts
  * Evaluation
    * ![](https://ws4.sinaimg.cn/large/006tNc79ly1g21slu2mz5j30ci0cuq4m.jpg =200x200)
    * Node s expanded
    * Single cell to neural net
    * $(p, v) = f_{\theta}(s)$
  * Training
    * Error measured by loss function
      1. Error of policy head(cross entropy)
      2. Error of value head
      3. Regularization term to keep size of weights in check 

#### Self-play Games
  * play whoel game
  * For each state $s_t$ in game:
    1. Run MCTS on $s_t$
    2. Sample move to play according to number of simulations it received
  * Finish game get outcome z(win = 1 or loss = -1)
  * State tuples($s_t,\pi_{t},z_t$) for learning after end of game
    * $s_t$ = state at time step _t_
    * Game = sequence of states $s_1,s_2,...$
    * $\pi_{t}$ = probability distribution derived from visit count of moves in MCTS of $s_t$
    * $z_t$ = result from current player's point of view(z or -z, negamax)
  * Learing from self-play games
    * For each game we randomly sample tuples ($s_t,\pi_{t},z_t$) from all tuples stroed from the game
    * Adjust net weight $\theta$ by gradient descent
    * $(p, v) = f_{\theta}(s)$
    * Make policy _p_ better match $\pi$
    * Make value _v_ better match $z$






