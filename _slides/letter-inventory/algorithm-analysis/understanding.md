---
title: Understanding
nav_order: 2
---

Let's apply the runtime analysis process to analyze an algorithm that returns the index of `target` in an `int[] array`, or -1 if `target` is not in the array.

```java
static int indexOf(int[] array, int target) {
    for (int i = 0; i < array.length; i++) {
        if (array[i] == target) {
            return i;
        }
    }
    return -1;
}
```

The behavior of the `indexOf` algorithm depends on the input values.

<details markdown="1">
<summary>Describe each step of the algorithm's implementation details in English.</summary>

1. Initialize an integer index counter, `i`.
1. Loop over the length of the array. On each iteration, if the `array[i]` is the same as the given `target`, return the current index. Otherwise, increment `i`.
1. If no elements in the array are the same as the given `target`, return -1.
</details>
