---
title: Go versions
tags: [Notebooks/Cmput 496]
created: '2019-04-16T02:44:13.559Z'
modified: '2019-04-16T02:59:27.978Z'
---

# Go versions 
## Go0
* Totally random
* fills eyes
* game last very long
* very slow

## Go1
* random player
* does not recognize or prevent longer loop repetition
* very slow
* move represented by index of point in array
* stops playing at sing point eyes
* we cannot even search 7 moves deep with Go1
* selecte moves uniformly at random 
* no pass except at very end avoid filling eyes

## Go2
* same algorithm with G1, but faster

## Go3
* almost-random simulaitons based player
* clearly better than random
* avoid self atari
* filter eye-filling moves
* simple monte carlo player
* Go3 implements several variations of simulation-based players
* Go3 implements two different simulation policies(random and rule based)
* Go3 implements two different move selection algorithms at the root
* pass earlier if it has the best winrate
* UCB in Go3
* 1-ply search

## Go4
* simulation based player with probabilistic simulations
* used features in simulaiton policy
* simple feature implementation in Go4
* use better move prediction
* use MM to learn weights

## Go5
* simple feature implementation in Go5
* MCTS
