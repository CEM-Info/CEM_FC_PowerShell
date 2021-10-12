---
layout: default
title: Data Types
parent: Quality
nav_order: 6
---

# Data Types
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Type parameters (generics)

**Always include the type parameter when dealing with generic classes like `ArrayList`, `TreeSet`, etc.** Failing to do so will likely lead to casting that clutter up the code and/or unsafe type operations.

Bad
: ```java
  Stack visited = new Stack();
  ```

Good
: ```java
  Stack<String> visited = new Stack<>();
  ```

## Interface types

**Always declare variables of a specific interface type instead of the class type, where applicable.** This includes field declarations and parameter and return types in method headers. By working with more general types rather than the specific class type, our code will be more generalized and more flexible. For example, a method that has a parameter of type `List` will be able to accept anything that implements the List interface (`LinkedList`, `ArrayList`, etc.). This is more flexible than a method that defines a parameter of type `LinkedList` that can only accept a `LinkedList`.

Bad
: ```java
  ArrayList<String> names = new ArrayList<>();
  ````

Good
: ```java
  List<String> names = new ArrayList<>();
  ```

## Casting

**Avoid casting to object types.** Casting to object types is essentially disregarding the safety net of the type system that Java provides. It may achieve the desired behavior, but it is usually a sign that we should change the logic of our program elsewhere. Casting to object types should only be done if truly necessary.

Casting to primitive types to actually convert values is fine, however, e.g.

```java
int truncated = (int) (Math.random() * 5);
```

## Prefer simple data types

Sometimes we have options for how we want to represent the data and either option(s) will be able to produce correct behavior. Instead of using a more complicated representation that can do everything we want and more, we should try use the representation that fits the specific problem the best. The intent and logic of your code will be simpler to another reader. Some examples are listed below.

- If you're using an `int` to keep track of whether it's one value or another, you likely want to use a `boolean` instead.
- If you're using a `String` to keep track of a single letter, you probably want to use a `char`.
- If you're using `Integer` because you want to keep track of a sum, you probably can just use `int`.

The point of a data structure is to store related values. If a data structure is only ever used to store one or two values, we prefer to use those value(s) directly.
