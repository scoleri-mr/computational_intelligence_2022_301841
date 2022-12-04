# Lab 3 
The goal of this lab is trying different approaches to train an agent to play Nim. 
We refer to the version of Nim in which the player that takes the last object wins. More details about the game can be found  [here]('https://en.wikipedia.org/wiki/Nim'). 

## Collaboration
The code in this folder is developed in collaboration with  
- Jonathan Damone (s301514)
- Salvatore Licata (s295798)

## Sources
The starting code for this lab is written by professor Squillero and can be found in [this]('https://github.com/squillero/computational-intelligence/blob/master/2022-23/lab3_nim.ipynb) file.

## 3.0: basic hard coded rules
To better understand the problem and implement a first approach to play the game we use some very basic hard coded rules. In particular:
- If we only have two lines left (with a number of objects greater than 0) the player should always make the move that makes those two lines contain the same number of objects. This way, whatever the other player does, the first player can mirror that move on the other row and always win.
- If the sum of the remaining objects in all the rows is odd the player should make a move that will make this sum even.
- If we are not in one of the two described situations the player can either take all the objects from the shortest row (with probability p) or from the longest row (with probability 1-p)

## 3.1: An agent using fixed rules based on nim-sum (i.e., an expert system)
For this task we use a genetic algorithm that allows us to chose a certain linear combination of different rules. The fitness function is calculated evaluating the genome (combination of rules) against a semi-optimal strategy and against a random strategy.
I chose to not use the optimal strategy for the fitness in order to give a winning chance to the strategy found by the GA.
More details can be found in the [code]('https://github.com/scoleri-mr/computational_intelligence_2022_301841/blob/main/lab3/lab3.ipynb')
