---
title: Binary trees
nav_order: 1
---

Decision trees represent a specific application of a more general data structure known as a **binary tree**. If linked nodes are analogous to single structural recursion, then binary trees are analogous to multiple (degree 2) structural recursion.

Binary tree
: A tree where each node has either 0, 1, or 2 children.

![Tree Terminology](https://docs.google.com/drawings/d/e/2PACX-1vS1GgwSRvFdhzuPiBW2jigJ4EWmz3oUhd-mDw8gPp0SISbsEyMIvmaxx3B0nruDvlLmtVpOZmpyzn8Q/pub?w=960&h=540)

```java
public class IntTree {
    private IntTreeNode overallRoot;

    private static class IntTreeNode {
        public int data;
        public IntTreeNode left;
        public IntTreeNode right;
    }
}
```

Like linked nodes, each `IntTreeNode` is recursively defined. A binary tree is either empty or non-empty.

Empty binary tree
: The root `IntTreeNode` is null.

Non-empty binary tree
: The root `IntTreeNode` contains some `data`, a `left` subtree, and a `right` subtree. Each subtree is also a binary tree.
