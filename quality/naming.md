---
layout: default
title: Naming
parent: Quality
nav_order: 5
---

# Naming
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

The names of the public methods and the class must appear exactly how they appear in the spec (case matters). If these names are not exactly correct, the provided main program should fail to compile if you try to.

## Casing

- Fields, local variables, and methods should be `camelCased`, where every word after the first begins with capitalization.
- Class names and constructors should be `UpperCamelCased`. This is camel casing but the first word also begins with capitalization.
- Class constants should be `SCREAMING_CASE`, where words are all uppercase and separated by underscores.

Private helper methods that aide a constructor are still methods (have explicit return types and aren't used with `new`) and should be camelCased unlike the constructor itself.

## Descriptiveness

**Use descriptive names that will help out another reader of your code.** Giving some kind of context for what the value(s) is or giving a high-level 1/2 word description is usually appropriate.

For the following example, assume we're trying to name a `List` that will keep track of the names of each chapter in a book. Since we have some context for what we want to use this variable for, we can try and come up with a descriptive name.

`List<String> l = new ArrayList<>();`
: `l` isn't descriptive. It really doesn't say anything about what the values in `l` or `l` itself represent.

`List<String> listOfStrings = new ArrayList<>();`
: Restating the type may seem better, but it doesn't actually help a reader understand the code any more easily. A reader still doesn't have any context or high level understanding what `listOfStrings` represents.

`List<String> values = new ArrayList<>();`
: Every variable stores a value, so this one is a little bit too vague to be helpful.

`List<String> chapterTitles = new ArrayList<>();`
: Good! This one gives some context for what the list represents.

While one-letter names may be easy to type, they aren't descriptive. Other readers of your code will likely ponder over their meaning if they need to understand what your code is doing. There are some appropriate uses, however, like for `for` loop variable names. They're also used to describe values that are temporary or so general that there isn't really any context to describe. But for the most part, try to use more helpful names when you can think of them. Other readers will likely appreciate it.
