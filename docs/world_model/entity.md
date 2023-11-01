---
title: Entity
layout: default
parent: World Model
nav_order: "20"
---

# Entity

## Representation

Within the present framework, the agent's world model encompasses entities, each resembling a class instance from Object-Oriented Programming (OOP). Each entity comprises a concept and an assortment of fields. The concept defines which fields it can have and their default value if it's present. For instance, a concept of a human might define fields such as "name", "age", and "gender". Entities don't have to provide values for all fields.  

Entities are represented in the following format:

```python
CID {
    field1=Entity,
    field2=Entity,
    ...
}
```

Here, "CID" stands for [Concept ID]({% link docs/world_model/concept.md %}#concept-identifiers), and "Entity" signifies another entity. 
Some entities have literals as field values, like numbers or strings:

```python
String {
    value="hello"
}
```

```python
Number {
    value=2
}
```

```python
Boolean {
    value=True
}
```

Literals can only be used with the field named `value`. All other fields must have another entity as a value.

A representation of a human within this world model could be depicted as:

```python
Human {
    name=String {
        value="John"
    },
    age=Number {
        value=29
    }
}
```

For entities with compound concepts, the representation consolidates into a singular line, as shown:

```python
EntityWithDescription{entity=Human,description=Young} {
    name=String {
        value="Sarah"
    }
}
```

Often, one can deduce the value of a particular field by analyzing other fields. For instance, one can ascertain a person's full name by combining their first and last names, or infer the birth date from their age combined with the current date. Such extrapolations are facilitated through mechanisms known as "field getters".

## Field Getters

Within the knowledge base, a concept's fields are interlinked with tasks. These tasks can compute a field's value, provided the necessary input fields are either available or can be derived.

..IMAGE GOES HERE..

The accompanying image illustrates a concept, "Human", with three fields: "first_name", "last_name", and "full_name". The "full_name" field has an associated getter that is activated when its value is sought, and both the "first_name" and "last_name" fields are populated.  

Each entity possesses a unique, affiliated concept. This is pivotal because it is imperative to distinguish between concepts, allowing for individual contemplation. Consider two identical white pawns on a chessboard. Despite both belonging to the "Pawn" concept, they are distinct entities. Thus, we attribute a unique concept to each, derived from "Pawn" (for simplicity, let's call it PawnInstance). These distinct concepts enable the formulation of specific knowledge about each pawn. Without this differentiation, knowledge would be limited to generic information about pawns.