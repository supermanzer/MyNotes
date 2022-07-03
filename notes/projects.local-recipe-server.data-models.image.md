---
id: tzRIbPhcnUFIhERjOHFwC
title: Image
desc: ''
updated: 1643498017675
created: 1643497716608
---

Since it may take more than one image to contain all the text in a readable format, it is nessary to allow more than one image to be associated with a recipe.

|Field|Type|Description|
|----|----|----|
|**ID**| BigInt| Primary Key|
|**RecipeID**| BigInt | FK relating to Recipe|
|**ImageFile**| FileField| Link to image file in filesystem|
