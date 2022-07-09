This interface allows the user to upload photos of recipes. The saving of the file to the application server file system will trigger the parsing service to extract text from the images and assign text to data models.

Depending on the amount of time necessary to perform this action, the following step may occur within the same request/response loop or require a more asynchronous approach.  

Once the parsing service returns a representation of the extracted & assigned text, this should be presented to the user in a format that asupports modification of the text and data objects assigned as well as choose whether to save the recipe or cancel. Given the les-than-perfect images likely to be gathered, it seems like assuming occasional incorrect parsing of the images into text and/or incorrect data object assignment is a safe assumption to make.

Therefore this interface will consist of two views.

## Upload File(s)
This view needs to support the loading of multiple image files and making a POST request that transmits them to the server.

## Edit/Save Results
This view will accept the structured text output from the parsing service and present the the user the ingredients, amounts, units, and steps as editable text.  At this point only the Recipe and Image records have been saved. If the use decides to cancel at this point, those records along with the associated files will be removed.  This allows the user to abandon the attempt if they decide they want to try better photos or the work of editing the resulting parsed text does not merit the saving of the recipe.

If the user selects the save option, this will create/assign the Ingredient, Step, and associative records to complete the recipe.  It will use the current representation of the text and structure in the user interface to ensure any changes made by the user in this view is reflected in the saved records.