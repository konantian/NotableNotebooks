---
title: Lecture 17 - Memory-Augmented Monte Carlo Tree Search
tags: [Notebooks/Cmput 496]
created: '2019-03-24T19:57:59.017Z'
modified: '2019-04-16T14:25:17.964Z'
---

# Lecture 17 - Memory-Augmented Monte Carlo Tree Search
## Memory-Augmented Monte Carlo Tree Search
  * Solve problem of MCTS
    1. Most nodes are leaves or near leaf
    2. Most nodes have few simulations on most nodes near the leaves(using interpolate the value of similar nodes)
    3. Evaluation is noisy(can be improved by similar states)
  * Find similar states,use values of similar states to **improve evaluation**
    * Similar states: States are similar if they share lots of features or they "point in similar direction"
    * Compare two feature vectors
    ![](https://ws1.sinaimg.cn/large/006tNc79ly1g1yjxzao0yj30du0b6wfh.jpg =250x250)
    * Find similar state in memory
      * Measure: cosine similarity
      * Similarity is 1 if they have same direction(same feature)(如果两个feature一样，则similarity是1)
    * Using memory with MCTS
      * **Selection** Compute state value by linear combination of state value and memory value
      * **Evaluation** Evaluate state by both Monte Carlo and memory
      * **Backup** update MC value and memory value in tree
    * MCTS has very few samples on nodes near the leaves(越靠近root的node有更多的sample，越远的越少).**We can "interpolate" the value of similar nodes**

## Machine Learning for Heuristic Search
**ML most useful for heuristic Search**
  * Learn an evaluation function
    * For complex problems:cannot learn all the facts
    * Learn general knowledge from examples
    * Find interesting trends, **correlations** in your data(比如可以学习fuanction的参数)
    * Learn a function from data
      * Approxiamte the data as well as possible(avoid under fitting)
      * Robust against noisy data
      * **Avoid overfitting**
  * Learn a move generation policy
  * Learn a search control for the tree search
  * Learn a filter
  * Learn time control
    * How much time to use on each move?
    * Spend more time on more important decisions
  * Remembering Facts
    * Transposition table
    * Endgame Database
    * Memory and cache
    * Tabular learning

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
    * **Garbage in garbage out**
  * Experience
    * real world, learn from observations of the effects of real actions

**Error function**
  * Learn a value for how good each move is and pick the move with highest value
  * We do not care about the function itself, instead, we care about the move ordering

**Representation of the Model**
  1. simple is good - helps avoid overfitting
  2. as complex as needed to represent what we need
  3. functios which represent general assumptions about our world
  4. functions for which we have efficient learning algorithms
  * Examples of models
    1. Linear models using features $f_i$ as input
    2. Neural network using raw data as input

**Output of learning process**
  1. Classiﬁers: good/bad move, ﬁlter/don’t ﬁlter for search,
  2. Move evaluation or move probabilities
  3. State, position evaluation
  4. Local evaluation, e.g. territory maps










