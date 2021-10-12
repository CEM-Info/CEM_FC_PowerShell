---
title: DNA Strand
nav_order: 0
---

In the context of programming, **main memory** refers to the temporary workspace that is used by currently-running programs. Main memory works like a very large array. When we create a `new int[10]`, Java communicates with the operating system to reserve a chunk of main memory large enough to fit 10 integers. This chunk of memory is **contiguous**: all of the items are next to each other with no gaps in between.

Say we want to represent a list of the following numbers, `[42, -3, 17, 9]`.

Contiguous memory
: | 42 | -3 | 17 | 9 | | | | | |

In an `ArrayIntList`, the `i`-th item in the list is always stored at `elementData[i]`. As a result, `ArrayIntList` can provide fast access to the value at any particular index so methods like `get` are constant-time operations. But maintaining this invariant slows down `removeFront` or remove-in-the-middle, which can be important for efficiently modeling and simulating biological data.

Computational biology is an interdisciplinary area of computer science focused on programming computers to understand biological data, such as DNA, the carrier of genetic information in living things. Each **DNA strand** is made up of smaller units called nucleotides. There are four different nucleotides present in DNA: A, C, G, and T. Every human cell has billions of nucleotides, some of which are the same (or at least very similar) across almost all humans while other portions vary across the population. Computer programs can be used to analyze DNA for criminal justice and to simulate biological processes for scientific research.

{{ site.modules | where: 'title', 'DNA Strand' | first }}

What would a list implementation look like if it was not represented in terms of contiguous memory? In **non-contiguous memory**, elements can be stored anywhere. One possibility is shown below.

Non-contiguous memory (one possibility)
: | 42 | | | 9 | | -3 | | | 17 |

Non-contiguous memory provides more flexibility since an item can be added anywhere. It's now much more difficult to know the location of the next element in the list. Collections based on non-contiguous memory address this problem by storing two pieces of information per element:

1. The actual `data` value of the element.
1. A reference to the `next` element in the list.
