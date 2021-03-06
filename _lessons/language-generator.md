---
title: Language Generator
nav_order: 5
has_children: true
has_toc: false
summary: Due Nov 5
---

# Language Generator
{: .no_toc .mb-2 }

Generating sentences with recursion and randomness.[^1]
{: .fs-6 .fw-300 }

[^1]: Julie Zelenski. 1999. Random Sentence Generator. In Nifty Assignments 1999. <https://www-cs-faculty.stanford.edu/~zelenski/rsg/>

In syntactocentric linguistics, **recursive syntax** (embedding phrases within phrases) has been hypothesized to be the critical feature of human language capacity. Although this claim has been challenged in recent decades, generating understandable human language remains a key challenge for computer programming given the infinite expressiveness of human language. Can we define a program to generate all possible English sentences?

{% assign module = site.modules | where: 'title', page.title | first %}
{{ module }}

Most (if not all) human languages involve combining words in certain ways that correspond to valid sentences. The rules that determine valid and invalid sentences are part of the language's grammar.

Formal language
: A set of words and symbols along with a set of production rules defining how those symbols may be used together. For example, "A boy threw the ball." is a valid sentence, but "A threw boy ball the" makes no sense, because the words were put together in an invalid manner.

Grammar
: A way of describing the syntax and symbols of a formal language. When constructing sentences, words are put together in grammatically-correct ways using structures such as sentences, noun phrases, and objects. Grammars consist of two types of **symbols** that represent either individual words (**terminal**) or combinations of words such as phrases and sentences (**non-terminal**).

**Generative grammar** is a linguistic theory that supposes a system of rules can be followed to generate every possible grammatical expression in a formal language. For example, consider this formal language with the following terminals and non-terminals.

Terminals
: the, a, boy, girl, runs, walks

Non-terminals
: - A **sentence** consists of an **article** followed by an **object** followed by a **verb**.
  - An **article** consists of either "the" or "a".
  - An **object** consists of either "boy" or "girl".
  - A **verb** consists of either "runs" or walks".

This language contains the following valid sentences.

- the boy runs
- the boy walks
- a boy runs
- a boy walks
- the girl runs
- the girl walks
- a girl runs
- a girl walks

## Specification

Implement a `LanguageGenerator` class that generates valid strings according to the production rules defined by the given `Grammar`. A `Grammar` consists of a `Supplier` field with a `get()` method that returns a `Map<String, String[]>` representing the production rules.

`LanguageGenerator(Grammar grammar)`
: Constructs a new `LanguageGenerator` for the given grammar.

`LanguageGenerator(Grammar grammar, Random random)`
: Constructs a new `LanguageGenerator` for the given grammar and source of randomness.

`String generate(String target)`
: Returns a string generated by following the production rule for the given `target`. The resulting string should be compact: there should be exactly one space between each terminal and no leading or trailing spaces. Choose between potential production rules for the given `target` by calling `random.nextInt` so that each possibility is equally likely to be chosen.

The base case occurs when the `target` is a terminal symbol. Otherwise, in the recursive case (a non-terminal symbol):

1. Choose a random production rule for the given non-terminal `target` symbol.
1. For each symbol in the production rule, recursively `generate` an occurrence of that symbol.

Split a production rule on one or more whitespace characters by calling `split("\\s+")`.

```java
String text = "lots of spaces";
String[] terms = text.split("\\s+");
// ["lots", "of", "spaces"]
```

Call the `trim` method to remove leading and trailing whitespace from the final result.

```java
String text = "   lots   of  spaces    ";
String trimmed = text.trim();
// "lots   of  spaces"
```

## Web app

To launch the web app, **Open Terminal** <svg class="inline-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 82" fill-rule="evenodd" stroke-linejoin="round" stroke-miterlimit="2" id="terminal"><path d="M44.518 70.139H100v11.097H44.518z"></path><path d="M7.845 73.347L0 65.502l28.826-28.828L0 7.845 7.845 0l36.673 36.674L7.845 73.347z" fill-rule="nonzero"></path></svg>, paste the following command, and press Enter.

```sh
javac -cp ".:/course/lib/*" Server.java && java -cp ".:/course/lib/*" Server; rm *.class
```

Then, open the **Network** <svg class="inline-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 71" fill-rule="evenodd" stroke-linejoin="round" stroke-miterlimit="2" id="wifi"><path d="M0 20.693l9.091 9.091c22.592-22.592 59.225-22.592 81.818 0L100 20.693c-27.593-27.59-72.363-27.59-100 0zm36.364 36.364L50 70.693l13.637-13.637c-7.502-7.545-19.727-7.545-27.273.001zM18.182 38.875l9.091 9.091c12.544-12.544 32.91-12.544 45.455 0l9.091-9.091c-17.544-17.545-46.046-17.545-63.637 0z" fill-rule="nonzero"></path></svg> dropdown and select host 0.0.0.0:8000.

When you're done, return to the terminal and enter the key combination `Ctrl` `C` to close the server.

## Grading

**Mark** the program to submit it for grading. In addition to the automated tests, the final submission will also undergo code review for [internal correctness]({{ site.baseurl }}{% link quality/index.md %}) on comments, variable names, indentation, data fields, and code quality.

Control structure errors
: [Extra recursive cases or extra base cases that are not needed.]({{ site.baseurl }}{% link quality/zen.md %}#recursion-zen) For example, introducing additional "arm's length" base cases that solve the problem preemptively.

Method errors
: [Unnecessary parameters with redundant information when it could be accessed from another source.]({{ site.baseurl }}{% link quality/class-design.md %}#parameters)

Data structure errors
: Excessive inefficiency when using collections. For example, using a for-each loop to find a value in a map when `get` would return the value directly.
