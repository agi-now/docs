---
title: Concept
layout: default
parent: Glossary
---
In order to simplify processing of incoming information people put labels on everything. A group of particles we labeled as `apple` will cause this label to activate in our heads when light bounces of it into eyes. Concept is just another word for "label".
Concepts in our system have unique identifiers (CID).
## Compound Concepts

Unlike simple (atomic) concepts like `apple`, compound concepts are always abstract, they can become concrete when we fill all their fields.
For example a concept a red apple:
```python
EntityWithDescription {
	entity=Apple,
	description=ColorRed
}
```
This concept is abstract, like `animal`, but unlike `animal` the idea that this concept has can be extended by supplying fields, in this case `entity` and `description`.
Without compound concepts we would have to have atomic concepts like `RedApple`, `BlackCar`, `YellowCar`, etc in the knowledge base, but with compound concepts it's enough to create `EntityWithDescription`, `Apple`, `Car` and the colors to be able to express all the combinations of entities and descriptions.