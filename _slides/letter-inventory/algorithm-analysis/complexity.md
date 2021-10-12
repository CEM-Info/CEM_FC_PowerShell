---
title: Complexity
nav_order: 0
---

Beyond whether or not a program is correct, computer scientists are often concerned about the **complexity** of a program. We actually already have quite a bit of experience with one particular kind of complexity that arises from how we design abstractions for our programs. For instance, pulling repeated code out into a method gives it a name and makes it easier for the reader to understand the behavior of the program. **Cognitive complexity** is about how easy it is to understand a program. In this course, we consider cognitive complexity from the perspective of code quality (internal correctness).

But code is just one way for programmers to communicate ideas to others, and writing code requires worrying about getting the code to work, which might take a lot more time than simplying coming up with the idea for the program. Instead, programmers often communicate ideas to others in terms of **algorithms**, the more generalizable list of steps behind the code. Whereas code is specific to a particular programming language, we can communicate algorithms in natural languages like English too. In fact, whenever we're describing a program to someone else in English, what we're really describing is an algorithm.

Algorithms are the ideas that power apps.

- In Autocomplete, we defined the `Term` **data type** that an algorithm will use to display matching terms in descending weight order.
- In Letter Inventory, we'll define a `LetterInventory` **data type** that an algorithm will use to display the most similar suggestions.
- But next week, for Search Engine, we'll define an **algorithm** for surfacing relevant web pages based on a given query.

When we consider algorithms, we're not only interested in correctness. Today, we'll study one metric for **algorithm analysis** called **time complexity**: how long it takes for an algorithm to run on an abstract (conceptual model) computer.
