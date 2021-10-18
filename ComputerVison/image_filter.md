## 图像滤波


### 1. 图像滤波

> 滤波是一种用于修正或增强图像的技术。用滤波实现的图像处理运算包括平滑、锐化和边缘增强等。 - [1]

图像滤波的方法应用十分广泛，我们日常见到的各种图像都是经过图像滤波处理之后得到的。根据不同的分类标准，可以将图像滤波分为不同滤波方法。

- 根据滤波的作用域不同可以分为：空间域滤波和频率域滤波。
- 根据滤波特点，可以分为：平滑滤波，锐化滤波，边缘增强滤波等。


参考资料：
- [1] [图像滤波](https://ww2.mathworks.cn/help/images/linear-filtering.html)
- [2] [Image Filtering](https://ai.stanford.edu/~syyeung/cvweb/tutorial1.html)


### 平滑

平滑，是利用某种方法去除数据中的噪声而保持数据中其他信息不变。

平滑方法的分类：
- 利用局部信息
- 利用拟合信息


一些常见的平滑方法：
- Kernel smoother
- Laplacian smoothing
- Smoothing spline
- Low-pass filter
- Moving average
- Exponential smoothing
- Digital filter


注意：平滑与曲线拟合是有一些不同的，具体的不同之处需要进一步去探索。

参考资料：
- [1] [Smoothing](https://en.wikipedia.org/wiki/Smoothing)
- [2] [Kernel](https://en.wikipedia.org/wiki/Kernel_(image_processing))
- [3] [Convolution](https://en.wikipedia.org/wiki/Convolution)

#### **Kernel smoother**

kernel 平滑算法是根据 kernel 和局部数据来计算平滑结果的方法。

- Gaussian kernel smoother：高斯核
- Nearest neighbor smoother：最近邻
- Kernel average smoother：均值核
- Local linear regression：局部线性回归，寻找最小平方差问题
- Local polynomial regression：局部多项式回归


参考资料：
- [1] [Kernel smoother](https://en.wikipedia.org/wiki/Kernel_smoother)




