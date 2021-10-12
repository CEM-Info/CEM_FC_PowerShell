---
title: Linked nodes
nav_order: 1
---

**Linked nodes** are a non-contiguous memory data structure, which we represent in Java by defining a `ListNode` class. Each `ListNode` maintains two fields.

1. The actual `data` value of the element.
1. A reference to the `next` element in the list.

```java
public class ListNode {
    public int data;
    public ListNode next;

    public ListNode(int data) {
        // Construct a ListNode with the ListNode(data, next) constructor
        this(data, null);
    }

    public ListNode(int data, ListNode next) {
        this.data = data;
        this.next = next;
    }
}
```
{: overlay="Implementer" }

<details markdown="1">
<summary>How can a ListNode also contain a field of type ListNode?</summary>

Remember that Java stores references to objects, not the objects themselves. The value of a `ListNode` variable is a reference to a `ListNode` object somewhere else in memory.

An analogy could be to think about browsing websites online. Many websites often have a link back to the home page (typically the website's logo), even on the home page itself. There's no problem with this circular setup since we don't follow a link until it is clicked. In the same way, Java does not follow references until a program requests its value.
</details>

Note that the fields of the `ListNode` class are declared `public`. In most programming situations, this would expose the `ListNode` implementation to the client, thus breaking our public method encapsulation and external correctness guarantees. But in this case, we can make sure that the client never knows about the `ListNode` class by defining it as a `private static class` nested inside a public `LinkedIntList` class. Earlier, we solved queue ADT problems using the `LinkedList` class without knowing about linked nodes because of this encapsulation!
