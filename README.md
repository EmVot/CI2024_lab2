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
This solution tries to implement the strategies of evolutionary algorithms seen during the course till October 31st.

Let's begin with the definition of the individual and its genotype: the individual is coded as the (ordered, of course) sequence of visited cities, i.e. using a fixed length integer array. I chose this representation based on the following factors:
1. its structure semplicity, in terms of:
   + Computational cost: as calculating the cost of the arcs is a direct access to the cost matrix, and the representation is a simple vector of integers instead of more complex data structures as tuples or sets
   + Readness: The 'readness' of the inidividual may seem abstruse in terms of vectos of cities, but since the transaltion is quite simple (again, a direct access to a transaltion matrix), the individual phenotype benefits of a very simple mapping.
2. its simple manipulability: while developing genetic algorithms which involve crossovers, mutations etc... it is very convinient having some data structure which is easy to maipulate, and an array of integers is the simplest genomes collection we can work on
3. its intrinsic information encoding: since genes ordering *the* key element of the TSP, sequence order must be a 'must-be' information carrier in the genotype; the natural ordering of integers encodes this property effectevly and elegantly, avoiding more complex comparisons we should develop whith other represenataions. Moreover is the best theoretical representation for 'one-time items' problem approach, which aims to find the best order with no repetition.

Let's move on to the choice of evolution strategies in terms of mutations and crossovers
For one-time items representation we can choose mutuation strategy among:
+ Swap
+ Scramble
+ Insert
+ Inversion

Approaching TSP the best suited choices seem to be:
1. Insert: as preserves most of the relative order, which assumes more importance as the starting point for the algorithm will be the solution found with the first-defined greedy algorithm
2. Inversion: because swapping the starting and ending point may (very unlikely) be the key element to escape local minima

With regard to crossover strategies, serveral choices are available, but as suggested by the professor, we try to implement the *Inver Over Crossover (IOX)*.
According to the professor IOX tested on some quite complicated problem outeprformed sub-optimal algorithms. Moved by curiosity I tried implementing another crossover strategy and benchmarking them; for this purpose the *Partially Mapped Crossover (PMX)* is selected, because of its natural fitness for the problem: In PMX, in fact, the idea is to preserve relative positions and partial sequences from two parent solutions, creating offspring that inherit ordering constraints.

Now let's consider the popoulation management model.
For the population management a modern GA flow is chosen, i.e:
+ Select parents
+ Perform crossover to generate offspring
+ Mutate the offspring with a probability p_m (implemented in the mutaions definitions)

For the parent selection the 'Tournament selection' strategy is chosen, sinc it does not require population ordering and the selective pressure can be easly adjusted.
Therefore a 'Steady state' model [(mu+lambbda)-ES] will be deployed.






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

 
