# Dog Breed Classifier

## Link to Medium Blog Post https://fmstahl.medium.com/udacity-capstone-dog-breed-classifier-cd00acd533fd

## Table of Contents
1. [Introduction](https://github.com/flstahl/udacity-disaster-response-pipeline#introduction)
2. [File Descriptions](https://github.com/flstahl/udacity-disaster-response-pipeline#file-descriptions)
3. [Installation](https://github.com/flstahl/udacity-disaster-response-pipeline#installation)
4. [Results](https://github.com/flstahl/udacity-disaster-response-pipeline#results)


## Introduction
This project is my final project submission for the Udacity Data Science Nano Degree Program.

In this project, we have built a CNN-based application allowing to classify images that accepts a file path to an image and first determines whether the image contains a human, dog, or neither. Then,
if a dog is detected in the image, return the predicted breed.
if a human is detected in the image, return the resembling dog breed.
if neither is detected in the image, provide output that indicates an error.

In this exercise, we have created an end-to-end application and compared different CNN concepts and model architectures along the way. Starting off by creating a CNN fully from scratch we then proceed to using transfer learning, a concept where we make use of already pre-trained CNN models and using them as a starting point.

The overall project consisted of 7 steps.

Step 0: Import Datasets

Step 1: Detect Humans

Step 2: Detect Dogs

Step 3: Create a CNN to Classify Dog Breeds (from Scratch)

Step 4: Use a CNN to Classify Dog Breeds (using Transfer Learning)

Step 5: Create a CNN to Classify Dog Breeds (using Transfer Learning)

Step 6: Write Algorithm

Step 7: Test Algorithm


## File Descriptions
### File: bottleneck_features
contains pre-computed bottleneck features for VGG16 and ResNet50 model (courtesy of Udacity)

### Folder: haarcascades
OpenCV's implementation of Haar feature-based cascade classifiers

### Folder: saved_models
saved model files for 3 created and used CNN models

### Folder: test_images
contains test images for final test of algorithm

### File: dog_app.ipynb
Jupyter notebook containing all code

### File : extract_bottleneck_features.py
function to extract bottleneck_features from pre-trained models (courtesy of Udacity)



## Installation
-----
PIL                         5.2.0
cv2                         3.3.1
extract_bottleneck_features NA
keras                       2.0.9
matplotlib                  2.1.0
numpy                       1.12.1
pandas                      0.23.3
session_info                1.0.0
sklearn                     0.19.1
tqdm                        4.11.2
-----

Click to view modules imported as dependencies

-----
IPython             6.5.0
jupyter_client      5.2.4
jupyter_core        4.4.0
jupyterlab          1.0.9
notebook            5.7.0
-----
Python 3.6.3 | packaged by conda-forge | (default, Dec  9 2017, 04:28:46) [GCC 4.8.2 20140120 (Red Hat 4.8.2-15)]
Linux-4.15.0-1083-gcp-x86_64-with-debian-stretch-sid

## Results
The following accuracy was achieved with each model on the test set.
CNN from scratch : 1.1962%
CNN from VGG16 : 39.8325%
CNN from ResNet50 : 77.1531%

We see a substantial improvement from the initial CNN created and trained from scratch to the second model based on VGG16 all the way to our final ResNet50 implementation.
The reason for these drastic improvements in performance are manifold. Part of it can likely be associated with the training data as well as the model size. 

For the CNN trained from scratch, we have chosen (after some experimentation) a quite large architecture with ~ 733,000 parameters. In comparison to the original ResNet50 architecture (23 million parameters) this still seems reasonable. Our experiments showed that a large number of parameters is useful for extracting important features needed for the classification. 
On the other hand, however, a large ratio of parameters to test samples creates a high risk of overfitting. This might be one of the problems our initial model had. Additionally to this, a small training data set generally creates the risk of not providing enough "data mass" for the model to be accurately trained.
When comparing our initial model to the second one, where we used transfer learning and utilized the pre-trained VGG16, we see that the VGG16-based model only has ~68,000 parameters, therefore a lower risk of overfitting. The overall good performance was already established during the pre-training phase where the model was trained on more than 1,000,000 images. 

Now, when comparing VGG16 to ResNet50, it is necessary to take into account the different complexities of the two model architectures. While VGG16 consists of 16 layers and contains about 138 million parameters, the ResNet50 model features 50 layers and has 23 million parameters. For the task at hand, the latter architecture seems to be most suitable. 

Overall, we can conclude that transfer learning and, therby, making use of the extensive training that has already been performed when using these pre-trained models allows us to significantly speed up deployment and at the same time drastically improves the performance given a relatively small training data set.
