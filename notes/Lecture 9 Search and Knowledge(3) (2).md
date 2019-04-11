---
title: Lecture 9 Search and Knowledge(3)
tags: [Notebooks/Cmput 496]
created: '2019-04-11T04:29:25.422Z'
modified: '2019-04-11T05:39:53.213Z'
---

# Lecture 9 Search and Knowledge(3)

### Boolean Minimax search
  * Zero sum: Each point we win, the opponent loses
  * **OR** node = **MAX** node(we maximize score), **AND** node = **MIN** node(opponent minimizes our score)
  * Stop search early(Can stop as long as one child achive one of the following)
    1. We know the highest possible score(我们已经搜索到了最大可能的分数，剩下的child不会再超过这个值了)
    2. We have a bound, and only want to know if we can reach at least that bound. 
  * Plain minimax/negamax
    * Inefficient: **No Pruning**. It searches all $b^d$ paths
  * How pruning tree
    1. If maximum possible value is reached, return directly,prune remaining moves
    2. Prune when reaching "good enough" value
      * Bound value(m) is given to us, we can do **two** boolean searches to verify if $m$ is the minimax result(最好情况下，我们只需要一次search，最多需要2次搜索)
          * **First search**:
          score $v >= m$ are wins(**lower bound** on true minimax value)
          score $v < m$ are loses(**upper bound** on true minimax value)
          * **Second search**:
          score $v > m$ win(**lower bound** on true minimax value)
          score $v <= m$ lose(**upper bound** on true minimax value)
          * If first search return lose, just stop
          * If first search return win and second search return lose, minimiax value equal to m
          * If first search return win and second search return win
           minimax value greater than m
      * Boudn value update during the search

  * Boolean searches and proof trees
    * Our winning strategy: achieve at least $m$
    * Opponent's strategy: prevent us from getting more than $m$
    * Result: No player can do better than $m, m$ is the lower bound as well the upper bound against a perfect opponent

### Alpha beta Search
  * Lower and upper bound ($\alpha,\beta$)
  * Prune a position if its value falls outside the ($\alpha,\beta$)
    1. $v < \alpha$ we ill avoid this position, need better choice
    2. $v > \beta$ opponent will avoid this position, need better choice
    3. $v = \beta$ opponent can also ignore this position
  * Negmax alpha beta
    1. Everything is from the current player's point of view
    2. Negate scores when changing from player to opponent on each level
    3. Window ($\alpha,\beta$) becomes ($-\beta,-\alpha$) for opponent(我们想尽可能赢更多，对手希望尽可能损失更少)
    ![](https://ws3.sinaimg.cn/large/006tNc79ly1g1yn0qvvyqj31m60u0dw7.jpg =600x600)

