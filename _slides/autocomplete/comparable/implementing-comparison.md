---
title: Implementing comparison
nav_order: 1
---

In Autocomplete, we will implement the `Term` data type, which represents a possible autocompletion term. Similar to how the `println` method (client) depends on `toString`, the autocomplete algorithm (client) depends on functionality to **compare any two autocompletion terms** in the form of a `compareTo` public method.

The `compareTo` method takes another instance of the same class and returns an `int` representing the comparison relationship between the current and other instance.

- If `this < other`, then `this.compareTo(other) < 0`.
- If `this == other`, then `this.compareTo(other) == 0`.
- If `this > other`, then `this.compareTo(other) > 0`.

For example, in the `Balance` class, we can define a `compareTo` method to compare the current balance's value against another balance. (Rest of the class is omitted.)

```java
public class Balance {
    private int totalCents;

    public int compareTo(Balance other) {
        return this.totalCents - other.totalCents;
    }
}
```
{: overlay="Implementer" }

This way, we define larger balances as "greater than" smaller balances.

- If `this.totalCents < other.totalCents`, then `this.compareTo(other) < 0`.
- If `this.totalCents == other.totalCents`, then `this.compareTo(other) == 0`.
- If `this.totalCents > other.totalCents`, then `this.compareTo(other) > 0`.

Sun anticipated programmers would need to write classes that implemented `Comparable`, so they provided helper methods for many commonly-used data types including `int`, `double`, and `String`. For objects such as `String`, we can be the client of the `String` class's `compareTo` method by calling `compareTo` ourselves.

However, we can't call `this.totalCents.compareTo(other.totalCents)` directly since `totalCents` is an `int` primitive type, not an object. Instead, the `Integer` and `Double` classes provide a special static method `compare` that returns the `compareTo` result between two numbers, `x` and `y`.

```java
public class Balance {
    private int totalCents;

    public int compareTo(Balance other) {
        return Integer.compare(this.totalCents, other.totalCents);
    }
}
```
{: overlay="Implementer" }

<details markdown="1">
<summary>Describe a change that would make smaller balances "greater than" larger balances.</summary>

Negate the result before returning it, or subtract `this.totalCents` from `other.totalCents`.

```java
public int compareTo(Balance other) {
    return -Integer.compare(this.totalCents, other.totalCents);
    // return other.totalCents - this.totalCents;
}
```
{: overlay="Implementer" }
</details>

We prefer `Integer.compare` and `Double.compare` instead of subtracting numbers directly because of a subtlety when returning the difference of two `double` values as an `int`. Java **truncuates** `double` values when converting to `int`. For example, suppose we defined balances in `double totalDollars` rather than `int totalCents`. If we take a $1.75 balance and compare it with a $1.00 balance, the difference of $0.75 is truncated down to 0 so the two balances would be considered the same!
