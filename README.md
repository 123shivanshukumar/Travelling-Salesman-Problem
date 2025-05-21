# Travelling-Salesman-Problem
A project on developing a heuristic algorithm for the famous [Travelling Salesman Problem](https://en.wikipedia.org/wiki/Travelling_salesman_problem). 

### The Problem 
Given a list of cities with pairwise distance given between them ( basically a positive weighted undirected and complete graph), what is the minimum distance Hamiltonian cycle i.e., a path that starts at a city and ends at the same one, covering each city exactly once. The problem has been shown to be [NP Hard](https://en.wikipedia.org/wiki/NP-hardness) by Richard Karp. 

**Our Setting**: We consider an 2D cartesian system with the coordinates of cities given to us. We aim on developing heuristic solutions that run in polynomial time.

### Our approach:
1. We first analyse a traditional heuristic called [Simulated Annealing](https://en.wikipedia.org/wiki/Simulated_annealing). This is a greedy heuristic which trades off between exploration and exploitation. First a random cycle is initialised, and for several iterations we do the following: swap two aribitrary cities in position, accept even if the total distance increases, with some probability. This probability decreases as the algorithm proceeds, making it rigid to changes while allowing it to explore in the initial phases. This helps preseve local optimality as well as expands our search space. Since the complexity of this approach depends on the number of iterations (intial temperature), it is a [pseudo-polynomial time](https://en.wikipedia.org/wiki/Pseudo-polynomial_time) algorithm.
2. **Polar optimisation**: Simulated annealing is computationally expensive and needs a lot of iterations to come to a good solution. We devise an algorithm called polar optimisation: we start at a city that is closest to the centroid of the cities, and then iteraitvely : look at the two nearest cities that make the least **angle** with this city.Among these two we choose the city with the minimum angle. We now connect this with the original city and delete it. We repeat the procedure till only one city is left. Here angle refers to the angle made between two line segments with one endpoint as the centroid.\ Next we go through the cities in a serial order, take a city adjacent to a chosen city, and swap the neighbors of this pair if the overall distance decreases.\ We also extend this to an optimisation based on a triple of cities, instead of a pair.\ Empirically, the two optimisations applied one after the other for about 5 - 7 iterations gave results close to (1) on average. In fact we able to outperform (1) on some instances. This algorithm is polynomial (quasilinear) in the number of cities.
3. Using convex hulls: We also try to form series of [Convex Hulls](https://en.wikipedia.org/wiki/Convex_hull) and disconnect the largest path formed in between the points of the convex hulls as an alternate approach. Although this does not perform well on the minimisation version of the problem but we think this might a non trivial way to solve the maximisation version of the problem.

The methods have been described in detail in the [Report](Travelling_Salesman_Problem.pdf)

Also attached are some cool animations in the [animations](animations) directory. 

### Contributors
- [Shivanshu Kumar](https://github.com/123shivanshukumar/)
- [Ventrapragada Krishna Sameer](https://github.com/VentrudingMeitantei)
- [Deenabandhan](https://github.com/Deenabandhan)
