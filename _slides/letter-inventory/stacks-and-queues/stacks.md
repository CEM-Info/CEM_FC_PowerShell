---
title: Stacks
nav_order: 2
---

The **stack** abstract data type allows adding and removing elements from the "top" of the stack. Imagine a stack of plates. The most common of way of interacting with the stack of plates is to add a plate to the top or remove a plate from the top.

- `push` an element to the top of the stack.
- `pop` to remove and return the top element from the stack.
- `peek` to return but not remove the top element from the stack.
- `size` to return the number of elements in the stack.

Consider the following code snippet.

```java
Stack<String> stack = new Stack<String>();
stack.push("puppy");
stack.push("cat");
stack.push("dog");
System.out.println(stack.pop());
```
{: overlay="Client" }

The first element removed by `stack.pop()` is "dog" since "dog" was at the top of the stack.

<details markdown="1">
<summary>Which element would be removed by a second pop operation?</summary>

The next element removed by `stack.pop()` would be "cat" since "cat" is on top of "puppy" in the stack.
</details>

There's one weird detail about stacks in Java. Stacks are an abstract data type, so they aren't necessarily tied to one specific data structure implementation. Unfortunately, Java's `Stack` class has a critical design flaw: it's a **class**, not an interface. This means that the left hand side and right hand side of an assignment statement will both be declared with the `Stack` class, rather than using an interface type.

Note
: The Java `Stack` class has many other methods beyond `push`, `pop`, `peek`, `size`, and `isEmpty`, but they're off-limits for this course since they aren't part of the stack ADT. (Poor design!)

Because stacks add to the top and remove from the top, we consider them last-in, first-out (LIFO) structures. In other words, the most recently-pushed element is the element that will be the first to be removed.
