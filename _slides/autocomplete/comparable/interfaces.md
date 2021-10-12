---
title: Interfaces
nav_order: 2
---

We've just implemented the `compareTo` method, but it turns out that this isn't enough to implement a comparison relationship! One key difference between `toString` and `compareTo` is that every class contains a `toString` method (the default returns a gibberish string), but not every class necessarily contains a `compareTo` method.

The goal of compiling a Java program is to guarantee that it can run. The Java compiler checks to make sure all of the programs in the ecosystem can work together, but it can't maintain that guarantee across all data types since `compareTo` is not automatically provided until a programmer writes the method.

To communicate the fact that we've written a valid and complete `compareTo` method, the class header must also `implements Comparable<...>` where `...` is replaced with the same type.

```java
public class Balance implements Comparable<Balance> {
    private int totalCents;

    public int compareTo(Balance other) {
        return Integer.compare(this.totalCents, other.totalCents);
    }
}
```
{: overlay="Implementer" }

We read the class header as, "A public class `Balance` that can be compared against other instances of `Balance`." The class is now **comparable**: it can be compared against other instances of the same type.

`Comparable`
: The interface that requires a single method, `compareTo`. It accepts a generic type that represents the class of the other object to be compared against.
