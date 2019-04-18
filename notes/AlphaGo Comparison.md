---
title: AlphaGo Comparison
tags: [Notebooks/Cmput 496]
created: '2019-04-15T05:16:06.916Z'
modified: '2019-04-16T02:07:05.162Z'
---

# AlphaGo Comparison
## AlphaGo Fan
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

**Network Architecture**
  * SL policy network(new)
    * predicting next most likely moves
    * Maximize likelihood of human move
    * MCTS with this network is already much better than all previous 
    Go programs
    * learns from labeled game data created by strong RL policy
  * RL policy network
    * prediction of the best possible (winning) moves.
    * learning for training DCNN policy net
    * Learns from self play
    * adjust weights of net to learn from winner of each game
    * keeps a pool of previous networks as opponents to avoid overfitting
  * RL value network(new)
    * output a scale value
    * tell us how good is a board position is
    * state evalution
    * Given position in Go, computes probability of winning
    * No search no simulations
    * Learns mapping from state s to expected outcome of the game
    * Value net outputs single number:evaluation of s
  * Same overall design for three

## AlphaGoLee
  * Much more RL than Fan
  * Trained from AlphaGo selfplay games not from RL policy games anymore
  * Larger neural net
  * 3 handicap stones stronger than AlphaGoFan in self-play

## AlphaGoMaster
  * Still uses handcrafted input features
  * Still uses rollouts as part of evaluation
  * Still uses initialization by SL net
  * Mostly same architecture as AlphaGo Zero

## AlphaGoZero
  * Master the game of Go without human knowledge
  * Learns entirely from self-play

**Search**
  * still MCTS
    * Used in learning(new)
    * used for playing

**Knowledge**
  * All knowledge created by machine learning from self-play
  * Knowledge represented by deep residual neural net
  * Combines policy and value nets into one net with two "heads"
  * Both move and position evaluation learned together
  * No more simulations to end of game.

**Deep Residual Neural Network (Resnet)**
  * Two head architecture
    * Deep net
    * Two outputs:(p,v)
    * p vector of move probabilities p(s,a) for each move a
    * v value of s
  * Policy head
    * learns to predict what the search would do
    * How frequently should each move be tried in MCTS
    * minimize cross-entropy between predicted probability of move and frequency of move as selected by MCTS
    * Cross-entropy: measures how well one probability distribution can predict another
  * Value head
    * Computes probability of winning
    * trained from selfplay
    * minimize squared error between predicted value v and final result z of game
  * Exploitation term Q,value of simulation ending in in-tree state s =value head evaluation of s. No more simulation beyond the tree,no more evaluation component from rollouts.

**training**
  * Error measured by loss function
  * error of policy head,error of value head,regularization term to keep size of weights in check

