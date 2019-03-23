---
title: Lecture 12 Simulation and Monte Carlo Tree Search
tags: [Notebooks/Cmput 325]
created: '2019-02-03T18:20:24.118Z'
modified: '2019-03-23T04:27:59.465Z'
---

# Lecture 12 Simulation and Monte Carlo Tree Search
## Monte Carlo Simulation
**Simulation**
> Simulation is the imitation of the operation of a real-world process or system over time

**Monte Carlo simulation**
> Learn information from random sequences of decision steps

**Monte Carlo Sampling**
  * Advantages:
    1. General method
    2. No assumptions on type of funciton
    3. Fast method
  * Disadvantages: 
    1. Convergence of the basic method is slow
    2. High variance(but not bias)
    3. Coulde be faster if the funciton is smoothness
    4. Fall-back for cases without nice structure

## Simulation model
**Garpage out principle**
  * A simulation can only be as good as the underlying model
  * If you feed great data to an invalid model, you typically get garbage.(如果使用不好的数据给好的模型，出来的结果也会不尽人意)

**Games with Change elements**
  * Using random simulations is a natural idea

**Games without change element**
  * Using random simulaitons is much less natrual
  * Often, it works very well
  * TicTacToe
    * Form given states, finish game with moves selected uniformly at random
'''
    def simulate(self):
    '''python
