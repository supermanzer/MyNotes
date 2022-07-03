---
id: SbTEpvK2XGGDODacWdxot
title: Recipe Ingredient
desc: ''
updated: 1643496538878
created: 1643496243727
---

This model is the associative entity that relates ingredients to recipes. It stores data that are unique to this relationship, i.e. quantity and unit.

|Field|Type|Description|
|----|----|----|
|**ID**| BigInt| Primary Key
|**RecipeID**|BigInt| FK relating to Recipe|
|**IngredientID**|BigInt| FK relating to Ingredient|
|**Quantity**|Int| Quantity of the ingredient in the recipe|
|**Unit**|Text| The unit the quantity represents (e.g. cup, pinc, teaspoon)|
