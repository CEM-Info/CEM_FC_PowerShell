---
title: LinkedIntList
nav_order: 1
---

The `LinkedIntList` class represents a linked list of integers by maintaining a single `ListNode` field called `front`. Let's implement the `toString` method as an example. Apply the standard traversal starting from the `front` of the list but instead of printing out each element, append it to the `result` string.

```java
public class LinkedIntList {
    private ListNode front;

    public LinkedIntList() {
        front = null;
    }

    // post: Returns a text representation of the list
    public String toString() {
        if (front == null) {
            return "[]";
        } else {
            ListNode current = front;
            String result = "[";
            while (current.next != null) {
                result += current.data + ", ";
                current = current.next;
            }
            result += current.data + "]";
            return result;
        }
    }
}
```
{: overlay="Implementer" }

<details markdown="1">
<summary>ArrayIntList kept track of the size of the list as a field. Why is size not needed here?</summary>

`ArrayIntList.size` separated the in-use array indices from the not-in-use array indices.

But in a linked list, each linked node is in use. Each element in a linked list is represented by exactly one `ListNode` instance. The linked list ends when we hit the `null` reference at the end of the linked nodes.
</details>

LinkedIntList class invariant
: The `i`-th item in the list is always stored in the `i`-th node from the `front`.

- **Before any public method call**, the class invariant must hold for external correctness.
- In the implementation, the class invariant can be temporarily broken so long as it is later restored.
- **After any public method call**, the class invariant must hold for external correctness.
