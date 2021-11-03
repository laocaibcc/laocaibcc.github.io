
## 图像分割

<font color=red>预估时间：4h</font>

> 在计算机视觉领域，图像分割（segmentation）指的是将数字图像细分为多个图像子区域的过程。图像分割的目的是简化或改变图像的表示形式，使得图像更容易理解和分析。 - [1]


方法分类：
- 非神经网络方法
  - 二值化
  - 聚类法
  - 直方图法
  - 边缘检测
  - 区域生长
  - 水平集方法
  - 小波变换方法
- 神经网络方法
  - [ ] **UNet 系列**： U-Net，ResUNet，VNet

 

参考资料：
- [1] [Image segmentation](https://en.wikipedia.org/wiki/Image_segmentation)
- [2] [Image Segmentation Using Deep Learning: A Survey](https://arxiv.org/abs/2001.05566)
- [3] [UNet-family](https://github.com/ShawnBIT/UNet-family)

<br>

### UNet 系列


#### U-Net

论文介绍
- 1.网络结构：首次提出 U 型网络，先4次下采样，后4次上采样。
  - 前面的浅层卷积层与后面的深层卷积层有连接

<img src='resource/image_segmentation/img_01.png' height=300>

- 2.损失函数（目标方程）：带有权重的交叉熵函数（公式1所示）。
  - p（x） 是预测为该类（x）的概率，softmax 计算得到。
  - 权重是基于边缘距离计算得到，如公式2所示
  - d1（x） 是 x 与最近细胞边缘的距离， d2（x） 是 x 距离第二近细胞边缘的距离。

<img src='resource/image_segmentation/img_02.png' height=50>
<br>
<img src='resource/image_segmentation/img_03.png' height=65>

- 3.训练过程：多分类的像素分割，也可以成为分类问题。
- 4.其他：
  - 数据增广



#### ResUNet




参考资料：
- [1] [U-Net: Convolutional Networks for Biomedical Image Segmentation](https://arxiv.org/abs/1505.04597)
- [2] [U-Net](https://en.wikipedia.org/wiki/U-Net)
- [3] [Deep Residual Learning for Image Recognition](https://arxiv.org/abs/1512.03385)
- [4] [Road Extraction by Deep Residual U-Net](https://arxiv.org/abs/1711.10684)





