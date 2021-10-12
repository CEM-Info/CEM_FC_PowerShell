---
title: Enumeration problems
nav_order: 1
---

Let's reflect on the recursive enumeration problems that we've solved thus far. Regardless of whether we represented each solution as a new string or as a list or as a stack, all of the problems involved recursively enumerating **ordered lists with repetition**.

Ordered list with repetition
: A particular arrangement of elements where the order matters and each element may be used 0 or more times.

For example, in `fourAB`, we recursively enumerated all length-4 ordered lists of {A, B} with repetition. In both the string and list versions of `rollDice`, we recursively enumerated all `dice`-length ordered lists of {1, 2, 3, 4, 5, 6} with repetition.

Whereas choose-explore-unchoose was a strategy for adapting recursive enumeration (to lists rather than strings, for example), it's not solving a fundamentally different type of problem. It turns out that there are many different types of problems that can be solved with the idea of recursive enumeration. We'll also learn how to solve a second type of problem: recursively enumerating **unordered sets without repetition**.

Unordered set without repetition
: A set of some (or all) elements where the order doesn't matter and each element may be used either 0 or 1 times. Since elements cannot be repeated, each recursive subproblem must keep track of which remaining elements can still be used.
