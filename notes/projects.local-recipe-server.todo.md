---
id: ykosvctv284qjvdsp13tbwj
title: Todo
desc: ''
updated: 1648399622422
created: 1647183828137
---
A simple list of next steps in various parts of the application implementation

## Front-End
- [x] Add `ingredient` auto-complete field with `multiple, clearable, chips`
- [x] Add `search` sync parameter to Recipes data table and trigger recipe list API requests on change.

## API
- [x] Convert Ingredient creation in the `confirm` action to `get_or_create` to avoid duplicating ingrdient records.
- [x] Buid out `RecipeIngredient` Serializer.
- [x] Add serialization of related `RecipeIngredient` records to the `Recipe` serializer and return complete recipe.
- [x] Add `ingredients` search parameter to `Recipe` endpoint
- [x] Modify `get_queryset` method for `Recipe` endpoint to accept ingredients as a filter
- [x] Add an Ingredient Endpoint

## Data Model
- [x] Add a unique `name` constraint to the Ingredient data model


## Services
- [ ] Implement text recognition
