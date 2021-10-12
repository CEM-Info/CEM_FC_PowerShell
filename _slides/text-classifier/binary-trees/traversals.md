---
title: Traversals
nav_order: 2
---

Since each node in a binary tree has two children, recursive traversal is the best way to explore the values in a tree. Similar to recursive linked list traversal, we'll want to introduce a public/private pair to maintain a reference to the `root` of the current subtree. There are three ways of traversing a binary tree depending on when the current node is processed in comparison to its children. Consider the following `IntTree`.

<svg width="auto" viewBox="0.00 0.00 264.39 276.16">
<g id="graph0" class="graph" transform="scale(1 1) rotate(0) translate(4 272.1607)">
<polygon fill="#ffffff" stroke="transparent" points="-4,4 -4,-272.1607 260.3869,-272.1607 260.3869,4 -4,4"/>
<!-- overallRoot -->
<g id="node1" class="node">
<text text-anchor="middle" x="129.6935" y="-245.9607" font-family="Roboto" font-size="14.00" fill="#000000">overallRoot</text>
</g>
<!-- 17 -->
<g id="node2" class="node">
<ellipse fill="none" stroke="#000000" cx="129.6935" cy="-175.4673" rx="20.8887" ry="20.8887"/>
<text text-anchor="middle" x="129.6935" y="-171.2673" font-family="Roboto" font-size="14.00" fill="#000000">17</text>
</g>
<!-- overallRoot&#45;&gt;17 -->
<g id="edge1" class="edge">
<path fill="none" stroke="#000000" d="M129.6935,-232.0795C129.6935,-224.4058 129.6935,-215.2377 129.6935,-206.5375"/>
<polygon fill="#000000" stroke="#000000" points="133.1936,-206.289 129.6935,-196.2891 126.1936,-206.2891 133.1936,-206.289"/>
</g>
<!-- cx_17 -->
<!-- 17&#45;&gt;cx_17 -->
<!-- 41 -->
<g id="node6" class="node">
<ellipse fill="none" stroke="#000000" cx="72.6935" cy="-98.0804" rx="20.8887" ry="20.8887"/>
<text text-anchor="middle" x="72.6935" y="-93.8804" font-family="Roboto" font-size="14.00" fill="#000000">41</text>
</g>
<!-- 17&#45;&gt;41 -->
<g id="edge2" class="edge">
<path fill="none" stroke="#000000" d="M117.3253,-158.6755C109.6318,-148.2303 99.5999,-134.6102 90.9961,-122.9292"/>
<polygon fill="#000000" stroke="#000000" points="93.7861,-120.8154 85.0375,-114.8394 88.1499,-124.9668 93.7861,-120.8154"/>
</g>
<!-- 9 -->
<g id="node7" class="node">
<ellipse fill="none" stroke="#000000" cx="183.6935" cy="-98.0804" rx="18" ry="18"/>
<text text-anchor="middle" x="183.6935" y="-93.8804" font-family="Roboto" font-size="14.00" fill="#000000">9</text>
</g>
<!-- 17&#45;&gt;9 -->
<g id="edge3" class="edge">
<path fill="none" stroke="#000000" d="M141.6778,-158.2926C149.2545,-147.4345 159.1443,-133.2615 167.4254,-121.3939"/>
<polygon fill="#000000" stroke="#000000" points="170.5273,-123.0649 173.3795,-112.8612 164.7867,-119.0592 170.5273,-123.0649"/>
</g>
<!-- cx_17&#45;&gt;9 -->
<!-- ocx_9 -->
<!-- 40 -->
<g id="node11" class="node">
<ellipse fill="none" stroke="#000000" cx="235.6935" cy="-20.6935" rx="20.8887" ry="20.8887"/>
<text text-anchor="middle" x="235.6935" y="-16.4935" font-family="Roboto" font-size="14.00" fill="#000000">40</text>
</g>
<!-- ocx_9&#45;&gt;40 -->
<!-- ocx_41 -->
<!-- 25 -->
<!-- ocx_41&#45;&gt;25 -->
<!-- 41&#45;&gt;cx_17 -->
<!-- 41&#45;&gt;ocx_41 -->
<!-- 29 -->
<g id="node8" class="node">
<ellipse fill="none" stroke="#000000" cx="20.6935" cy="-20.6935" rx="20.8887" ry="20.8887"/>
<text text-anchor="middle" x="20.6935" y="-16.4935" font-family="Roboto" font-size="14.00" fill="#000000">29</text>
</g>
<!-- 41&#45;&gt;29 -->
<g id="edge4" class="edge">
<path fill="none" stroke="#000000" d="M60.8938,-80.5201C54.1315,-70.4563 45.5205,-57.6413 38.0042,-46.4555"/>
<polygon fill="#000000" stroke="#000000" points="40.7497,-44.2658 32.2672,-37.9177 34.9395,-48.17 40.7497,-44.2658"/>
</g>
<!-- 41&#45;&gt;25 -->
<!-- 9&#45;&gt;ocx_9 -->
<!-- 81 -->
<g id="node10" class="node">
<ellipse fill="none" stroke="#000000" cx="157.6935" cy="-20.6935" rx="20.8887" ry="20.8887"/>
<text text-anchor="middle" x="157.6935" y="-16.4935" font-family="Roboto" font-size="14.00" fill="#000000">81</text>
</g>
<!-- 9&#45;&gt;81 -->
<g id="edge6" class="edge">
<path fill="none" stroke="#000000" d="M177.9232,-80.9057C174.8848,-71.8621 171.0738,-60.5191 167.5813,-50.1237"/>
<polygon fill="#000000" stroke="#000000" points="170.8685,-48.918 164.3659,-40.5534 164.233,-51.1474 170.8685,-48.918"/>
</g>
<!-- 9&#45;&gt;40 -->
<g id="edge7" class="edge">
<path fill="none" stroke="#000000" d="M193.967,-82.7912C200.9217,-72.4411 210.2811,-58.5124 218.3733,-46.4695"/>
<polygon fill="#000000" stroke="#000000" points="221.3169,-48.3641 223.9892,-38.1118 215.5068,-44.46 221.3169,-48.3641"/>
</g>
<!-- 29&#45;&gt;ocx_41 -->
<!-- 81&#45;&gt;ocx_9 -->
</g>
</svg>

Pre-order traversal
: Process the current `root` node then process the `left` and `right` children.
: ```java
  public void print() {
      print(overallRoot);
  }

  private void print(IntTreeNode root) {
      if (root != null) {
          System.out.print(root.data + " ");
          print(root.left);
          print(root.right);
      }
  }
  ```
: ```
  17 41 29 9 81 40
  ```

In-order traversal
: Process the `left` child, then process the current `root` node, and then process the `right` child.
: ```java
  public void print() {
      print(overallRoot);
  }

  private void print(IntTreeNode root) {
      if (root != null) {
          print(root.left);
          System.out.print(root.data + " ");
          print(root.right);
      }
  }
  ```
: ```
  29 41 17 81 9 40
  ```

Post-order traversal
: Process the `left` and `right` children and then process the current `root` node.
: ```java
  public void print() {
      print(overallRoot);
  }

  private void print(IntTreeNode root) {
      if (root != null) {
          print(root.left);
          print(root.right);
          System.out.print(root.data + " ");
      }
  }
  ```
: ```
  29 41 81 40 9 17
  ```
