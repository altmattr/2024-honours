# Current Technical Solutions For Object Detection Using AI 

# What is object detection 
Object detection is a computer vision technique that identifies and locates objects within an image or video. Specifically, object detection draws bounding boxes around these detected objects.

Object detection can be broken down into machine learning-based approaches and deep learning-based approaches.

In more traditional ML-based approaches, computer vision techniques examine various features of an image, such as the colour histogram or edges, to identify groups of pixels that may belong to an object. These features are then fed into a regression model that predicts the object's location and label.

On the other hand, deep learning-based approaches employ convolutional neural networks (CNNs) to perform end-to-end, unsupervised object detection, in which features don’t need to be defined and extracted separately

# How It Works 

Deep learning-based object detection models can be broadly categorized into two parts: an encoder and a decoder. The encoder processes the image to extract features that help identify objects' locations and labels. The decoder then uses these features to predict bounding boxes and labels for each object.

The simplest decoder is a pure regressor, which directly predicts the location and size of each bounding box based on the encoder's output. While simple and potentially effective when the number of objects is known and fixed, this approach has limitations, significantly when the actual number of objects varies.

An advancement over the pure regressor is the region proposal network (RPN), which suggests possible object-containing regions in an image. These proposed regions are then analyzed to confirm objects' presence and labels. This method allows for more flexibility and accuracy but is computationally more demanding.

Single shot detectors (SSDs) represent a middle ground using predefined regions based on a grid of anchor points across the image, allowing for the detection of objects at various scales and aspect ratios. However, SSDs often produce overlapping detections, requiring post-processing techniques like non-maximum suppression to refine the results.

The accuracy of object detection models is typically measured by intersection-over-union (IOU) for location accuracy and per cent correct for label accuracy.

Several models have emerged within this framework:

R-CNN and its derivatives (Faster R-CNN, Mask R-CNN) utilize region proposal methods, offering high accuracy with improved computational efficiency over time. Mask R-CNN, in particular, is noted for its performance in server-side applications.

Single-shot detector models (YOLO, MobileNet + SSD, SqueezeDet) are optimized for speed and efficiency, making them suitable for mobile or embedded systems. They vary mainly in their encoder designs and anchor configurations.

CenterNet approaches object detection by predicting the centre points of objects, avoiding the need for region proposals, and showing greater efficiency and accuracy than SSD and R-CNN methods.

These models represent the evolution and variety of approaches in deep learning for object detection, each with its strengths, limitations, and ideal use cases.


# Evidence
* https://fritz.ai/object-detection/
* https://hal.science/hal-03836472
* https://ieeexplore.ieee.org/document/9843697
* https://ieeexplore.ieee.org/abstract/document/9520347  
