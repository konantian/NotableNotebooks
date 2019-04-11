---
title: Lecture 11 Search and Knowledge(5)
tags: [Notebooks/Cmput 496]
created: '2019-03-23T03:59:23.276Z'
modified: '2019-04-11T02:00:28.042Z'
---

# Lecture 11 -- Search and Knowledge(5)
## Knowledge in heuristic search
**Knowledge using in Heuristic Search**
  * Evaluate states
  * Evaluate action

**Interpretations of knowledge**
  * Probabilities(概率更大的move会更容易被选到)
  * Preferences(优先级更高的move会更容易被选到)
  * Ordering
  * Ranking

**Representing knowledge**
  * Rules
  * Patterns
  * Features
  * Neural nets

**search techniques**
  * Knowledge free search
    * Blind search(完全随机搜索)
    * Random sampling
    * Boolean negamax or alphabeta
  * "Black box" heuristic evaluation function
    * Depth-limited alphabeta search(已知good moves不会超过某个深度)
    * Move ordering heuristic(将更好的move优先搜索)
    * State evaluation(state评估函数，用于决定哪个state价值更高)
    * Move evaluation(move评估函数，用于决定哪个move可以走向更好的state)
    * Time control
    * Search depth control
    * DAG vs tree(减少重复的state)
    * State representation(通过用1维array来代表棋盘可以提升搜索速度)

## Evaluation
**State Evaluation**
  * Mapping from(full) state to one number
  * Measure how good is that state
  * Also called "Evaluation function" and "position Evaluation"
  * Interpretation
    * Number: Represent the value of this state,used for **relative ranking** of state
    * Probability: Represent the probability that this state is the best state
  * Exact evaluation for leaf nodes and heuristic evaluation of non-terminal states(通过计算leaf node的价值回传给上面👆的node来计算别的node的价值)


**Move Evaluation**
  * Mapping from move(Action) to number
  * Measure how good is that move
  * Use as a filter to prune bad moves
  * Also called "Action value" "Move value" and "Q-value in machine learning" 
  * Interpretation
    * Number: Represent the value of this move,used for **relative ranking** of moves(数字本身不重要，重要的是相对的优先顺序)
    * Probability: Represent the probability that this move is the best move

**Evaluation Interpretation**
  * Similar evaluation values for similar states
  * All states with the same evaluation are "equally good"
  * Same probability of winning for equally good states
  * Higher evaluation = higher probability of winning

**Winning Probability interpretation**
  * Winning probability is the minimax score
  * Pefect player would know the certainty of the winning probability
  * Can use machine learning estimates of win probabilities

**Relation between state evaluation and move evaluation**
  * If we have state evaluation, it is easy to get move evaluation
    * Do 1 ply search
    * Slow with large branching factor
  * If we have move evaluation, it is hard to get state evaluation
    * Slow and noisy result

## Evaluation Knowledge
**Acquiring Knowledge**
  * Machine learning
  * Local goal-directed search
  * Hancoded rules

**Representing knowledge**
  * Handcoded rules
  * Simple features
    * Each feature is a boolean state about a state or a move
    * Move feature vector: $(0,0,1,...,1,1,0,...,1,0,...0,0,...)$
  * Pattern databases
  * Neural nets

**Benson's Algorithm**
> Benson's algorithm finds stones and territories that are unconditionally alive



