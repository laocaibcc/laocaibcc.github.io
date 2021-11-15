## 深度学习网络结构




### 网络结构基础

- [ ] 卷积层
- [ ] transposed conv
- [ ] pooling 层
- [ ] batch normalization
- [ ] fully connected
- [x] 激活函数


不同的网络结构比较：
### 经典的网络结构
- Efficent net
- resnet
- dense net
- inception net
- VGG
- Resnet-101
- Inception v2
- Inception v3
- Inception Resnet (v2)
- MobileNet
- SE layer
- FEM layer



### 网络结构
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


更加详细的可以参考：
> "[池化方法总结（Pooling）](https://blog.csdn.net/mao_kun/article/details/50507376)" - mao_kun 


#### Fully Connected

全部连接层

#### Convolution
**卷积**  
图像卷积本质是提取不同的图像的邻域特征，不同的卷积核也会得到不同的 feature，便于进行匹配。



参考资料：
- [理解深度学习中的卷积](http://www.hankcs.com/ml/understanding-the-convolution-in-deep-learning.html) - 码农场  
- [通俗理解卷积神经网络（cs231n与5月dl班课程笔记）](https://blog.csdn.net/v_july_v/article/details/51812459) - v_JULY_v  
- [卷积网络中的通道(Channel)和特征图](https://www.jianshu.com/p/bf8749e15566) - 坂本龙一
- [CS231n: Convolutional Neural Networks for Visual Recognition.](http://cs231n.github.io/)  - Stanford  
- [Unsupervised Feature Learning and Deep Learning.](http://ufldl.stanford.edu/tutorial/) - Stanford


### Batch Normalizaiton

> Batch Normalizaiton 是一种通过对输入数据重新居中和重新缩放的归一化方法，使得人工神经网络收敛更快、更稳定。

**归一化**:提高模型的泛化能力，具有更加广泛的适应性。  

参考资料：
- [Batch Normalization 学习笔记](https://blog.csdn.net/hjimce/article/details/50866313) - hjimce  
- [论文笔记：Batch Normalization](http://jermmy.xyz/2017/09/02/2017-9-2-paper-notes-batch-normalization/) - Jermmy
- [Batch normalization](https://en.wikipedia.org/wiki/Batch_normalization)




### Transposed Convolution

反卷积：
- 上采样的时候会用到


参考资料：
- [1] [What is Transposed Convolutional Layer?](https://towardsdatascience.com/what-is-transposed-convolutional-layer-40e5e6e31c11)



### 经典的网络结构

- VGG
- ResNet
- Dense Net
- Inception Net
- SE layer


