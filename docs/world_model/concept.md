---
title: Concept
layout: default
parent: World Model
nav_order: "10"
---
# Concept

## What is a Concept

Assigning concepts or labels  plays a pivotal role in simplifying the comprehension of incoming data. When an individual perceives a real-world object, such as an apple, photons striking the retina initiate a cognitive process that assigns a categorical label, "apple", to that object. This process essentially hinges on the assignment of a concept, which can be thought of as a mental label or tag.

Concepts within our system are systematically cataloged and identified through unique Concept Identifiers (CIDs).

## Concept Identifiers

CID is a unique identifier to the concept. While it is advisable to assign human-readable names to concepts for practicality, it's essential to acknowledge that CIDs themselves lack inherent semantic meaning. This characteristic affords us the flexibility to allocate arbitrary IDs to concepts without disrupting system integrity.

CIDs for atomic concepts are constrained to alphanumeric characters.

For compound concepts (section about them can be found below), the CID is defined as follows:

```
Name{field1=CID1,field2=CID2, ...}
```

The fields are sorted alphabetically, with the "Name" component adhering to the naming conventions applied to atomic CIDs.
Compound concepts must list all their fields. If field is not populated, use default concept for this field.
If a field is used to add hierarchical relation to the concept, use `&=` instead of an equal sign.

Examples of CIDs:
- `Apple`
- `Color`
- `EntityWithDescription{description=EntityDescription,entity&=Entity}`
- `EntityWithDescription{description=ColorRed,entity&=Apple}`
- `EntityWithDescription{description=RedColor,entity&=EntityWithDescription{description=BigSize,entity&=Apple}}`

## Hierarchical Relations of Concepts
In our conceptual framework, both atomic and compound concepts exhibit hierarchical relationships. Atomic concepts often form the foundational elements of these hierarchies, while compound concepts, with their combination of fields, enable the expression of more intricate relationships. 
For example concept `Lion` is a child of `Animal` and `Animal` is a child of `Concept`, which also makes `Lion` a child of `Concept` (the relation is transitive).
Compound concepts can have regular parents and parents defined via fields.
Hierarchical relations are stored in Conceptual Knowledge Base.

## Compound Concepts

Diverging from atomic concepts, which are relatively straightforward labels like `Apple`, compound concepts exhibit a more abstract nature. A compound concept only materializes into a concrete concept when all its constituent fields are populated with specific data. To illustrate, let's examine the concept of a red apple:

```python
EntityWithDescription {
    entity=Apple,
    description=RedColor
}
```

*For simplicity we don't follow CID convention in this examples*
This compound concept, much like the  `Animal` concept, is abstract. However, unlike `Animal`, the meaning of this concept is shaped by providing field values, in this case, `entity` and `description`. Without the compound concepts, our knowledge base would include numerous atomic concepts like `RedApple`, `BlackCar`, `YellowCar`, and so forth. By leveraging compound concepts we can describe arbitrary combinations of concepts.

### Defaults for fields
By default compound concepts must define default subconcepts for all fields, for example:
```python
EntityWithDescription {
    entity=Entity,
    description=EntityDescription
}
```
Usually defaults will be abstract atomic concepts.

### Recursion
Compound concepts can have other compound concepts as their fields:
```python
EntityWithDescription {
    entity=EntityWithDescription {
        entity=Apple,
        description=BigSize
    },
    description=RedColor
}
```
This concept describes an idea of a big red apple.
Compound concepts can have arbitrary number of fields.

### Compound Concepts are not parents
It is possible to use compound concepts to define hierarchical relations, for example `Animal{type=Lion}`, but hierarchical relations must not be defined this way, use knowledge graph for this. 

### Transitive Fields
Fields of compound objects can be transitive,  which mean that they transit hierarchical information. 
For example the concept 
```python
EntityWithDescription {
	entity=Apple,
	description=BigSize
}
```
is an extended concept of `Apple`, which means that everything that applies to `Apple`, also applies to the compound concept.
But this is only true for the field `entity`, field `description` does not have this property in this compound concept. It wouldn't make sense to make the `description` field transitive because `EntityWithDescription` is not a `Description`, it's an extension of `Entity`.
