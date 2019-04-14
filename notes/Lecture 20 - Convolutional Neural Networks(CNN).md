---
title: Lecture 20 - Convolutional Neural Networks(CNN)
tags: [Notebooks/Cmput 496]
created: '2019-03-28T21:18:35.569Z'
modified: '2019-04-14T21:05:10.876Z'
---

# Lecture 20 - Convolutional Neural Networks(CNN)
## Convolutional Neural Networks(CNN)
### CNN 
  * Hugely successful in image recognition tasks
  * Later applied to move prediction in Go
  * Main idea
    * Start learning locally
    * Higher layers can learn successively more globally
  * Each neuron depends only on a small **closely related group** of neurons on the previous layer
### Local Receptive Field
  * Typical sizes 5 x 5, 3 x 3(similar to simple features, 3x3 pattern)
  * First hidden layer: represent many simple local features
  * **The network itself decides what the features are**

### Weight Sharing
  * Want to learn a universally useful set of local features
  * Idea: share weights across all neurons
  * Each neuron on the same level computes the same function but with different input variables(在同一层的神经元有相同的function，唯一区别只是输入的variable不一样)
  * Same weight used everywhere on the board
  * Consequence:
    * Each layer can only learn a single feature
    * To learn more, we use several copies of the layer
  ![](https://ws2.sinaimg.cn/large/006tNc79ly1g20mcjuyctj30a807sdgf.jpg =250x250)

### Feature Maps
  * Consequence of weight sharing
  * Each layer can only learn a single feature

### Deep Convolutional NN Concepts
  * Repeat many layers of local filters, processing pipeline
  * Higher-level features build from simpler local features

Pooling:
> reduce from region(e.g. 2x2 region) to single neuron by averaging

Padding
> aritificial outside elements to prevent shrinking(extend图像，加一圈边框)

  * Often: **fully connected layers at the end of pipeline**

## Deep Convolutional Neural Networks for Go
### Inputs for neural networks
  1. Raw input, three channels,19x19 bitmap(boolean array)
  2. Input with liberty information, sevel channels

### Architecture
  * Many convolution layers
  * Many small convolutional filters
  * Zero-padding to keep each layer at size 19x19
    * Add extra rows and columns with values of 0 around the edges after applying filters
  * One fully connected layer at the top
  * ReLu activation function

### ReLU Activation Function
  * ReLU stands for rectified linear unit
  * f(x) = max(0,x)
  * 0 for x < 0(如果小于0，就变成0)
  * 1 for x > 0(如果大于0，就不变)
  * More efficient than sigmoid
  ![](https://ws3.sinaimg.cn/large/006tNc79ly1g20mqlpicgj30ew0cat9u.jpg =250x250)

### Training Method
  * Basic gradient descent algorithm
  * Initialize weights randomly
  * 10 "epoches" of training over all data
  * Measured three metrics
    1. Accuracy: How often is the network's move equal to the master move?(best case 100% accuracy)
    2. Rank: In the ordered list of moves as ranked by the net, where is the master move(best case rank 1)
    3. Probability: What probability did the net assign to the master move?(best case probability 100%)


