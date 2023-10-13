---
title: Concept
layout: default
parent: Glossary
---
## What is a Concept

Assigning concepts or labels  plays a pivotal role in simplifying the comprehension of incoming data. When an individual perceives a real-world object, such as an apple, photons striking the retina initiate a cognitive process that assigns a categorical label, "apple", to that object. This process essentially hinges on the assignment of a concept, which can be thought of as a mental label or tag.

Concepts within our system are systematically cataloged and identified through unique Concept Identifiers (CIDs).

## Compound Concepts

Diverging from atomic concepts, which are relatively straightforward labels like `Apple`, compound concepts exhibit a more abstract nature. A compound concept only materializes into a concrete concept when all its constituent fields are populated with specific data. To illustrate, let's examine the concept of a red apple:

```python
EntityWithDescription {
    entity=Apple,
    description=RedColor
}
```

This compound concept, much like the  `Animal` concept, resides in the realm of abstraction. However, unlike `Animal`, the meaning of this concept is shaped by providing field values, in this case, `entity` and `description`. Without the framework of compound concepts, our knowledge base would necessitate the inclusion of numerous atomic concepts like `RedApple`, `BlackCar`, `YellowCar`, and so forth. By leveraging compound concepts, we can efficiently express diverse entity-description combinations through the creation of `EntityWithDescription`, `Apple`, `Car`, and individual colors.

## Concept Identifiers

CID is a unique identifier to the concept. While it is advisable to assign human-readable names to concepts for practicality, it's essential to acknowledge that CIDs themselves lack inherent semantic meaning. This characteristic affords us the flexibility to allocate arbitrary IDs to concepts without disrupting system integrity.

In the context of atomic concepts, CIDs are constrained to alphanumeric characters.

For compound concepts, the CID is defined as follows:

```
Name{field1=CID1,field2=CID2, ...}
```

The fields are sorted alphabetically, with the "Name" component adhering to the naming conventions applied to atomic CIDs.
