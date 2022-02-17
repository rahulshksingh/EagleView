# EagleView DL/ML Assignment
In this project we will train the YOLOv4 network on 2 classes 'Car' , 'Person' with the given image dataset and run the detection on a real video caught on a moving traffic camera.
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



For more one can look into the YOLOv4 model paper.The link is given below:
https://arxiv.org/pdf/2004.10934.pdf
