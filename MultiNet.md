# MultiNet: Real-time Joint Semantic Reasoning for Autonomous Driving

Published on Dec 22, 2016
By University of Toronto, FZI Research Center, University of Cambridge
* Marvin Teichmann et. al. *

## Problem 
* Joint classification, detection and segmentation of images.
* Fast computation times, suitable for autonomous vehicles.

## Core Ideas
* Unified architecture where the encoder is shared between various tasks. - facilitates fast inference and transfer learning between tasks.
* Encoder - consists of convolution and pooling layers from VGG network.
* Detection decoder combines ideas from YOLO and Fast RCNN.

## Advantages
* Fast, 95 ms per frame 
* Good performance on small datasets - state of the art for Road detection on the KITTI dataset.

## Connections to previous work
* YOLO, ReInspect and Overfeat - Regression based decoder
* Fast RCNN

## The model architecture
* Encoder: 
  13 layers of the VGG16 Network - results in feature tensor of shape 39x12x512.
* Decoder:
  * Classification decoder: FCN and Softmax
  * Detection decoder - Regression based decoder instead of region proposal
    - predicts cooordinates of the bounding boxes.
    - Re-zoom layer predicts residuals.
  * Segmentation decoder: FCN architecture

![](multiNet.png?raw=true)

## The training protocol
* One hot encoding for classification and segmentation.
* Loss: Cross-entropy + L1 loss on bounding box co-ordinates.
* Combined training strategy : merging the gradients computed by each loss on independent mini-batches.
* Encoder: VGG weights on ImageNet
* Adam optimizer
* Dropout - convolutions in the decoder
* Metrics:
  - MaxF1 score for segmentation
  

## Experiments
### KITTI Dataset
Top of the leaderboard for segementation - trained only on a few hundred images.

![](multiuNetOutput.png?raw=true)

## Speed
94 ms for combined detection and segmentation.




