---
title: Public/private pairs
nav_order: 2
---

All of these recursive `sum` algorithms share a common constraint: **the domain is defined by a single parameter**, `data`.

`int sum(int[] data)`
: Each subproblem is defined solely by `data`.

Given the same `data` array as input, the method should always produce the same outcome. This makes it tricky to represent different subproblems without constructing new arrays. Let's change the domain of the method to workaround this constraint.

`int sum(int[] data, int i)`
: Each subproblem is defined by the pair of values, `data` and `i`.

To maintain a simple `public` interface, we'll keep the `public` method header the same and move all of the recursive code into a `private` helper method.

```java
public static int sum(int[] data) {
    return sum(data, 0);
}

private static int sum(int[] data, int i) {
    if (data.length == i) {
        return 0;
    } else {
        return data[i] + sum(data, i + 1);
    }
}
```

The role of the `public` method is to start the recursive process by calling the `private` helper method. Each recursive call to the helper method processes the element at `data[i]` before making a recursive call for the sum of the remaining elements. Note that we also changed the base case to correspond with `i` reaching the end of `data.length`.

Recall that the original iterative approach also maintained a counter variable for the index `i`. When converting iterative algorithms to recursive algorithms, variables that change between each iteration must be represented as parameters to the recursive algorithm.

Public/private pair
: Define a `private` helper method that accepts a larger domain of parameters.

The advantage of introducing this public/private pair is that the client does not need to know any of the implementation details or setup any of the recursive variables. This also lets the implementer change their implementation however they want by introducing new variables without breaking client code.
