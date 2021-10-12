---
layout: default
title: Efficiency and Redundancy
parent: Quality
nav_order: 7
---

# Efficiency and Redundancy
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

A lot of what we define to be important for efficiency boils down to "don't do anything unnecessary". Knowing what's necessary and what isn't can be difficult, but following the way the spec phrases certain implementation details will lead you in the right direction. Unfortunately, there's no hard and fast rule for finding every inefficiency. To find them, you will have to dedicate some time to reason about your code.

As a general rule, reduce or remove complicated expressions and logic where reasonably possible.

## Creating new objects

**Avoid making objects that you don't need.** This can be tricky to spot, but in particular you should review your code statements that instantiate `new` objects or call other methods that do so. Making sure that every object you instantiate is necessary (no other available methods can provide the same or reasonable behavior) and logical will give some sense of security here.

The first example makes a `new ArrayList<>();` just to discard it in the next line. When we set `words = generateWords()` in the second line, the previous value of `words` is lost (unless it's saved elsewhere). The second example doesn't throw away any newly made objects.

Bad
: ```java
  List<String> words = new ArrayList<>();
  words = generateWords();
  ```

Good
: ```java
  List<String> words = generateWords();
  ```

## Recomputing values

Avoid recomputing complex expressions and method calls. **If you have to use the value of a method call or a complicated expression more than once, you should store it in a well-named variable.** Using the value stored in this variable will give you instant access instead of recomputing the value by evaluating the method call or expression again. This will also clear up the clutter of your code by replacing generic symbols and expressions with a name to describe some context.

There are some methods that are fast enough that storing the value in a variable for the future doesn't save us anything. For example, the `size()` method for any data structure we use in this course will have the same instant access whether we store it or call the method. In such a case, efficiency is not an issue we have to worry about.

## Factoring

If you have lines of repeated or very similar code that need to be executed in different places, group the code of the task into a private helper method. Putting the code into one place instead of several will make making changes easier, as well as make our code more readable.

Code inside if/else structure should represent different cases where the code is inherently different. This means duplicate lines of code or logic in an if/else structure should be factored out to come before or after, so that they are only written to happen once, unconditionally.

Bad
: Note that there are repeated lines of logic that actually always happen, instead of conditionally like how our structure is set up. We can factor these out to simplify and clean our code.

  ```java
  if (x % 2 == 0) {
      System.out.println("Hello!");
      System.out.println("I love even numbers too.");
      System.out.println("See you later!");
  } else {
      System.out.println("Hello!");
      System.out.println("I don't like even numbers either.");
      System.out.println("See you later!");
  }
  ```

Good
: ```java
  System.out.println("Hello!");
  if (x % 2 == 0) {
      System.out.println("I love even numbers too.");
  }  else {
      System.out.println("I don't like even numbers either.");
  }
  System.out.println("See you later!");
  ```

Tip
: Review any if/else structures you write and make sure there are no duplicate lines of code or logic at the beginning or the end.

## Redundant conditional logic

This section details issues with writing unnecessary if/else logic that can be omitted. We will refer to any control flow like if, else, etc. as conditional logic.

### Loops

Good bounds and loop conditions will already deal with certain edge case behavior. Avoid writing additional conditional logic that loop bounds already generalize.

Bad
: The `if` here is redundant. The loop won't produce any output (or even run) if n were 0 or negative in the first place, so we should remove the check.

  ```java
  if (n > 0) {
      for (int i = 0; i < n; i++) {
          System.out.println("I love loops < 3");
      }
  }
  ```

### Already known values

By using control flow (if/else/return) properly, you can guarantee some implicit facts about values and state without explicitly checking for them. The examples listed below add in redundant conditional logic that should be removed.

Bad
: Because `someTest` was tested for alone in the first if, future branches of the if/else structure know `someTest` must be false, so the check for `!someTest` is redundant and can be omitted.

  ```java
  if (someTest) {
      ...
  } else if (!someTest ...) {
      ...
  }
  ```

Bad
: At the second `if` statment, we know that `someTest` must have been false, so it's not necessary to check its value again.

  ```java
  if (someTest) {
      throw exception/return
  }
  if (!someTest) {
      ...
  }
  ```

## Reuse existing code and methods

**Avoid re-implementing the functionality of already existing methods, by just calling those existing methods.**

In the following example, the two methods are almost identical, except `indexOf` is more powerful/flexible than `contains`. So, `contains` can actually just use a call to `indexOf` to reuse already written behavior.

```java
public int indexOf(int value) {
    for (int i = 0; i < size; i++) {
        if (elementData[i] == value) {
            return i;
        }
    }
    return -1;
}
```

Bad
: ```java
  public boolean contains(int value) {
      for (int i = 0; i < size; i++) {
          if (elementData[i] == value) {
              return true;
          }
      }
      return false;
  }
  ```

Good
: ```java
  public boolean contains(int value) {
      return indexOf(value) >= 0;
  }
  ```

The classes you will use in this course (`String`, `ArrayList`, `TreeMap`, etc.) will provide many useful methods, and you should aim to take advantage of them by using them. Rewriting existing behavior is less flexible, redundant, and by writing more lines of code you raise the risk of encountering more bugs.
