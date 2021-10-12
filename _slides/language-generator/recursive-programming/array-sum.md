---
title: Array sum
nav_order: 1
---

Let's implement a recursive method `sum` that takes an `int[]` and returns the sum of the values in the array. We can solve this problem iteratively by keeping track of a counter variable for the index `i` and summing the result so far with `total`.

```java
public static int sum(int[] data) {
    int total = 0;
    for (int i = 0; i < data.length; i++) {
        total += data[i];
    }
    return total;
}
```

<details markdown="1">
<summary>Describe an outline for a recursive sum algorithm.</summary>

1. The simplest valid input to the problem is an empty `data` array.
1. A subproblem for `[1, 2]` could be the rest of the `data`: `[2]`. Since we're breaking down the problem by looking at one less element, we only need to include one base case for the empty `data` array.
1. Since the `sum([2])` is just 2, we can add the value at `data[0]` to arrive at the final solution.
</details>

There are several details that Java programmers need to be careful about when turning this outline into code. The following code does not work!

```java
public static int sum(int[] data) {
    if (data.length == 0) {
        return 0;
    } else {
        return data[0] + sum(data);
    }
}
```

<details markdown="1">
<summary>Why doesn't this recursive method work?</summary>

In our outline's recursive case, we wanted to break down the problem by reducing the `data` by one element. Here, we're not changing the `data` array when we pass it to the next recursive call. So the program will continue recursing on the original `data` array!
</details>

Studying the iterative implementation can point us to a solution. The iterative implementation keeps track of an index `i`. Each iteration of the loop processes the element at `data[i]`. How might we represent this idea in a recursive algorithm?

An initial (but incorrect) approach to  be to introduce an index `i` as a local variable. Each recursive call to `sum` gets its own parameters and local variables. These parameters aren't shared between recursive calls!

```java
public static int sum(int[] data) {
    if (data.length == 0) {
        return 0;
    } else {
        int i = 0;
        int value = data[i];
        i++;
        return value + sum(data);
    }
}
```
