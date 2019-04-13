---
title: Quiz Review
tags: [Notebooks/Cmput 496]
created: '2019-04-11T19:04:00.999Z'
modified: '2019-04-13T05:30:37.367Z'
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
#### Improving simulaitons with rules and patterns(Lecture 13)
  1. Our scaling experiment against the Go2 random player showed that the simulation­based player Go3 with 100 simulations is clearly better than with 50 simulations.
  :x: **Go3 with 100 simulations has same performance with simulations with 50**
  2. A strength of Go3 is that it avoids making silly threats.
  :x: **Go3 still play threat moves,it's just simulations based player**
  3. During its simulations, Go3 models its opponent as another simulation­based player.
  :x: **Go3 models it's opponent as random player**
  4. In one example, Go3 found that it needed to make two eyes, without having any special knowledge about how to make eyes.
  :white_check_mark: **Since making two eyes will given highest winrate**
  5. An ideal simulation policy would always win from a start state that is winning and lose from a start state that is losing.
  :white_check_mark:
  6. In simulations, low variance is more important than low bias.
  :x: **Low bias is much more important than low vairance**
  7. In selfatari, a player removes the last liberty of their own stones.
  :x: **In selfatari a player play a move return own stones to one liberty**
#### Probabilistic simulation policies(Lecture 14)
  8. Deterministic simulations are better than random ones.
  :x: **Deterministic simulaitons are not better than random ones**
  9. A rule­based simulation policy can also be viewed as a probabilistic policy.
  :white_check_mark: **Because it plays pattern moves with higher probability and plays other moves with smaller probability**
  10. When developing probabilistic simulation policies, the probabilities are usually determined by using machine learning.
  :white_check_mark:
### Quiz 9
#### UCB and monto carlo tree search(Lecture 16)
  1. The main idea of selective game tree search is to increase the branching factor of the search.
  :x: **Selective game tree is for reduce the branching factor**
  2. All selective search algorithms require game­specific knowledge for move selection.
  :x: **They does not require knowledge of game specific**
  3. Selective alphabeta search works well in Go.
  :x: **Usually, only 1-10 moves of all moves are good**
  4. Given a (b,d) tree with b=10, d=5 and a simple simulation­based player which selects moves uniformly at random. Let n be one leaf node in the tree. What is the probability of a single simulation reaching n?
  5. In simulation­based players, the average value of a small number of good moves is usually closer to the true min or max than the average value of all moves.
  :white_check_mark:
#### Probabilistic simulation policies(Lecture 14)
  6. In a Bernoulli distribution with p = 0.6, the outcome 0 (loss) is at least as likely as the outcome 1 (win).
  :x: **The probability of win is $1-0.6 = 0.4$**
  7. Assume that in a Bernoulli experiment we get 60 wins out of 100 tries. Then p = 0.6 .
  :x: **P is unknown, we only can approximate p but never get close to the real value**
  8. Given a Bernoulli experiment with p = 0.98 . Then it is possible that we get 0 wins out of 5 tries.
  :white_check_mark:
  9. We have seen that running a simulation­based player, with a fixed simulation policy from a fixed Go position gives a Bernoulli experiment with some probability p.

  Now we change the experiment by sampling the Go position uniformly at random from the set of all legal Go positions in each round. What happens?
  **This is another Bernoulli experiment, but possibly with a diﬀerent probability p'.**
  10. Running more simulations reduces the bias but not the variance.
  :x: **Runing more simulations reduce variance but not bias**
  11. The confidence interval is the smallest interval which contains the true value.
  :x: **Confidence interval is the range in which the true value is estimated to be,but not smallest range**
  12. The confidence level measures how likely we are to win a Bernoulli experiment.
  :x: **Confidence level is probability that the range contains the true value**
#### UCB(Lecture 16)
  13. The UCB algorithm selects the move with largest confidence interval.
  :x: **UCB selects moves with most visited**
  14. The UCT algorithm decides how to grow its game tree by using the statistics from previous simulations.
  :white_check_mark: **It using the statistics about the visit count and win rate**
  15. Both UCB and UCT try to balance Exploration and Exploitation.
  :x: **We need both exploration and exploitation**
  16. Assume we are in the middle of a Monte Carlo Tree Search, which uses simulations, and have already expanded the tree a bit. Of the four steps in Monte Carlo Tree Search, which steps have to be done in every further iteration?
  **Selection Simulation Backpropagation**
  17. In regular MCTS, we do not store the states reached during the default policy phase. What would happen for a complex search problem if we would store them in the tree as well?
  **We would run out of memory quickly, Most of those states would be useless since they are never reached again, The shape of the tree would become extremely unbalanced**
  18. In the root of a tree of depth 1, the UCT formula is identical to the UCB formula.
  :white_check_mark: 
  19. The Max­Robust child move selection method sometimes extends the search to decide the move to play.
  :white_check_mark: **We need to determine better move between move with higher winrate and more visited count if two moves are different**
  20. Selecting the move to be played after a search according to highest winrate is the most popular method in MCTS.
  :x: **The most popular method in MCTS is according to the visit count**
### Quiz 10
#### Machine learing introduction(Lecture 17)
  1. Assume we have already learned a move generation policy. Then it is easy to convert this policy into a state evaluation function.
  :x: **policy cannot be converted to evaluation function**
  2. Tabular learning can be used to improve some game­playing programs.
  :white_check_mark: 
  3. To get good results for move prediction in Go, a learning program must be able to generalize from the given training data.
  :white_check_mark: 
  4. Unsupervised learning is learning without training data.
  :x: **Unsupervised learning is learning without label on training data**
  5. A rule of thumb is to re­use 10% of your training data as test data.
  :x: **Use 10% of data from the original dataset as test data**
  6. Overfitting can be caused by the learning algorithm being confused by the noise in the training data.
  :white_check_mark: 
  7. Overfitting means that the learned function over­specializes to the training data.
  :white_check_mark: 
  8. In linear regression we try to fit the training data as well as possible to a given line.
  :x: **We try to find best function to approximate the data**
  9. Machine learning sometimes works with raw input data, so we do not always need to develop other input features.
  :white_check_mark:  **Raw input in neural network**
#### Machine learning(Lecture 18)
  10. In a linear model, weights represent the strength of connection between features.
  :x: **Weights reprensent the strength of the feature, larger weight means better feature**
  11. Neural networks are a special case of linear regression methods.
  :x: **Neural networks are a kind of function**
  12. A Go program can learn feature weights even from games that it played itself.
  :white_check_mark:
  13. A better move predictor can sometimes lead to a worse overall player, when it is used as knowledge inside MCTS.
  :white_check_mark:
  14. One limit of move prediction is that different moves can have the same value, which makes it to hard to predict which one is chosen.
  :white_check_mark:
  15. One limit of move prediction is that human players may have different preferences and biases in complex situations.
  :white_check_mark:
  16. If a feature has ten different possible values, we can represent it by ten boolean features.
  :white_check_mark:
  17. Given a Go position p. The goal of learning feature weights is to find the move from p which has the single feature with the highest value.
  :x: **We use learned feature weights to select good moves in program**
  18. The Bradley­Terry model evaluates the strength of a group of moves.
  :x: **The Bradley­Terry model evaluates the strength of a group of features**
  19. In each iteration, the Minorization­Maximization (MM) Algorithm exactly solves an approximation of a difficult optimization problem.
  :white_check_mark: **MM finds an approximation function of the original function to optimize**
  20. In UCT with additive knowledge, the knowledge term added to the UCT score of the children of the root is larger at the beginning of a search than at the end.
  :white_check_mark:

### Quiz 11
#### Neural Network(Lecture 19)
  1. A neural network in Computing Science is a pretty accurate model of a neural network in the human brain.
  :x: **It is an approximate model not accurate**
  2. Synapses are smaller nerve cells which transmit information between neurons.
  :x: **Synapses are gap between nurons, not nerve cells**
  3. Most synapses transmit information only via electrical currents.
  :x: **Sometimes via chemicals as well**
  4. Humans have far more neurons than any animal.
  :x: **Elephant has more neurons than human**
  5. In the usual neural network architectures in computing science, all connections are between one layer of neurons and the next.
  :white_check_mark:
  6. A network can be trained by changing its weights to reduce the errors in the output.
  :white_check_mark:
  7. In the sigmoid function, if x is a large negative number, the value sigma(x) is close to 1.
  :x: **X close to 0**
  8. The sigmoid function is upper bounded by 1.
  :white_check_mark:
  9. There are different types of activation functions, but their most important property is that they are all linear.
  :x: **Some activation functions are not linear**
  10. In backpropagation, the amount of weight changes is computed from the partial derivatives of the error function.
  :white_check_mark:
  11. The chain rule simplifies the computation of the gradients of all weights in backprop.
  :white_check_mark:
  12. In Recurrent Neural Networks, the connection between neurons is changed from a tree structure to a DAG.
  :x: **From a tree to a DCG**
  13. In theory, Neural Networks with one hidden layer exist which can approximate any continuous function arbitrarily well.
  :white_check_mark:
  14. In the fully connected architecture, each neuron in a neural network is connected to each other neuron.
  :x: **Each neuron on layer n connected to each neuron on layer n+1**
#### Deep Learning(Lecture 20)
  15. A Convolutional NN is an example of a sparse NN.
  :white_check_mark:
  16. Deep Convolutional NN typically use a fully connected layer at the start of the processing pipeline.
  :x: **Use fully connected layer at the end of pipeline**
  17. The derivative for a ReLU Activation Function is simpler to compute than for a sigmoid function.
  :white_check_mark:
  18. Compared to move evaluation with simple features, Deep Convolutional NN typically return a larger number of good moves for one input position.
  :x: **DCNN focused on very small number of moves**
  19. The first Deep Convolutional NN trained by DeepMind was both deeper and larger than the net developed by Clark and Storkey.
  20. Consider the first Deep Convolutional NN developed by DeepMind, as described in the paper by Maddison, Huang, Sutskever and Silver. Claim: without any search, this network could win a majority of games against strong open source MCTS programs which ran 10000 simulations per move.
  :x: 
### Quiz 12
#### Reinforement learning and Alpha Go(Lecture 21)
  1. A single DCNN evaluation of a policy net produces a probability map for all moves on a Go board.
  :white_check_mark:
  2. The credit assignment problem is a central problem in both supervised and reinforcement learning.
  :x: **It's center problem of reinforcement learning only**
  3. The programs Neurogammon and TD­Gammon both apply Reinforcement Learning to learn neural networks for backgammon.
  :x: **Neurogammon use neural network and TDGammon use reinforcement learning**
  4. TD­Gammon uses search as well as neural network evaluation.
  :white_check_mark:
  5. In TD(lambda), rewards that are in the future count less than immediate rewards.
#### Alpha Go(Lecture 22)
  6. In the AlphaGo Fan version, the policy network trained with reinforcement learning has more neurons than the policy network trained with supervised learning.
  :x: **They have the same neurons**
  7. In the AlphaGo Fan version, the training process for the value network uses learning from labeled training data.
  :white_check_mark:
  8. When using only its neural networks without MCTS, AlphaGo Fan is almost as strong as when it uses MCTS.
  :x: **When using MCTS, AlphaGo Fan is much bettern than without MCTS**
  9. For move prediction, the AlphaGo Fan RL policy net works better than the SL policy net.
  :white_check_mark:
  10. The RL policy net in AlphaGo is trained using the TD(lambda) algorithm.
  :x: ****
