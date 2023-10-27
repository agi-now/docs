---
title: World Model
layout: default
nav_order: "50"
---
# World Model

In order to process incoming events, generate new knowledge and reason about the world the agent needs to be able to represent the world internally. 
In the current framework agent's world model contains entities that are represented with a data strucutre similar to a class instance from OOP. 
It has a concept and a list of fields. Concept defines possible fields, some of them might be set. For example an idea of a human might have fields like "name", "age", "gender", etc.
Generally entities are represented like this:
```python
CID {
    field1=Entity,
    field2=Entity,
    ...
}
```
Where "CID" is a concept id and "Entity" is another entity.
There are special entities that represet literal values like numbers, strings, etc:
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

Representation of a human inside the world model might look something like this:
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

If a concept of an entity is compound then it's written in one like, like this:
```python
EntityWithDescription{entity=Human,description=Young} {
    name=String {
        value="Sarah"
    }
}
```

It is usually possible to find the value of a field by having the values of other fields.
For example it is possible to find the persons full name from first and last name. 
Or we can calculate the birth date from age and current date.
This is implemented via something that is called "field getters".

## Field Getters
In the knowledge base the fields of a concept are connected to the tasks that can be called to calculate the value of a field, given that the required input fields are present or can be calculated.

..IMAGE GOES HERE..

In this image we have a concept of a "Human" and three fields - "first_name", "last_name" and "full_name". The field "full_name" has a getter that will be called if we need the value of this field and the fields "first_name" and "last_name" are set.

Each entity has a unique concept associated with it. 
This is required because we want to have a unique idea for each concept to be able to think about them separately.
Imagine two white pawns on a chess board. Even though they are both of the "Pawn" concept, they are distinct in our heads, so we need to assign each one a unique concept that is a child of "Pawn" (actually PawnInstance, but let's simply for this example). This unique concepts will allow us to create knowledge about each pawn sepearately. Without them we would be only able to represent knowledge about pawns in general.
