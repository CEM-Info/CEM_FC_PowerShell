---
title: Inheritance
nav_order: 1
---

We've often declared our data structures using the following syntax, prefering to use the interface type wherever possible. **Interface inheritance** defines the rules for checking that `ArrayList` implements all of the behavior required by the `List` interface.

```java
List<Integer> numbers = new ArrayList<Integer>();
```

In contrast, Java also allows for **implementation inheritance** where classes can be derived from other classes, **inheriting** fields and methods from those other classes. Every class has only one direct superclass that can be explicitly declared with the `extends` keyword. In the absence of any explicit superclass, every class is implicitly a subclass of `Object`. This is why classes defined without `equals` or `toString` can still call those methods because their implementations are inherited from `Object.equals` and `Object.toString`.

But inheritance can get hairy! Sometimes, it's not clear why inheritance doesn't compile or doesn't give the expected output. Consider the following classes. Which method does each statement actually call?

```java
public class Main {
    public static void main(String[] args) {
        Term term = new FancyTerm();
        FancyTerm fancy = new FancyTerm();

        term.compareTo(term);
        term.compareTo(fancy);
        fancy.compareTo(term);
        fancy.compareTo(fancy);
    }
}

class Term implements Comparable<Term> {

    // Implement Comparable<Term>
    public int compareTo(Term other) {
        System.out.println("Term.compareTo(Term)");
        return 0;
    }
}

class FancyTerm extends Term {

    // Override inherited compareTo(Term)
    public int compareTo(Term other) {
        System.out.println("FancyTerm.compareTo(Term)");
        return 0;
    }

    // Specialized compareTo(FancyTerm)
    public int compareTo(FancyTerm other) {
        System.out.println("FancyTerm.compareTo(FancyTerm)");
        return 0;
    }
}
```
