# Machine Learning Tutorial 

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/danforthcenter/plantcv-tutorial-machine-learning/HEAD?labpath=index.ipynb)

The naive Bayes multiclass approach is an extension of the naive Bayes approach. It can be trained to output binary images given an input color image. Unlike the naive Bayes method, the naive Bayes multiclass approach can be trained to classify two or more classes, defined by the user. Additionally, the naive Bayes multiclass method is trained using colors sparsely sampled from images rather than the need to label all pixels in a given image.

To train the classifier, we need to build a table of red, green, and blue color values for pixels sampled evenly from each class. The idea here is to collect a relevant sample of pixel color data for each class. The size of the sample needed to build robust probability density functions for each class will depend on a number of factors, including the variability in class colors and imaging quality/reproducibility. To collect pixel color data we currently use the Pixel Inspection Tool in ImageJ. Each column in the tab-delimited table is a feature class (in this example, plant, pustule, chlorosis, or background) and each cell is a comma-separated red, green, and blue triplet for a pixel.

Once a satisfactory sample of pixels is collected, save the table as a tab-delimited text file. Use plantcv-train.py to use the pixel samples to output probability density functions (PDFs) for each class.

plantcv-train.py naive_bayes_multiclass --file pixel_samples.txt --outfile naive_bayes_pdfs.txt --plots

The output file from plantcv-train.py will contain one row for each color channel (hue, saturation, and value) for each class. The first and second column are the class and channel label, respectively. The remaining 256 columns contain the p-value from the PDFs for each intensity value observable in an 8-bit image (0-255).

Once we have the plantcv-train.py output file, we can classify pixels in a color image in PlantCV. In the example image for this tutorial we have already collected pixels and created the probability density functions for each class.

## Tutorial tags/keywords

Naive Bayes, Machine Learning, disease quantification, flatbed scanner, leaf 

## Citations

Abbasi A, Fahlgren N. 2016. Naive Bayes pixel-level plant segmentation. In: 2016 IEEE Western New York Image and Signal Processing Workshop (WNYISPW). 1–4. DOI: 10.1109/WNYIPW.2016.7904790.
