---
title: Autocomplete
nav_order: 1
has_children: true
has_toc: false
summary: Due Oct 8
---

# Autocomplete
{: .no_toc .mb-2 }

Implementing a comparable data type for efficient autocomplete.[^1]
{: .fs-6 .fw-300 }

[^1]: Kevin Wayne. 2016. Autocomplete-Me. In Nifty Assignments 2016. <http://nifty.stanford.edu/2016/wayne-autocomplete-me/>

Autocomplete is a feature of many modern applications that automatically helps the user complete an input query based on a list of predicted terms. We can implement predictive autocomplete in three steps: sorting the terms by query string; binary searching to find all query strings that start with a given prefix; and sorting the matching terms by relevance.

{% assign module = site.modules | where: 'title', page.title | first %}
{{ module }}

## Specification

Implement a `Term` class that represents an autocomplete term---a query string and an associated integer weight. Each instance of the `Term` class can be compared against other instances of the `Term` class in two different ways.

1. Compare query by [lexicographic order][] so that terms appear in dictionary order.
1. Compare weight by descending order so that the most heavily-weighted terms appear first.

[lexicographic order]: https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/String.html#compareTo(java.lang.String)

`Term(String query, int weight)`
: Constructs a term with the given non-null `query` string and `weight`.

`int compareTo(Term other)`
: Compares to another term in lexicographic order by query and ignoring case.

`int compareToByReverseWeight(Term other)`
: Compares to another term in descending order by weight.

`String query()`
: Returns this term's query.

`int weight()`
: Returns this term's weight.

`String toString()`
: Returns this term's query.

## Run, Check, Mark

The **Run** button will run the `main` method in the `Term` class. Modify the `main` method to test different combinations and print the results to check that they match your expectations.

The **Check** button will display a link to open the Java visualizer for stepping through the `main` method.

The **Mark** button will run a suite of automated tests to check that the program meets the specification.

## Web app

To launch the web app, **Open Terminal** <svg class="inline-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 82" fill-rule="evenodd" stroke-linejoin="round" stroke-miterlimit="2" id="terminal"><path d="M44.518 70.139H100v11.097H44.518z"></path><path d="M7.845 73.347L0 65.502l28.826-28.828L0 7.845 7.845 0l36.673 36.674L7.845 73.347z" fill-rule="nonzero"></path></svg>, paste the following command, and press Enter.

```sh
javac Server.java && java Server cities.tsv; rm *.class
```

Then, open the **Network** <svg class="inline-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 71" fill-rule="evenodd" stroke-linejoin="round" stroke-miterlimit="2" id="wifi"><path d="M0 20.693l9.091 9.091c22.592-22.592 59.225-22.592 81.818 0L100 20.693c-27.593-27.59-72.363-27.59-100 0zm36.364 36.364L50 70.693l13.637-13.637c-7.502-7.545-19.727-7.545-27.273.001zM18.182 38.875l9.091 9.091c12.544-12.544 32.91-12.544 45.455 0l9.091-9.091c-17.544-17.545-46.046-17.545-63.637 0z" fill-rule="nonzero"></path></svg> dropdown and select host 0.0.0.0:8000.

When you're done, return to the terminal and enter the key combination `Ctrl` `C` to close the server.

## Grading

**Mark** the program to submit it for grading. In addition to the automated tests, the final submission will also undergo code review for [internal correctness]({{ site.baseurl }}{% link quality/index.md %}) on comments, variable names, indentation, and code quality.

[Commenting errors]({{ site.baseurl }}{% link quality/commenting.md %})
: Class header missing or doesn't describe both student and program.
: Blind copying of text from assignment writeup.

Readability errors
: [Lines over 100 characters long.]({{ site.baseurl }}{% link quality/formatting.md %}#column-limit-and-line-wrapping)
: [Not following Java naming conventions.]({{ site.baseurl }}{% link quality/naming.md %}#casing).
: [One-letter or nondescriptive field names.]({{ site.baseurl }}{% link quality/naming.md %}#descriptiveness)
: Method or constructor does not have a blank line before it.

Class design errors
: [Extra public methods or constructors not in the specification.]({{ site.baseurl }}{% link quality/class-design.md %}#access-modifiers)
: [Not including either public or private for a method declaration.]({{ site.baseurl }}{% link quality/class-design.md %}#access-modifiers)
