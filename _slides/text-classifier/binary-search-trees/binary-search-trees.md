---
title: Binary search trees
nav_order: 0
---

In order to speed-up `contains` on a binary tree, we'll introduce **binary search trees**. Binary search trees are closely related to the **binary search** algorithm introduced earlier for finding the index of a target element in a **sorted array**. In each iteration of the binary search algorithm, half of the elements under consideration can be discarded, resulting in a logarithmic runtime. Can we organize the elements in a binary tree to speed-up binary search?

<details markdown="1">
<summary>Why is binary search in a sorted linked list so much slower than in a sorted array?</summary>

While arrays provide fast random access to the element at a given index, linked lists need to iteratively/recursively traverse to the given index.
</details>

To speed up binary search on a linked list, make the middle node the root for fast access. In order to reach items in the left half of the data structure, flip the direction of the edges and recursively apply this pattern to each sublist.

<div style="--aspect-ratio: 720 / 405; --add-height: 29px"><iframe src="https://docs.google.com/presentation/d/e/2PACX-1vTGFBnc04g8rghiLpJWiM9VEINE9taRs5qZyM8ImLgi5zNBqpvEei0YWGwkj2pOgV2_SqmGAXRJKw4v/embed?start=false&loop=false&delayms=3000" frameborder="0" width="720" height="434" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe></div>

Sortedness is a key property of binary search trees. Remember how `TreeSet` and `TreeMap` iterate over elements in-order? That's because they use a fast binary search tree implementation!

Binary search tree invariant
: For every non-empty node in a binary search tree:
  - All elements in its left subtree are less than the node's `data`.
  - All elements in its right subtree are greater than the node's `data`.
  - The left and right subtrees are also binary search trees.

This definition is recursive: in a valid binary search tree, the binary search tree invariant must hold for every subtree. The invariant specifies exactly where an element must reside in the tree (relative to the location of other elements).

```java
// pre : Binary search tree invariant.
// post: Returns true if the value is in this tree, false otherwise.
public boolean contains(int value) {
    return contains(overallRoot, value);
}

private boolean contains(IntTreeNode root, int value) {
    if (root == null) {
        return false;
    } else if (root.data == value) {
        return true;
    } else if (value < root.data) {
        return contains(root.left, value);
    } else {
        return contains(root.right, value);
    }
}
```
