---
title: Lecture 8 Search and knowledge(2)
tags: [Notebooks/Cmput 496]
created: '2019-04-11T03:11:31.253Z'
modified: '2019-04-11T04:05:23.653Z'
---

# Lecture 8 Search and knowledge(2)
**Solving game**
> Find the correct outcome of the game with best play by both players

**Winning strategy**
> How to play if we have a win(game solved).It is a tree.

**Prove a Win**
> To prove a win we need to find a winning strategy. Then, build a strategy bottom-up

### Winning Strategy
  * Out turn: It is enough to know **one** winning move
  * Opponent turn: We need to win against **all** their moves
  * It includes **one** move when it's our turn and **all** moves when it's the opponent's turn
  * Winning strategy tree has branches at every second level(自己回合的时候，只有一个branch，因为有一个move是win就够了。对手回合的时候，有很多个branch，必须考虑对手所有情况)
  * Depth 1
  ![](https://ws1.sinaimg.cn/large/006tNc79ly1g1yj14qq6sj30820f40tt.jpg =100x100)
  X can win in one move
  * Depth 3
  ![](https://ws4.sinaimg.cn/large/006tNc79ly1g1yj29yvb9j30l80i2tcm.jpg =250x250)
  d = 1 my turn: one move
  d = 2 opponent's turn: one branch for each opponent reply
  d = 3 my turn: one move in each brach -> win

### AND/OR Tree
  * In a game tree, position it is our turn:
    OR node(we only need one winning move)
  * Position where it is the opponent's turn
    And node(we have to win all opponent's move)
  * Each AND node leads to OR node and each OR node leads to AND node
  * Leaf Node: Terminal states of the game

### Minimax Algorithm - Boolean Version
  ![](https://upload.wikimedia.org/wikipedia/commons/thumb/6/6f/Minimax.svg/2880px-Minimax.svg.png =400x400)
  * Runtime depends on
    1. Depth of search
    2. Witdh(branching factor)
    3. Move ordering - stops when first winning move found(Pruning)

### Negmax Algorithm
  ![](http://3.bp.blogspot.com/-TDKEBW6kdRE/VECFPGzHZjI/AAAAAAAAADQ/HpXBnkCI_R4/s1600/negamax_tree.jpg =500x500)


### Proof Tree(Solution tree)
  * Subtree P of game tree G is a proof tree iff **P contains the root** of G and **All leaf nodes of P are wins**
  * If interior AND node is in P then all its children are in P
  * If interior OR node is on P,then at least one child is in P
  * Works on DAG even on arbitray graph
  * Wants to find a minimal or at least a small proof tree
  * Size of proof tree: General pattern for best case:$1,1,b,b,b^2, b^2,b^3,b^3$
  * Search is most efficient if it looks only at the proof tree(proof tree是最小的子树，实际中，不太可能) 
