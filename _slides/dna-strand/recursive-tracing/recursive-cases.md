---
title: Recursive cases
nav_order: 2
---

Say we want to implement `writeStars`, a method that takes an integer `n` and prints out `n` asterisks `*` followed by a new line. We can solve this by defining an iterative algorithm.

```java
// pre : n >= 0
// post: Prints a line containing the given number of stars
public static void writeStars(int n) {
    for (int i = 0; i < n; i++) {
        System.out.print("*");
    }
    System.out.println();
}
```

In order to solve the `writeStars` problem using recursion, we'll temporarily disallow ourselves from using iteration. (This is not a general rule. Many recursive algorithms use recursion together with iteration to solve problems.)

One way to solve this problem without using any loops is to write out every possible case using `if` statements. But this gets tedious very quickly. How do we even cover all possible values of `n`?

```java
public static void writeStars(int n) {
    if (n == 0) {
        System.out.println();
    } else if (n == 1) {
        System.out.print("*");
        System.out.println();
    } else if (n == 2) {
        System.out.print("*");
        System.out.print("*");
        System.out.println();
    } else if (n == 3) {
        System.out.print("*");
        System.out.print("*");
        System.out.print("*");
        System.out.println();
    } ...
}
```

This is where recursion can help. Notice the `n == 3` case contains the same code from `n == 2` but with an extra asterisk at the beginning. We can factor-out the repeated code and call the `n == 2` case with `writeStars(2)`.

```java
public static void writeStars(int n) {
    if (n == 0) {
        System.out.println();
    } else if (n == 1) {
        System.out.print("*");
        System.out.println();
    } else if (n == 2) {
        System.out.print("*");
        System.out.print("*");
        System.out.println();
    } else if (n == 3) {
        System.out.print("*");
        writeStars(2);
    } ...
}
```

Notice the `n == 2` case also contains the same code as the `n == 1` case! And the `n == 1` case also contains the same code as the `n == 0` case!

```java
public static void writeStars(int n) {
    if (n == 0) {
        System.out.println();
    } else if (n == 1) {
        System.out.print("*");
        writeStars(0);
    } else if (n == 2) {
        System.out.print("*");
        writeStars(1);
    } else if (n == 3) {
        System.out.print("*");
        writeStars(2);
    } ...
}
```

<details markdown="1">
<summary>What are the steps for evaluating writeStars(3)?</summary>

1. Call `writeStars(3)`, use the `n == 3` case.
1. Print `*`.
1. Call `writeStars(2)`, use the `n == 2` case.
1. Print `*`.
1. Call `writeStars(1)`, use the `n == 1` case.
1. Print `*`.
1. Call `writeStars(0)`, use the `n == 0` case.
1. Print a new line.
</details>

More generally, every case except for `n == 0` can be rewritten with two statements.

```java
public static void writeStars(int n) {
    if (n == 0) {
        // Base case
        System.out.println();
    } else {
        // Recursive case
        System.out.print("*");
        writeStars(n - 1);
    }
}
```

<details markdown="1">
<summary>What are the steps for evaluating writeStars(3)?</summary>

1. Call `writeStars(3)`, use the `n >= 1` case.
1. Print `*`.
1. Call `writeStars(2)`, use the `n >= 1` case.
1. Print `*`.
1. Call `writeStars(1)`, use the `n >= 1` case.
1. Print `*`.
1. Call `writeStars(0)`, use the `n == 0` case.
1. Print a new line.
</details>

This recursive program has two parts: a **base case** and a **recursive case**.

Base case
: A simple input that is computed directly.

Recursive case
: A complex input that is computed with recursive calls to smaller subproblems.

