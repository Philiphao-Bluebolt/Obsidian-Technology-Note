+ Topics - Object Detection, Pose Estimation, Human Action Recognition

Video Understanding is the process of extracting desired contents and information from the video. Here we will cover three topics of video understanding. Nowadays, most state-of-the-art video analysis algorithms make use of AI technologies.

+ Object Detection
	+ [[#Object Detection Introduction]]
	+ [[#Object Detection Metrics]]
		+ [[#Mean Average Precision (mAP)]]
		+ [[#Floating Point Operations (FLOPs)]]
	+ [[#Two-Stage Detector]]
		+ [[#R-CNN]]
		+ [[#Faster R-CNN]]
	+ [[#One-Stage Detector]]
		+ [[#YOLO]]
	+ [[#Emerging Methods]]
		+ [[#Swin Transformer]]
		+ [[#Detection Transformer]]
+ Object Tracking
+ Pose Estimation
+ Human Action Recognition

---
## Object Detection Introduction

Object detection algorithms are fundamental of most video understanding tasks. It recognizes an object in an image or a video and marks it with a bounding box.

Here are three types of network-based object detection algorithms 

| Type        | Speed     | Accuracy | Typical Methods                               |
| ----------- | --------- | -------- | --------------------------------------------- |
| Two-Stage   | Low       | High     | Faster-RCNN, Mask-RCNN, SPP-net, FPN          |
| One-Stage   | High      | Low      | Yolo, SSD, CenterNet, EfficientDet            |
| Lightweight | Very High | Low      | MobileNetV2-based SSD, SqueezeNet, ShuffleNet |


---
## Object Detection Metrics

The process is also called **Prediction** in the context of machine learning. Some metrics are used to measure the efficiency and precision of the detection model.

### Mean Average Precision (mAP)

mAP is a training metrics used in the process of training a network-based object detection model. It measures the detection precision 


### Floating Point Operations (FLOPs)

FLOPs is a operation metrics measuring how fast a detection model can run. Just as indicated by its name, the metrics calculates the total of required floating point operation in a single forward pass in the network while detection. 

---
## Two-Stage Detector

Two-Stage Detector is the most accurate detector type with more complex and slower performance. Several methods of this type are based on the R-CNN model.

### R-CNN

RCNN stands for Region-based Convolution Neural Network. It's a variety of CNN model which features image region bounding before inputing into the network and use Supporting Vector Machine for region classification.

### Faster R-CNN

Faster R-CNN is a improved version of R-CNN which applys convolution to the whole image instead of thousands of bounding region based on the original image. It only takes an average of $0.5\%$ of the R-CNN running time to detect once.

---
## One-Stage Detector

One-Stage Detector only applies regression and classification on the original image without convolution. The most popular one-stage detector is the YOLO algorithm.

### YOLO

YOLO stands for You Only Look Once, indicating the one-stage characteristics of the alogorithm. It mainly consists of three part: Backbone, Neck and Head.

+ **Backbone** - Intended for **feature extraction**, it's made up of different layer of pretrained models targeting feature extraction of different scales.

+ **Neck** - Intended for **feature fusion**, method including up-sampling and concatenation.

+ **Head** - Intended for **Prediction**, it detects and classifies the object based on the features.  

YOLO has envolved for nearly a decade, its performance is still increasing. 

---
## Emerging Methods

There's some new object detection algorithms that based on the transformer architecture.

### Swin Transformer



### Detection Transformer



---
## Object Tracking Introduction

Object tracking aims to continuous detect the same object in sequential frames of a video. It's the expansion of object detection problem into the time domain.

Object tracking problems need to consider two factors

+ **Appearance** - how does the object look like
+ **Motion** - where will the object appear at in the following frames 

Multiple object tracking is the most common object tracking task. It requires more than one object to be tracked simutaneously. Some common challenge includes:

+ **Target Similarity** - some target objects look alike
+ **Disturbance** - some non-target objects interfere the tracking process
+ **Occlusion** - the target objects heavily overlapped with each other in the image

### Tracking by Detection

Tracking by detection method is based on object detection and motion prediction. It mainly consists of three steps

1. **Detection** - detect the object at a frame
2. **Motion Prediction** - using motion model to predict the position in the next frame.
3. **Data Association** - match and calibrate the prediction 




---
##