#**REINFORCEMENT LEARNING FOR TIC-TAC-TOE GAME**#

**Objective**
The objective of the lab is to use RL for training an agent at playing tic-tac-toe game.

**Strategy**
The strategy used is a model-free one, in particular the On-Policy Monte-Carlo control has been used.
The idea is to compute for each pair (state,action) a value that is proportional to the probability of winning the game from that state making that specific action. 
Using the MC method the agent learns from complete episodes, just at the end of the game. In this sense, the value Q(s,a) is updated toward the *ACTUAL* return. The updating of the dictionary that contains the state-action values occurs every episode.

During the training games the agent can have two possible approaches in choosing the next action:
1) Random Approach: starting from a given state it decides the next move choosing randomly among all the available moves.
2) Greedy Approach: starting from a given state it decides the next move based on the state-action dictionary, selecting the move that has the highest value.

It is necessary to keep both the approach for the *EXPLORATION VS EXPLOITATION* trade-off, in order to ensure continual exploration. It is handle through the *epsilon parameter*: with probability epsilon the agent make a random move, with probability 1-epsilon the agent chooses the greedy action. In addition, the probability of doing random actions decreases over the training.

**Training and Testing**
The training has been split in three branches:
1) Training of an agent that starts the game with the following setting for the reward (win = 1, lose = -1, draw = 0)
2) Training of an agent that does not make the first move with the following setting for the reward (win = 1, lose = -1, draw = 0)
3) Training of an agent that does not make the first move with the following setting for the reward (win = 1, lose = -1, draw = 2)


For the final type of agent, the concept of assigning a reward of 2 in the event of a draw arose from the observation that the first player in a tic-tac-toe game has a higher likelihood of winning. Consequently, the optimal strategy might involve not actively seeking victory but rather focusing on avoiding defeat.
It has been observed that when an agent is trained with the objective of winning when not playing as the first player, it consistently experiences losses. Conversely, when the agent is trained by placing greater emphasis on draws, it avoids losses altogether.

**Improvements**
It could be useful inserting in the game some implicit rule in order to give also immediate rewards and not just final one, passing from a model-free to a not model-free algorithm.
Of course, in order to do that it is necessary knowing the best strategies of tic-tac-toe.

At the end of the code, it is also present a function to play against the agent. It is not so intuitive but could be interesting to acknowledge if the agent has reached a good level of 'smartness'.
