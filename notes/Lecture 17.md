---
title: Lecture 17
tags: [Notebooks/Cmput 496]
created: '2019-03-24T19:57:59.017Z'
modified: '2019-03-24T21:30:44.411Z'
---

# Lecture 17 
## Memory-Augmented Monte Carlo Tree Search
  * Solve problem of MCTS
    1. Most nodes are leaves or near leaf
    2. Most nodes have few simulations
    3. Evaluation is noisy
  * Find similar states,use values of similar states to improve evaluation
    * Similar states: States are similar if they share lots of features or they "point in similar direction"
    * Compare two feature vectors
    ![Similar Features](@attachment/cmput496/similar_feature.png)
    * Find similar state in memory
      * Measure: cosine similarity
      * Similarity is 1 if they have same direction(same feature)(如果两个feature一样，则similarity是1)
    * Using memory with MCTS
      * **Selection** Compute state value by linear combination of state value and memory value
      * **Evaluation** Evaluate state by both Monte Carlo and memory
      * **Backup** update MC value and memory value in tree
    * MCTS has very few samples on nodes near the leaves(越靠近root的node有更多的sample，越远的越少).We can "interpolate" the value of similar nodes

## Machine Learning for Heuristic Search






