---
title: Machine abstraction
nav_order: 0
---

We've now seen two types of abstraction: data abstraction (e.g. lists, sets, maps) and functional abstraction (e.g. domain, range, behavior). These abstractions specify a contract between the client of the abstraction and the implementer of the abstraction. For example, a client that calls a method can only expect it to work if they pass in valid arguments (preconditions) and if the implementer has written the correct code to produce the expected outputs (postconditions).

In this lesson, we'll explore an even more fundamental abstraction that underlies all of the programming in the past, present, and foreseeable future.

Machine abstraction
: A model of a computer system that specifies how the computer system works in terms of input, possible operations, and output.

Machine abstractions are all around us. All of the computer and smart-things in our daily lives are machine abstractions. Machine abstraction is the reason behind how the Java programs that we write can run on a laptop, in a datacenter, or on a chip embedded in a toy. The web browser that you're using to read this document on the internet is also a machine abstraction. The browser takes as input a program specifying the web page layout and interactive components. It then reads the program, builds the layout, and adds interactivity.

The details behind how all of this works is complicated to say the least. The web browser is a machine abstraction for the internet. The web browser is a program, and the programming language is a machine abstraction. The program is running on an operating system, which is also a machine abstraction. The operating system is sending instructions to the processor hardware, a machine abstraction. The principle of machine abstraction allows all of these components to change independently: we can update our web app independent of the web browser independent of the programming language independent of the operating system independent of the processor hardware.

Each of these layers could be a lifetime of study on its own. The concept of a **notional machine** distills the complexity of a machine abstraction down to only the parts that are relevant to us as learners. The question for this lesson is, "What parts of the Java's machine abstraction are relevant to us as programmers?"
