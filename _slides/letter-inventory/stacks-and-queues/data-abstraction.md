---
title: Data abstraction
nav_order: 0
---

Last week, we saw how the `Balance` class represented an example of **abstraction**.

> The `Balance` class defines public methods so that other programs written by anyone, anywhere, at anytime before or after it can rely on its functionality as long as they know how to interface with it.

The public methods of the `Balance` class represent a **functional abstraction** since they allow clients to use the `Balance` class without understanding its implementation details.

<details markdown="1">
<summary>How does functional abstraction apply to collection types like ArrayIntList?</summary>

Similarly, the `ArrayIntList` class defines public methods, such as `add`, `remove`, and `indexOf`, that allow other programmers (clients) to use the `ArrayIntList` class without understanding its implementation details.
</details>

Earlier, we defined `ArrayIntList` as a collection that can be used to store a list (ordered sequence) of integer data and introduced the concept of a class invariant.

> ArrayIntList class invariant
> : The `i`-the item in the list is always stored at `elementData[i]`.

The wording is deliberate: the **list** concept is separate from the underlying `elementData` array. The other indices of the `elementData` may contain any values. An `ArrayIntList` implements the list concept with an `int[]`. `ArrayIntList` is an example of **data abstraction**.

ArrayIntList data abstraction
: The separation of the list concept (client view) from the underlying array (implementer view).
: **Abstract data type (ADT)**
  : The concept of a list as an ordered sequence with operations such as `add`, `remove`, and `indexOf`.
: **Data structure**
  : The underlying array that the implementer must maintain so that the client can use `ArrayIntList` as a list.

`ArrayIntList` is a Java class that binds these two concepts: the list **abstract data type** that informs the client how to use the class and the array **data structure** that actually provides the behaviors for the class's public methods. Next, we'll introduce the idea of different abstract data types and see what happens. In the coming weeks, we'll see how (and why) we might also want to switch out the data structure too.
