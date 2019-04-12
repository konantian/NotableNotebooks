---
title: Quiz Review
tags: [Notebooks/Cmput 496]
created: '2019-04-11T19:04:00.999Z'
modified: '2019-04-12T03:08:09.702Z'
---

# Quiz Review
### Quiz 4 
#### size of state space(Lecture 4)
  1. Assume a **tree** has branching factor **b=10** and depth **d=3**. How many leaf nodes does it have?
  **$b^d= 10^3 = 1000$**

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
  **$1+10+10+10=31$ nodes**
#### sequential decision(Lecture 5)
  6. When we organize sequences into trees, some sequences might not share any nodes.
  :x: : **Since any two sequences shares at least one node(the root node)**
  7. In the DAG model, two sequences can start differently but merge later.
  :white_check_mark: : **Two sequences can start differently but merge later if they reach equivalent states later**
  8. In the tree model, two sequences can start differently but merge later.
  :x: : **For any equivalent states in tree, they have unique path from root to it, they cannot merge together**
#### optimization(Lecture 6)
  9. According to Don Knuth, premature optimization is the root of all evil.
  :white_check_mark:
  10. One use of Amdahl's law is to show limits of code optimization. Assume a program spends 90% of its time in one function f. We manage to optimize f, so it now runs 10 times faster. How much faster is the whole program?
  $\frac{1}{(1-0.9)+\frac{0.9}{10}}=5.26$

### Quiz 5
#### minimax search(lecture 7)
  1. Assume that our alphabeta­based solver has a bug, such that it sometimes does not generate all of our moves. However, it always generates the opponent's moves correctly. Claim: If the search returns a win for us, this result is correct.
  :white_check_mark: **In OR node, one winning move is enough**
  2. Same buggy solver as in Question 01. Claim: If the search returns a loss for us, this result is correct.
  :x: **Since it cannot generate all of our moves correctly, there might be a winning move in remain moves**
  3. To use depth­limited alphabeta search, we need to have an evaluation function.
  :white_check_mark: **The depth limit has to be determined by the evaluation function**
#### minimax search(2)(lecture 8)
  4. A winning strategy for a player must specify a move for every state in the whole state space where it is the player's turn.
  :x: **The winning strategy includes one move when it's our turn and all moves for opponent's turn**
  5. If we follow a winning strategy, we will always end up in a winning terminal position, no matter what the opponent plays.
  :white_check_mark:
  6. A proof tree represents a winning strategy.
  :white_check_mark:
  7. The same state can have both a proof tree and a disproof tree for the same winning condition.
  :x: **A state can only have a proof tree **OR** a disproof tree under one winning condition**
  8. The same state can have both a proof tree and a disproof tree if the winning conditions are different.
  :white_check_mark: **Under two winning conditions, a state can have both proof tree and disproof tree**
#### minimax search(3)(lecture 9)
  9. The best case for boolean minimax search is when it searches the best move last.
  :x: **The best case is search best move first,and it needs only one search**
  10. In negamax search, the evaluation of all leaf nodes is from the root player's point of view.
  :x: **Always from the current player's point of view**
  11. An AND node in an AND/OR tree corresponds to a MAX node.
  :x: **OR node corresponds to a MAX node, In order node, we have to select child with max value**
  12. In the negamax framework, AND and OR nodes are treated exactly the same by the algorithm.
  :white_check_mark:
  13. In minimax, an AND node is a win if at least one child is a win.
  :x: **an AND node is win if all it's childs are win**
  14. Alphabeta search can stop as soon as it finds a move that is better than the first move tried.
  :x: **Stops as soon as it find a winning move**
  15. For games with only two outcomes (win­loss), how do boolean negamax and standard alphabeta search as in alphabeta.py compare in terms of pruning power?
  **They are essentially the same, similar performance**
  16. Search 1: We use boolean negamax search to solve a game with of constant branching factor b=5 and constant depth d=10. Assume that the game is a win for the first player and that our program has perfect move ordering. Let n1 be the number of nodes searched.

  Search 2: after we further improve our program, it can now solve the same game while searching to a depth of only 8. Let n2 be the number of nodes searched now.
  Question: Approximately, what is the ratio n1/n2?
  $n1 = 1+5+5+25+25+125+125+625+625+3125+3125=7811$
  $n2 = 1+5+5+25+25+125+125+625+625=1561$
  $\frac{n1}{n2} = \frac{7811}{1561} \approx 5$
  17. Negamax Alphabeta can prune the search as soon as a child has a value of beta or more (from current player's point of view).
  :white_check_mark: **Since beta is the upper bound, if there is a child can achieve this bound or even higher, we can just stop search**
  18. In Negamax Alphabeta, the alpha value is the minimum that the current player is guaranteed to achieve so far.
  :white_check_mark: **alpha is the lower bound**
  19. If we guess a minimax value m, then we can verify that it is correct by using one boolean minimax search.
  :x: **We need two boolean minimax search except the best case**
  20. Plain minimax, without alphabeta pruning, will visit all leaf nodes of a game tree.
  :white_check_mark: **There is no pruning in plain minmax**

### Quiz 6
#### minimax search(4)(lecture 10)
  11. A transposition table can be used to compute the principal variation (PV) even after the search is finished.
  :white_check_mark:
  12. Part of what a hash function does is to determine which entry in a transposition table is used to store a position.
  :white_check_mark:
  13. In our Tic Tac Toe example, our hash function was perfect: each different position also had a different hash code
  :white_check_mark:
  14. With 64 bit Zobrist hashing, if we have two different Go boards, their hash code is guaranteed to be different.
  :x: **64 bit Zobrist hashing is not enough, it cannot guaranted the hash code to be unique**
  15. We can use a transposition table for finding a proof, but we need to verify the result to avoid problems with hash collisions.
  :white_check_mark: **We always need to verify the result when using transposition table**
  16. Given a state evaluation function, it is easy to construct a move evaluation function from it.
  :white_check_mark: 
  17. Assume we search a chess position with an evaluation function that can return either exact or heuristic values. We use exact values for win = 1000, draw = 0, loss = ­1000 for terminal states, and other numbers (not equal to these) for non­terminal states. The result of a depth­limited alphabeta search is 0. Claim: this proves that the game is a draw.
  :x: **For depth-limited search, the result is estimate(heurisitc value), it cannot proves anything**
  18. We do a depth­limited alphabeta search of a checkers position, with a heuristic evaluation function for this game. Assume that all heuristic evaluation scores are larger than proven­loss and smaller than proven­win.

  The search does not always reach the end of the game. It returns a proven­draw minimax score. Claim: we can trust this result, the position must be a draw.
  :x: **Same reason as above**
  19. Same setting as question 18. Now the search returns a proven­win score. Claim: we can trust this result, the position must be a win.
  :white_check_mark:
  20. Same setting as question 18. Now the search returns a proven­loss score. Claim: we can trust this result, the position must be a loss.
  :white_check_mark:
### Quiz 7
#### Simulations(Lecture 12)
  1. Numerical Integration with Monte Carlo has no bias, it will approximate the true area more and more closely when using enough simulations.
  :white_check_mark:
  2. The main idea of Markov Chain Monte Carlo is simulating particles through biased random walks.
  :white_check_mark:
  3. We can balance physics errors in our simulation model by doing more simulations.
  :x: **We cannot balance the errors, if the model is invalid or has errors**
  4. For SAT solving, systematic search is always slower than local search
  :x: **No clear winner, different strengths/weaknesses**
  5. In games with chance such as backgammon, random simulations work well when given enough simulations.
  :white_check_mark: **Simulations always works well in games with chance element**
  6. In TicTacToe, random simulations work well when given enough simulations.
  :white_check_mark: **In games without chance element, simulations are less natural but always works well**
  7. Against a weak opponent, a simulation­based player can do even better than a perfect player.
  :white_check_mark:
  8. Go3 builds a deep search tree while running random simulations.
  :x: **Go3 is flat monte carlo, which is only 1-ply deep search**
  9. Like Go1, Go3 can play a pass only at the very end, to avoid eye­filling moves.
  :x:
  10. Given enough simulations, our Go3 simulation­based player becomes almost perfect.
  :x: **It is true in Tictactoe but not Go**

### Quiz 8

### Quiz 9

### Quiz 10

### Quiz 11

### Quiz 12
