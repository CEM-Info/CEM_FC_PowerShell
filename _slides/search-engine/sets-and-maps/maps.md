---
title: Maps
nav_order: 3
---

The **map** abstract data type associates a set of unique **keys** with a collection of **values**, where each key is associated with a value.

- `containsKey` returns true if the given `key` is in the map.
- `get` returns the value associated with the given `key`, or null if the `key` is not in the map.
- `put` associates the given `key` with the given `value`.
- `remove` to remove the entry for the given key and return its associated value.

Maps relate two types of data: keys and values. Suppose we want to build a letter inventory for the string "Washington" using a `HashMap` where the keys are characters and the values are integers.

```java
Map<Character, Integer> inventory = new HashMap<Character, Integer>();
// Add character count mappings to the inventory
inventory.put('a', 1);
inventory.put('g', 1);
inventory.put('h', 1);
inventory.put('i', 1);
inventory.put('n', 2);
inventory.put('o', 1);
inventory.put('s', 1);
inventory.put('t', 1);
inventory.put('w', 1);
```
{: overlay="Client" }

To later add the inventory for the string "State", we can call `put` again with the same key and the updated value. The new entry will overwrite the old entry for the given key.

```java
// Add [aetts] to the [aghinnostw] inventory
inventory.put('a', inventory.get('a') + 1);
inventory.put('e', 1);
inventory.put('s', inventory.get('s') + 1);
inventory.put('t', inventory.get('t') + 2);
```
{: overlay="Client" }

For-each loops are more complicated since we need to specify whether we want to loop over the `keySet()` or the collection of `values()`.

```java
for (char letter : inventory.keySet()) {
    int count = inventory.get(letter);
    System.out.println(name + ": " + count);
}
```
{: overlay="Client" }

<details markdown="1">
<summary>Why isn't there a method to return the key associated with a given value?</summary>

Keys in a map are unique, so there is only one value for each key. But values are not necessarily unique. There are many letters in the `inventory` with a count of 1, so it's impossible to say which key the client wants in particular.
</details>

Like sets, there also exists a `TreeMap` class that also implements the `Map` interface and maintains its keys in sorted order.

```java
Map<Character, Integer> inventory = new TreeMap<Character, Integer>();
```
{: overlay="Client" }
