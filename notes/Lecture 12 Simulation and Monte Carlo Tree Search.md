---
title: Lecture 12 Simulation and Monte Carlo Tree Search
tags: [Notebooks/Cmput 496]
created: '2019-03-23T02:32:16.065Z'
modified: '2019-03-23T04:46:24.634Z'
---

# Lecture 12 Simulation and Monte Carlo Tree Search
## Monte Carlo Simulation
**Simulation**
> Simulation is the imitation of the operation of a real-world process or system over time

**Monte Carlo simulation**
> Learn information from random sequences of decision steps

**Monte Carlo Sampling**
  * Advantages:
    1. General method
    2. No assumptions on type of funciton
    3. Fast method
  * Disadvantages: 
    1. Convergence of the basic method is slow
    2. High variance(but not bias)
    3. Coulde be faster if the funciton is smoothness
    4. Fall-back for cases without nice structure

## Simulation model
**Garpage out principle**
  * A simulation can only be as good as the underlying model
  * If you feed great data to an invalid model, you typically get garbage.(如果使用不好的数据给好的模型，出来的结果也会不尽人意)

**Games with Change elements**
  * Using random simulations is a natural idea

**Games without change element**
  * Using random simulaitons is much less natrual
  * Often, it works very well
  * TicTacToe
    * Form given states, finish game with moves selected uniformly at random
  ```python
    def simulate(self):
        allMoves = self.legalMoves()
        random.shuffle(allMoves)
        i = 0
        while not self.endOfGame():
          self.play(allMoves[i])
          i += 1
        return self.winner(),i
  ```

## Use Simulations as Evaluation funciton
**Evaluate a state**
  * Exact answer:
    1. Run solver
    2. Compute minimax value
  * Heuristic:
    1. Depth-limited alphabeta search
    2. Run simulations,score the final result

**Simulation-based player**
  1. Uses 1 step lookahead(Flat Monte Carlo) to evaluate all moves(只考虑将来的一步)
  2. For each legal moves:
    1. Run n simulations
    2. Measure the winrate
  3. After all simulations play move with highest winrate

**Compare between simpulation player and perfect player
  * Sim(100)
    * Perfect player never loses in either color
    * 100 is not enought to get precise number
    * More simulaitons is better(模拟越多效果越好)
    * Close to perfect in TicTacToe but not all games

  * Sim(1000)
    * Can exploit random better than the perfect player
    * Tie-breaking towards moves that are more successful(由于随机性，即使是一样好的move，simulation会找出相对更好的move)
    * Can sometimes have higher winrate than pefect player
