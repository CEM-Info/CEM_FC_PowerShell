---
title: x = change(x)
nav_order: 1
---

Say we want to implement a recursive `LinkedIntList.add` method. An iterative algorithm loops through the list to the last element in order to reassign its `next` field to a new `ListNode`.

```java
// post: Appends the given value to the end of the list.
public void add(int value) {
    if (front == null) {
        front = new ListNode(value);
    } else {
        ListNode current = front;
        while (current.next != null) {
            current = current.next;
        }
        current.next = new ListNode(value);
    }
}
```
{: overlay="Implementer" }

We can directly translate the iterative algorithm to a recursive algorithm by introducing a `private` helper method.

```java
public void add(int value) {
    if (front == null) {
        front = new ListNode(value);
    } else {
        add(front, value);
    }
}

private void add(ListNode current, int value) {
    if (current.next == null) {
        current.next = new ListNode(value);
    } else {
        add(current.next, value);
    }
}
```
{: overlay="Implementer" }

This code works, but the `public` and `private` methods share some redundant code. Both methods include base cases for creating the same `new ListNode(value)` and only differ in assigning to either the `front` of the list or the `current.next`. The `x = change(x)` pattern is a strategy for factoring-out this redundancy by making one additional recursive call beyond the typical base case.

`x = change(x)`
: A recursive algorithm pattern for factoring out redundant base cases involving assignment of the same value to different fields.

  1. Modify the return type to return a reference to a node.
  1. In the base case(s), modify the condition and return a reference to a node.
  1. In the recursive case(s), assign the returned node reference to a field.

Note that the condition for the base case now checks that `current == null` rather than `current.next == null`. Instead of stopping at the last node, the recursive calls continue until `current == null`.

```java
public void add(int value) {
    front = add(front, value);
}

private ListNode add(ListNode current, int value) {
    if (current == null) {
        return new ListNode(value);
    } else {
        current.next = add(current.next, value);
        return current;
    }
}
```
{: overlay="Implementer" }

<details markdown="1">
<summary>Why return current in the recursive case?</summary>

The practical reason is to satisfy the Java compiler: the code won't run unless every if-case returns a `ListNode`. By returning `current` back to the caller, the current recursive subproblem is signaling that no change is necessary to the current linked node structure. Remember that each recursive case will reassign `current.next`, but in a long linked list, many of these `next` fields don't need to be changed.
</details>

<details markdown="1">
<summary>Why reassign front in the public method?</summary>

Consider the case of an empty list. Since `front == null`, Java will immediately use the base case and return a reference to a new `ListNode` with the given `value`. That new `ListNode` is the new `front` of the list!
</details>

The `x = change(x)` concept is something that we might remember from our earlier definition of **functional abstraction**: we're using the return values to help compute the complete result. Formally, we define the **range** as the possible return values of a function.

In recursive algorithm design, there are two ways of communicating between the current recursive problem and its subproblems.

Domain
: The current recursive problem can **send information to its subproblems** by passing them as inputs (parameters).

Range
: The current recursive problem can **receive information from its subproblems** by processing their outputs (return values).
