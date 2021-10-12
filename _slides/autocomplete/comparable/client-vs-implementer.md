---
title: Client vs implementer
nav_order: 0
---

Any Java programmer can define their own **data types** by writing Java classes. Earlier, we implemented a `Balance` class that represented a currency amount in dollars and cents. We discussed two ways of implementing the `Balance` class.

1. Using two fields: `dollars` and `cents`.
1. Or using only one field: just `totalCents`.

But computer programs, such as the `Balance` class, do not exist in isolation. They're part of a larger ecosystem of programs that connect and communicate with each other to get things done. It turns out that this idea is a powerful example of **abstraction**: our `Balance` class defines public methods so that other programs written by anyone, anywhere, at anytime before or after it can rely on its functionality as long as they know how to interface with it.

Let's understand this by asking a question: **How exactly does Java print out a $1.50 balance?**

```java
Balance balance = new Balance(1, 50);
System.out.println(balance);
```

1. `System.out` evaluates to an instance of Java's `PrintStream` class that has a `println` method.
1. Control is transferred to the `println` method in order to print out the balance.
1. But in 1996, Sun (the original developers behind Java 1.0) could not have known exactly how we would define our `Balance` class. One field, two fields, or something completely different?

Sun chose to resolve this design challenge by having the `println` method call the balance's `toString` method. By including a `toString` **public method** in the `Balance` class, any program written by anyone, anywhere, at anytime can get a string representation of a balance.

In this example, we consider Sun the **client** of our `toString` method. We (the programmer for the `Balance` class) are the **implementer** of the `toString` method.

Client
: The requester of some method or service.

Implementer
: The provider of some method or service.
