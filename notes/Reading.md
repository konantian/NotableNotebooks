---
title: Reading
tags: [Notebooks/Cmput 496]
created: '2019-04-13T17:09:25.500Z'
modified: '2019-04-14T03:38:20.422Z'
---

# Reading
## 20 years after Deep Blue
* Computer scientists had for decades viewed chess as a meter stick for artificial intelligence.
* CMT students built the first computer - called Deep Thought to beat a grand master
* 1989, Kasparow beat Deep Thought handily in the two games
* IBM was impressed enough with the CMU teams'technology and developeed an early version of Deep Blue
* Deep blue lost to  Kasparov in 1996,but win one game out of six games
* The speed of deep blue was doubled in 1997, as well as more patterns and more chess knowledge
* 1997 deep blue search 6-8 paris of moves
* There is no machine learng and neural network used in deep blue 1997, just alpha-beta search in parallel

## Checker is sovled
* weakly solved games both the result and a strategy for achieving it from the start of the game are known
* Strongly solved games have the result computed for all possible positions that can arise in the game
* Check is not the first nontrival game to be solved
* Checker has been weakly solved,program can achieve at least draw against all opponent playing either black or white
* Important parts of the checkers proof have been independently verified
* Proof of checks contains 1.Endgame databases 2.Proof tree 3.Proof solver
* The program can quickly extract information from the database
* The manager used proof number search algorithms to identify prioritized list of positions
* Proven positions need no further work, partially proven positions need additional work
* Chinook use alpha-beta serach to nominal serach depths of 17-23 ply
* In 19 three-moves opening, only one opening is proven to loss all others are draw
* Some grandmaster checkers players were not surprised that the game was a draw.
* The number of possible checkers positions is largest when 23 pieces are on the board
* Retrograde analysis was an important part of the checkers proof.
* Some checkers openings required a search that was over 150 ply deep.
* Not all the investigated opening were proven to be draw
* Alpha-beta pruning reduced the size of the proof tree in checkers.
* The longest line analyzed was 154 ply
* The checkers computation pushes the boundary of what can be archieved by search-intensive algorithms
* Chess will remain unsolved for a long time

## Solving Go on small boards
* Many games have been solved using a search-based approach, Go is a notable exception.
* Mini go Solver solves all square boards up to 5x5 and can be applied to any enclosed problem of similiar size.
* There are no good nor cheap evaluation function for 19x19 Go board
* The Euler number of a binary image, is the number of objects minus the number of holes in those objects
* A set of stones is said to be unconditionally alive if they cannot be captured and never require any defensive
move.
* Benson's algorithm can be extended to determine safety under local alternating play
* Benson-controlled regions are formed by the unconditionally-alive blocks and their vital regions (eyespace), as classified by Benson’s algorithm.
* Open regions are not connected to unconditionally-alive stones (which is common early in the game) or are between unconditionally-alive stones of both sides.
* Closed regions are surrounded by unconditionally-alive stones of one colour
* Unconditional territory can further be used for reducing the branching factor
* It just means that after that depth the Principal Variation and value of the move were no longer affected by deeper searches
* static analysis of unconditional territory is more expensive than a simple evaluation at the leaves 
* On todays’ standard PC MIGOS is not yet ready to take on the empty 6x6 board
*
*


