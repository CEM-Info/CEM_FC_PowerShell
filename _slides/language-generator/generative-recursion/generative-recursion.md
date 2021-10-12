---
title: Generative recursion
nav_order: 1
---

Iteration can be used within a recursive algorithm to process data of arbitrary size. For example, in the `isReducible` method, we used a `for` loop to test out each of the different words that result from crossing-out (one at a time) each letter in the original word. `isReducible` is an example of **multiple recursion** (`word.length()` number of recursive calls) and **structural recursion** (each recursive call is given a shorter word).

In contrast to structural recursion, **generative recursion** does not necessarily decompose problems into smaller subproblems.

Generative recursion
: Recursion on newly-generated data, rather than structural subproblems.

We'll typically apply computer-generated randomness to generate the new data. Java's `Random` class has three useful methods.

`int nextInt()`
: Returns a random (positive, zero, or negative) integer.

`int nextInt(int max)`
: Returns a random integer in the range from 0 (inclusive) to `max` (exclusive).

`double nextDouble()`
: Returns a random real number in the range from 0.0 (inclusive) to 1.0 (exclusive).

`boolean nextBoolean()`
: Returns a random boolean value.
