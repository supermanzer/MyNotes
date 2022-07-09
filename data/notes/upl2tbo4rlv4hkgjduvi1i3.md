Because our recipes consist of multiple data models but we want to to present them as whole documents we need to coordinate the serialization.

## Recipe-Ingredient Serializer
When we are serializing the ingredients for a recipe, most of what we want is actually in the relationship entity.  This serializer should return the following fields as a JSON object.
* `name` - [[projects.local-recipe-server.data-models.ingredient]] data model
* `quantity` - [[projects.local-recipe-server.data-models.recipe-ingredient]] data model
* `unit` - [[projects.local-recipe-server.data-models.recipe-ingredient]] data model

## Recipe Serializer
This serializer returns the data object that the List/Detail components of our API will interact with.  It will return the following fields.
* `title` - [[projects.local-recipe-server.data-models.recipe]] data model
* `steps` - [[projects.local-recipe-server.data-models.recipe]] data model
* `recipe-ingredients` - An array of serialized [[projects.local-recipe-server.data-models.recipe-ingredient]] data models
