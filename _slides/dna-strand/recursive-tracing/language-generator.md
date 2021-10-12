---
title: Language Generator
nav_order: 1
---

It turns out that humans use recursion in everyday English. English grammar allow syntactic recursion with phrases embedded within phrases.[^1] (In the following examples, brackets denote recursive structure.)

[^1]: Edward Gibson. 9.59J Lab in Psycholinguistics. Spring 2017. Massachusetts Institute of Technology: MIT OpenCourseWare, <https://ocw.mit.edu>. License: [Creative Commons BY-NC-SA](https://creativecommons.org/licenses/by-nc-sa/4.0/).

Conjunction
: [[John and Mary] and Bill]

Clausal complements
: [John thinks that [Mary said that [the girl cried]]]

Possessives
: [[[[John]'s mother]'s brother]'s house]
: [the house of [the brother of [the mother of [John]]]]

In syntactocentric linguistics, **recursive syntax** (embedding phrases within phrases) has been hypothesized to be the critical feature of human language capacity. Although this claim has been challenged in recent decades, generating understandable human language remains a key challenge for computer programming given the infinite expressiveness of human language. Can we define a program to generate all possible English sentences?

{{ site.modules | where: 'title', 'Language Generator' | first }}

Recursive algorithms present one direct approach for answering this question. But before we try to tackle that question, we'll study recursive algorithms for problems that we already know how to solve in order to build a foundation for answering these bigger questions in the future.
