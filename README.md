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

## LAB2  
Solution to the set covering problem using a genetic algorithm.  
Tried with:
- fusion crossover
- one point cut crossover
- probability to have crossover fixed at 0.7 (and 0.3 for mutations)
- increasing probability to have a mutation and decreasing probability to have crossover with the passing of generations
- parameter tuning
- plot to show the convergence of the algorithm for N=100

## LAB3
Train agents to play the game of Nim.
- 3.0: Basic hard coded rules to better understad the game and some appropriate strategies
- 3.1: An agent using fixed rules based on nim-sum (i.e., an expert system)
- 3.2: An agent using evolved rules. We use a GA to find a linear combination of some rules that will create a player able to win against a random strategy and against a semi-optimal strategy
