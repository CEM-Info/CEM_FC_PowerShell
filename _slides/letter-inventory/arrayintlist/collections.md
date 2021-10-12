---
title: Collections
nav_order: 1
---

Letter inventories are a specific type of collection. A **collection** is an object that stores **elements** (data). Almost every problem that we'll solve in this course involves defining algorithms that use collections to store and manipulate data.

To help us learn how to design a letter inventory, we'll study how Java implements a popular collection type called `ArrayList` by building a simplified `ArrayIntList` class. An `ArrayIntList` can be used to store a **list** (ordered sequence) of integer data.

```java
// An ArrayIntList stores a list of integers
public class ArrayIntList {
    private int[] elementData;
    private int size;

    // Constructs an empty list
    public ArrayIntList() {
        elementData = new int[10];
        size = 0;
    }

    // Appends the given value to the end of the list
    public void add(int value) {
        elementData[size] = value;
        size += 1;
    }
}
```
{: overlay="Implementer" }

Internally, the `ArrayIntList` class maintains two fields: an `int[] elementData` representing the list of integers and an `int size` representing the current number of elements in the list.
