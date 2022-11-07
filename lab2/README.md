# Lab 2
The goal of this exercise is to solve the non uni-cost set covering problem with a genetic algorithm.

## Collaboration
The code in this folder is developed in collaboration with  
- Jonathan Damone (s301514)
- Salvatore Licata (s295798)

## Sources
The necessary material to develop this code was found in [this](https://github.com/squillero/computational-intelligence/tree/master/2022-23) folder and in particular using the [one-max](https://github.com/squillero/computational-intelligence/blob/master/2022-23/one-max.ipynb) file.
The fusion function used as crossover is the implementation of the one found in [[1]](#1).

## Evolution Algorithm
- cross-over functions:
    - crossover: basic cross-over tecnique that receives the two parents, cuts randomly the genomes of the parents p1 and p2 in the same position and then it concatenates the first part of p1 with the second part of p2.
    - fusion: based on the work in [[1]](#1). It checks bit by bit the two parents: if the corrisponding bits are equal the child will have the same bit in the same position, if the parents' bits are different the child will have with higher probability the bit that belongs to the parent with higher fitness.

    The fusion cross-over is computationally very expensive since it has to compare the two parents and create the child bit by bit. It produces slightly better results especially for smaller N.

- Mutation: we use a mutation function that randomly changes only one list from the parent.  
As the algorithm starts to converge and the crossover does not bring any significant improvement, increasing the mutation rate should lead to better results.
We tried gradually increasing the probability to have a mutation with respect to the crossover and the results are slightly improved.

## Parameter tuning
- tournament_size: this parameter was kept to 2 as adviced in [[1]](#1)
- population_size and offspring size: tuning performed with the standard crossover (for all given values of N) and with the fusion crossover (up to N=100). It's relevant to notice that the best results are obtained with offspring size greater than population size. 
- for the purpose of this lab I selected 30 as the maximum number of allowed generations with no further improvement (after 30 generations with no improvement the search stops). This value could further be tuned.


## Results
Here are presented the best results obtained with the standard crossover, the tuning of population and offspring size and a variable probability for crossover/mutation. For other results and more relevant details refer to the [code](https://github.com/scoleri-mr/computational_intelligence_2022_301841/blob/main/lab2/lab2_set_covering_GA.ipynb).  
`DEBUG:root: Solution found for N=5: w=(5, -5) (bloat=0%) after 40 generations. Evaluate called 400 times.`  
`DEBUG:root: Solution found for N=10: w=(10, -10) (bloat=0%) after 35 generations. Evaluate called 770 times.`  
`DEBUG:root: Solution found for N=20: w=(20, -23) (bloat=15%) after 90 generations. Evaluate called 1260 times.`  
`DEBUG:root: Solution found for N=100: w=(100, -183) (bloat=83%) after 43 generations. Evaluate called 17845 times.`  
`DEBUG:root: Solution found for N=500: w=(500, -1442) (bloat=188%) after 62 generations. Evaluate called 66836 times.`  
`DEBUG:root: Solution found for N=1000: w=(1000, -3400) (bloat=240%) after 84 generations. Evaluate called 277200 times.`  

## References
<a id="1">[1]</a> 
J.E. Beasley *, RC. Chu. A genetic algorithm for the set covering problem. European Journal of Operational Research 94 (1996) 392-404.
