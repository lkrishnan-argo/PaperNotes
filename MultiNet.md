# MultiNet: Real-time Joint Semantic Reasoning for Autonomous Driving

Published on Dec 22, 2016
By University of Toronto, FZI Research Center, University of Cambridge

*Marvin Teichmann et. al.*

## Problem 
* Joint classification, detection and segmentation in one forward pass.
* Fast computation time, suitable for autonomous vehicles.

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

![](multinet-results.png?raw=true)

## Speed
95 ms for combined detection and segmentation.

## Code
https://github.com/MarvinTeichmann/MultiNet

## Comments
Code base in TensorFlow v1.0, python 2.7




