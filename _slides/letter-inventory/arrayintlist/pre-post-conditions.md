---
title: Pre/post conditions
nav_order: 3
---

A **getter** method for `ArrayIntList` elements can be written in a few lines.

```java
// Returns the integer at the given index in the list
public int get(int index) {
    return elementData[index];
}
```
{: overlay="Implementer" }

<details markdown="1">
<summary>Give an example of a problematic input index to the get method.</summary>

Calling `get(-8)` or `get(100000)` would cause an `ArrayOutOfBoundsException`.

A more subtle example: any index greater than or equal to the size of the list but still within the bounds of the underlying `elementData` array. `get` would return whatever "garbage" value was stored in the vacant array index.
</details>

To tell the client about these errors, we'll introduce a documentation format called **pre/post conditions**.

Preconditions
: Conditions that the client needs to follow in order for the method to behave as intended.

Postconditions
: The intended behavior of a method assuming preconditions hold.

```java
// pre : 0 <= index < size()
// post: Returns the integer at the given index in the list
public int get(int index) {
    return elementData[index];
}
```
{: overlay="Implementer" }

While these comments are helpful for the client, it would be better to add validation checks in the code to prevent unintended behavior from occurring when the preconditions are not met. Here are two approaches.

Returning a dummy value
: We can return a specific dummy value to notify the client. For example, some implementations of `indexOf` (returns the index of a given value in a list) return -1 if the value is not contained in the list. Since the client knows that the only valid indices that should be returned from `indexOf` are in the range `0 <= index < size()`, -1 signifies a false result. If implemented this way, this behavior should be clearly documented!

<details markdown="1">
<summary>Why might it be bad for get to return -1 when given an invalid index?</summary>

The client might have actually added the value -1 as an **element** to the list earlier, so they wouldn't know if the -1 returned from `get` represented the dummy value or the value that they added to the list.
</details>

Throwing an exception
: The implementer can report a problem to the client by throwing an exception. Most of the time, we prefer this approach.
