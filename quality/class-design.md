---
layout: default
title: Class Design
parent: Quality
nav_order: 4
---

# Class Design
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Fields

### Initialize fields inside the constructor

Do not initialize fields at declaration. This is both a flexibility and readability rule. It's possible that you want to initialize a field to different values in different constructors. Initializing a field at declaration and again in a constructor is both redundant and distracting.

### Declare all fields private access

This modifier ensures clients of the class cannot modify the internal data without using an allowed (`public`) method.

Note
: There is one exception to this rule. For node classes (`ListNode`, `AssassinNode`, `IntTreeNode`, `QuestionNode`, `HuffmanNode`), it is acceptable (and encouraged) to use `public` fields so that the client (you) can directly manipulate the field references to other nodes without using setter methods.

Why? As you'll see when inner classes are introduced, ideally these classes would be `private` inner classes, as clients should be abstracted away from the nodes themselves. Being an inner class also means that the field access modifiers wouldn't matter. However, we're writing them as separate classes, so public field access is the way to allow the nodes to be manipulated in the natural/conventional way.

### Avoid extra fields

The more fields your class has, the more difficult it becomes to maintain and reason about your code. With more fields, each instance of the class will also take up more memory.

Tip
: When revising your code, watch out for fields that are only used in one public method, and/or that are recomputed/cleared every call to a specific method. These can likely be simplified to local variables within the scope of that public method/its private helper methods. Also watch out for redundant fields that can be inferred from the properties of other fields.

## Class Constants

**Class constants should be declared with `public`, `static`, `final` modifiers.**

1. `public` allows a client to directly interact with the constant
2. `static` means the constant is associated with the class rather than a specific instance of the class. (e.g. each instance of a class should have its own independent fields from other instances, but it's fine if they all share the same class constant value)
3. `final` prevents the constant from being assigned a new value. i.e. the initialized value is final.

Create and use class constants when directed by the spec and where appropriate. A good creation/use of a constant constitutes replacing a raw value that is used multiple times in your program with a constant that stores the value, but with more descriptive and readable name. This also provides more flexibility if the raw value ever needs to change.

Note
: Class constants should be initialized at declaration unlike how fields should be initialized in the constructor.

Tip
: Watch out for using raw numbers aka "magic values" in your code. These values might confuse another reader of your code, so you should avoid them and consider other options. There may be a useful method or way to access the value that is more logical, or the spec might have more information.

## Methods

### Access modifiers

**Methods (and constructors) to implement that are listed in the spec should all be declared `public`,** so that clients can call these methods. **Any additional methods/constructors you write in the class should be declared `private`,** so that these methods can only be called internally. This will not only prevent clients from calling these methods in ways that might corrupt your fields or otherwise break your program, but also simplify the functionality a client will have to deal with.

### Parameters

**Avoid extra parameters.** For the same reasons to cut down on fields, simplifying the number of parameters can simplify the code. Watch out for unused parameters or parameters whose values can be inferred by other parameters.

### Returns

**Avoid unnecessary returns.** If you pass in a reference to an object as a parameter, there's no reason to define your method to return that same reference. Wherever called the method already has a reference to the object, as it was able to pass it in the first place, so returning the same value back is redundant. In fact, defining a method to have a redundant return may imply that you made a copy of the object passed in, and may confuse a reader of your code.

Bad
: This method unnecessarily defines a return that always returns the reference to the original object. Because whoever called this method has a reference to the `List` object, we can change this method's return type to void to simplify the method.

  ```java
  public List<String> generateNames(List<String> toFill) {
      // add some elements to toFill
      ...
      return toFill;
  }
  ```

Good
: ```java
  public void generateNames(List<String> toFill) {
      // add some elements to toFill
      ...
  }
  ```

Note
: For the public methods defined in the spec, the parameters and returns listed are required. You should define your method headers to match with the same parameters and returns. For private methods, however, you are in control of the design. This is where extra parameters and returns come into play.

### Unspecified behavior

**Do not add additional behavior beyond what's described in the spec.** This includes additional exceptions. Only include exceptions listed in the specification for each method.

**Do not modify object parameters passed to public methods, unless allowed by the spec.** An unsuspecting client of the method may not have wanted their data dismantled while your method ran for a different purpose.

## Constructors

- When applicable, **reduce redundancy by using the `this()` keyword to call another constructor** in the same class. Generally, the constructors that assume more defaults (fewer parameters) call the more general constructors (more parameters).
- Clients of a class should never have to set fields of an object immediately after construction. There should be a constructor included for this situation. The general behavior of a constructor is to set up the state of an object correctly, and this should encompass setting fields.
- Clients of a class should never have to pass in dummy values to a constructor to set up the desired state. Instead, there should be a constructor included so that only the relevant parameters need to be passed.
- Only implement constructors that are used somewhere.

## Scope

It is generally good practice to keep variables in the most local scope possible. Remember that the scope of a variable is the closest pair of curly braces that surround it. In the following example, the variable `nextScore` has been declared in the scope of the entire method, but note that declaring it in such a wide scope is actually not necessary.

Bad
: ```java
  public static void printTenScores(Scanner console) {
      int nextScore;
      for (int i = 1; i <= 10; i++) {
          System.out.print("next score? ");
          nextScore = console.nextInt();
          System.out.println("score " + i + " = " + nextScore);
      }
  }
  ```

Notice that `nextScore` is only ever accessed inside of the for loop, so we can actually localize its scope to just the loop itself rather than the whole method.

Good
: ```java
  public static void printTenScores(Scanner console) {
      for (int i = 1; i <= 10; i++) {
          System.out.print("next score? ");
          int nextScore = console.nextInt();
          System.out.println("score " + i + " = " + nextScore);
      }
  }
  ```

By localizing scope, our code becomes simpler to reason about, because we've minimized the number of different variables floating around at any given location in our code. Note that eliminating unnecessary fields is often just an example of localizing variables. Also note that "re-declaring" the variable `nextScore` inside the loop is just fine efficiency-wise because of how the compiler will optimize our code. In this course, you shouldn't ever have to worry about micro-optimizations like the number of variable declarations.
