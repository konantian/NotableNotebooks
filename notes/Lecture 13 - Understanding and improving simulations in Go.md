---
title: Lecture 13 - Understanding and improving simulations in Go
tags: [Notebooks/Cmput 496]
created: '2019-03-23T22:22:16.623Z'
modified: '2019-04-11T19:03:49.532Z'
---

# Lecture 13 - Understanding and improving simulations in Go
## Uniformly random simuluations
**Strengths**
  1. Can find many simple tactics
  2. Can find sure wins near the end
  3. Can avoid many simple blunders that the random player may play
  4. Improves with number of simulations, up to a limit
**Weaknesses**
  1. Assume that the opponent plays randomly(现实中对手往往不会随机下棋)
  2. It will play the moves that work best against random
  3. Those moves may fail against strong opponents


**Ideal simulaitons vs reality**
  * Ideal simulations
    * An ideal simulation would preserve wins and losses(如果开局位置是赢，那么一定能赢，如果开局位置是输，那么一定会输)
    * minimax score = mean and variance = 0(exact answer)
    * Bias = 0
  * Real simulations
    * minimax != mean and variance > 0
    * Bias > 0
    * High bias: 模拟次数越多，误差越大
    * High variance：模拟次数越多，结果越分散

## Improving simulations
**Filter**
  * Decides whether a move should be used or not
  * Avoid some huge blunders in simulated games(避免走特别坏的move)
**Selective move policies**
  * Find promising moves based on rules
  * If promising moves exist ignore all other moves(如果找到足够好的move就忽略剩下所有的move)
**Rules and Patterns**
  * Generate only moves that typically good, urgent(和filter相反，只留下足够好的moves)
  * We can combine filter and rules together(利用rule产生moves，再用filter过滤掉不好的moves)
  

  
