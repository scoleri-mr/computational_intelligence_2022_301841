# LAB1
The complete solution can be found in [lab1.ipynb](https://github.com/scoleri-mr/computational_intelligence_2022_301841/blob/main/lab1/lab1.ipynb)
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
