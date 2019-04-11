---
title: Quiz Review
tags: [Notebooks/Cmput 496]
created: '2019-04-11T19:04:00.999Z'
modified: '2019-04-11T19:38:58.300Z'
---

# Quiz Review
### Quiz 4 
#### size of state space(Lecture 4)
  1. Assume a **tree** has branching factor **b=10** and depth **d=3**. How many leaf nodes does it have?
  $b^d= 10^3 = 1000$

  2. Assume a **tree** has branching factor b=10 and depth d=3. How many total nodes does it have?
  $b^0 + b^1 + b^2 + b^3=10^0+10^1+10^2+10^3=1111$

  3. A tree with b=100, d=10 has more nodes than a tree with b=10, d=100
  :x:$100^{10} =10^{20} < 10^{100}$

  4. Given a DAG with d=3. Each node except the leaves has 10 children, and each node except the root and its children has 10 incoming edges. The children of the root have only one incoming edge. How many leaves does this DAG have?

| Depth|#of nodes|
|:--:|:--:|
|0|0|
|1|10|
|2|10|
|3|10|
  5. Given the same DAG as in Question 04. How many nodes in total does it have?
  $1+10+10+10=31$ nodes
#### sequential decision(Lecture 5)
  6. When we organize sequences into trees, some sequences might not share any nodes.
  :negative_squared_cross_mark: : Since any two sequences shares at least one node(the root node)
  7. In the DAG model, two sequences can start differently but merge later.
  :white_check_mark: : Two sequences can start differently but merge later if they reach equivalent states later
  8. In the tree model, two sequences can start differently but merge later.
  :negative_squared_cross_mark: : For any equivalent states in tree, they have unique path from root to it, they cannot merge together
  9. According to Don Knuth, premature optimization is the root of all evil.
  :white_check_mark:
  10. One use of Amdahl's law is to show limits of code optimization. Assume a program spends 90% of its time in one function f. We manage to optimize f, so it now runs 10 times faster. How much faster is the whole program?
  $\frac{1}{(1-0.9)+\frac{0.9}{10}}=5.26$

#### optimization(Lecture 6)

### Quiz 5

### Quiz 6

### Quiz 7

### Quiz 8

### Quiz 9

### Quiz 10

### Quiz 11

### Quiz 12
