This model represents an individual step or set of instrutions for executing the recipe.  

|Field|Type|Description|
|----|----|----|
|**ID**| BigInt| Primary Key|
|**RecipeID**| BigInt| FK relating to Recipe|
|**Order**| Int | Numeric represenation of the order of the step as it relates to the Recipe|
|**Step**|Text| Recipe directions|
