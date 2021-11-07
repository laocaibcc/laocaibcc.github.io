
## 半监督学习

<font color=red>预估时间：4h</font>

> 。 - [1]



Semi-supervised learning

半监督学习方法训练的流程：
- [ ] 原理
- [ ] 算法流程
- [ ] 常见的方法和网络结构
- [ ] 结果表现


基于以下至少一种假设：
- 1.平滑假设（Smoothness Assumption）：如果两个样本 x1，x2 相似，则它们的相应输出 y1，y2 也应如此。这意味着如果两个输入相同类，并且属于同一簇，则它们相应的输出需要相近，反之亦成立。
- 2.聚类假设（Cluster Assumption）： 当两个样例位于同一聚类簇时，它们在很大的概率下有相同的类标签。这个假设的等价定义为低密度分离假设，即分类决策边界应该穿过稀疏数据区域，而避免将稠密数据区域的样例分到决策边界两侧
- 3.流形假设（Manifold Assumption）：将高维数据嵌入到低维流形中，当两个样例位于低维流形中的一个小局部邻域内时，它们具有相似的类标签。

实验表明：SSL 不满足这些假设或模型假设不正确时，无类标签的样例不仅不能对学习性能起到改进作用，反而会恶化学习性能，导致SSL的性能下降。



常见的损失函数：
- MSE：均方差误差
- KL散度：
- JS散度：

具体到每一种算法，核心思想是没有变化的，即最小化未标记数据与其扰动输出两者之间的距离，但计算输出的形式上有很多变化。


参考资料：
- [1] [Semi-supervised learning](https://en.wikipedia.org/wiki/Semi-supervised_learning)
- [2] [长文总结半监督学习（Semi-Supervised Learning）](https://bbs.cvmart.net/articles/3322)
- [3] [Kullback–Leibler divergence](https://en.wikipedia.org/wiki/Kullback%E2%80%93Leibler_divergence)
- [4] [Jensen–Shannon divergence](https://en.wikipedia.org/wiki/Jensen%E2%80%93Shannon_divergence)

<br>


常见的半监督方法：
- Pi-Model：Temporal Ensembling for Semi-Supervised Learning
- Temporal Ensembling：Temporal Ensembling for Semi-Supervised Learning
- Mean teachers：Mean teachers are better role models: Weight-averaged consistency targets improve semi-supervised deep learning results
- UDA：Unsupervised Data Augmentation for Consistency Training
  - UDA 证明了针对性的数据增强效果明显优于无针对性的数据增强，
- 测试分析

Proxy-label Methods
 - 测试分析

