---
layout: default
title: Source File Structure
parent: Quality
nav_order: 1
---

# Source File Structure
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Package statements

Do not include package statements in your submission.

## Import statements

Use wildcard import statements instead of specific imports. Use statements like `import java.util.*;` over `import java.util.ArrayList;`

## Ordering of class contents

Place field declarations at the top of your class.

The order of how you place methods is up to you, but it helps readability to maintain some kind of logical ordering. One common ordering is to include all constructors in the beginning, then all other public methods before private methods. Programmers also commonly choose to put related public/private pair methods together so that another viewer of the code can see the pair at the same time.
