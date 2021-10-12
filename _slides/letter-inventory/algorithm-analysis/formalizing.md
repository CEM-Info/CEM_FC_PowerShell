---
title: Formalizing
nav_order: 4
---

To summarize our findings, we can say the following about the runtime of `indexOf`.

Simple English
: In the worst case (when the `target` is not in the `array`), the number of steps that it takes to evaluate `indexOf` is directly correlated with N, the length of the `array`.
: In the best case (when `array[0] == target`), it takes about 4 steps to evaluate `indexOf` regardless of the length of the `array`.

This description succinctly captures the different factors that can potentially affect the runtime of `indexOf`. While this description captures all of the ideas necessary to convey the key message, computer scientists will typically enhance this description with mathematics to capture a more general geometric intuition about the runtime.

Order of growth
: In the worst case, the **order of growth of the runtime** of `indexOf` is **linear** with respect to N, the length of the `array`.
: In the best case, the **order of growth of the runtime** of `indexOf` is **constant** with respect to N, the length of the `array`.

The **order of growth** relates the size of the input to the time that it takes to evaluate the algorithm on that input. Mathematicians formally defined a notation for order of growth using **big-O** ("big oh"). Computer scientists then adopted this notation for algorithm analysis in the 1970s. However, many programmers nowadays mistakenly use big-O notation when they really mean **big-Θ** ("big theta"). The mathematical notation that best represents "directly correlates" is big-Θ notation.

Big-Θ notation
: In the worst case, the runtime of `indexOf` is in Θ(N) [the family of functions whose order of growth is linear] with respect to N, the length of the `array`.
: In the best case, the runtime of `indexOf` is in Θ(1) [the family of functions whose order of growth is constant] with respect to N, the length of the `array`.

This notation makes it easy to compare algorithms!
