This Project aims to have Real Time Obstacle Detection and position estimation, with the goal of informing the visually impaired users about the surrounding obstacles and their spatial position using navigations.

TensorFlow’s Object Detection API is a very powerful tool that can quickly enable anyone (especially those with no real machine learning 
background like myself) to build and deploy powerful image recognition software. 
Here, we have created a nagigation system to aid the visually impaired people which will try to identify and recognise the obstacles in the 
path and navigate the person to avoid accident. 

The 3 main components of the project are:
1. Obstacle detection and recognition
2. Proximity alert based on distance estimation
3. Navigation alert 

Dataset used:

Coco dataset (It coontains 90 classes and almost covers all indoor and outdoor objects)

Real time Obstacle detection is done using pretrained models of:
1. Faster RCNN
2. SSD
3. YOLO

Among the three detection models, Faster RCNN is most accurate but is slow as compared to SSD.

Installation instructions:

1. Install tensorflow and all the other required dependencies

2. Clone the tensorflow models github repository: 
 git clone https://github.com/tensorflow/models.git
 
3. To use the object detection API of tensorflow:

   apt-get -qq install libprotobuf-java protobuf-compiler
   
   protoc ./models/research/object_detection/protos/string_int_label_map.proto --python_out=.
   
   cp -R models/research/object_detection/ object_detection/
   
   rm -rf models
   
4. Select the object detection model:

for SSD, MODEL_NAME = 'ssd_inception_v2_coco_2017_11_17'

for Faster RCNN with inception, MODEL_NAME = 'faster_rcnn_inception_resnet_v2_atrous_coco_2017_11_08'

Fater RCNN with ResNet, MODEL_NAME = 'faster_rcnn_resnet101_coco_2017_11_08'

5. Area of interest is defined using proximity defining. Refer function - region_of_interest() in the code

6. Obstacle detection and recognition is done upon the extracted frames in the area of interest.

7. Detected obstacles are estimated to be near of far away

8. Based upon the direction of motion/placement of the object, the person is advised to moved accordingly in an appropriate direction


References:

https://github.com/endernewton/tf-faster-rcnn 

https://cv-tricks.com/object-detection/faster-r-cnn-yolo-ssd/

https://medium.com/@WuStangDan/step-by-step-tensorflow-object-detection-api-tutorial-part-1-selecting-a-model-a02b6aabe39e
