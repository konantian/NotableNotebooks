---
title: Lecture 17
tags: [Notebooks/Cmput 496]
created: '2019-03-24T19:57:59.017Z'
modified: '2019-03-24T21:56:34.046Z'
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
**ML most useful for heuristic Search**
  * Learn an evaluation function
    * For complex problems:cannot learn all the facts
    * Learn general knowledge from examples
    * Find interesting trends, correlations in your data
  * Learn a move generation policy
  * Learn a search control for the tree search
  * Learn a filter
  * Learn time control
  * Remembering Facts
    * Transpostition table

**Supervised VS Unsupervised Learning**
  * Supervised learning: Learn from labeled training data - labeled with the correct result
    * learn from master moves in game records. Label of position = move played by the master
  * Unsupervised learning: unlabeled training data,learn from reward, which is often delayed
    * learn from playing games. Reward = win/loss at the end of the game
  * Semi-supervised learning
    * Some (often small) amount of labeled data
    * Some (large) amount of unlabeled data

**Learn with a model vs learn from experience**
  * Model
    * allows us to try out actions and observe results in simulator
    * learn from simulated experience from experiments within the simulator
  * Experience
    * real world, learn from observations of the effects of real actions

**Representation of the Model**
  1. simple is good - helps avoid overfitting
  2. as complex as needed to represent what we need
  3. functios which represent general assumptions about our world
  4. functions for which we have efficient learning algorithms







