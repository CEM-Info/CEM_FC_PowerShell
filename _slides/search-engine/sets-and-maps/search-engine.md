---
title: Search Engine
nav_order: 0
---

Earlier, we saw that the worst-case order of growth of the runtime for `countUnique` with an `ArrayList` is in Θ(N<sup>2</sup>), where N is the length of the list. The `ArrayList.contains` algorithm may need to scan over the entire list on each iteration of the `while` loop.

```java
public static int countUnique(Scanner input) {
    List<String> words = new ArrayList<String>();
    int count = 0;
    while (input.hasNext()) {
        String word = input.next();
        if (!words.contains(word)) {
            count++;
        }
        words.add(word);
    }
    return count;
}
```
{: overlay="Client" }

On a real dataset containing all of Shakespeare's words, it takes about 3.5 minutes to determine that Shakespeare used 33,505 unique words.[^1] Designing programs for data on the internet might require dealing with even more data every second!

[^1]: This is an overcount since `Scanner` splits tokens on whitespace, so words can include punctuation.

Web search engines are software systems that organize information on the internet so that users can discover web pages related to a search query. We can implement a basic web search engine by building an index that associates each term (word) to all web pages in which it appears. A search query can be answered by returning the documents that contain all of the terms in a given query.

{{ site.modules | where: 'title', 'Search Engine' | first }}
