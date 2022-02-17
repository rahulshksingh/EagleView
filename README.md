# EagleView DL/ML Assignment
In this project we will train the YOLOv4 network on 2 classes 'Car' , 'Person' with the given image dataset and run the detection on a real video caught on a moving traffic camera.
# Data Preprocessing
converted coco data format(.json) into darknet format(.txt) & for this conversion, i have used convert2Yolo.py,
# Model
YOLO stands for You Only Look Once. It’s an object detection model used in deep learning use cases, of which there are mainly 2 main families:

1.Two-Stage Detectors
2.One-Stage Detectors

YOLO belongs to the family of One-Stage Detectors. In a sliding window + classification approach, you look at the image and classify it for every window.Compared to YOLOv3, YOLOv4 has improved again in terms of accuracy (average precision) and speed (FPS), the two metrics we generally use to qualify an object detection algorithm as shown in the below graph: image And the best part of the YOLOv4 model is that model training can be done on a single GPU. Given below is the architecture of the model:

# Backbone(Dense Block & DenseNet)
To improve accuracy, we can design a deeper network to extend the receptive field and to increase model complexity. And to ease the training difficulty, skip-connections can be applied. We can expand this concept further with highly interconnected layers.
A Dense Block contains multiple convolution layers with each layer Hi composed of batch normalization, ReLU, and followed by convolution. Instead of using the output of the last layer only, Hi takes the output of all previous layers as well as the original as its input. i.e. x₀, x₁, …, and xᵢ₋₁. Each Hi below outputs four feature maps. Therefore, at each layer, the number of feature maps is increased by four — the growth rate.

CSPDarknet53-YOLOv4 uses CSP darknet53 as backbone.


# Neck
Object detectors composed of a backbone in feature extraction and a head (the rightmost block below) for object detection. And to detect objects at different scales, a hierarchy structure is produced with the head probing feature maps at different spatial resolutions.

# Bag of Specials (BoS) for backbone
1.Mish activation,

2.Cross-stage partial connections (CSP), and

3.Multi-input weighted residual connections (MiWRC)


# Bag of Freebies (BoF) for backbone
1.CutMix and Mosaic data augmentation,

2.DropBlock regularization, and

3.Class label smoothing


# Framework
Darknet yolov4:
https://github.com/AlexeyAB/darknet

# Primary Analysis
Overall performance for model is good it is coming up with MAP(78%) but due to limited data size & limited training resources(google colab) i am able to trained for 3500 steps.

# False positive
Model is doing good on static images but on tiny/complex objects it's doing false prediction.

# Recommendations
1.To get a best detection model, we need good quality of 2000 instances for each class.
2.To reduce false positive prediction we need to analysis of results & also need to add background images.
3.Also can tune different hyperparameters(data augmentation,activation function,loss,filters etc.)

# Conclusion
Even on limited resouces model is working well. For any subject to improvement on detection capacity, we can do further analysis of model & testing of output.

For more one can look into the YOLOv4 model paper.The link is given below:
https://arxiv.org/pdf/2004.10934.pdf

# important links
input-https://drive.google.com/file/d/19aqBZHfi0XbBf1yi-rC8qjF_5MT61uK5/view?usp=sharing

output-https://drive.google.com/file/d/14LYw0YFht87E5eUzsx-1sm9gnjbQp_4k/view?usp=sharing

Model Weight-https://drive.google.com/drive/folders/1PZV8p-UspGUoykdD2UvC787VEzLtHpds?usp=sharing

dataset-https://drive.google.com/file/d/1X6Qj5osQw_ir3CuGZ_96eVIbSMt6f9fH/view?usp=sharing
