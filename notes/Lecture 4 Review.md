---
title: Lecture 4 Review
tags: [Notebooks/Cmput 496]
created: '2019-04-10T18:34:07.765Z'
modified: '2019-04-10T20:41:15.645Z'
---

# Lecture 4 Review

## Decision making
### Tasks involve only the present
  * Reflexes(本能反应是下意识的，无需考虑将来的影响)
  * Intuitive Decisions(直觉)
  * Image recognition, only the past informaiton needed

### Tasks need future(looking ahead)
  * Much reasoning involves thinking about the future, in order to **make decisions now**
  * Many complications and limitations about future prdictions(关于未来的预测总是复杂并且带很多限制的，因为我们不知道)
    1. The possible actions
    2. The goals of others
    3. How to evaluate different outcomes
    4. How to compute with limited resources


### Assumptions about decision making
  * The state of the world is completely known at each time(Exception, Card games,online and computer games)
  * There are terminal states
  * The possible actions in each state are known
  * An action changes the state to a new state in a known deterministic way
  * No chance element(Exception: Dice games,3)


### Two player Games
  * Examples: Chess, checkers, Go, Tic-tac-toe
  * Zero sum(my win is opponent's loss)零和游戏


### State,Game state
  #### **Complete description of the current situation**(用来描述当前的完整游戏情况，例如，下一步该谁走了，双方各自的move历史。游戏情况同时对双方都是透明的)
    * 在Go1以及别的程序中，我们用simple_board.py中的SimpleGoBoard Class来表示
  * States plus rules of game allows us to determine actions
  * Often include **part of** history of the game(从游戏开始到当前的一系列moves)
  #### State vs History
    * Some games need history: Ko(repetition) rule depends on previous move
    * TicTactoe does not need history
  #### History only State
    * Works in principle, rules pluse complete history shows the state exactly
    * But inefficient if always replay all actions from the begining up to current move
  #### State space
    * A graph with all possible states of a problem
    * Edges in graph show how states are connected by actions
    ##### Type of state space
      * Tree is easiest for search, DCG hardest
      * Tic Tac Toe : DAG
      * Go without repetition : DCG
      * Got with simple ko rules: DCG
      * Go with full repetitions rule: DAG
      * Reason for using DAG instead of DCG:
        1. Avoid repetition in state spaces
        2. Different move order can lead to same result
      * Tree
        * Simplest state space model
        * Every action lead to a new state
        * Only one path from root to a node
        * Pros and Cons
          * Advantages:
            1. Simplest model
            2. Single path to each node
            3. No dependencies
          * Disadvantages:
            1. Duplication, no re-use of information
            2. State space can be much larger than needed
            3. Search can become very inefficient, repeat searching many copies of sub-tree
        
  #### Terminal State
    * A terminal state has no possible moves(actions)
    * No outgoing edges in graph

### Action, Move
  * Leads from one state to another
  * In Go1, move represented by idnex of a point in array and color

### Game result
  * Win/loss
    * Go with non-integer komi
  * Win/loss/draw
    * Chess, checkers, tic-tac-toe, Go with integer komi


