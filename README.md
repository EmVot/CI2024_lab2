# CI2024_lab2
Laboratory 2 for Computational Intelligence Course

## General overview
The file <lab2-ipynb> contains the solution of the laboratory; in the <Logs> folder you can find costs and steps for all the solutions, organized as:
+ Greedy logs: which containts the journey calculated a vaery simple greedy algorithm

## Code structure
The solution take in considerations two approaches to solve the TSP:
1. A greedy algorithm whihch takes in consideration only the relative distance between the current city and the next candidate one
2. A more refined algorithm which is capable of making smarter decisions
   
## Proposed solutions analysis
Since the TSP is known for being an NP-H combinatorial problem, I propose two sets of algorithms capable of finding a sub-optimal solution. Data can be found at:
 https://github.com/squillero/computational-intelligence/tree/master/2024-25/cities

### Simple greedy solution
The first solution is a very simple and fast greedy algorithm; it makes decisions considering the nearest city not yet visited.
Acknowledging that the algorithm is quite identical to the one proposed by the professor, it is actually the most efficient in terms of computational time, and since the focus of this laboratory verges on the second algorithm I did not changed it since solving the TSP using other heuristics like MSTs already gives very good solutions and are not as simple as requested.

### Solution which implements EA strategies 


## Experiments and conclusions
The results of all the expreiments are stored in the <Logs> folder, divided by proporsed algorithm. 
All of the results are comapred to the ones reported at:
https://www.wolframcloud.com/obj/giovanni.squillero/Published/Lab2-tsp.nb
taken for comparison metric

### Simple greedy solution
The greedy solution is not able to provide a good approximation of the best solution even wiith a very limited set of cities, like that in Vanutau.
This might be explained by the very nature of a 'greedy algorithm', i.e. at the very end of the process in inevitably will be forced to visit most distant cities, whihc increase a lot the travel time being very likely one of the furthest from the last visited one.
The results are shown below:
| Country | Best Solution Provided by Wolfram | Greedy Solution | Steps |
|---------|-----------------------------------|------------------|-------|
| Vanuatu | 1345.54                           | 1475.53         | 8     |
| Italy   | 4172.76                           | 4436.03         | 46    |
| Russia  | 32722.5                           | 42334.16        | 167   |
| USA     | 39028.59                          | 48050.03        | 326   |
| China   | NULL                              | 63962.92        | 726   |




## Conclusions

 
