---
title: Logic
layout: default
nav_order: "55"
published: true
---

## Work In Progress

## Requirements

Agent's logic must be represented in a way that is:

- Easy to read and edit by people
- Easy to read and edit by the agent
- Allows pattern matching to be done on the code flow
- Allows interpretable execution

Let's go over each requirement separately

### Easy to read and edit by people

Usually program logic is represented using programming languages, like Python, Javascript or C++.
So this sound like a perfect solution for this requirement. Python was chosen as the language for the agent's logic.

### Easy to read and edit by the agent

The agent is expected to be able to edit the code written in Python, even though at the moment pattern matching is not advanced enough.

### Allows pattern matching to be done on the code flow

And here are where the problems begin.
We want the agent to be able to think about it's actions just like it thinks about the incoming data.
Process of thinking is based on conceptual representations, the power of this process lies in abstractions.
In order to be able to think abstractly about the code we need to know the code flow - what is going to be executed and in which case. The code does not provide this explicitly because the next line of code to be executed is often not the one directly bellow the current line. This information can be extracted from the code though and it needs to be done before we want to do pattern matching on the code flow.  

### Allows interpretable execution

The perfect data structure for this is a Control Flow Graph (CFG).
It shows necessary information for pattern matching, it can be interpreted by following the flow of the graph.
But it's not easy to read or edit by people, so we will need to convert the Python code into CFG.

### Implementation

Described CFG converter and interpreter are implemented in the library called `agci` (Agent Code Interpreter).



---

The simplest way to add it would be branching, but there are more powerful abstractions over it. Imagine the agent knows how to adds two numbers. It takes both of them and returns their sum. But what if we asked it to add the number of files in the directory A and directory B. Those are also numbers, even though not explicit, the agent needs to evaluate them first and then add. We could have a branch that checks if the first number is not a literal number, then check if it's a number of files and then a million other checks of what it could be, but there is a better way. We just need to convert the input to the number, whatever the input is. Each abstract concept can define it's way of converting to a number. In this case a concept of "a number of files in a directory" will have an associated convert.