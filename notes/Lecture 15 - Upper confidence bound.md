---
title: Lecture 15 - Upper confidence bound
tags: [Notebooks/Cmput 496]
created: '2019-03-24T02:54:04.851Z'
modified: '2019-04-12T04:57:23.312Z'
---

# Lecture 15 - Upper confidence bound
## Mistakes and regret in simulations
**Mistakes**
  * we will make mistakes since we make decisions based on random experiments
  * Measure mistakes
    1. Probability of making wrong choice
      * Arm i has best winrate Pi, but we choose arm j with Pj < Pi
    2. Simple regret
      * Regret = 0 if you play a best move
      * Regret > 0 if you don't
      * Can try out arms for free
      * Evaluate how bad our move choice j is compared to best choice i
      * Make more sense in simulations since we have no cost in trying anything.
    3. Cumulative regred(used in UCB)
      * Each arm pull costs money
      * Regret pi-pj for every pull of an arm j
      * **UCB is designed to minimize cumulative regret**

## UCB Algorithm
**UCB Formula**
  * UCB stands for upper confidence bound
  * Define Upper Confidence Bound for move i by
  $U C B(i)=\hat{\mu_i}+C \sqrt{\frac{\log N}{n_{i}}}$ $\text { move }=\underset{i \in \text { moves }}{\arg \max } U C B(i)$
  * C is the exploration constant, larger c require higher confidence level and focus on exploration.Smalle $c$ focus on exploitation(c越大，会更多探索，c越小，会更多选择当前已知最好的move)
  * When C is very large, UCB becomes very similar to the simple uniform exploration strategy
  * At end: play the most-pulled arm(被拉的最多的杆说明更好)

**UCB vs Simple simulation player**
  * UCB is much more efficient(因为好的move被simulate更多次相对于不好的move)
  * UCB will quickly focus almost all of its effort on small number of most promising moves
  * UCB will never stop exploring other moves because of the log N term
  * UCB will try the really bad-looking moves only very rarely
  * UCB does not fix any other problems of the simulation player except the efficiency
  * Still only 1 ply deep tree search

**Optimism in the Face of Uncertainty**
  * Principle of **optimism in the fact of uncertanty**:assume the best plausible outcome for each move
  * Upper confidence bound represents the best plausible value of a move

**Strengths and limitations of UCB**
  * Strengths
    1. It does not waster much time on hopeless moves
  * Limitations
    1. It does not fix any other problems of simulation player
    2. It reaches the performance limits of simple simulation-based player play more quickly
    3. still only 1 ply deep "Tree search"
    4. After move 1,still plays randomly for both opponent and player
    5. Still vulnerable to all biases in the simulation policy
    

