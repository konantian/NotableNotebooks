---
title: Questions
tags: [Notebooks/Cmput 496]
created: '2019-04-10T20:06:43.150Z'
modified: '2019-04-13T02:52:15.350Z'
favorited: true
pinned: true
---

# Questions
1. Why tree is easiest for search and DCG hardest, how about DAG?

**in tree everything is independent,only one parent for each node**
**a node have multiple parents in DAG,we need to update more nodes in backpropagation**
**In DCG,thre are cycles, the child can be in subtree of itself, a node has parent of itself. we cannot just compute the value directly**

2. Reasons for using DAG instead of DCG and tree?

**DAG can be much smaller and no cycles, no duplications**

3. Always interger komi in Go?
**not always integer for avoid draw**

4. Why different sequences, different states in tree model are duplication?
**value only depend on state not sequences. They are duplication because they are equivalent state, although they might have different history, it does not matter.**

5. Why single path to each node is advantage?
**less nodes to update, less computations,less complex**

6. Why dependencies are needed except tree?
**there are no overlap in tree but in DAG, overlap of subtrees, because mutiple nodes leads to same node**

7. Is the percentage of program that is speeded up before optimize or after?
**it's percentage of executation time of that part on total execution time of the whole program before optimize**

8. In winning stratey, in our turn, how to detect which is a winning move and which is not? Just consider one move or as well as the future?
**using search until to the leaf nodes, it's always win whatever opponent's response, it's guaranted to win the opponent, that's winning move**

9. Given candidate minimax value m, in what kind of situations we need only one search?
**If the search reuslt is one of the lower bound and upper bound, we can just stop here. Otherwise, we need at most two search to verify this value**

10. Why alphabeta_depth_limited_tictactoe_test.py is blind search?
**not using any heuristic funciton**

11. For PV, if there exist two proof trees, is that guaranted that there exist at least one intersection node for both proof trees?
**They always have intersection,for examples, few parents have common children, the root node**

12. Perfomance of minmax compare to negamax and Alphabeta?
**in the best case, first move is the winning move**
**difference between minimax and alphabeta is no pruning in minimax**

13. Tree estimates is exact at depth 0 ... 5?
**because in the best case, we only need 5 moves to win but formula will count 6.**

14. DAG: No savings at lower levels?
**saving is different path to same nodes, in lower levles, there are no same nodes**

15. Massive savings deeper in DAG, why?
**In deeper of DAG, there are many nodes are equivalent and different paths leads to them, which saved a lot of duplication nodes**

16. If strongest move is tried first, alphabeta or negamax, which is more effective?
**yes**

17. Why depth-limited search need evaluation function?
**using heuristic function to approximate the value**

18. Why winning strategy does not have to include a move for every state in current play's turn?
**not need to know the move in state that I am not play**

19. IS that true that every state in state space has a proof tree or disproof tree?
**depends on winning condisitions, in finite game tree, every state has proof tree or disproof tree**


20. What's the mean of variance and bias in monto carlo simulations?


21. Why using random simulaitons is much less natural and it still works well on games without chance element?
**not the best idea**

22. Why shuffle once is not enough in Tictactoe?
**Because every moves are legal, same with Gomoku**

23. In depth-limited search, how heuristic evaluation funciton works?


24. Why Sim(1000) can have better performance than perfect in TictacToe? How about other games?
**for other games, if the opponent is random player, it's still possible**

25. Why deterministic simulations are not better than random one?
**only simulation once in deterministic**

26. What's the extreme case for selective minimax search?
**it's always heuristic search**

27. Why run one simulations in root node of MCTS? More simulations?

28. Steps shoudld be done during each iteration of middle of MCTS? Why backpropagation?
**For each iterations, it contains selection simulation and backpropagation, since it has to reach the terminal states in each iteration and back up the value from bottom to root node**

29. In the root of a tree of depth 1, why UCT and UCB are same?

30. How to solve the first problem of MCTS?

31. Why we use severl copies of the layer to learn more features?

32. Do we use move predictor in MCTS?

33. Why each layer can only learn one feature?

34. In DNN, the fully connected layer are at top layer, is that same as start of the processing pipeline?

