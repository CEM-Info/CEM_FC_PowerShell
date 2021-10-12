---
title: Exceptions
nav_order: 4
---

We can check preconditions by adding an `if` statement. In order to stop the program within the `if` statement, **throw an exception**.

```java
// pre : 0 <= index < size() (throws IllegalArgumentException if not)
// post: Returns the integer at the given index in the list
public int get(int index) {
    if (index < 0 || index >= size) {
        throw new IllegalArgumentException();
    }
    return elementData[index];
}
```
{: overlay="Implementer" }

In this example, we chose to `throw new IllegalArgumentException()`. There are many different types of exceptions, each of which informs the client of a different problem. Don't worry about which one to use: for the purpose of this course, we'll walk you through the exceptions that need to be thrown when they become relevant.

Note that we also documented this exception by adding it to our method comment.
