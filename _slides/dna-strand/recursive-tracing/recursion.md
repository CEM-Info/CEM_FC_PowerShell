---
title: Recursion
nav_order: 0
---

Throughout the course so far, we've seen that the choice of **data abstraction** affects how we solve programming problems. For example, we learned about certain templates for solving list problems, stack problems, queue problems: each of which required us to engage differently with how we organize code to manipulate data in a program.

For the remaining half of the course, we'll study an equivalent paradigm shift in the context of **functional abstraction**. Earlier, we presented a narrow definition of functional abstraction focusing on the relationship between client and implementer.

> The `Balance` class defines public methods so that other programs written by anyone, anywhere, at anytime before or after it can rely on its functionality as long as they know how to interface with it.

A more general definition for functional abstraction considers all **algorithms** as having three parts.

1. All algorithms take parameters as input.
1. All algorithms perform computation with the given parameters.
1. All algorithms return results based on the computations.

**Recursive algorithms** represent a style of solving problems by combining solutions to smaller subproblems.

1. Recursive algorithms take parameters as input.
1. Recursive algorithms perform computation with the given parameters.
   1. Identify smaller **subproblems** that can be solved independently.
   1. Solve each smaller subproblem with **recursive calls**.
   1. Combine the result of each subproblem to compute the complete result.
1. Recursive algorithms return results based on the computations.
