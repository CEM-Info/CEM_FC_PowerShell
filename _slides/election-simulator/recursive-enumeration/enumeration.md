---
title: Enumeration
nav_order: 1
---

**Recursive enumeration** (also known as **exhaustive search**) is a recursive problem-solving technique that solves problems by systematically enumerating (listing out) all solutions in the solution space. Consider the recursive algorithm `fourAB` that prints out all strings of length 4 composed only of the letters "a" and "b".

<details markdown="1">
<summary>What are three possible solutions to the fourAB problem?</summary>

- aaaa
- abba
- babb
</details>

To enumerate the solutions to `fourAB`, we can list out the solutions in a table.

| aaaa | abaa | baaa | bbaa |
| aaab | abab | baab | bbab |
| aaba | abba | baba | bbba |
| aabb | abbb | babb | bbbb |

<details markdown="1">
<summary>What patterns do you notice in the above table?</summary>

- The first two columns have solutions that only start with an "a".
- The first column only has solutions that start with "aa".
- The first column, first two entries only has solutions that start with "aaa".
- The very first entry is "aaaa".
</details>

By arranging the solutions in an organized structure, we can identify recursive partial solutions.

- The left two columns are associated with prepending an "a" to the start of all a/b strings of length **3**.
- The right two columns are associated with prepending a "b" to the start of all a/b strings of length **3**.

Recursive enumeration differs from typical recursive algorithms. Unlike structurally-recursive algorithms that break down their inputs into subproblems, enumerating algorithms work backwards by starting with empty data and generating larger and larger partial solutions until a complete solution is obtained.

Outline for defining recursive enumeration algorithms
: 1. Start the recursive algorithm with empty data.
  1. Recursively generate larger partial solutions.
  1. At each base case, report the completed solution.

```java
public static void main(String[] args) {
    fourAB("");
}

public static void fourAB(String soFar) {
    if (soFar.length() == 4) {
        System.out.println(soFar);
    } else {
        fourAB(soFar + "a");
        fourAB(soFar + "b");
    }
}
```

The following (partial) recursive **decision tree** shows each decision (diamond) made during the execution of the first branch of `fourAB`.

1. Starting with the empty string, add an "a".
1. From the string "a", add another "a".
1. From the string "aa", add another "a".
1. From the string "aaa", add another "a".
1. Since "aaaa" is length 4, print "aaaa".
1. Return back to "aaa", add a "b".
1. Since "aaab" is length 4, print "aaab".
1. ...

{::comment}
digraph{
    ranksep=0.5
    nodesep=0.75
    node[shape=none, margin=0, fontname=Roboto]
    {
        node[shape=diamond]
        ""
        a
        aa
        ab
        aaa
        aab
        b
    }

    "":w -> a:n
    a:w -> aa:n
    a:e -> ab:n
    aa:w -> aaa:n
    aa:e -> aab:n
    aaa:w -> aaaa:n
    aaa:e -> aaab:n
    "":e -> b:n
}
{:/comment}

<svg width="auto" viewBox="0.00 0.00 332.00 332.00">
<g id="graph0" class="graph" transform="scale(1 1) rotate(0) translate(4 328)">
<polygon fill="#ffffff" stroke="transparent" points="-4,4 -4,-328 328,-328 328,4 -4,4"/>
<g id="node1" class="node">
<polygon fill="none" stroke="#000000" points="243,-324 216,-306 243,-288 270,-306 243,-324"/>
</g>
<!-- a -->
<g id="node2" class="node">
<polygon fill="none" stroke="#000000" points="189,-252 162,-234 189,-216 216,-234 189,-252"/>
<text text-anchor="middle" x="189" y="-229.8" font-family="Roboto" font-size="14.00" fill="#000000">a</text>
</g>
<!-- &#45;&gt;a -->
<g id="edge1" class="edge">
<path fill="none" stroke="#000000" d="M216,-306C192.5213,-306 189.4584,-285.2001 189.0596,-262.0243"/>
<polygon fill="#000000" stroke="#000000" points="192.5595,-261.979 189,-252 185.5596,-262.0207 192.5595,-261.979"/>
</g>
<!-- b -->
<g id="node7" class="node">
<polygon fill="none" stroke="#000000" points="297,-252 270,-234 297,-216 324,-234 297,-252"/>
<text text-anchor="middle" x="297" y="-229.8" font-family="Roboto" font-size="14.00" fill="#000000">b</text>
</g>
<!-- &#45;&gt;b -->
<g id="edge8" class="edge">
<path fill="none" stroke="#000000" d="M270,-306C293.4787,-306 296.5416,-285.2001 296.9404,-262.0243"/>
<polygon fill="#000000" stroke="#000000" points="300.4404,-262.0207 297,-252 293.4405,-261.979 300.4404,-262.0207"/>
</g>
<!-- aa -->
<g id="node3" class="node">
<polygon fill="none" stroke="#000000" points="135,-180 108,-162 135,-144 162,-162 135,-180"/>
<text text-anchor="middle" x="135" y="-157.8" font-family="Roboto" font-size="14.00" fill="#000000">aa</text>
</g>
<!-- a&#45;&gt;aa -->
<g id="edge2" class="edge">
<path fill="none" stroke="#000000" d="M162,-234C138.5213,-234 135.4584,-213.2001 135.0596,-190.0243"/>
<polygon fill="#000000" stroke="#000000" points="138.5595,-189.979 135,-180 131.5596,-190.0207 138.5595,-189.979"/>
</g>
<!-- ab -->
<g id="node4" class="node">
<polygon fill="none" stroke="#000000" points="243,-180 216,-162 243,-144 270,-162 243,-180"/>
<text text-anchor="middle" x="243" y="-157.8" font-family="Roboto" font-size="14.00" fill="#000000">ab</text>
</g>
<!-- a&#45;&gt;ab -->
<g id="edge3" class="edge">
<path fill="none" stroke="#000000" d="M216,-234C239.4787,-234 242.5416,-213.2001 242.9404,-190.0243"/>
<polygon fill="#000000" stroke="#000000" points="246.4404,-190.0207 243,-180 239.4405,-189.979 246.4404,-190.0207"/>
</g>
<!-- aaa -->
<g id="node5" class="node">
<polygon fill="none" stroke="#000000" points="81,-108 54,-90 81,-72 108,-90 81,-108"/>
<text text-anchor="middle" x="81" y="-85.8" font-family="Roboto" font-size="14.00" fill="#000000">aaa</text>
</g>
<!-- aa&#45;&gt;aaa -->
<g id="edge4" class="edge">
<path fill="none" stroke="#000000" d="M108,-162C84.5213,-162 81.4584,-141.2001 81.0596,-118.0243"/>
<polygon fill="#000000" stroke="#000000" points="84.5595,-117.979 81,-108 77.5596,-118.0207 84.5595,-117.979"/>
</g>
<!-- aab -->
<g id="node6" class="node">
<polygon fill="none" stroke="#000000" points="189,-108 162,-90 189,-72 216,-90 189,-108"/>
<text text-anchor="middle" x="189" y="-85.8" font-family="Roboto" font-size="14.00" fill="#000000">aab</text>
</g>
<!-- aa&#45;&gt;aab -->
<g id="edge5" class="edge">
<path fill="none" stroke="#000000" d="M162,-162C185.4787,-162 188.5416,-141.2001 188.9404,-118.0243"/>
<polygon fill="#000000" stroke="#000000" points="192.4404,-118.0207 189,-108 185.4405,-117.979 192.4404,-118.0207"/>
</g>
<!-- aaaa -->
<g id="node8" class="node">
<text text-anchor="middle" x="27" y="-13.8" font-family="Roboto" font-size="14.00" fill="#000000">aaaa</text>
</g>
<!-- aaa&#45;&gt;aaaa -->
<g id="edge6" class="edge">
<path fill="none" stroke="#000000" d="M54,-90C30.5213,-90 27.4584,-69.2001 27.0596,-46.0243"/>
<polygon fill="#000000" stroke="#000000" points="30.5595,-45.979 27,-36 23.5596,-46.0207 30.5595,-45.979"/>
</g>
<!-- aaab -->
<g id="node9" class="node">
<text text-anchor="middle" x="135" y="-13.8" font-family="Roboto" font-size="14.00" fill="#000000">aaab</text>
</g>
<!-- aaa&#45;&gt;aaab -->
<g id="edge7" class="edge">
<path fill="none" stroke="#000000" d="M108,-90C131.4787,-90 134.5416,-69.2001 134.9404,-46.0243"/>
<polygon fill="#000000" stroke="#000000" points="138.4404,-46.0207 135,-36 131.4405,-45.979 138.4404,-46.0207"/>
</g>
</g>
</svg>
