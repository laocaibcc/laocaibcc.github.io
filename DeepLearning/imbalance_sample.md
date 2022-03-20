## 样本不均衡问题



为了发现问题，首先需要合适的评估方法，确保能够发现样本不均衡问题被发现，而不是被指标忽略。

从两个角度出发：
- 数据：通过数据重采样等方法缓解样本不均衡问题
- 算法：从算法层面，增加对少数样本的关注。


### 数据角度


- 数据降采样：对类别数量足够的数据，进行下采样。
- 数据过采样：
- K-折交叉验证
- 模型 ensemble：在不同的 dataset 下训练出来的模型
- SMOTE (Synthetic Minority Over-sampling Technique)

### 算法角度

深度学习常见的方法

- 测试分割



参考资料：
- [1] [Training Region-based Object Detectors with Online Hard Example Mining](https://arxiv.org/abs/1604.03540v1)
- [2] [Focal Loss for Dense Object Detection](https://arxiv.org/abs/1708.02002)
- [3] [SMOTE: Synthetic Minority Over-sampling Technique](https://arxiv.org/abs/1106.1813)
- [4] [Multi-Class Imbalanced Classification](https://machinelearningmastery.com/multi-class-imbalanced-classification/)


