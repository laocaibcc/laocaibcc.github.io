## 深度学习网络结构


Content
- 基础网络结构
- 常见的 Network block
- 常见的 Network backbone


### 基础网络结构

#### Pooling
卷积神经网络中的卷积层是对图像的一个邻域进行卷积得到图像的邻域特征，亚采样层就是使用 pooling 技术将小邻域内的特征点整合得到新的特征。 pooling 确实起到了整合特征的作用,仿照人的视觉系统进行降维（降采样），用更高层的抽象表示图像特征。
pooling 的结果是使得特征减少，参数减少，但 pooling 的目的并不仅在于此。pooling 目的是为了保持某种不变性（旋转、平移、伸缩等）。

常见的几种 Pooling 方法:
- General Pooling：
- Overlapping Pooling：
- Spatial Pyramid Pooling：

常见的 pooling 操作：
- mean-pooling
- max-pooling
- Stochastic-pooling

<br>

#### **Fully Connected Layer**

全部连接层
<br>

#### **Convolution**

图像卷积本质是提取不同的图像的邻域特征，不同的卷积核也会得到不同的 feature，便于进行匹配。

<br>

#### **Batch Normalizaiton**

Batch Normalizaiton 是一种通过对输入数据重新居中和重新缩放的归一化方法，使得人工神经网络收敛更快、更稳定。

**归一化**:提高模型的泛化能力，具有更加广泛的适应性。  

<br>

#### **Transposed Convolution**

反卷积：
- 上采样的时候会用到

<br>

#### 前向传播与反向传播

- 通过输入样本x，按照模型结构与模型参数逐层计算，模型最后输出预测结果，这样一个从前往后递进传播的过程，就称为前向传播（Forward Propagation）
- 在训练过程中，经过前向传播后得到的最终结果跟训练样本的真实值总是存在一定误差，这个误差便是损失函数。想要减小这个误差，当前应用最广的一个算法便是梯度下降，于是用损失函数，从后往前，依次求各个参数的偏导，这就是所谓的反向传播（Back Propagation），一般简称这种算法为BP算法。
- （所以损失函数一般是需要可导？？？）




参考资料：
- [1] [池化方法总结（Pooling）](https://blog.csdn.net/mao_kun/article/details/50507376)
- [2] [What is Transposed Convolutional Layer?](https://towardsdatascience.com/what-is-transposed-convolutional-layer-40e5e6e31c11)
- [3] [Batch Normalization 学习笔记](https://blog.csdn.net/hjimce/article/details/50866313)
- [4] [论文笔记：Batch Normalization](http://jermmy.xyz/2017/09/02/2017-9-2-paper-notes-batch-normalization/)
- [5] [Batch normalization](https://en.wikipedia.org/wiki/Batch_normalization)
- [6] [理解深度学习中的卷积](http://www.hankcs.com/ml/understanding-the-convolution-in-deep-learning.html)
- [7] [通俗理解卷积神经网络（cs231n与5月dl班课程笔记）](https://blog.csdn.net/v_july_v/article/details/51812459)
- [8] [卷积网络中的通道(Channel)和特征图](https://www.jianshu.com/p/bf8749e15566)
- [9] [CS231n: Convolutional Neural Networks for Visual Recognition.](http://cs231n.github.io/)
- [10] [Unsupervised Feature Learning and Deep Learning.](http://ufldl.stanford.edu/tutorial/)
- [11] [前向传播与反向传播](https://www.cnblogs.com/chay/articles/10683235.html)


<br>

### 常见的 Backbone

- VGG
- Fully convolution network
- UNet
- Faster RCNN



<br>

### 常见的 Backblock

- Res block
- Dense block
- Attention block
- SE layer
- Inception block



