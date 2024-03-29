---
title: AGI Definition
layout: default
nav_order: "25"
---

# Work In Progress

# AGI Definition

## Abstract Definition
On a high level we define AGI as a system that is capable of performing tasks in domains familiar to people with performance being close to people.
This abstract definition is centered around people for a good reason. There is no evidence that people are truly generally intelligent, we don't know if generation is binary, maybe there is a scale to it and people are just the most generally intelligent agents we are aware of.
So in order to not rely on assumption that general intelligence is binary we will set our goal to achieve the human level.

## Technical Definition
AGI is a system that has sensory and control interfaces. Just like people have eyes, ears, etc and neurons to activate muscles. Sensors produce distorted raw image of the environment that is being processed with a mechanism for extracting abstractions. The system needs to transform raw data into abstract representations because environment is often too complex to work with it's raw representation. It would be probably impossible to think of the real world in terms of photons hitting our retina, so we use abstraction to represent the collections of those photons to think about real-world collections of elementary particles. After the system has abstract representation of the world it is capable to interact with the world in an intelligent way. There is no behavior that is intelligent objectively. Surviving isn't intelligent, it's just necessary for reproduction, which was necessary for our species to find itself alive today. So we won't set any requirements on the agents behavior that it must met in order to count intelligent. Instead we will define what functionality is needed for the agent to be useful for people.

### Actions
We want to be able to ask the agent to perform tasks. In order to do this the agent needs to associate our commands with actions. And of course not only commands should trigger actions, any information might do that. So we need to link the abstract representations to actions.
In order to have links to actions the agent needs to store those actions somewhere. 
But what are actions? If we remove all the abstractions (like branching), actions are sequences of control signals to the control interfaces. Whatever people's brain does inside, in the end it only sends out signals to control the body. The brain also changes itself, but nothing stops the agent to do it also via control signals.
So the agent should be able to send out signals to the control interfaces.
Of course the agent will need to have some non-linear behavior. And simple branching will not be enough. Imagine that the agent knows how to add two numbers, but instead of regular "add 2 and 5" it was given this: "add the number of files in directory ABC and the current day of month". Behavior of the agent depends on the concepts of the input data. If it was given two images of numbers, it would behave differently, then if it was given textual representation. Simple program would strictly expect a numeric type, but intelligent agent can work with different (known in advance) representations of data.
But what if the agent was able to understand the numbers given to it in the previous example? A simple program would fail it the inputs are incorrect, but we expect an intelligent agent to try and work around this problem. In order to do this even more "non-linear" behavior is required.

*to be continued...*