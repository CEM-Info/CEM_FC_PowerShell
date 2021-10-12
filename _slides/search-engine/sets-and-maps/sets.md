---
title: Sets
nav_order: 1
---

One way to speed up the `countUnique` method is to use a **set** abstract data type instead of a **list**. By restricting the public methods and changing the way clients interact with the collection, implementers can design more efficient data structures to speed up the running time to meet the demands of big data.

In contrast to lists, sets only contain unique elements and do not keep track of element positions (indices). The **set** abstract data type represents an unordered collection of unique elements.

- `add` an element to the set.
- `contains` to return whether or not a value is in the set.
- `remove` and return an element from the set.
- `size` to return the number of elements in the set.

Without the need to maintain element positions, set implementations organize data in more creative ways than storing elements according to index. The Java Collections framework provides two `Set` implementations called `HashSet` and `TreeSet`. We can rewrite the `countUnique` method to use a `HashSet`.

```java
public static int countUnique(Scanner input) {
    Set<String> words = new HashSet<String>();
    while (input.hasNext()) {
        String word = input.next();
        words.add(word);
    }
    return words.size();
}
```
{: overlay="Client" }

Since sets only contain unique elements, `words.size()` represents the number of unique words added to the set.

`HashSet`
: Elements are stored in a consistent but unpredictable order. For our purposes, the worst case runtime of all operations are constant with respect to the size of the set.

`TreeSet`
: Elements are stored in sorted order. The worst-case runtime of all operations are in Θ(log<sub>2</sub> N) with respect to N, the size of the set. Later, we'll learn about binary search trees, the data structure idea behind `TreeSet`.
