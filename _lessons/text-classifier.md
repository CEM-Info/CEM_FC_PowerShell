---
title: Text Classifier
nav_order: 7
has_children: true
has_toc: false
summary: Due Nov 19
---

# Text Classifier
{: .no_toc .mb-2 }

Implementing a decision tree data type for text classification.
{: .fs-6 .fw-300 }

Online abuse and harassment stops people from engaging in conversation. One area of focus is the study of negative online behaviors, such as **toxic comments**: user-written comments that are rude, disrespectful or otherwise likely to make someone leave a discussion. Platforms struggle to effectively facilitate conversations, leading many communities to [limit](https://meta.stackexchange.com/q/342779) or [completely shut down](https://en.wikipedia.org/wiki/R/The_Donald#Quarantine,_restriction,_ban_and_successor) user comments. In 2018, the [Conversation AI](https://conversationai.github.io/) team, a research initiative founded by [Jigsaw](https://jigsaw.google.com/) and Google (both part of Alphabet), organized a public competition called the [Toxic Comment Classification Challenge](https://www.kaggle.com/c/jigsaw-toxic-comment-classification-challenge) to build better machine learning systems for detecting different types of of toxicity like threats, obscenity, insults, and identity-based hate.

Warning

: Machine learning models are trained on human-selected and human-generated datasets. Such models reproduce the bias inherent in the data. The included data representation algorithms also encode overly-simplistic assumptions about natural language by treating each occurrence of a word as independent from all other words in the text. Any usage of a word, no matter the context, is considered equally toxic. Don't use this in a real system!

  When the Conversation AI team first built toxicity models, they found that the models [incorrectly learned to associate](https://medium.com/the-false-positive/unintended-bias-and-names-of-frequently-targeted-groups-8e0b81f80a23) the names of frequently attacked identities with toxicity. In 2019, the Conversation AI team ran another competition about [Unintended Bias in Toxicity Classification](https://www.kaggle.com/c/jigsaw-unintended-bias-in-toxicity-classification), focusing on building models that detect toxicity across a range of diverse conversations.

  The provided datasets contain text that may be considered profane, vulgar, or offensive.

{% assign module = site.modules | where: 'title', page.title | first %}
{{ module }}

Toxic comment classification is a special case of a more general problem in machine learning known as **text classification**. Discussion forums use text classification to determine whether comments should be flagged as inappropriate. Email software uses text classification to determine whether incoming mail is sent to the inbox or filtered into the spam folder.[^1]

![Spam email classifier]({{ site.baseurl }}{% link assets/images/spam-classifier.png %})

[^1]: Google Developers. Oct 1, 2018. Text classification. In Machine Learning Guides. <https://developers.google.com/machine-learning/guides/text-classification>

## Specification

Implement a `TextClassifier` data type, a binary decision tree for classifying text documents.

`TextClassifier(Vectorizer vectorizer, Splitter splitter)`
: Constructs a new `TextClassifier` given a fitted `vectorizer` for transforming data points and a `splitter` for determining the splits in the tree.

`boolean classify(String text)`
: Returns a boolean representing the predicted label for the given `text` by recursively traversing the tree.

`void print()`
: Prints a Java code representation of this decision tree in if/else statement format without braces and with 1 additional indentation space per level in the decision tree. Leaf nodes should print "return true;" or "return false;" depending on the label value.

  ```
  if (vector[318] <= 5.273602694890837)
   if (vector[1116] <= 5.093549034038833)
    return false;
   else
    return false;
  else
   if (vector[893] <= 5.313808994135437)
    return false;
   else
    return false;
  ```

`void prune(int depth)`
: Prunes this tree to the given `depth`. Each pruned subtree is replaced with a new node representing the subtree's majority label. For example, pruning the above decision tree to depth 1 would result in the following structure.

  ```
  if (vector[318] <= 5.273602694890837)
   return false;
  else
   return false;
  ```

Modify and run the `Main` class to debug your `TextClassifier`. Several classes and interfaces are included to handle the machine learning components of the `TextClassifier`. The most useful methods are described below.

### Vectorizer

The `Vectorizer` interface defines algorithms for transforming English text into a `double[][]` design matrix for the `Splitter` interface. A **design matrix** consists of an array of `double[]` vectors, where each **vector** represents a single example text from the dataset (such as a comment or an email). The choice of `BM25Vectorizer` or `LSAVectorizer` algorithm determines how the English text is converted into a numeric representation.

`double[][] transform(String... texts)`
: Returns the design matrix for the given texts.

When implementing the `classify` method, given a single `text`, `vectorizer.transform(text)[0]` evaluates to a vector that can be passed to `Split.goLeft`.

### Splitter

The `Splitter` interface provides a `split` method for dividing the given data points into left and right. The `RandomSplitter` is provided for debugging and visualization purposes while the `GiniSplitter` computes the optimal split based on information theory.

`Splitter.Result split()`
: Returns the best split and the left and right splitters, or null if no good split exists. The `Splitter.Result` class represents the left and right splitters that result from applying a split.

`boolean label()`
: Returns the majority label for this splitter.

When constructing a `TextClassifier`, call `split()` and use the `Splitter.Result` to determine the decision rules. Since the decision tree is a recursive data structure, this process will continue until `split()` returns null, in which case the program should construct a new leaf node containing only the majority label.

### Split

The `Split` class represents a decision rule for splitting vector data.

`boolean goLeft(double[] vector)`
: Returns true if and only if the given vector lies to the left of this decision rule.

`String toString()`
: Returns a string representation of this decision rule, `vector[index] <= threshold`.

## Web app

To launch the web app, **Open Terminal** <svg class="inline-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 82" fill-rule="evenodd" stroke-linejoin="round" stroke-miterlimit="2" id="terminal"><path d="M44.518 70.139H100v11.097H44.518z"></path><path d="M7.845 73.347L0 65.502l28.826-28.828L0 7.845 7.845 0l36.673 36.674L7.845 73.347z" fill-rule="nonzero"></path></svg>, paste the following command, and press Enter.

```sh
javac -cp ".:/course/lib/*" Server.java && java -cp ".:/course/lib/*" Server toxic.tsv; rm *.class
```

Then, open the **Network** <svg class="inline-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 71" fill-rule="evenodd" stroke-linejoin="round" stroke-miterlimit="2" id="wifi"><path d="M0 20.693l9.091 9.091c22.592-22.592 59.225-22.592 81.818 0L100 20.693c-27.593-27.59-72.363-27.59-100 0zm36.364 36.364L50 70.693l13.637-13.637c-7.502-7.545-19.727-7.545-27.273.001zM18.182 38.875l9.091 9.091c12.544-12.544 32.91-12.544 45.455 0l9.091-9.091c-17.544-17.545-46.046-17.545-63.637 0z" fill-rule="nonzero"></path></svg> dropdown and select host 0.0.0.0:8000.

## Grading

**Mark** the program to submit it for grading. In addition to the automated tests, the final submission will also undergo code review for [internal correctness]({{ site.baseurl }}{% link quality/index.md %}) on comments, variable names, indentation, data fields, and code quality.

Data structure errors
: Not using `x = change(x)` when appropriate to simplify code.
