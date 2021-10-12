---
title: Letter Inventory
nav_order: 2
has_children: true
has_toc: false
summary: Due Oct 15
---

# Letter Inventory
{: .no_toc .mb-2 }

Implementing a character vector data type with arrays.
{: .fs-6 .fw-300 }

Natural language processing (NLP) is an interdisciplinary area of computer science focused on programming computers to work with natural languages used by humans everyday. Since all data in computers are ultimately represented as numbers, a key challenge in NLP is **vectorization**: the process of turning a natural language text into a meaningful numeric representation.

A **letter inventory** is a data type that represents a character-by-character count vectorization for letters in the English alphabet. Each letter inventory keeps track of how many a's, how many b's, etc. are contained in a given string. For example, the letter inventory for the string "Washington State" corresponds to `[aaeghinnosstttw]`. The case of the letter is ignored, so 's' and 'S' are exactly the same.

{% assign module = site.modules | where: 'title', page.title | first %}
{{ module }}

## Specification

Implement a `LetterInventory` data type that represents an inventory of the 26 letters in the English alphabet. It should be represented with an array.

`LetterInventory(String data)`
: Constructs an inventory of the letters in the given string, ignoring the case of letters and ignoring any non-alphabetic characters. Store the inventory (how many a', how many b's, ...) as an array of 26 counters (one for each letter) along with any other necessary data fields.

`int get(char letter)`
: Returns a count of how many of this letter are in the inventory. Letter might be lowercase or uppercase. If a nonalphabetic character is passed, throw an `IllegalArgumentException`.

`void set(char letter, int value)`
: Sets the count for the given letter to the given value. The given letter might be lowercase or uppercase. If a nonalphabetic character is passed or if value is negative, throw an `IllegalArgumentException`.

`int size()`
: Returns the sum of all of the counts in this inventory. This operation should be fast in that it should store the size rather than having to compute it each time this method is called.

`boolean isEmpty()`
: Returns true if this inventory is empty (all counts are 0). This operation should be fast in that it should not need to examine each of the 26 counts when it is called.

`String toString()`
: Returns a `String` representation of the inventory with the letters all in lowercase and in sorted order and surrounded by square brackets. The number of occurrences of each letter should match its count in the inventory. For example, an inventory of 4 a's, 1 b, 1 l and 1 m would be represented as `[aaaablm]`.

`LetterInventory add(LetterInventory other)`
: Constructs and returns a new `LetterInventory` object that represents the sum of this letter inventory and the other given `LetterInventory`. The counts for each letter should be added together. The two `LetterInventory` objects being added together (`this` and `other`) should not be changed by this method.
: ```java
  LetterInventory washington = new LetterInventory("Washington");
  LetterInventory state = new LetterInventory("State");
  System.out.println(washington.add(state));
  ```
: `washington` corresponds to `[aghinnostw]`, `state` corresponds to `[aestt]`, and the result of adding them corresponds to  `[aaeghinnosstttw]`.

`LetterInventory subtract(LetterInventory other)`
: Constructs and returns a new `LetterInventory` object that represents the result of subtracting the other inventory from this inventory (i.e., subtracting the counts in the other inventory from this object's counts). If any resulting count would be negative, return `null`. The two `LetterInventory` objects being subtracted (`this` and `other`) should not be changed by this method.

The values of type `char` have corresponding integer values. There is a character with value 0, a character with value 1, a character with value 2, and so on. Different values of type `char` can be compared using the less-than and greater-than operators.

```java
char c = 'w';
if (c >= 'a') {
    // Since 'w' >= 'a', we'll take this branch
    ...
}
```

Use `char` arithmetic to determine array indices and offsets. `char` represents characters as numbers. The lowercase letters are all grouped together: 'a' then 'b' then 'c' and so on. Likewise, uppercase letters are also grouped together: 'A' then 'B' then 'C' and so on. This numbering system allows us to determine the distance between two letters using subtraction: `'c' - 'a'` is 2 since 'c' is 2 letters after 'a' in the alphabet. To programmatically compute the letter 8 alphabet positions after 'a', use addition and then cast the result to `char`. (The result is the letter 'i'.)

```java
char result = (char) ('a' + 8);
```

Getting the lowercase version of some text depends on whether the text is a `String` or a `char`. Since strings are objects in Java, we can call the `toLowerCase` instance method. But since `char` values are just numbers, Java provides the `Character.toLowerCase` static method instead.

```java
String s = "Washington State";
String l = s.toLowerCase();
```

```java
char c = 'W';
char l = Character.toLowerCase(c);
```

## Development strategy

One of the most important techniques for software professionals is to develop code in stages rather than trying to write it all at once. This development strategy is formally known as **iterative enhancement** or **stepwise refinement**. Writing code in stages enables software developers to test each stage independently for correctness.

First, add stubs for each required operation so that we can run tests without implementing the entire class. An example constructor could throw an `UnsupportedOperationException`.

```java
public LetterInventory(String s) {
    throw new UnsupportedOperationException("not implemented yet");
}
```

Then, write the program in three stages.

Constructing a `LetterInventory` and examining its contents
: First, implement the constructor, `size`, and `isEmpty` methods. Then, implement the `get` method. Finally, implement the `toString` method.

Methods for modifying a `LetterInventory`
: Add the `set` method, which allows the client to change the number of occurrences of an individual letter.

Complex behavior
: Implement the `add` method and then implement the `subtract` method.

## Web app

To launch the web app, **Open Terminal** <svg class="inline-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 82" fill-rule="evenodd" stroke-linejoin="round" stroke-miterlimit="2" id="terminal"><path d="M44.518 70.139H100v11.097H44.518z"></path><path d="M7.845 73.347L0 65.502l28.826-28.828L0 7.845 7.845 0l36.673 36.674L7.845 73.347z" fill-rule="nonzero"></path></svg>, paste the following command, and press Enter.

```sh
javac Server.java && java Server data/english.txt; rm *.class
```

Then, open the **Network** <svg class="inline-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 71" fill-rule="evenodd" stroke-linejoin="round" stroke-miterlimit="2" id="wifi"><path d="M0 20.693l9.091 9.091c22.592-22.592 59.225-22.592 81.818 0L100 20.693c-27.593-27.59-72.363-27.59-100 0zm36.364 36.364L50 70.693l13.637-13.637c-7.502-7.545-19.727-7.545-27.273.001zM18.182 38.875l9.091 9.091c12.544-12.544 32.91-12.544 45.455 0l9.091-9.091c-17.544-17.545-46.046-17.545-63.637 0z" fill-rule="nonzero"></path></svg> dropdown and select host 0.0.0.0:8000.

When you're done, return to the terminal and enter the key combination `Ctrl` `C` to close the server.

## Grading

**Mark** the program to submit it for grading. In addition to the automated tests, the final submission will also undergo code review for [internal correctness]({{ site.baseurl }}{% link quality/index.md %}) on comments, variable names, indentation, data fields, and code quality.

[Commenting errors]({{ site.baseurl }}{% link quality/commenting.md %})
: Class header missing or doesn't describe both student and program.
: Method header missing or does not document pre and post-conditions.
: Method header does not describe exceptions that are thrown when preconditions are violated, including the specific type of exception and the conditions under which it is thrown.
: Method header does not document important behavior including subtle cases like an empty structure or a search value not found.
: Implementation details included in comments for a class or its public methods.

Control structure errors
: [Bad Boolean Zen.]({{ site.baseurl }}{% link quality/zen.md %}#boolean-zen)

[Data structure errors]({{ site.baseurl }}{% link quality/data-types.md %}#prefer-simple-data-types)
: Extra data structures (including strings) that aren't necessary.
: Bad usage of arrays, e.g. unusual indexing/usage.

Class design errors
: [Extraneous data fields.]({{ site.baseurl }}{% link quality/class-design.md %}#avoid-extra-fields)
: [Initializing non-final data fields outside of a constructor.]({{ site.baseurl }}{% link quality/class-design.md %}#initialize-fields-inside-the-constructor)
: [Non-private data fields.]({{ site.baseurl }}{% link quality/class-design.md %}#fields-should-always-be-declared-with-the-private-access-modifier)
: [Using a specific numerical value when the value can be obtained in a more general way.]({{ site.baseurl }}{% link quality/class-design.md %}#class-constants) For example, even if an array called `data` is expected to be of length 100, code to manipulate it after construction should use `data.length` instead of 100.
