---
title: Linked lists
nav_order: 0
---

In this lesson, we'll solve linked list problems with recursive algorithms by combining three key ideas.

1. `LinkedIntList` is an implementation of the list ADT with one field, `ListNode front`.
1. A recursive algorithm can be defined by identifying base cases, solving recursive subproblems, and then combining the result of each subproblem.
1. If the domain overly-constrains the subproblem representation, introduce a new `private` helper method with additional parameters.

What does the standard traversal for linked lists look like as a recursive algorithm?

Iterative traversal for linked lists
: Use a local variable to traverse the list. At each `ListNode`, perform some computation (like printing) before moving to the next node.
: ```java
  public void print() {
      ListNode current = front;
      while (current != null) {
          System.out.print(current.data + " ");
          current = current.next;
      }
  }
  ```
  {: overlay="Implementer" }

Recursive traversal for linked lists
: Use a parameter to traverse the list. Each recursive call is responsible for processing a single `ListNode` by performing some computation (like printing) before moving to the next node.
: ```java
  public void print() {
      print(front);
  }

  private void print(ListNode current) {
      if (current != null) {
          System.out.print(current.data + " ");
          print(current.next);
      }
  }
  ```
  {: overlay="Implementer" }

<details markdown="1">
<summary>Identify the base case and recursive case.</summary>

The implicit base case occurs when `current == null`. There is nothing left to do in the traversal.

In the recursive case, the method prints out the `current.data` and makes a recursive call to process the next element in the list.
</details>

The recursive traversal templates for linked lists is one example of a broader family of recursive templates known as **structural recursion**. The linked nodes data structure is recursive: each linked node is either `null` or a `ListNode` instance, so each recursive call processes a node according to its recursive definition.

In fact, all of the recursive programs we've studied so far are examples of structural recursion. When recursively reversing a string, each subproblem reduced the length of the string by 1. When recursively binary searching, each subproblem cut in half the `high - low` portion the sorted array. Later, we'll study generative recursion, a family of recursive templates that doesn't follow this pattern.
