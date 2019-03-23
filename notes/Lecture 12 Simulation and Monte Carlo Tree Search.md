---
title: Lecture 12 Simulation and Monte Carlo Tree Search
tags: [Notebooks/Cmput 496]
created: '2019-03-23T02:32:16.065Z'
modified: '2019-03-23T04:17:06.041Z'
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
  * If you feed great data to an invalid model, you typically get garbage.
