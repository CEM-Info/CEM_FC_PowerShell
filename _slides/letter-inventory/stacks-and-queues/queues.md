---
title: Queues
nav_order: 3
---

While stacks are last-in, first-out (LIFO), **queues** are first-in, first-out (FIFO). Whereas stack operations only allow changes to the top, queue operations allow changes to the "front" and the "back" of the queue. Imagine people waiting in the checkout line at the grocery store. When someone wants to checkout, they're added to the back of the queue (which might be empty). The first person to checkout is the person at the front of the line.

- `add` an element to the back of the queue.
- `remove` and return the element at the front of the queue.
- `peek` to return but not remove the element at the front of the queue.
- `size` to return the number of elements in the queue.

Consider the following code snippet.

```java
Queue<String> queue = new LinkedList<String>();
queue.add("puppy");
queue.add("cat");
queue.add("dog");
System.out.println(queue.remove());
```
{: overlay="Client" }

The first element removed by `queue.remove()` is "puppy" since "puppy" was at the front of the queue.

This time, Java got the design right for queues. `Queue` is an interface in Java, which means that we can't instantiate it directly. Instead, we need to use an implementation such as `LinkedList`---the same `LinkedList` that also implements the `List` interface.

This is the powerful idea behind ADTs. By declaring an object such as a `LinkedList` as the interface type `Queue`, we're signalling to the human reading the program that we intend to use this object in queue-like ways, rather than all of the possible ways that we might use a list.
