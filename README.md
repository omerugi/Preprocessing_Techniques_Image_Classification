# Preprocessing Techniques for Image Classification

![cat_and_dog_logo](https://user-images.githubusercontent.com/57361655/133896265-f0be9e80-b4d5-493f-b47d-8e54608763b8.jpg)

## Introduction
In this project we tried to solve a classification problem using only ML models and preprocessing techniques.
The idea is not to foucuse on the models but on the preprocessing of the data to achive better results.

Models: SVM, KNN, Random Forest, Logistic Regression.

Preprocessing Techniques: Edge detection, MeanRGB, and feature-extraction - Bag of Visual Words (SIFT, k-means, histograms).

## Dataset
![image](https://user-images.githubusercontent.com/57361655/133897477-15a2c6cc-f15d-4a03-87d2-c0c738ea5581.png)

Link: https://www.kaggle.com/tongpython/cat-and-dog

This dataset contains difficult data cats and dogs - different sizes and dirty imgs.
The training contains 8k imgs and test 1k, with even numbers of images from each label.
Because the dataset is of raw images first we need to read each one, resize, and then reffer to the pixels as featuers.
The featuers for each sample is big meaning the demention is big, while also they have no "sence" behind them only the pixel value,
this makes the classification problem all the more difficult.

## Bssic Ground Truth
To have a basic result to compare with, we did simple preprocessing and tested the models.

1. Resize - set all the images to the same size.
2. Gray Scale - reduce the demention from 3 (RGB) to 1 (Gray)
3. Flatteren
4. Test Models - SVM, KNN, Random Forest, Logistic Regression

## Data Preprocessing

### Gray Scale
Reduce the demention from 3 (RGB) to 1 (Gray), each pixel value will be 0-255.

### Mean RGB
Reduce the demention from 3 (RGB) to 1, but each pixel value will be the mean value from each on of the dementions - Red Green Blue.

### Edge detection
Finding the eadges of the images and use the result. At first we wanted to use Canny but wanted to use a more modern model.

Using Structured Forests / Structured Edge detector - For more details:
https://debuggercafe.com/edge-detection-using-structured-forests-with-opencv/

### BoVW - Bag of visual words (Feature extraction)
How to:
1. Read each sample as RGB and resize 90x90
2. Extraction of 50 key points, that would be the new features, using SIFT. (each key point is represented as a vector of size 128)
3. Using K-Means clustering on the new features we extracted, this in order to cluster togther similar feature groups.
4. For each smaple create a histogram - the size of the hist is the amount of centers from the K-Means. And for each smaple we count the fetuers it contains.
5. Normalizing
6. Run the models on the hist that represent each smaple.


## Parameters Optimization

### Grid Search
Receving many parametes and try to find the best combination.

### Random Grid Search
Receving many parametes, but is randomly picking parameters to find a good combination that give good results.
The idea is to optimize the parametes search and not try all combinations.

## Results

### Models with Parameters Optimization
![image](https://user-images.githubusercontent.com/57361655/133900068-432df4ca-a64c-463c-93ba-aa715d541131.png)

![image](https://user-images.githubusercontent.com/57361655/133900467-f1f8179f-4291-4832-b637-e920312be7bd.png)

### Models with Data Preprocessing
![image](https://user-images.githubusercontent.com/57361655/133901768-e2c8c1fa-c867-4ff2-9cf8-718517c3a17b.png)

### BoVW
![image](https://user-images.githubusercontent.com/57361655/133905492-1dd1a7ae-e08e-45bc-8c9a-b9d0e0eeda84.png)

