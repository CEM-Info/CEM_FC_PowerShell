---
title: Traversal
nav_order: 0
---

Managing `ListNode` references by hand is tedious and tricky. In this lesson, we'll explore how we can implement a data abstraction so that clients can take advantage of the performance benefits of linked nodes without learning how to manipulate linked nodes. Our goal will be to define a **linked list**, a list data type based on the linked nodes data structure.

Many list operations such as `add`, `remove`, and `get` depend on accessing particular nodes at a given index in the linked list. Suppose a `list` contains many nodes whose values we want to print out. We could start by trying to write something like:

```java
System.out.print(" -> " + list.data);
System.out.print(" -> " + list.next.data);
System.out.print(" -> " + list.next.next.data);
System.out.print(" -> " + list.next.next.next.data);
...
```
{: overlay="Implementer" }

This code is quite brittle: it only works if the number of print statements is exactly the same as the size of the list.

<details markdown="1">
<summary>What happens if the number of print statements is greater than the size of the list?</summary>

Eventually, one of the `list...next` fields will be `null`, representing the end of the list. Java will throw a `NullPointerException` when the code attempts to access the `data` field of that `null` reference.
</details>

This problem is more generally known as **traversing** the list by examining each element one at a time.

Standard traversal for linked lists
: Use a local variable to traverse the list. At each `ListNode`, perform some computation (like printing) before moving to the next node.
: ```java
  ListNode current = list;
  while (current != null) {
      System.out.print(" -> " + current.data);
      current = current.next;
  }
  ```
  {: overlay="Implementer" }

`current` is the variable whose value is a **reference** to the current node. It begins at the front of the list. At the end of each iteration of the loop, `current` is reassigned to the `next` node in the list. The loop ends when `current` reaches the `null` reference at the end of the list.
