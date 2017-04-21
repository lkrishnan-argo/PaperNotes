# SSD: Single Shot MultiBox Detector
Published on 29 Dec 2016.
By UNC, Google and Univ. of Michigan
* Wei Liu et al.*

## Problem 
Detecting objects of different sizes in images using a single deep neural network.

## Core Ideas
* Discretizes the space of bounding boxes into a set of default boxes, over diff aspect ratios and scales.
* Does the above per feature map location.
* At test time, generate score for each class in each default box and adjust the default box.
* Combines predictions from multiple feature maps - to handle objects of different sizes.

## Advantages
* Does not require object proposals, pixel resampling -- cheaper compute
* Fast - 59 FPS vs 7 FPS in prev.method
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


## Implementation details
![](ssd-default-boxes.png?raw=true)


## Experiments
### Dataset 1

### Dataset 2



## Speed
59 FPS, can get faster with improvements in base network.

## Conclusions and Extensions



## Comments/Questions 
* This method requires significantly more labeling effort.

