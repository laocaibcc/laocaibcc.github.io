
## 目标检测

> 目标检测是利用计算机视觉和图像处理技术，检测数字图像或者视频中特定类型的语义物体。 - [1]


参考资料：
- [1] [Object detection](https://en.wikipedia.org/wiki/Object_detection)

方法分类：
- 非神经网络方法
  - Harr 特征
  - SIFT 特征
  - HOG 特征
- 神经网络方法
  - Region Proposals系列（R-CNN，Fast R-CNN, Faster R-CNN, cascade R-CNN）
  - SSD
  - YOLO 系列
  - RefineDet
  - Retina-Net
  - Deformable convolutional networks 


### RCNN
对RCNN的介绍，下面这篇博客做了比较详细的介绍：

>[【目标检测】RCNN算法详解  - shenxiaolu1984](https://blog.csdn.net/shenxiaolu1984/article/details/51066975#fn:1)


**网络结构**
![network](https://img-blog.csdn.net/20160405214721512)

#### 一些疑问

---
### Fast RCNN
同上，Fast RCNN的介绍，可以参考：

>[【目标检测】Fast RCNN算法详解  - shenxiaolu1984](https://blog.csdn.net/shenxiaolu1984/article/details/51036677)

**网络结构**
![network](https://img-blog.csdn.net/20160411214438672)


---
### Faster RCNN

>[【目标检测】Faster RCNN算法详解  - shenxiaolu1984](https://blog.csdn.net/shenxiaolu1984/article/details/51152614)

**网络结构**
![network](https://img-blog.csdn.net/20160415133947737)


---
### Speed/accuracy trade-offs for modern convolutional object detectors

#### Three meta-architecture:
- Faster R-CNN
- R-FCN
- SSD

#### Architectural configuration
- feature extractor
    - VGG
    - Resnet-101
    - Inception v2
    - Inception v3
    - Inception Resnet (v2)
    - MobileNet
- number of proposals
- Output stride settings for Resnet and Inception Resnet

#### Loss function configuration
- matching
- box encoding
- Location loss



#### Analyses
- Accuracy vs time: Faster R-CNN get better accuracy, but slower.
- feature extractor: Resnet is quite good(pretrained model is better)
- object size: larger easy to detect, faster rcnn do better in small object
- image size: input resolution can significantly impact detection accuracy.
- number of proposals: more proposals, higher accuracy, 50 proposals can get quite high accuracy
- FLOPs analysis: for denser block models such as Resnet 101, FLOPs/GPU time is typically greater than 1.
- Memory analysis: larger and more powerful feature extractors requiring much more memory.

