Folder with labs and project for the computational intelligence 2022/2023 course
## Collaboration
The code in this folder is developed in collaboration with  
- Jonathan Damone (s301514)
- Salvatore Licata (s295798)
## LAB1
Set Covering solution implemented in python using 
- greedy algorithm (not optimal but feasible for N=1000)
- combinations (memory error for N greater than 20)
- graph search (computation time excessive for N greater than 20)  

(after deadline)
- vanilla hill climbing  
- (1+1) Evolution Strategy

### LAB1 reviews:
- [assigned review](https://github.com/RaminHedayatmehr/CI-2022-23/issues/2)
- [review of my choice](https://github.com/GabriG23/computational-intelligence-2022-2023-s303435/issues/1)

## LAB2  
Solution to the set covering problem using a genetic algorithm.  
Tried with:
- fusion crossover
- one point cut crossover
- probability to have crossover fixed at 0.7 (and 0.3 for mutations)
- increasing probability to have a mutation and decreasing probability to have crossover with the passing of generations
- parameter tuning
- plot to show the convergence of the algorithm for N=100

### LAB2 reviews:
- [review 1](https://github.com/angelicaferlin/computational_intelligence_2022/issues/4)
- [review 2](https://github.com/Eliafontana/Computational_Intelligence_2022-23_S290188/issues/3)

## LAB3
Train agents to play the game of Nim.
- 3.0: Basic hard coded rules to better understad the game and some appropriate strategies
- 3.1: An agent using fixed rules based on nim-sum (i.e., an expert system)
- 3.2: An agent using evolved rules. We use a GA to find a linear combination of some rules that will create a player able to win against a random strategy and against a semi-optimal strategy  
- 3.3: An agent using minmax with alpha-beta pruning and a maximum depth. We also use a cache to improve performance in terms of games won and computation time. The caches for different nim_size are saved and loaded to play future games with the same nim_size even faster.
- 3.4: An agent using reinforcement learning trained against the optimal strategy. We perform a parameter tuning on the random factor and the learning rate. 

### LAB3 reviews:
- [review 1](https://github.com/FlavioPatti/Computational-Intelligence_2022-23/issues/8)
