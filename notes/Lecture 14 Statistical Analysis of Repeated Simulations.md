---
title: Lecture 14 Statistical Analysis of Repeated Simulations
tags: [Notebooks/Cmput 496]
created: '2019-03-23T23:44:54.014Z'
modified: '2019-03-24T02:24:33.333Z'
---

# Lecture 14 Statistical Analysis of Repeated Simulations
## Probabilistic simulation policies
**Stochastic vs Deterministic simulation policies**
  * Stochastic simulation
    1. Need to be stochastic, randomize moves
      * The main idea of sampling
      * The variance can be reduced by getting more samples
    2. Need to explore different move sequences
  * Deterministic
    1. All simulations from same start state play the same sequence, have the same result

**Probabilistic simulation**
  * Play pattern moves with higher probability
  * Play other moves with smaller probability
  * Can also use as a "soft" filter: give(likely) bad moves a low probability
  * Each move has different probability
  * Probabilities are better suited for many machine learning methods

**Uniforum random**
  * Each move has same probability

## Statistical Analysis of Repeated Simulations
**Borel's Law of Large Numbers**
  * Repeating experiments many times will get results close to expectation
  * This estimate will be very rought when n is small(当n很小的时候，结果往往不准确)
  * Improves as n gets large, and approaches true p
   

