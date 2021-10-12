---
layout: default
title: Formatting
parent: Quality
nav_order: 2
---

# Formatting
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Indentation

Each time a curly brace is opened, increase the indent level. When the closing curly brace occurs and ends the code block, the indent should return to the previous indent level. The indent level applies to both code and comments throughout the block defined by the curly braces.

Choose 3 or 4 spaces to be your indent level and stay consistent.

## Spacing

Java is not a whitespace sensitive language, but maintaining good spacing throughout your program helps your code be more readable for human eyes. Most Java programmers follow the below spacing conventions for their programs.

- Class headers: `public class SomeClass {`
- Method headers: `public static void someMethod(int number1, int number2) {`
- Method calls: `someMethod(4, 3);`
- Loops:
  - `for (int i = 0; i < 4; i++) {`
  - `while (someTest) {`
  - `for (String s : list) {`
- Arrays: `int[] someArray = new int[4];`
- Variable initializations: `int someNumber = 4;`
- Expressions:
  - `int x = 4 * (3 + 2) - 1;`
  - `boolean result = test1 && test2 || (x != 3);`

The spacing around methods also matters. Remember to **leave a blank line before each method comment** for readability.

## One statement per line

Each time you finish a statement with a semicolon, you should use a new line to begin the next statement.

Note
: The exception to this rule is that the `for` loop header should have its 3 parts all on one line.

## Column limit and line wrapping

No line should exceed 100 characters in length.

Terminology Note
: When code that might otherwise legally occupy a single line is divided into multiple lines, this activity is called **line-wrapping**. Use line-wrapping to break up long lines that would otherwise exceed 100 characters, as described below.

When line-wrapping, each line after the first (each continuation line) should be indented at least one level. Common choices for how much to indent include 2 levels of indentation or lining up elements from the previous line of the long line.

Bad
: It's good that this line is wrapped to maintain the 100 char line limit, but the continued line should be indented at least 1 indentation level.

  ```java
    public static void method1(String param1, String param2, String param3,
  String param4, String param5) {
      ...
  }
  ```

Good
: This method header is properly indented and uses 2 levels of indentation for the broken up line.

  ```java
    public static void method1(String param1, String param2, String param3,
          String param4, String param5) {
      ...
  }
  ```

Good
: This method header is also properly indented, and lines up elements from the broken up line.

  ```java
    public static void method1(String param1, String param2, String param3,
                               String param4, String param5) {
      ...
  }
  ```

Tip
: Extracting method calls into a local variable may solve the problem without the need to line-wrap.

## Exceptions

**Exception code should come at the top of the method.** Everything related to checking for and throwing the exception (computing a value to be used in the condition, the if statement itself) counts as exception code. Any code unrelated to the exception conditions/throwing should be placed lower than exception code. This is both an attempt to fail early to avoid unnecessary computation and a readability rule.

If an exception check cannot be checked at the beginning of the method (e.g. requires significant computation/additional statements), check for it when it can be more easily detected as the method continues.

Bad
: This example doesn't check/throw for the exception at the very beginning of the method.

  ```java
  public static int countVowels(String name) {
      int total = 0;
      if (name.length() <= 1) {
          throw new IllegalArgumentException();
      }
      ...
  }
  ```

**Do not attach else statements onto exception checks to connect regular behavior code.** Following an exception check, non-exception code should not be placed in an attached else. This is another readability rule (mostly done by convention. Another reason: why indent all of the method's regular behavior code a whole level if the structure is still clear without indenting?) as well as a logic rule. Exception code is fundamentally different than regular method behavior code, and shouldn't be connected to regular behavior with one long if/else structure. Doing so almost implies the if/else branches are on the same level of importance or that they are related.

Bad
: This example attaches an `else` to an exception check. This leads to indenting all the normal behavior code, which makes it a little bit harder to read.

  ```java
  public static int countVowels(String name) {
      if (name.length() <= 1) {
          throw new IllegalArgumentException();
      } else {
          int total = 0;
          ...
      }
  }
  ```

Good
: This one is perfect! No else attached with regular behavior and the check for exception is at the top of the method.

  ```java
  public static int countVowels(String name) {
      if (name.length() <= 1) {
          throw new IllegalArgumentException();
      }
      int total = 0;
      ...
  }
  ```

Note
: `else if` logic that checks for more exceptions are fine. Just don't use else to have a branch for the method's normal behavior code. For example the following code structure would be fine.

  ```java
  if (exceptionCheck) {
      throw exception1
  } else if (exceptionCheck2) {
      throw exception2
  }
  // non-exception behavior code here
  ```

## Curly Brace Style

- No line break before the opening brace.
- Line break after the opening brace.
- Line break before the closing brace.
- Line break after the closing brace, *only if* that brace terminates a statement or terminates the body of a method, constructor, or class. For example, there is *no* line break after the brace if it is followed by `else`.

```java
public static void method1(int times) {
    for (int i = 0; i < times; i++) {
        if (i % 2 == 0) {
             System.out.print(i);
        } else {
             System.out.print("x");
        }
        System.out.println(" hello");
    }
}
```
