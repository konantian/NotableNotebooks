---
title: Lecture 19 - Neural Networks(NN)
tags: [Notebooks/Cmput 496]
created: '2019-03-26T04:21:07.792Z'
modified: '2019-04-12T22:10:39.379Z'
---

# Lecture 19 - Neural Networks(NN)
## Neural Networks
### Definition:
  * A neural network in computing science is a function. 
  * It takes input(s) and produces output(s).
  * It has many parameters(weights) which are determined by learning(training).
  * **Deep neural networks can approximate(almost) any function in practice**
  * Training NN:
    * Supervised learning
    * Reinforcement learning

### Neural network in computing science
  * Massively simplified, abstract model
  * Used as a powerful function approximator for(almost) arbitrary functions
  * Single neuron: Implements a simple mathematical function from it's inputs to its output
  * Connections between neurons:
    * Each connection has a weight
    * Expresses the strength of the connection
    ![](https://ws1.sinaimg.cn/large/006tNc79ly1g1yjvoko3ij30dk0f8go6.jpg =250x250)
  * Nonlinear actinvation function $\phi$
  * Output used as input for neurons on next layer

### Supervised Training of a Network
  * View the whole network as a function $y=f(x)$
  * Both x and y are vectors of numbers
  * Train by supervised learning from set of data($x_i$,$x_j$)
  * Compute errors - difference between $y_j$ and $f(x_j)$
  * Compute how error depends on each weight $w_i$ in network
  * Gradient descent - adjust weights $w_i$ in network to reduce there errors

### Sigmoid Function
  * Nonlinear function, popular for activation function
  ![](https://ws3.sinaimg.cn/large/006tNc79ly1g1yjwzjpoij30io08y0to.jpg =400x400)
  * x large negative number: $e^{-x}$ ver large, $\sigma{(x)}$ close to 0
  * x large positive number: $e^{-x}$ ver small, $\sigma{(x)}$ close to 1

### Back propagation
  * 反向传播（英语：Backpropagation，缩写为BP）是“误差反向传播”的简称，是一种与最优化方法（如梯度下降法）结合使用的，用来训练人工神经网络的常见方法。该方法对网络中所有权重计算损失函数的梯度。这个梯度会反馈给最优化方法，用来更新权值以最小化损失函数。

  * 反向传播要求有对每个输入值想得到的已知输出，来计算损失函数梯度。因此，它通常被认为是一种监督式学习方法，虽然它也用在一些无监督网络（如自动编码器）中。它是多层前馈网络的Delta规则的推广，可以用链式法则对每层迭代计算梯度。反向传播要求人工神经元（或“节点”）的激励函数可微。

  * Error:$E=\sum_{i}\left(y_{i}-f\left(x_{i}\right)\right)^{2}$

  * Gradient descent in back propagation:
    * Choice of step size $\epsilon$ is important
    * Go too far($\epsilon$ too large) - overshoot the minimum
    * Go too little($\epsilon$ too small) - very slow decrease of E
  * Partial Derivative - Intuition
    * $\frac{\partial E}{\partial w_{i}}>0$ - Small decrease in $w_i$ will decrease E
    * $\frac{\partial E}{\partial w_{i}}=0$ - Small change in $w_i$ will have no effect on E
    * $\frac{\partial E}{\partial w_{i}}<0$ - Small increase in $w_i$ will decrease E
    * Partial derivative qunatifier the effect of **leaving everything else constant**

### Chain Rule
  * $z=f(x), y=g(z)=g(f(x))$ -> $\frac{\partial y}{\partial x}=\frac{\partial y}{\partial z} \times \frac{\partial z}{\partial x}$


### Activation function
  * In artificial neural networks, the activation function of a node defines the output of that node, or "neuron," given an input or set of inputs. This output is then used as input for the next node and so on until a desired solution to the original problem is found.
  * Simoid function is one of activation function
    * $y = \sigma{(z)} = \sigma{(\sum_{i=1}^{m}{w_ix_i})}$
  * 通常来说，一个人工神经元网络是由一个多层神经元结构组成，每一层神经元拥有输入（它的输入是前一层神经元的输出）和输出，每一层（我们用符号记做）Layer(i)是由Ni(Ni代表在第i层上的N)个网络神经元组成，每个Ni上的网络神经元把对应在Ni-1上的神经元输出做为它的输入，我们把神经元和与之对应的神经元之间的连线用生物学的名称，叫做突触（英语：Synapse），在数学模型中每个突触有一个加权数值，我们称做权重，那么要计算第i层上的某个神经元所得到的势能等于每一个权重乘以第i-1层上对应的神经元的输出，然后全体求和得到了第i层上的某个神经元所得到的势能，然后势能数值通过该神经元上的激活函数（activation function，常是∑函数（英语：Sigmoid function）以控制输出大小，因为其可微分且连续，方便差量规则（英语：Delta rule）处理。），求出该神经元的输出，注意的是该输出是一个非线性的数值，也就是说通过激励函数求的数值根据极限值来判断是否要激活该神经元，换句话说我们对一个神经元网络的输出是否线性不感兴趣。


### Network types
  * Feed-forward NN
    * Information flows in one direction from input to output(数据不会从后往前传播)
  * Recurrent NN
    * Directed cycles in the network
    * Popular in natural language processing, speech and handwriting recognition
    * LSTM(Long short-term memory) 

### Nerual Networks as Universal Approximators
> NN with at least one hidden layer can approximate any continuous function arbitrarily well, given enough neurons in the hidden layer

  * Does not mean approximate **_any_** function well
  * By adding more and more hidden neurons, we can make the rror smaller and smaller
  * The theorem is only about continuous function. But we can also approximate functions with discontinuous **jumps pretty well**.
  * Multilayer "deep" networks is necessay althought 1 hidden layer is enough **in theory**.
    1. Efficiency of learning
    2. Size of representation
    


  
  


