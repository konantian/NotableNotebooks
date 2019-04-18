---
title: Lecture 18 - Machine learning and UCT
tags: [Notebooks/Cmput 496]
created: '2019-03-24T21:59:25.849Z'
modified: '2019-04-16T14:56:26.292Z'
---

# Lecture 18 - Machine learning and UCT
## Machine learning with simple features
### Simple Features
  * 1 stands for active feature, 0 stands for inactive feature
  * boolean-valued statement about a move
  * Example:$(0,0,1,1,0,1,0,0,0,1,...)$
  * List of indices of active featuree:$(2, 3, 5, 9,...)$
  * In Go, **in each group of features**, only one is active
    * Example: area around each move matches exactly one of the about 950 patterns

### Distance Features
  * Measure distance between two points on board
  * Points$(x1,y1)$ and $(x2,y2)$
  * Distance metric: $d(dx,dy) = dx+dy+max(dx+dy)$
  * Feature group
    1. Distance to previous stone (last move by opponent)
    2. Distance to previous own stone (our move before that)
    3. Line on the board (counting from edge)

### Pattern features
  * Feature group: 3x3 are centered on candidate move
  * Move can also be on edge of board


### Evaluation Function from Simple Features
  1. Evaluate one move m
  2. Check which features are active for m
  3. Learn a weight for each feature
  4. Compare between all moves by evaluation function(linear combination)
  5. Sum all terms that are active
  $\sum_{i=1}^{\infty} w_if_i$
  $eval(m) =  0 × w_0 + 1 × w_1 + 0 × w_2 + 0 × w_3 + 1 × w_4 = w_1 + w_4$
  6. Coulom's approach: $\operatorname{eval}(m)=\prod_{f_{i}=1} w_{i}$


### Move Prediction
  * Predict which move a master player would choose in a given position
  * Example of supervised learning position is labeled by the master move(通过机器学习大量master的下棋方法，预测新的位置master会下哪一步)
  * Why move prediction
    1. Use for move ordering in search
    2. Use for better moves in simulation policies
  * Fast vs Slow 
    * Fast: use simple features(效果不好但是快)
    * Slow: use deep neural network(训练会花费大量时间，但效果更好)
  * As classification Problem
    * Compute score for each legal move
    * class 1 = {highest scoring move}
    * class 2 = {all other moves}
    * The problem is solved when $m$* has the highest score(说明我们找到的的分数最好的move就是m*)
  * Game data
    * Games records with master moves
    * Games between professional players
    * Games between amateur players
    * Games between computer programs
    * More variety/weaker palyers may be better

### Tabular learning vs learning with features
  * Tabular learning:
    1. Just memorizes which particular moves were good in particular positions
    2. **_No generalization_**
  * Learning with features
    1. Learn which features are generally good or bad
    2. Learn which features work in many examples
    3. This approach provides **_generalization_** to new positions, not seen before
    4. Much more useful in practice, each new game has different positions

### Compare between two weights and two moves
  * Assumptions
    1. Strength can be measured on a linear scale but features cannot be strongly dependent

  * **Weights(Strength of the feature, lager weight means better feature)**
  P(feature $f_i$ beats $f_j$) = $\frac{w_i}{w_i+w_j}$
  ![](https://ws3.sinaimg.cn/large/006tNc79ly1g20htr5nc1j30p00goq64.jpg =300x300)
  * Moves
  P(move $m_1$ beats move $m_2$) = $\frac{strength(m_1)}{strength(m_1)+strength(m_2)}$
  * Example:
    * $m_1$ has feature $f_1,f_2,$ strength $w_1 * w_2$
    * $m_2$ has feature $f_2,f_5,f_6$ strength $w_2 * w_5*w_6$
    * p($m_1$ beats $m_2$) = $\frac{w_1 * w_2}{w_1 * w_2+w_2 * w_5 * w_6}$

### Genrealized Bradley-Terry Model
  * Goal : find weights $w_i$ for all features
  * Maximize $L=\prod_{j=1}^{N} P\left(R_{j}\right)$
  * Where $P(R_j)$ is probability of playing master move in test case j

### Minorization-Maximization(MM)
  * Problem: it is diffuicult to maximize L directly(由于L非凸或者不连续，数学性质不好，不方便直接算极值时)
  * Approach: find a simpler formula m which minorizes L:
    (找一个可以替代的函数，拥有更好的优化性质，进行优化)
    * m approximates L
    * m(x) < L(x)

### Learning process
  1. Collect training data
  2. Label each move in each positions by it's features
  3. Run MM to compute feature weights
  4. Use the weights as knowledge in program to select good moves

  
## How to use the learned model
### From move weights to move probabilities
  * Some applications require probabilities not just weights
  * Idea: run MM to learn feature weights $w_i$
  * Compute the strength of each move as product of its features'weights
  * Choose each move with probability proportional to its strength

### Extension of MM
  1. LFR: Learn interaction terms as well as individual feature weights. Learn only the most important interactions
  2. FBT: The weight it computes are just numbers, larger weights are better but no interpretation as probabilities

### Limits of learning form Game records
  1. Can only learn what is in the data(只能学习数据中存在的，对于新的情况反映不好)
  2. Can only learn what can be represented in our model(很多复杂的情况因为没法表示，所以学习不到)
    * Neural nets are much more powerful to represent high-level concepts than simple features

### Limits of move prediction
> A better move predictor does not necessarily make a better player

  1. Playing moves that are good “on average” may fail in such situations
  2. Can never reach 100% prediction
    * Multiple equally good moves(当有好几个move一样好的时候，会选择哪个难以确定)
      * Same point value in endgame(当好几个move可以在游戏结束是到达同样state的时候)
      * Forcing moves(不得不走的move，但是不一定什么时候走)
      * Moves may have different strong and weak features which balance each other(不同强度的feature互相抵消)
    * Different definitons of "Best" move

## Using knowledge in UCT
  * Use knowledge
    1. Initialization of node statistics
    2. Additive knowledge term
    3. Multiplicative knowledge term
  * Regular UCT:select best child by UCT formula,count number of 
  simulations and wins
  $U C T(i)=\hat{\mu_i}+C \sqrt{\frac{\log n_{p}}{n_{i}}}$
  * Improvement :Initialize with other non 0 value to encode knowledge about moves
    1. Initialization of Node statistics
      * Give good moves some initial wins
      * Give bad moves some initial losses
      * Decay over time: Over time, real simulation statistics dominate over initialization
      * Size of $n_i$ expresses how reliable the knowledge is
      * Winrate of $\frac{w_i}{n_i}$ expresses how good or bad the move is
    2. Additive knowledge
      * add a term to UCT formula
      * $$UCT(i) = \hat{\mu_i} + \textbf{knowledgeValue(i)} + c\sqrt{\frac{logn_p}{n_i}}$$
      * KnowledgeValue(i) computed from simple features or neural network
      * Decay over time:must be explicitly programmed
      * Multiply knowledge term by some decay factor
    3. Probabilistic UCT
      * explore promising moves more
      * $$PUCT(i) = \hat{\mu_i} + p_i + c\sqrt{\frac{logn_p}{n_i}}$$
      * Probability $p_i$ that move i is the best
      * Decay over time:yes, since divide by $n_i$ in the exploration term

  
  
