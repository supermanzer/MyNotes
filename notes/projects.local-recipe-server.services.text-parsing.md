---
id: Wl7xkoMZgCm0faeX2LfZn
title: Text Parsing
desc: ''
updated: 1643504298860
created: 1643503444838
---
This service function consumes an array of image files or, more likely,filepaths and returns a single corpus of extracted text.  

## Tech Choices
This is the area of this project I am least familiar with and the most likely to take some further research and experimentation to get right.  Based on initial cursory investigations, the Python package [PyTesseract](https://pypi.org/project/pytesseract/) appears to be a good place to start.

## Output
This is perhaps a tricky thing to define.  While not all, some recipes include a preamble or story relating to how the recipe was arrived at or the cultural provenance.  While informative and engaging, these details are not pertinent to executing the recipe.  The intent of this application is to allow users to define those recipes they care about by saving them so it is assumed the user already knows why they should care about them.  

However, it is not the job of this service function to make those decisions.  This service exists to extract text from image files and should not be burdened by addtional business logic.  The only functionality beyond extracting text from a single image file to be included here is the appending of text from successive images to a single corpus in the case of multiple images being assocaited with a single recipe.  The recognition of line breaks, event when between successive images, will also be key as these breaks will be necessary to inform the assignment function that consumes the extracted text.
