---
title: World Model
layout: default
nav_order: "50"
has_children: true
---

# World Model

## Entity
To effectively process incoming events, generate novel knowledge, and reason about the environment, an agent requires a robust internal representation of the world. Within the present framework, the agent's world model encompasses entities, each resembling a class instance from Object-Oriented Programming (OOP). Each entity comprises a concept and an assortment of fields. The concept defines which fields it can have and their default value if it's predent. For instance, a conceptualization of a human might incorporate fields such as "name", "age", and "gender". Entities don't have to provide values for all fields.  