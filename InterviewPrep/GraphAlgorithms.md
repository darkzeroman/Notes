This needs a lot of work

# Graph Search

Floyd's cycle-finding algorithm:

* Coloring Algorithm:
* Hopcroft-Karp Algorithm
    * takes as input a bipartite graph and produces as output a maximum cardinality matching – a set of as many edges as possible with the property that no two edges share an endpoint.
* Topological Sort:

Euclidean Minimum Spanning Tree:

* Longest Path Problem: simple path of max length in a given graph, NP Hard

MST:

* Kruskals: sparse graphs, O(E log V)
    * Add lowest cost edges until all vertices are connected.
* Prim's: dense graphs, O(E log V)
    * Start with a vertex, find edge with the lowest weight and add to tree. Continue by adding all edges with the lowest weight until all vertices are in tree.


Shortest Path Problem:

* Bellman-Ford algorithm: single source shortest paths, edges may be negative
    * Detects negative cycles, but if there is one, answer is not correct
* Djikstra's algorithm: non-negative edge weights
* Floyd-Warshall algorithm: all pairs shortest path problem 
	

Increase the number of edges in the path, increases the set of vertices we allow as intermediate nodes in the path.

Starting from the same base case (the shortest path that uses no intermediate nodes), we'll go on to consider the shortest path that's allowed to use node 1 as an intermediate node, the shortest path that's allowed to use {1,2} as intermediate notes, and so on.

Bellman Ford Algorithm



# AI Algorithms

######Type A:
 
consider all moves for a fixed number of turns in the future and determine the best move. Select the initial move for that path. Determine players' future moves and move favorable positions. [MiniMax, AlphaBeta, NegMax]

###### Type B: 

Adds some adaptive decision based upon the knowledge of the game rather than static evaluation functions. Have some reasoning. Adaptive decision based upon knowledge of the game rather than static evaluation functions. Explore more real choices than useless ones. [Iterative Deepening]
	


###### A* Search

* Equation: f = g + h
* g : estimates shortest sequence of moves from initial state to n
* h: estimates shortest sequence of moves from n to the goal state
* f: estimates shortest sequence of moves from initial to goal state through n
* h(n) : the estimate should be less than or equal to the real value, or admissible.
* g(n): should be equal or greater than the real value
* if h = 0, then A* is Dijkstras

Iterative Deepening: state search strategy uses repeated iterations of limited depth-first search, with each iteration increasing the depth limit.  Reduces non-productive searching.

