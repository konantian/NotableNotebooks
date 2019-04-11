---
title: Lecture 14 - Statistical Analysis of Repeated Simulations
tags: [Notebooks/Cmput 496]
created: '2019-03-23T23:44:54.014Z'
modified: '2019-04-11T19:03:52.484Z'
---

# Lecture 14 - Statistical Analysis of Repeated Simulations
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
  * This estimate will be very rough when n is small(当n很小的时候，结果往往不准确)
  * Improves as n gets large, and approaches true p(n越大，结果越精确)

**Bernouli Experiment**
  * Random experiment, typically repeated many times, same fixed p
  * Each single experiment draws from Bernouli distribution for p
  * Simulation is a Bernouli Experiment
    1. Finite tree
    2. Finitely many leaves
    3. Finitely many paths to leaves
    4. Each leaf has fixed value 0(和局) or 1(赢）
    5. In each node, the simulaiton policy has a fixed distribution over its children
    6. The winning probability at the root is just the probability of choosing a path leading to a win
**Flat simulation player(1 ply tree)**
  * If we increase n run more and more simulations, the winrate for c will stabilize
  * Winrate will converge to the "true winrate"
  * Winrate may be far from true minimax value(bias产生于假设对手也是随机下子)

**Benefits of More simulations**
  * Reduce variance(but not bias)
  * Better selection when serveral moves are almost tied for first
  * Rule out "unlucky" cases which occur with low number of simulations(次数越多，产生偶然性的几率越低)

**Confidence Interval**
  * Confidence Interval:A range in which the true value is estimated to be
  * Confidence level: Probability that the range contains the true value
  * For lower confidence level, the intervals are smaller - more chance of error(包含的数据过少，不太可能包括true mean)
  * For higher confidence level, the intervals are larger - less chance of error(包含的数据足够多，很可能包括true mean)




