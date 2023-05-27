## Models
The basic data models defined to support this application are shown below:

### Ingredient
![[projects.local-recipe-server.data-models.ingredient]]

### Recipe Ingredient
![[projects.local-recipe-server.data-models.recipe-ingredient]]

### Step
![[projects.local-recipe-server.data-models.step]]

### Image
![[projects.local-recipe-server.data-models.image]]

### Recipe
![[projects.local-recipe-server.data-models.recipe]]

## Thoughts
### Steps
I was/am not certain about breaking out steps into their own model or using a JSON field to store an array of parsed steps. However, I have some ideas for features I want to enable in the UI and I think that separate step data objects will facilitate this.  Perhaps that could have been implemented in the business logic layer or event in the presentation layer.  I may refactor this after some work on the user-interface.