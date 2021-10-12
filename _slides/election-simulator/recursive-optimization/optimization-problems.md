---
title: Optimization problems
nav_order: 2
---

Recursive enumeration allows us to print all solutions. But some problems don't require enumerating all solutions.

Optimization
: A type of problem that requires finding the optimal (best) solution from among a space of many potential candidate solutions.

Combinatorial optimization
: A specific type of optimization problem whose potential candidate solutions can be generated recursively.

The main difference between enumeration and optimization is in how we combine the result of each subproblem to compute the complete result (the final step in the outline for defining recursive algorithms). In recursive enumeration algorithms, we typically don't have to do anything for this step since the base case just prints out each solution, so recursive enumeration algorithms typically have a `void` return type. In contrast, recursive optimization algorithms **need to return a single solution**, so some additional work is needed to combine the result of each subproblem.
