---
title: For-each loop
nav_order: 2
---

One key limitation of the set ADT is that there's no `get` or `peek` methods for accessing elements. Since lists maintain indices, `List` clients can print out each word with a for loop.

```java
List<String> words = ...
for (int i = 0; i < words.size(); i++) {
    String word = words.get(i);
    System.out.println(word);
}
```
{: overlay="Client" }

However, sets don't maintain element indices! Instead, iterating over a set of words requires a new Java syntax called the **for-each loop**.

```java
Set<String> words = ...
for (String word : words) {
    System.out.println(word);
}
```
{: overlay="Client" }

Elements are considered in an order determined by the set implementer. Since `TreeSet` stores elements in sorted order, a for-each loop over a `TreeSet` of words will consider each word in dictionary order. The ordering of elements in a `HashSet`, in contrast, is not easy to interpret.

For-each loops can also be used with other collection types as well. For-each loops help simplify code by removing the need to maintain additional loop counter variables.

The main drawback of the for-each loop is that it does not allow modification to the collection. For example, we can't add or remove elements from the collection within a for-each loop.

```java
for (String word : words) {
    System.out.println(word);
    words.add("hello"); // will not work
}
```
{: overlay="Client" }
