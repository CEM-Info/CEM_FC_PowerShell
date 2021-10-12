---
title: Data types
nav_order: 6
---

All Java programs consist of data and algorithms. Throughout most of CSE 142, we wrote Java programs by defining static methods, focusing primarily on algorithms. In CSE 143, we'll focus on writing Java programs by defining **data types**. Data types represent units of information in a program, including primitive data types that represent the smallest unit of information (such as numbers) and composite data types that combine other data types (such as arrays of numbers). In this course, we'll examine the complexities of the relationship between data and algorithms by defining our own data types that combine human information with computational algorithms.

Our first case study is on **Autocomplete**, a feature of many modern applications that helps the user complete an input query. Our goal in this module is to define the behavior for a `Term` class, where each `Term` object represents a single autocompletion option. It might not seem like much, but defining this basic data type is the first small but important step towards developing an app like Autocomplete.

{{ site.modules | where: 'title', 'Autocomplete' | first }}
