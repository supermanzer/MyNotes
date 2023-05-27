The purpose of this function will be to consume a corpus of text and, using imperitive rules, correctly assign text to the corresponding data model, thereby constructing a recipe.

## Rules
The application of any sort of machine learning would require such a large set of data on which to train, as well as text recognition algorithms I am not familiar with, that I think it would be easier to simply write these rules myself.  Using line breaks, bullet or numbered formatting, and the presence/absence of numbers in the text will be used to classify distinct text elemets in the corpus this function accepts as it's sole parameter.

## Output
While this function will break out the text provided into the representations matching the data models present in this application, it does nto create records in the database.  These data model representations will be returned in JSON string formatting.  This will alow the editing of the text by users without excessive database write operations.
