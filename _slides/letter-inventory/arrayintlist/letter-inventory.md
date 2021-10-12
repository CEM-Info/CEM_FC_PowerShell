---
title: Letter Inventory
nav_order: 0
---

Natural language processing (NLP) is an interdisciplinary area of computer science focused on programming computers to work with natural languages used by humans everyday. Since all data in computers are ultimately represented as numbers, a key challenge in NLP is **vectorization**: the process of turning a natural language text into a meaningful numeric representation.

A **letter inventory** is a data type that represents a character-by-character count vectorization for letters in the English alphabet. Each letter inventory keeps track of how many a's, how many b's, etc. are contained in a given string. For example, the letter inventory for the string "Washington State" corresponds to [aaeghinnosstttw]. The case of the letter is ignored, so 's' and 'S' are exactly the same.

{{ site.modules | where: 'title', 'Letter Inventory' | first }}

We can use letter inventories to autocorrect text as the user types!
