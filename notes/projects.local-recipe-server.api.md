---
id: 7wwsf6v4iuzqkcmyb5epker
title: API
desc: ''
updated: 1647186640172
created: 1645898468761
---
This section defines how the client will interact with what resources in our application.  Since we offer some complex features (on the Create Recipe side), this will be more than just a simple CRUD REST API.

## Create Recipe Endpoints

* **POST** `/recipes` - Initial recipe creation endpoint, this will initiate the text recognition and parsing processes.
    * **Parameters:** 
        * `images` - An array of image files representing a single recipe
    * **Returns:**
        * `recipe_json` - a JSON representation of the parsed recipe

* **POST** `/recipes/confirm` - User confirmation/correction of parsed recipe text and organization
    * **Parameters:**
        * `recipe_json` - JSON representation of user confirmed/corrected recipe
    * **Returns:**
        * `recipe_id` - The ID identifying the recipe record created in the DB. This can also be used in a redirect to the detail view of the created recipe.

---

## Read Recipe Endpoints

* **GET** `/recipes` - A list endpoint for viewing existing recipe records
    * **Parameters:**
        * `ingredients` - (Optional) filters recipes returned by relationship to the ingredient(s).
    * **Returns:**
        * `recipes` - A paginated list of recipes.
* **GET** `/recipes/:id` - A detail endpoint for viewing an individual recipe.
    * **Parameters:** - `None`
    * **Returns:**
        * `recipe` - A single recipe record, including ingredients and steps.

* **GET** `/ingredients` - A list endpoint for ingredient records
    * **Parameters:** - `None`
    * **Returns:**
        * `ingredients` - An unpaginated list of ingredients

* **GET** `/recipes/:id/ingredients` - A list endpoint for ingredients related to a single recipe.
    * **Parameters:** - `None`
    * **Returns:**
        * `ingredients` - A list of ingredients for a specific recipe

* **GET** `/recipes/:id/steps` - A list endpoint for steps related to a single recipe.
    * **Parameters:** - `None`
    * **Returns:**
        * `steps` - A list of steps to execute the recipe