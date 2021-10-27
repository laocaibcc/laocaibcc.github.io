### Deep Learning



#### 深度学习开发的一般步骤

深度学习的入门
- 深度学习的整体流程
- 各个模块的方法和数学原理
- 针对不同任务的结合方法

#### 模块简介

##### 目录
- 激活函数
- 损失函数
- 优化方法
- 网络结构
    - Pooling
    - Fully Connected
    - Convolution
- Batch Normalization <font color=#FF0000>  

<font color=#FFOOOO>待处理</font>    
non-saturating neurons：  
backforward and forward 比较
anchor  
bouding box regression  
hard mining  
rpn  
selective search  
ensemble of classifiers  
Transfer Learning  

</font>

---

### 优化方法（Optimization）

如何选择优化方法？
全局最优化，避免局部最优化

常见的优化方法有：
- SGD(stochastic gradient descent)
- Momentum
- Nesterov
- Adagrad
- Adadelta
- RMSprop
- Adam
- Adamax
- Nadam

更多资料，可以参考：
- [An overview of gradient descent optimization algorithms](http://ruder.io/optimizing-gradient-descent/)
- [深度学习最全优化方法总结比较（SGD，Adagrad，Adadelta，Adam，Adamax，Nadam）](https://zhuanlan.zhihu.com/p/22252270)



### 网络结构
#### Pooling
卷积神经网络中的卷积层是对图像的一个邻域进行卷积得到图像的邻域特征，亚采样层就是使用 pooling 技术将小邻域内的特征点整合得到新的特征。 pooling 确实起到了整合特征的作用,仿照人的视觉系统进行降维（降采样），用更高层的抽象表示图像特征.      
设定pooling的size(m\*n)，卷积特征需要相应的划分为不相连的m\*n块。  
pooling 的结果是使得特征减少，参数减少，但 pooling 的目的并不仅在于此。pooling 目的是为了保持某种不变性（旋转、平移、伸缩等）.

常见的几种 Pooling 方法:
- **General Pooling**
- **Overlapping Pooling**
- **Spatial Pyramid Pooling**

更加详细的可以参考：
> "[池化方法总结（Pooling）](https://blog.csdn.net/mao_kun/article/details/50507376)" - mao_kun 

##### Pooling 具体操作
常用 pooling  操作有mean-pooling， max-pooling 和 Stochastic-pooling 等。  

**mean-pooling**  
对邻域内特征点只求平均。假设pooling的窗大小是2x2, 在forward的时候，就是在前面卷积完的输出上依次不重合的取2x2的窗平均，得到一个值就是当前mean pooling之后的值。backward的时候，把一个值分成四等分放到前面2x2的格子里面就好了。
```
forward: [1 3; 2 2] -> [2]
backward: [2] -> [0.5 0.5; 0.5 0.5]
```

**max-pooling**  
对邻域内特征点取最大。forward的时候你只需要把2x2窗子里面那个最大的拿走就好了，backward的时候你要把当前的值放到之前那个最大的位置，其他的三个位置都弄成0。
```
forward: [1 3; 2 2] -> 3
backward: [3] -> [0 3; 0 0]
```
据相关理论，特征提取的误差主要来自两个方面：   
（1）邻域大小受限造成的估计值方差增大  
（2）卷积层参数误差造成估计均值的偏移  
一般来说，mean-pooling能减小第一种误差，更多的保留图像的背景信息，max-pooling能减小第二种误差，更多的保留纹理信息。

**Stochastic-pooling**  
介于两者之间，通过对像素点按照数值大小赋予概率，再按照概率进行亚采样，在平均意义上，与mean-pooling近似，在局部意义上，则服从max-pooling的准则。  
stochastic pooling方法非常简单，只需对feature map   中的元素按照其概率值大小随机选择，即元素值大的被选中的概率也大。而不像max-pooling那样，永远只取那个最大值元素。


#### Fully Connected
After several convolutional and max pooling layers, the high-level reasoning in the neural network is done via fully connected layers. **Neurons in a fully connected layer have connections to all activations in the previous layer**, as seen in regular neural networks. Their activations can hence be computed with a matrix multiplication followed by a bias offset.  
too many weights, waste time and memory, lead to overfiting  


#### Convolution
**卷积**  
图像卷积本质是提取不同的图像的邻域特征，不同的卷积核也会得到不同的feature，便于进行匹配。


>[理解深度学习中的卷积](http://www.hankcs.com/ml/understanding-the-convolution-in-deep-learning.html) - 码农场  
>[通俗理解卷积神经网络（cs231n与5月dl班课程笔记）](https://blog.csdn.net/v_july_v/article/details/51812459) - v_JULY_v  
>[卷积网络中的通道(Channel)和特征图](https://www.jianshu.com/p/bf8749e15566) - 坂本龙一

**convolution layer**

> "The convolutional layer  will compute the output of neurons that are connected to local regions in the input, each computing a dot product between their weights and a small region they are connected to in the input volume."   


> [CS231n: Convolutional Neural Networks for Visual Recognition.](http://cs231n.github.io/)  - Stanford  
> [Unsupervised Feature Learning and Deep Learning.](http://ufldl.stanford.edu/tutorial/) - Stanford


### Batch Normalizaiton
<font color=#FF0000> 待处理 </font>  

**归一化**:提高模型的泛化能力，具有更加广泛的适应性。  

>[Batch Normalization 学习笔记](https://blog.csdn.net/hjimce/article/details/50866313) - hjimce  
>[论文笔记：Batch Normalization](http://jermmy.xyz/2017/09/02/2017-9-2-paper-notes-batch-normalization/) - Jermmy  



