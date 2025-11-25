# N-Queens Solver — AI Search Techniques (CSP, Local Search, Informed Search)

A comprehensive implementation and comparative analysis of **six AI search algorithms** to solve the generalized **N-Queens Problem** (4 ≤ N ≤ 25).
This project evaluates classical and modern AI search strategies, visualizes performance, and provides an interactive interface for experimentation.


## Project Overview

The **N-Queens Problem** requires placing **N queens** on an **N × N chessboard** such that no two queens attack each other.
This project generalizes the problem, implements multiple solution strategies, and compares their performance using:

* Runtime
* Iterations / Node Expansions
* Success Rate
* Conflicts
* Optimality


### Interactive Interface

Built with `ipywidgets` for algorithm selection, input parameters, and visualization.


### Extensive Error Handling

Validates board size, algorithm selection, and prevents invalid comparisons.

---

## State Representation & Constraints

The board is represented as a **1-D array** of length N:

```
board[i] = column position of queen in row i
```

This representation automatically enforces:

* **Row constraint**
* Efficient checking of:

  * **Column conflicts**
  * **Diagonal conflicts**

Constraint checks:
```
board[i] != board[j]                                  # Column
abs(board[i] - board[j]) != abs(i - j)                # Diagonal
```

## Algorithms Implemented

### Backtracking with Forward Checking (CSP)

* Uses **MRV (Minimum Remaining Values)**
* Uses **LCV (Least Constraining Value)**
* Applies **forward checking** after each assignment
* **Complete** and **guaranteed to find a solution**
* Prunes invalid branches early


### Simulated Annealing

* Starts with random configuration
* Accepts worse moves with probability `e^(ΔE/T)`
* Uses cooling schedule
* Good scalability
* Not complete, but effective for large N


### Random-Restart Hill Climbing

* Generates best successor among all moves
* Random restarts so tries to escape local minima or plateau
* Not complete
* Optimal depending on restarts


### A* Search
```
f(n) = g(n) + h(n)
```

* Complete
* Optimal if heuristic is admissible
* High memory usage


### Greedy Best-First Search

* Prioritizes states with minimum conflicts `h(n)`
* Very fast
* Not complete
* May get stuck in loops
* Not optimal

### Iterative Deepening Search (IDS)

* Depth-limited DFS repeated with increasing depth
* Complete
* Very memory-efficient
* Slow for large N


## Future Improvements

* Add **Min-Conflicts** heuristic solver
* Add **parallel random restarts** (multiprocessing)
* Implement **timeout-based partial return**
* Improve admissible heuristic for A*
