---
title: Class invariants
nav_order: 2
---

So what's the difference between an `ArrayIntList` and a raw `int[]`? Lists disagree with two key features of arrays.

1. Array elements can be stored at any index.
1. Array size is fixed and cannot be changed after construction.

These two features are part of what make arrays so useful as building blocks for programs. But they also inconvenience client programmers in two ways.

1. Since array elements can be stored at any index, there can be empty indices between elements.
1. Since array size is fixed, full arrays cannot store any more elements. (A larger array needs to be constructed, and all of the elements need to be copied over.)

Lists help clients store **ordered sequences of elements** without having to worry about these inconveniences. Our study of `ArrayIntList` will primarily focus on the first point about the location of array elements. Unlike `int[]`, `ArrayIntList` enforces a **class invariant** (a relationship that must always hold) between the values in `elementData` and the `size` field.

ArrayIntList class invariant
: The `i`-th item in the list is always stored at `elementData[i]`.

- **Before any public method call**, the class invariant must hold for external correctness.
- In the implementation, the class invariant can be temporarily broken so long as it is later restored.
- **After any public method call**, the class invariant must hold for external correctness.
