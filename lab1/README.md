# LAB1
The complete solution can be found in [lab1.ipynb](https://github.com/scoleri-mr/computational_intelligence_2022_301841/blob/main/lab1/lab1.ipynb)

# About our work
## Enhanced Greedy
The first approach considered is a modified greedy algorithm. Even though this approach is not optimal it gives a satisfactory performance both in terms of visited nodes and computation time. The bloat, as we will see in the results, grows alongside N but it’s still acceptable. The “standard” greedy approach would be to just get a subset that discovers the most numbers; in our approach, we considered the lengths of the lists as a parameter to choose the lists as well.  
`subset=max(P_sets, key=lambda s: len(s-covered)/lengths[P_sets.index(s)])`  
With this line, we run through every set in P_sets and find a set s that discovers a lot of new numbers while also maintaining a lower length. 
## Combinations
The second approach can be considered “brute force”. It simply computes all the possible combinations of lists and in the end chooses the combination of lists in which the total number of elements is minimal. 
This technique is optimal but it’s very inefficient and (on my device) it can only run for up to N=20. If we attempt to run this code for N=100 we predictably obtain a memory allocation error. 
## Graph Search
The other approach considered is a graph search with the use of a priority queue and a frontier. It’s an implementation of the Dijkstra algorithm that searches for the shortest path. In this case, the path is the subset of lists that allows us to cover all the elements from 0 to N and contains the least number of elements. The algorithm at the beginning adds all the lists to the frontier with associated cost = 0. Then for each list, it adds every other list and computes the cost for each couple of lists. The cost is the number of repeated elements in the current state. The algorithm keeps searching for the best solution; every time it computes the cost for all the neighbors of the current node it removes the current node from the frontier until it’s empty. At the same time, it saves the shortest path (in our case the subset of lists with the minimum number of elements) to reach a certain state, so in the end we will have the best subset that allows us to reach our goal with the minimum possible repeated numbers. 
## Vanilla Hill Climber (after deadline)
Hill climbing is a mathematical technique used to optimize a certain objective function. We start with a random solution to the problem and we make small (random) tweaks of the solution. At every step we evaluate the state we are currently in to move in the direction that allows us to maximize the objective function. In our case the evaluation is based on two parameters: the number of discovered elements and the number of repeated elements. We want to maximize the first and minimize the second; which is why our evaluation function returns a tuple with (discovered elements, - repeated elements). The chosen function to tweak the solution removes a random list from the current solution with a probability of 70% and adds a random list to the solution (still with a 70% robability).
## (1+1) Evolution Strategy (after deadline)
This approach is the simplest possible evolution strategy since it only involves one parent and one child. The code is almost identical to the one of the vanilla hill climber presented above. The only difference is the tweak function used to change the solution. In this case, with a 70% probability, we remove a random list r from the solution, we find the index of r in the problem P (which is a list of lists) and add to this index a random number obtained sampling a normal distribution with mean=0 and standard deviation = SIGMA. The result is used as index to select a new list to add to the solution. 


## Collaboration
This work was completed in collaboration with
- Jonathan Damone (s301514)
- Salvatore Licata (s295798)

## Sources
The greedy solution was implemented starting from the code in [Set-Cover-problem-solution-Python](https://github.com/AndreaRubbi/Set-Cover-problem-solution-Python/blob/master/Greedy.py)  
The Graph Search is based on the [8puzzle](https://github.com/squillero/computational-intelligence/blob/master/2022-23/8-puzzle.ipynb) search function

## Results
### Greedy:
Optimized solution for N=5: w=5 (bloat=0%), nodes visited=5  
Optimized solution for N=10: w=12 (bloat=20%), nodes visited=5  
Optimized solution for N=20: w=30 (bloat=50%), nodes visited=6  
Optimized solution for N=100: w=171 (bloat=71%), nodes visited=8  
Optimized solution for N=500: w=1256 (bloat=151%), nodes visited=12  
Optimized solution for N=1000: w=2913 (bloat=191%), nodes visited=13

### Combinations:
Optimized solution for N=5: w=5, nodes visited=2600  
Optimized solution for N=10: w=10, nodes visited=251125  
Optimized solution for N=20: w=23, nodes visited=1676081  

### Graph Search:
N = 5 found a solution with 5 elements; visited 32 states over 775 generated states  
N = 10 found a solution with 10 elements; visited 583 states over 29100 generated states  
N = 20 found a solution with 23 elements; visited 2864 states over 97342 generated states  

## Work afted deadline
### Vanilla Hill Climbing Search
Solution for N=5: w=5 (bloat=0%)  
Solution for N=10: w=11 (bloat=10%)  
Solution for N=20: w=24 (bloat=20%)  
Solution for N=100: w=214 (bloat=114%)  
Solution for N=500: w=1566 (bloat=213%)  
Solution for N=1000: w=3383 (bloat=238%)  

### (1+1) Evolution Strategy
Solution for N=5: w=5 (bloat=0%)  
Solution for N=10: w=13 (bloat=30%)  
Solution for N=20: w=28 (bloat=40%)  
Solution for N=100: w=205 (bloat=105%)  
Solution for N=500: w=1566 (bloat=213%)  
Solution for N=1000: w=3692 (bloat=269%)  