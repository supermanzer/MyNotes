
* **Service:** [[projects.local-recipe-server.services.text-parsing]]
* **Core Tech:** [PyTesseract](https://pypi.org/project/pytesseract/)

Accurate Optical Character Recognition (OCR) is the core of the Text Parsing service.

One of the key challenges in text recognition and parsing with recipes is the use of columnar text layouts.

Another significant challenge is the translation of ingredient lists.  The main challenge here so far is proper recognition of fractions, although list format icons can add some extra difficulty.

---

## Columnar Text
An initial attempt to to handle proper word order when extracting text from multiple columns has been attempted following [this guide](https://nanonets.com/blog/ocr-with-tesseract/).  Results have been less than ideal but introducing some imperitive coding logic may prove useful as well as refining my image pre-processing steps to provide maximum contrast while maintaining clarity.

### Next Steps
* Conduct more research into the [Open CV](https://pypi.org/project/opencv-python/) functions for detecting contours in the image for better splitting of by columns.  This should improve segmentation for text processing.

---

## Ingredient Lists
One of the most difficult to interpret characters present in ingredient lists are fractions.  Often these are translated to `Y` or `%` characters.  Numbers (depending on the font used) can also provide a significant difficulty.

### Next Steps
* Review [this tutorial](https://pyimagesearch.com/2021/08/30/detecting-and-ocring-digits-with-tesseract-and-python/) about configuring PyTesseract for digit recognition.
* Review [this SO Question](https://stackoverflow.com/questions/55994807/why-does-pytesseract-fail-to-recognise-digits-from-image-with-darker-background) regarding improved image preprocessing.
* Review [this Github Issue](https://github.com/tesseract-ocr/tesseract/issues/2274) regarding applying new training data to improve PyTesseract model for fraction recognition.