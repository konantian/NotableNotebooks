---
title: Lecture 20
tags: [Notebooks/Cmput 496]
created: '2019-03-28T21:18:35.569Z'
modified: '2019-03-29T03:32:52.344Z'
---

# Lecture 20 
## Convolutional Neural Networks(CNN)
### Local Receptive Field
  * Typical sizes 5 x 5, 3 x 3
  * First hidden layer: represent many simple local features
  * The network itself decides what the features are

### Weight Sharing
  * Want to learn a universally useful set of local features
  * Idea: share weights across all neurons
  * Each neuron on the same level computes the same function but with different input variables
  * Same weight used everyywhere on the board

### Feature Maps
  * Consequence of weight sharing
  * Each layer can only learn a single feature

### Deep Convolutional NN Concepts
  * Repeat many layers of local filters, processing pipeline
  * Higher-level features build from simpler local features
  * Pooling:reduce from region to single neuron by averaging
  * Padding: add aritificial outside elements to prevent shrinking
  * Often: fully connected layers at the end of pipeline

## Deep convolutional neural networks for Go
  

