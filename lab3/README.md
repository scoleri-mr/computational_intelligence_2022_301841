# Lab 3 
The goal of this lab is trying different approaches to train an agent to play Nim. 
We refer to the version of Nim in which the player that takes the last object wins and we don't pose a limit to the number of objects that can be taken in one move. More details about the game can be found [here](https://en.wikipedia.org/wiki/Nim). 

## Collaboration
The code in this folder is developed in collaboration with  
- Jonathan Damone (s301514)
- Salvatore Licata (s295798)

## Sources
- The starting code for this lab is written by professor Squillero and can be found in [this](https://github.com/squillero/computational-intelligence/blob/master/2022-23/lab3_nim.ipynb) file.
- The code for the genetic algorithm is the same one presented in [lab2](https://github.com/scoleri-mr/computational_intelligence_2022_301841/blob/main/lab2/lab2_set_covering_GA.ipynb).
- The min max strategy was implemented beginning with the work presented on [this website](https://realpython.com/python-minimax-nim/#lose-the-game-of-nim-against-a-python-minimax-player).
- Reinforcement learning was written starting from the code presented in class.
## 3.0: basic hard coded rules
To better understand the problem and implement a first approach to play the game we use some very basic hard coded rules. In particular:
- If we only have two lines left (with a number of objects greater than 0) the player should always make the move that makes those two lines contain the same number of objects. This way, whatever the other player does, the first player can mirror that move on the other row and always win.
- If the sum of the remaining objects in all the rows is odd the player should make a move that will make this sum even.
- If we are not in one of the two described situations the player can either take all the objects from the shortest row (with probability p) or from the longest row (with probability 1-p).  

These simple hard coded rules allow us to win almost every game played against both the pure random and the optimal strategy.

## 3.1: An agent using fixed rules based on nim-sum (i.e., an expert system)
We create a fixed strategy based on nim-sum. This strategy returns the move chosen by the optimal_strategy if there is a move to be made with nim_sum=0.
In case there is no optimal move the fixed strategy uses the hard coded rules written in point 3.0. This way even if there is no optimal move to be made the strategy will still make a move that does not benefit the opponent.  
Evaluating this strategy we see that it wins all the maches against both the random and the optimal_strategy.

## 3.2: An agent using evolved rules
We use a genetic algorithm that allows us to chose a certain linear combination of different rules. The fitness function is calculated evaluating the genome (combination of rules) against a semi-optimal strategy and against a random strategy.
The semi-optimal strategy behaves like the optimal strategy 80% of the times and like the random strategy the remaining 20%.  
I chose to not use the optimal strategy for the fitness in order to give a winning chance to the strategy found by the GA.
More details can be found in the [code](https://github.com/scoleri-mr/computational_intelligence_2022_301841/blob/main/lab3/lab3.ipynb).  
The evolved strategy wins more than 80% of the matches against the pure random, about half of the matches against the semi-optimal and of course loses against the optimal.

## 3.3: An agent using minmax
For this task we use the minmax technique with alfa-beta pruning and (possibly) a maximum depth. To improve the performance especially in terms of computation time we also save the sates and their scores in a cache.  
To avoid generating a new cache every time we play a game, we save in different files the caches corresponding to different nim_sizes using the pickle library. This way we only need to play one game for each nim_size to generate and save a cache that can be reused for every following game with the same size. Saving and loading caches will save us large amount of times especially for bigger nim_size: for example with 7 rows we can play a game in under two seconds.  
So far we generated the caches for nim_size up to 7. Note that to generate the caches we did not use a bound; for larger values of nim_size it becomes very difficult to play even one game without a bound so for a game with more rows we would need to use a bound.

## 3.4: An agent using reinforcement learning
We train an agent against the optimal strategy using the reinforcement learning tecnique. We choose to train using the optimal strategy because training against the random or the semi-optimal never allows us to win against the optimal strategy.
The algorithm is develped as follows:
- the `choose_move` function returns the move to be made. It chooses the move randomly with a probability given by the random_factor, otherwise it chooses the move with the highest reward.
- the `learn` function updates the rewards using the provided learning rate.
- the `reinforcement_learning` function assigns a negative reward to the states that lead to a lost game against the optimal strategy and assigns 1 to the states that allow the reinforcement learning agent to win. 
We perform a parameter tuning choosing from different values for the random factor and learning rate. This tuning shows us that unfortunately changing these parameters does not affect the performance of the agent in a significant manner. Still, we choose the best performing values ad use them to train the model.  

We manage to win more than 55% of the games against the optimal strategy, around 1% against the optimal and around 20% against the semi-optimal.

## Final results
Here I will present some of the results obtained evaluating different strategies against each other. Please keep in mind that the several random choices in our methods make it almost impossible to replicate the exact same result every time we run the code. The percentages shown here may vary.
`hard coded strategy VS random strategy -> hard coded wins 96%`  
`hard coded strategy VS optimal strategy -> hard coded wins 96%`  
`fixed optimal strategy VS random strategy -> fixed optimal wins 100%`  
`fixed optimal strategy VS optimal strategy -> fixed optimal wins 100%`  
`evolved strategy VS random strategy -> evolved wins 84%`  
`evolved strategy VS semi-optimal strategy -> evolved wins 47%`  
`evolved strategy VS optimal strategy -> evolved wins 0%`  
`minmax strategy VS random strategy -> minmax wins 100%`    
`minmax strategy VS optimal strategy -> minmax wins 54%`  
`reinforcement learning strategy VS random strategy -> reinforcement learning wins 61%`  
`reinforcement learning strategy VS optimal strategy -> reinforcement learning wins 1%`  
`reinforcement learning strategy VS semi optimal strategy -> reinforcement learning wins 19%`