---
title: 'Lecture 21 - RL,AlphaGo and Beyond'
tags: [Notebooks/Cmput 496]
created: '2019-03-29T03:35:41.688Z'
modified: '2019-04-13T03:25:00.032Z'
---

# Lecture 21 - RL,AlphaGo and Beyond
### Basic Concepts of RL
  * Observe input(state of game)
  * Produce move,action
  * Observe reward(quality of action)
  * Often, the reward is delayed(reward only at tend of game)

### Basic concepts of RL in Games
  * Play a game from some state s until the end
  * Receive reward at the end
  * Use that reward to learn about the quality of the individual moves played

### Credit Assignment Problem
  * Reward for long sequence of decisions
  * No direct reward for each single move decision
  * How can we tell which moves are good or bad?
  * Distribute reward from end of game over all actions
  * Main idea: iif same action happens in many different sequences, we can learn if it leads to more wins or losses

### RL vs Supervised Learning in Games
  * Supervised Learning
    * Label for each move
        * Good/bad, expert move/not expert move
    * Learn - minimize prediction error on given data set
    * Can use mathematical optimization techniques
  
  * Reinforcement Learning
    * Reward for whole game sequence only
    * Learn - try to improve gamplay by trial and error
    * Need to solve the credit assignment problem
  
## Backgammon
### Neurogammon Architecture
  * Six separate networks, for different phases of the game
  * Fully connected feed-forward nets
  * One hidden layer Trained with backprop
  * Supervised learning from 400 expert games
  * One more network to make doubling cube decisions
  * Trained on 3000 positions, hand-labeled
  * **Limitations**
    * Hand-engineered features are difﬁcult to create 
    * Human experts cannot explain much of what they are doing in a form that can be programmed 
    * Human expert games are difﬁcult to collect, and are not perfect

### TD-Gammon
  * Training by self-play
  * Learns from the outcome of games
  * Uses Temporal Difference(TD) learning
    * A technique for function approximation by RL
  * Much stronger than Neurogammon
  * **Close to top human players**
  * Changed opening theory
  * Changed the way the game is played by human experts
  * Small(1-3ply) Alphabeta search

### Computer Backgammon Now
  * Programs generally follow the TD-Gammon architecture
  * Bigger,faster, longer training
  * Endgame databases with exact winning probabilities
  * Considered almost perfect
  * **Much stronger than humans**

### TD Learning and TD($\lambda$)
  1. Learn a model
  2. Given only action sequences and rewards
  3. Learns a prediciton(what is the best move)
  4. Samples the environment(plays games)
  5. Compare learned estimate in each state with reward
  6. Learns from the difference
  7. Discount factor $\lambda$ for future rewards
  8. The sooner after the current state the reward happens, the higher the effect
  * TD high-level ideas
    * Usually, predictions from states closer to the end are more reliable
    * Bootstrapping - learn predictions from other predictions
    



