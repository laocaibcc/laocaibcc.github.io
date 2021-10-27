
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


### Region Proposal 系列

RCNN [1], Fast RCNN [2], Faster RCNN [3], cascade RCNN 都是基于 region proposal 方法来进行目标检测。

#### **RCNN**
RCNN 将 CNN 方法引入目标检测领域， 大大提高了目标检测效果，可以说改变了目标检测领域的主要研究思路。后续的 Fast RCNN, Faster RCNN 等都是该系列文章。

RCNN 算法流程如下：
- 1.候选区域生成： 一张图像生成1K~2K个候选区域（采用Selective Search 方法）
- 2.特征提取： 对每个候选区域，使用深度卷积网络提取特征（CNN）
- 3.类别判断： 特征送入每一类的SVM 分类器，判别是否属于该类
- 4.位置精修： 使用回归器精细修正候选框位置

论文的贡献：
- 速度：一般的目标检测方法是采用滑动窗口法来判断所有可能的区域，本文采用 Selective Search 方法预先提取一系列较可能是物体的候选区域。
- CNN 网络提取特征和有监督的训练：以往的目标检测算法一般都是提取人工设定的特征，本文采用神经网络的方法提取深度特征，并通过有监督的方法训练模型。

**待完成**
- [ ] Selective Search
- [ ] BBox Regression


#### **Fast RCNN**


#### **Faster RCNN**


参考资料：
- [1] [Rich feature hierarchies for accurate object detection and semantic segmentation](https://arxiv.org/abs/1311.2524)
- [2] [Fast R-CNN](https://arxiv.org/abs/1504.08083)
- [3] [Faster R-CNN: Towards Real-Time Object Detection with Region Proposal Networks](https://arxiv.org/abs/1506.01497)
- [RCNN- 将CNN引入目标检测的开山之作](https://zhuanlan.zhihu.com/p/23006190)


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

