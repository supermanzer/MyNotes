---
id: zLflC0uVAy1lZhlPHM70Y
title: View Recipe
desc: ''
updated: 1643503171581
created: 1643502014246
---

This interface is the pay off for all the hard work of parsing and checking text representations of recipes. A simple and easily readable representation of a recipe with no ads or unrelated content displayed.

It allows for searching recipes by name or ingredient, as well as filtering by ingredients.  The use cases supported are both finding a particular recipe the user is interested in as well as allowing the user to filter saved recipes by the ingredients they have/wish to consume.

The basic views of this interface are the list of recipes and the detail view of a specific recipe.

## List View
A simple list of recipe records saved by the user.  This view will support a search bar that searches against the recipe name (possible full text search?).  Filtering by ingredients will also be supported with an autocomplete field allowing the user to look up saved ingredients.

## Detail View
This view will present the elements of the recipe (excluding the image records).  The styling will favor clear readability over decoration. Initial design is to attempt to present all ingredients in a single view, while displaying each step individually.  Simple controls to increment steps forward and back will facilitate navigation from step to step when cooking and interactions with either a touchscreen or a mouse/keyboard must be kept to a minimum.
