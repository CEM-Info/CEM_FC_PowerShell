---
title: Text Classifier
nav_order: 0
---

Online abuse and harassment stops people from engaging in conversation. One area of focus is the study of negative online behaviors, such as **toxic comments**: user-written comments that are rude, disrespectful or otherwise likely to make someone leave a discussion. Platforms struggle to effectively facilitate conversations, leading many communities to [limit](https://meta.stackexchange.com/q/342779) or [completely shut down](https://en.wikipedia.org/wiki/R/The_Donald#Quarantine,_restriction,_ban_and_successor) user comments. In 2018, the [Conversation AI](https://conversationai.github.io/) team, a research initiative founded by [Jigsaw](https://jigsaw.google.com/) and Google (both part of Alphabet), organized a public competition called the [Toxic Comment Classification Challenge](https://www.kaggle.com/c/jigsaw-toxic-comment-classification-challenge) to build better machine learning systems for detecting different types of of toxicity like threats, obscenity, insults, and identity-based hate.

Warning

: Machine learning models are trained on human-selected and human-generated datasets. Such models reproduce the bias inherent in the data. The included data representation algorithms also encode overly-simplistic assumptions about natural language by treating each occurrence of a word as independent from all other words in the text. Any usage of a word, no matter the context, is considered equally toxic. Don't use this in a real system!

  When the Conversation AI team first built toxicity models, they found that the models [incorrectly learned to associate](https://medium.com/the-false-positive/unintended-bias-and-names-of-frequently-targeted-groups-8e0b81f80a23) the names of frequently attacked identities with toxicity. In 2019, the Conversation AI team ran another competition about [Unintended Bias in Toxicity Classification](https://www.kaggle.com/c/jigsaw-unintended-bias-in-toxicity-classification), focusing on building models that detect toxicity across a range of diverse conversations.

  The provided datasets contain text that may be considered profane, vulgar, or offensive.

{{ site.modules | where: 'title', 'Text Classifier' | first }}

Toxic comment classification is a special case of a more general problem in machine learning known as **text classification**. Discussion forums use text classification to determine whether comments should be flagged as inappropriate. Email software uses text classification to determine whether incoming mail is sent to the inbox or filtered into the spam folder.[^1]

![Spam email classifier]({{ site.baseurl }}{% link assets/images/spam-classifier.png %})

[^1]: Google Developers. Oct 1, 2018. Text classification. In Machine Learning Guides. <https://developers.google.com/machine-learning/guides/text-classification>

The simplest possible text classifier returns `true` for every input string: every string is classified as toxic (or spammy).

```java
public static boolean classify(String text) {
    return true;
}
```

One way to add more nuance is by introducing conditional statements so that the behavior of the method depends on the input string.

```java
public static boolean classify(String text) {
    if (text.toLowerCase().contains("free")) {
        if (text.toLowerCase().contains("won")) {
            ...
        } else {
            ...
        }
    } else {
        if (...) {
            ...
        } else {
            ...
        }
    }
}
```

But if there are infinitely many sentences, then there are also potentially infinitely many ways in which text can be interpreted as toxic (or spammy). To manage this complexity, we'll introduce a new recursive data type known as a **decision tree**.
