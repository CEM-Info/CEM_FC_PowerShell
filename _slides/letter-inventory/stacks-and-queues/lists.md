---
title: Lists
nav_order: 1
---

The **list** abstract data type represents an ordered sequence of elements.

- `add` an element to any given index in the list (shifting right subsequent elements as necessary).
- `get` to return the element at any given index in the list.
- `remove` the element at any given index in the list (shifting left subsequent elements as necessary).
- `size` to return the number of elements in the list.

In this lesson, we'll contrast lists with **stacks** and **queues**. Stacks and queues are simpler than lists: in fact, lists can do everything that stacks can do and also everything that queues can do too.

It might seem a bit unintuitive why programmers would prefer data types that do fewer things rather than data types that do more things.

<details markdown="1">
<summary>From a functional abstraction perspective, why might we prefer a simpler ADT?</summary>

Defining a public method is a commitment. If a public method lets "other programs written by anyone, anywhere, at anytime before or after it" to rely on its functionality, then that places a burden on the implementer to maintain that method and improve it. This burden increases program complexity and limits opportunities to improve performance. Related to this idea, a concept in software design that we'll explore at the end of the course is **deep classes**: classes that provide few public methods, but a lot of functionality.
</details>

### Interface types

Java provides classes and interfaces for many different collections and abstract data types in the `java.util` package. To use them, add an `import` statement to the top of each Java file.

```java
import java.util.*;
```

The `java.util` package represents abstract data types as interfaces and concrete implementations as classes. For example, instead of declaring `ArrayIntList list = new ArrayIntList();`, the better approach is to use the interface type `List` on the lefthand side of the assignment statement.

```java
List<String> list = new ArrayList<String>();
```
{: overlay="Client" }

This line of code creates a new `ArrayList<String>` (righthand side) and assigns it to a local variable of type `List<String>` (lefthand side). We'll later see that there are other ways of implementing the `List` interface with different tradeoffs, so it's useful to write client code using the general interface type where possible so that the implementation can be changed if necessary later on.

### Wrapper classes

To store a list of integers using Java's `ArrayList` class, we might write the following line of code.

```java
List<int> list = new ArrayList<int>();
```
{: overlay="Client" }

This doesn't work because Java disallows primitive types such as `int` and `double` from being used as the specialized type. Instead, specialized types need to be classes such as `String`. Java provides **wrapper classes** to represent primitive values as objects. For example, the wrapper class for `int` is called `Integer`. We can declare a list of integers as follows.

```java
List<Integer> list = new ArrayList<Integer>();
```
{: overlay="Client" }

Java will conveniently convert between the primitive type and the wrapper class automatically most of the time, so we can use the primitive type everywhere else.

```java
List<Integer> list = new ArrayList<Integer>();
list.add(1);
int first = list.get(0);
```
{: overlay="Client" }
