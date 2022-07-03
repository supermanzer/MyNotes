---
id: soHYpt885ozjQWUY3suoU
title: Step
desc: ''
updated: 1643504829242
created: 1643496842476
---
This model represents an individual step or set of instrutions for executing the recipe.  

|Field|Type|Description|
|----|----|----|
|**ID**| BigInt| Primary Key|
|**RecipeID**| BigInt| FK relating to Recipe|
|**Order**| Int | Numeric represenation of the order of the step as it relates to the Recipe|
|**Step**|Text| Recipe directions|
