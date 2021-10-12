---
title: Multiple recursion
nav_order: 0
---

All of the recursive algorithms we've studied so far are examples of **single recursion** and **structural recursion**.

Single recursion
: Each recursive case only makes a single self-recursive call.

Structural recursion
: Recursion that decomposes problems into structural subproblems progressing towards the base case.

In this lesson, we'll introduce two new types of recursive algorithms: **multiple recursion** (now) and **generative recursion** (later).

Multiple recursion
: At least one recursive case makes multiple self-recursive calls.

A classic example of **multple, structural recursion** is the Tower of Hanoi puzzle. Tower of Hanoi is a puzzle that consists of three rods (numbered 1, 2, and 3) and a number of disks of different sizes that can move between rods. The puzzle starts with `n` disks stacked in ascending order on a start rod (rod 1) with the smallest disk at the top. The objective is to move the entire stack from the start rod (1) to the end rod (3), obeying the following rules:

- Only one disk may be moved at a time.
- Each move consists of taking the top (smallest) disk and moving it to another rod, on top of any other disks already there.
- No disk may be placed on top of a smaller disk.

Play the Tower of Hanoi game by hand for 3 disks and try to solve it in the minimum number of moves (7 moves). Can you solve the game for 4 or even 5 disks? Pay attention to structural self-similarities in moves as you play the game.
