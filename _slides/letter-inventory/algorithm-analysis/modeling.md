---
title: Modeling
nav_order: 3
---

Modeling is about counting the number of steps or operations, such as assignments, boolean evaluations, arithmetic operations, method calls, etc.

```java
int a = 4 * 6;
int b = 9 * (a - 24) / (9 - 7);
```

The first assignment to `a` takes one step to compute `4 * 6` and one more step to assign the result, 24, to the variable `a`.

<details markdown="1">
<summary>How many steps does it take to assign a value to the variable b?</summary>

1. `a - 24`
1. `9 * (a - 24)`
1. `9 - 7`
1. `9 * (a - 24) / (9 - 7)`
1. Assignment to `b`
</details>

How do we apply this thinking to `indexOf`?

```java
for (int i = 0; i < array.length; i++) {
    if (array[i] == target) {
        return i;
    }
}
```

The goal of time complexity analysis is to make an argument about the running time of an algorithm. In most cases, we only care about **asymptotic analysis**: what happens for very large N (asymptotic behavior). We want to consider which algorithms are best suited for handling big amounts of data, such as the millions of nucleotides that make up our DNA. The running time differences between algorithms are easier to appreciate when we consider big data because even very slow algorithms will probably solve small problems quickly since computers are so fast nowadays. It's when we have big data that running time becomes a serious concern.

Asymptotic analysis
: Describes the step count in terms of N, the size of the input, as N becomes very large. In the case of `indexOf`, the number of steps it takes to compute `indexOf` is primarily determined by the length of the `array`, which we'll call N. A longer `array` may result in more iterations of the for loop.

When we talk about runtime in terms of "iterations of a loop", we're making an important conceptual simplification.

Cost model
: Instead of counting every single operation, the cost model is an operation used to estimate the overall order of growth. The number of iterations of the for loop is one possible cost model since it is directly correlated to the total number of steps that it takes to evaluate the algorithm.

<details markdown="1">
<summary>What factors affect the number of iterations of the for loop?</summary>

While the length of the `array` controls the stopping condition for the loop, the exact number of iterations also depends on the values in the `array` and the `target` value because the `return` statement will cause control to leave the `indexOf` method.
</details>

Case analysis
: Accounts for variation in step count based on interactions between factors. Even with a very long `array`, it's possible that the algorithm exits the `for` loop in the very first iteration if the `array[0] == target`. But it's also possible that the algorithm increments the counter and loops through the entire array without finding the `target`.

<details markdown="1">
<summary>Why don't we consider the case of a zero-length array as input?</summary>

Remember that we chose the length of the `array` as the asymptotic variable, so we're considering the number of steps it takes to evaluate the algorithm with a very long `array`, not a very small (or zero-length) one. While it's true that a zero-length array would run quite quickly on `indexOf`, it would also run very quickly with any reasonable algorithm, so this is not a very useful analysis for comparing algorithms.
</details>
