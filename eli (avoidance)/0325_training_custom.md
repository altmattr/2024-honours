As part of my research over the past two weeks, I have successfully trained a custom data set. I did encounter a number of issues, which I will go through now because discussing the results.

I originally grabbed a 200 image dataset focused on chess pieces, this dataset had already been annoanted and put into a yolov8 format. When I began the training, I noticed it was occuring very slowly, so after some investigation I realised it wasn't using the GPU, this was determined by observing the activity monitor on mac. To get around this, when launching a training session, you have to specify that it will use the GPU, and this achieved by setting 'device=mps'.

This improved the speed, but resulted in a new issue which is that the metrics that you want to be observing as the training the dataset, are no longer visible. The training is still occuring, and will work as a model once completed, but no metrics to see progression.

Seems to be a common issue on apple silicon macs, as far as I could find there is no solution, aside from using the CPU, but slowness being the tradeoff. https://github.com/ultralytics/ultralytics/issues/9113 - According to this may be labelling issues of the dataset, or other.

In terms of metrics I can no longer observe are as follows -
1.Box Loss: This represents the loss or error associated with the predicted bounding box coordinates compared to the ground truth bounding box coordinates. It is a measure of how accurately the model predicts the location and size of objects in the image.
2.Class Loss (Cls Loss): This represents the loss or error associated with the predicted class probabilities compared to the ground truth class labels. It measures how accurately the model predicts the presence and class of objects in the image.
3.Box Precision (Box P): This refers to the precision of predicted bounding boxes, which is the ratio of true positive predictions (correctly predicted bounding boxes) to the total number of predicted bounding boxes. It measures how accurately the model localizes objects in the image.
4.Box Recall (Box R): This refers to the recall of predicted bounding boxes, which is the ratio of true positive predictions to the total number of ground truth bounding boxes. It measures the ability of the model to detect all instances of objects in the image.
5.mAP50 (Mean Average Precision at IoU 0.5): This is a common evaluation metric used in object detection tasks. It measures the average precision of object detection across different classes at a specific Intersection over Union (IoU) threshold of 0.5. It provides an overall assessment of the model's performance in terms of both localization and classification accuracy.

During training we are looking for 1,2 to decrease, and 3,4,5 to increase.

