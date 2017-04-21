# SSD: Single Shot MultiBox Detector
Published in Dec 2015.
By UNC, Google and Univ. of Michigan

*Wei Liu et al.*

## Problem 
Detecting objects of different sizes in images using a single deep neural network.

## Core Ideas
* Discretizes the space of bounding boxes into a set of default boxes, over diff aspect ratios and scales.
* Does the above per feature map location.
* At test time, generate score for each class in each default box and adjust the default box.
* Combines predictions from multiple feature maps - to handle objects of different sizes.

## Advantages
* Does not require object proposals, pixel resampling -- cheaper compute
* Fast - 59 FPS vs 7 FPS in previous method
* Unified framework for training and inference

## Connections to previous work
* Overfeat 
* YOLO 
* Improvements:
  * Small convolutional filter to predict objects classes and offsets.
  * Seperate filters for different aspect ratios.
  * Applying filters to mulitple feature maps to detect objects of different scales.
  
## The model architecture
![](ssd.png?raw=true)
* First few layers are based on a standard architecture used for image classificaiton - VGG16.

## Implementation details
![](ssd-default-boxes.png?raw=true)

* Model loss is a weighted sum between localisation loss (smooth L1) and confidence loss.

## Experiments
### Dataset 1

### Dataset 2



## Speed
59 FPS, can get faster with improvements in base network.

## Conclusions and Extensions



## Comments/Questions 
* This method requires preprocessing labels to map them to default boxes. Ground truth boxes are mapped to default boxes with best Jaccard overlap, match all boxes above a threshold.

