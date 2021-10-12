---
title: Problem solving
nav_order: 0
---

Now that we've seen a number of templates and examples of recursive algorithms, let's practice writing our own recursive algorithms.

Outline for defining recursive algorithms
: 1. Identify one or more base cases.
  1. Decompose the problem into one or more smaller, independent subproblems.
  1. Combine the result of each subproblem to compute the complete result.

Base cases represent the smallest or simplest valid inputs to the algorithm. For problems involving integers, base cases are typically 0, 1, single-digit values, or negative numbers. For problems involving data structures, a common base case is an empty collection (with a caveat that we'll point out later).

Let's implement a method, `skipAdd`, that takes a non-negative integer `n` and returns the sum of every other integer between 0 and `n`. For example, `skipAdd(5)` should return 5 + 3 + 1 + 0 = 9 while `skipAdd(4)` should return 4 + 2 + 0 = 6.

<details markdown="1">
<summary>Outline how to solve skipAdd following the steps above.</summary>

1. The simplest valid input to the problem is 0, the smallest non-negative integer. We know `skipAdd(0)` should return 0.
1. A larger problem like `skipAdd(4)` relies on calling `skipAdd(2)` which then calls `skipAdd(0)`. Each recursive call is passed the input `n - 2`.
1. Since a recursive call to `skipAdd(2)` should return 2, the result of `skipAdd(4)` should be 6 = 4 + `skipAdd(2)`. In general, we compute the complete result by adding the value of `n`!
</details>

Turning the outline into code might look something like the following.

```java
// pre : n >= 0
// post: Returns the sum of every other integer between 0 and n
public static int skipAdd(int n) {
    if (n == 0) {
        return 0;
    } else {
        return n + skipAdd(n - 2);
    }
}
```

We can check our work by examining the domain of the method and verifying the result of each recursive subproblem. The **domain** of a function is all of the possible values of its inputs (parameters). `skipAdd(n)` depends on `skipAdd(n - 2)` to work correctly.

<details markdown="1">
<summary>Give an example input to skipAdd that will reveal a problem.</summary>

Since we're subtracting by 2, even inputs might do different things when compared to odd inputs. For example, `skipAdd(5)` will call `skipAdd(3)`, which will call `skipAdd(1)`, `skipAdd(-1)`, `skipAdd(-3)`, ... forever! It's like we've defined a `while` loop that continues forever because the loop condition is never false.

In reality, Java will throw a `StackOverflowException` and stop the program once it detects that there are too many recursive calls.
</details>

There are multiple ways of addressing this problem.

1. One way is to introduce a second base case.

   ```java
   // pre : n >= 0
   // post: Returns the sum of every other integer between 0 and n
   public static int skipAdd(int n) {
       if (n == 0) {
           return 0;
       } else if (n == 1) {
           return 1;
       } else {
           return n + skipAdd(n - 2);
       }
   }
   ```

1. Another way would be to combine these two base cases.

   ```java
   // pre : n >= 0
   // post: Returns the sum of every other integer between 0 and n
   public static int skipAdd(int n) {
       if (n == 0 || n == 1) {
           return n;
       } else {
           return n + skipAdd(n - 2);
       }
   }
   ```

Real world problems often involve several parameters that interact in different ways, so identifying the simplest base cases won't always be straightforward. Don't be afraid to add more base cases than necessary when starting out! Studying the relationships between more examples by writing them down is an effective strategy for identifying the relationships between recursive subproblems.
