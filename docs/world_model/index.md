---
title: World Model
layout: default
nav_order: "50"
has_children: true
---

# World Model
To effectively process incoming events, generate novel knowledge, and reason about the environment, an agent requires a robust internal representation of the world. This section describes data structures used to describe the internal representation of the world and motivation for those structures.

## Abstract Representation
World model represent well-bounded representations of a physical world, which is often hard to bound. For example a real-world collection of particles people would call "a puddle" does not have clear boundaries - water is constantly evaporating and condensing, it goes through the ground and mixes with it. But in people's head it's a single entity that they can reason about. The same approach was used in this framework - entities resemble a class instance from Object-Oriented Programming (OOP). 


