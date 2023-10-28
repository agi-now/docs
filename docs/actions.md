---
title: Actions
layout: default
nav_order: "80"
published: false
---

The simplest way to add it would be branching, but there are more powerful abstractions over it. Imagine the agent knows how to adds two numbers. It takes both of them and returns their sum. But what if we asked it to add the number of files in the directory A and directory B. Those are also numbers, even though not explicit, the agent needs to evaluate them first and then add. We could have a branch that checks if the first number is not a literal number, then check if it's a number of files and then a million other checks of what it could be, but there is a better way. We just need to convert the input to the number, whatever the input is. Each abstract concept can define it's way of converting to a number. In this case a concept of "a number of files in a directory" will have an associated convert