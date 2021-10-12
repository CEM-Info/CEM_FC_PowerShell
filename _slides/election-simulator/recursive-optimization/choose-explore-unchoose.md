---
title: Choose-explore-unchoose
nav_order: 0
---

Consider the recursive method `rollDice` that prints out all of the possible outcomes of rolling a given number of `dice`.

```java
public static void rollDice(int dice) {
    rollDice(dice, "");
}

private static void rollDice(int dice, String chosen) {
    if (dice == 0) {
        System.out.println(chosen);
    } else {
        for (int value = 1; value <= 6; value += 1) {
            rollDice(dice - 1, chosen + value);
        }
    }
}
```

Beyond solving problems with strings, many real-world recursive enumeration problems will use a data structure to represent solutions. However, working with data structures is more complicated than working with numbers and strings. What would happen if represented each solution in a list rather than string?

```java
public static void rollDice(int dice) {
    rollDice(dice, new ArrayList<Integer>());
}

private static void rollDice(int dice, List<Integer> chosen) {
    if (dice == 0) {
        System.out.println(chosen);
    } else {
        for (int value = 1; value <= 6; value += 1) {
            // Add the dice roll value to the chosen outcomes
            chosen.add(value);
            rollDice(dice - 1, chosen);
        }
    }
}
```

This algorithm contains a bug that's due to reference semantics work in Java!

<details markdown="1">
<summary>Describe the bug in your own words.</summary>

There is only a single list of `chosen` outcomes shared between every recursive call! Consider what happens after rolling the first dice and add 1 to the `chosen` list of outcomes. The recursion here makes sense: we want to pass the updated list of `chosen` outcomes to the next recursive call. But when we eventually return from the `rollDice` call, the `chosen` list will have completely changed!
</details>

In order to undo the unintended changes to the `chosen` list, remove the choice after the recursive call has finished exploring the subproblem.

Choose-explore-unchoose pattern
: For each option

  1. **Choose** the option.
  1. **Explore** the option.
  1. **Unchoose** the option.

```java
public static void rollDice(int dice) {
    rollDice(dice, new ArrayList<Integer>());
}

private static void rollDice(int dice, List<Integer> chosen) {
    if (dice == 0) {
        System.out.println(chosen);
    } else {
        for (int value = 1; value <= 6; value += 1) {
            // Choose the option
            chosen.add(value);
            // Explore the option
            rollDice(dice - 1, chosen);
            // Unchoose the option
            chosen.remove(chosen.size() - 1);
        }
    }
}
```
