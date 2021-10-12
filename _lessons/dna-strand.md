---
title: DNA Strand
nav_order: 4
has_children: true
has_toc: false
summary: Due Oct 29
---

# DNA Strand
{: .no_toc .mb-2 }

Implementing a DNA data type for scientific computing.[^1]
{: .fs-6 .fw-300 }

[^1]: Brian Yu and David Malan. 2020. DNA. In Nifty Assignments 2020. <http://nifty.stanford.edu/2020/dna/>

      Keith Schwarz. 2020. The Adventures of Links. In CS 106B Winter 2020. <https://web.stanford.edu/class/archive/cs/cs106b/cs106b.1204/handouts/260%20Assignment%207.pdf>

Computational biology is an interdisciplinary area of computer science focused on programming computers to understand biological data, such as DNA, the carrier of genetic information in living things. Each **DNA strand** is made up of smaller units called nucleotides. There are four different nucleotides present in DNA: A, C, G, and T. Every human cell has billions of nucleotides, some of which are the same (or at least very similar) across almost all humans while other portions vary across the population. Computer programs can be used to analyze DNA for criminal justice and to simulate biological processes for scientific research.

{% assign module = site.modules | where: 'title', page.title | first %}
{{ module }}

DNA profiling
: The process of determining an individual's genetic fingerprint for use in criminal justice. One place where DNA tends to have high genetic diversity is in **Short Tandem Repeats** (STRs). An STR is a short sequence of nucleotides that tends to repeat consecutively numerous times at specific locations inside human DNA. The number of times any particular STR repeats varies a lot among individuals. In the DNA samples below, for example, Alice has the STR `AGAT` repeated four times in her DNA, while Bob has the same STR repeated five times.[^2]
: Alice
  : CT**AGATAGATAGATAGAT**GACTA
: Bob
  : CT**AGATAGATAGATAGATAGAT**T

[^2]: Using multiple STRs, rather than just one, can improve the accuracy of DNA profiling. If the probability that two people have the same number of repeats for a single STR is 5%, and the analyst looks at 10 different STRs, then the probability that two DNA samples match purely by chance is about 1 in 1 quadrillion (assuming all STRs are independent of each other). So if two DNA samples match in the number of repeats for each of the STRs, the analyst can be pretty confident they came from the same person. CODIS, The FBI's [DNA profiling database](https://www.fbi.gov/services/laboratory/biometric-analysis/codis/codis-and-ndis-fact-sheet) considers 20 different STRs. In practice, since analysts know on which chromosome and at which location in the DNA an STR will be found, they can localize their search to just a narrow section of DNA. But we'll ignore that detail for this problem and check the entire strand each time.

## Specification

Implement a `DNAStrand` data type that represents DNA with linked `Nucleotide` nodes.

`DNAStrand(String dna)`
: Constructs a new `DNAStrand` with the given `dna` string representing nucleotide bases.

`int maxConsecutiveRepeats(DNAStrand substrand)`
: Returns the maximum number of consecutive repetitions of the nucleotides in `substrand` found within this strand. Throws an `IllegalArgumentException` if the `substrand` is null or empty. Assume the `substrand` is strictly shorter than `this`. Make sure to consider every node as a potential starting position for the maximum consecutive repeats.

There are a few additional requirements.

- Do not construct any arrays, lists, strings, or other data structures.
- Only the `DNAStrand` constructor may create `new Nucleotide(...)` instances.

## Web app

To launch the web app, **Open Terminal** <svg class="inline-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 82" fill-rule="evenodd" stroke-linejoin="round" stroke-miterlimit="2" id="terminal"><path d="M44.518 70.139H100v11.097H44.518z"></path><path d="M7.845 73.347L0 65.502l28.826-28.828L0 7.845 7.845 0l36.673 36.674L7.845 73.347z" fill-rule="nonzero"></path></svg>, paste the following command, and press Enter.

```sh
javac Server.java && java Server database.csv; rm *.class
```

Then, open the **Network** <svg class="inline-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 71" fill-rule="evenodd" stroke-linejoin="round" stroke-miterlimit="2" id="wifi"><path d="M0 20.693l9.091 9.091c22.592-22.592 59.225-22.592 81.818 0L100 20.693c-27.593-27.59-72.363-27.59-100 0zm36.364 36.364L50 70.693l13.637-13.637c-7.502-7.545-19.727-7.545-27.273.001zM18.182 38.875l9.091 9.091c12.544-12.544 32.91-12.544 45.455 0l9.091-9.091c-17.544-17.545-46.046-17.545-63.637 0z" fill-rule="nonzero"></path></svg> dropdown and select host 0.0.0.0:8000.

When you're done, return to the terminal and enter the key combination `Ctrl` `C` to close the server.

## Grading

**Mark** the program to submit it for grading. In addition to the automated tests, the final submission will also undergo code review for [internal correctness]({{ site.baseurl }}{% link quality/index.md %}) on comments, variable names, indentation, data fields, and code quality.

[Commenting errors]({{ site.baseurl }}{% link quality/commenting.md %})
: Method header does not describe the purpose of each parameter or does not describe the meaning of the return value of a non-void method.

Readability errors
: [Nondescriptive names for local variables or methods.]({{ site.baseurl }}{% link quality/naming.md %}#descriptiveness)

Control structure errors
: Bad use of if/else, e.g. empty branch, if/if instead of if/else, poor factoring, unnecessary tests.
: [Bad use of loops.]({{ site.baseurl }}{% link quality/zen.md %}#loop-zen) For example, including an unnecessary check before a loop that repeats the loop test.

Method errors
: [Not throwing exceptions at the top of a method]({{ site.baseurl }}{% link quality/formatting.md %}#exceptions) when detecting the error does not require significant computation.
: Using if/else instead of if for exception code (non-exception code should not be in an else branch).
: Modifying a parameter to a method when such modification was not part of the intended behavior.

Miscellaneous errors
: [Failure to simplify code.]({{ site.baseurl }}{% link quality/efficiency-redundancy.md %}) For example, not factoring out common code, extra tests or loops that aren't necessary. Create `private` "helper" method(s) to capture repeated code.
