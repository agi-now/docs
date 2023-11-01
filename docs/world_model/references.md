---
title: References
layout: default
nav_order: "90"
---

"where is Merry" DefiniteEntityReferenceFromProperName
"where is the cat" DefiniteEntityReference
"where is it" DefiniteSingularEntityReferenceFromPronoun
"where are they" DefinitePluralEntityReferenceFromPronoun
"I need an animal" IndefiniteEntityReference
"it is an animal" ClassReference
"bring all animals" DefiniteEntityGroupReference

Imagine we parsed a sentence "find it", where "it" stand for the cat.
Agent does not know how to find "it", but it knows how to look for cats.
So we need an extra step of resolving the reference.
For this we create this structure:

ActionOnEntityReference {
    action=FindActionInstance,
    reference=DefiniteEntityReference,
}

Which will trigger a function which take the reference and resolve it to a cat.
Then this function will construct the regular ActionOnEntity.

ActionOnEntity {
    action=FindActionInstance,
    entity=Cat,
}
