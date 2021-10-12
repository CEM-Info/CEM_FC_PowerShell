---
title: Binary search
nav_order: 5
---

It turns out that the best-known algorithm for many important problems takes exponential time, making it impossible to solve them in practice. To put that into perspective, an input of size N = 100 (e.g. `array.length == 100`) that takes a linear-time algorithm less than 1 second to evaluate would take an exponential-time algorithm about 10<sup>17</sup> **years** to compute a result.

The magnitude of improvement from exponential-time to linear-time is the same as the magnitude of improvement from linear-time to logarithmic-time. Logarithmic-time algorithms come up often in the study of computer algorithms, and they're the key to enabling computers to work with large datasets. Earlier, we saw how `indexOf` represented a worst-case linear-time algorithm. Let's analyze the runtime of **binary search**, a logarithmic-time algorithm for `indexOf` assuming a sorted array.

Suppose we have a `sorted` array of integers. Binary search is an efficient algorithm for returning the index of the `target` value in a `sorted` array.

<div style="--aspect-ratio: 720 / 405; --add-height: 29px"><iframe src="https://docs.google.com/presentation/d/e/2PACX-1vTir_A7eOXUQ5UhLEN9aG4bX466Xgh_ViaZACF_UlpcJZaWfsWIJCqu4b-KpCytEAJT7vpQBeUpvRFb/embed?start=false&loop=false&delayms=3000" frameborder="0" width="720" height="434" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe></div>
```java
static int binarySearch(int[] sorted, int target) {
    // Start looking at the whole sorted array
    int low = 0;
    int high = sorted.length - 1;
    // while low and high haven't met yet, there are still more indices to search
    while (low <= high) {
        // compute middle index and value
        int mid = low + (high - low) / 2;
        if (sorted[mid] < target) {
            low = mid + 1;
        } else if (sorted[mid] > target) {
            high = mid - 1;
        } else {
            return mid;
        }
    }
    return -1;
}
```

In each iteration of the loop, half of the elements under consideration can be discarded. The number of iterations of the `while` loop can be phrased as, "How many times do we need to divide N (length of the `sorted` array) by 2 until only 1 element remains?" This is the definition of the **binary logarithm**, or log<sub>2</sub>.

Alternatively, we could rephrase the question as, "How many times do we need to multiply by 2 to reach N?" To solve for 2<sup>x</sup> = N, we get x = log<sub>2</sub> N.
