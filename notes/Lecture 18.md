---
title: Lecture 18
tags: [Notebooks/Cmput 496]
created: '2019-03-24T21:59:25.849Z'
modified: '2019-03-25T18:40:09.210Z'
---

# Lecture 18
## Machine learning with simple features
### Simple Features
  * boolean-valued statement about a move
  * Example:$(0,0,1,1,0,1,0,0,0,1,...)$
  * List of indices of active featuree:$(2, 3, 5, 9,...)$
  * In Go, in each group of features, only one is active
    * Example: area around each move matches exactly one of the about 950 patterns

### Distance Features
  * Measure distance between two points on board
  * Points$(x1,y1)$ and $(x2,y2)$
  * Distance metric: $d(dx,dy) = dx+dy+max(dx+dy)$
  * Feature group
    1. Distance to previous stone (last move by opponent)
    2. Distance to previous own stone (our move before that)
    3. Line on the board (counting from edge)

### Evaluation Function from Simple Features
  1. Evaluate one move m
  2. Check which features are active for m
  3. Learn a weight for each feature
  4. Compare between all moves by evaluation funciton(linear combination)
  5. Sum all terms that are active
  $\sum_{i=1}^{\infty} w_if_i$
  $eval(m) =  0 × w_0 + 1 × w_1 + 0 × w_2 + 0 × w_3 + 1 × w_4 = w_1 + w_4$


### Move Prediction
  * Predict which move a master player would choose in a given position
  * Example of supervised learning position is labeled by the master move(通过机器学习大量master的下棋方法，预测新的位置master会下哪一步)
  * Why move prediction
    1. Use for move ordering in search
    2. Use for better moves in simulation policies
  * Fast vs Slow 
    * Fast: use simple features
    * Slow: use deep neural network(训练会花费大量时间)
  * As classification Problem
    * Compute score for each legal move
    * class 1 = {highest scoring move}
    * class 2 = {all other moves}

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
  * Weights(Strength)
  P(feature $f_i$ beats $f_j$) = $\frac{w_i}{w_i+w_j}$
  * Moves
  P(move $m_1$ beats move $m_2$) = $\frac{strength(m_1)}{strength(m_1)+strength(m_2)}$
  * Example:
    * $m_1$ has feature $f_1,f_2,$ strength $w_1 * w_2$
    * $m_2$ has feature $f_2,f_5,f_6$ strength $w_2 * w_5*w_6$
    * p($m_1$ beats $m_2$) = $\frac{w_1 * w_2}{w_1 * w_2+w_2 * w_5 * w_6}$
