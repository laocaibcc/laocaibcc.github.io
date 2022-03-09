
## 过拟合




### 1. 过拟合的定义


在深度学习中，过拟合通常是指模型在训练数据集上表现比较好，而在验证或者测试数据集上表现比较差。

<img src='resource/overfitting/img_02.svg' height=350>

<br>

### 2. 过拟合的表现

过拟合和欠拟合的比较

<img src='resource/overfitting/img_03.png' height=250>

在训练过程中，过拟合出现时会有如下特征：
- 训练 loss 下降，但是验证 loss 不收敛。
- 训练数据集上表现好,验证数据集上表现差。


<img src='resource/overfitting/img_01.png' height=350>

<br>

K-折交叉验证是用于评估模型的泛化性能的方法，常用来评估模型的过拟合问题。- [5]

<img src='resource/overfitting/img_04.png' height=300>

<br>

### 3. 如何避免过拟合


常见的方法：
- 增加训练数据
- 数据增广
- 输入数据增加噪声
- 特征筛选
- 交叉验证
- 简化数据情况：去除一些不好的数据
- 正则化
- Ensembling
- 及时停止训练
- 添加 dropout layer
- 简化模型


### 4. 附录

model ensembling 的方法

成模型一般考虑如下三种构造方式：
- Trainning Data: 不同单模型使用不同的训练数据
- Ensemble Models: 选择不同的单模型
- Combinations: 选择不同的组合方式



参考资料：
- [1] [What is Overfitting in Deep Learning and How to Avoid It](https://www.v7labs.com/blog/overfitting)
- [2] [Overfitting](https://en.wikipedia.org/wiki/Overfitting)
- [3] [4 – The Overfitting Iceberg](https://blog.ml.cmu.edu/2020/08/31/4-overfitting/)
- [4] [How to Avoid Overfitting in Deep Learning Neural Networks](https://machinelearningmastery.com/introduction-to-regularization-to-reduce-overfitting-and-improve-generalization-error/)
- [5] [Cross-validation (statistics)](https://en.wikipedia.org/wiki/Cross-validation_(statistics))
- [6] [深度学习的集成方法——Ensemble Methods for Deep Learning Neural Networks](https://www.cnblogs.com/szxspark/p/10144913.html)
- [7] [Ensemble Learning Methods for Deep Learning Neural Networks](https://machinelearningmastery.com/ensemble-methods-for-deep-learning-neural-networks/)
- [8] [A Gentle Introduction to Ensemble Learning Algorithms](https://machinelearningmastery.com/tour-of-ensemble-learning-algorithms/)


