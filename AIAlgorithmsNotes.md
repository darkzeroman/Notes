
######Type A:
 
consider all moves for a fixed number of turns in the future and determine the best move. Select the initial move for that path. Determine players' future moves and move favorable positions. [MiniMax, AlphaBeta, NegMax]

######Type B: 

Adds some adaptive decision based upon the knowledge of the game rather than static evaluation functions. Have some reasoning. Adaptive decision based upon knowledge of the game rather than static evaluation functions. Explore more real choices than useless ones. [Iterative Deepening]
	


######A* Search

* Equation: f = g + h
* g : estimates shortest sequence of moves from initial state to n
* h: estimates shortest sequence of moves from n to the goal state
* f: estimates shortest sequence of moves from initial to goal state through n
* h(n) : the estimate should be less than or equal to the real value, or admissible.
* g(n): should be equal or greater than the real value
* if h = 0, then A* is Dijkstras

Iterative Deepening: state search strategy uses repeated iterations of limited depth-first search, with each iteration increasing the depth limit.  Reduces non-productive searching.

