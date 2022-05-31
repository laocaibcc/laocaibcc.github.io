
## Python 迭代器与生成器


- 1.生成器
- 2.迭代器
- 3.生成器与迭代器的比较





### 2. 迭代器（iterator）

迭代器与可迭代之间的差别是：
- 







### 3. 迭代器与生成器的比较

### 1. 生成器（generator）

- 列表作为一个容器，其所占内存大小和元素个数成正比，也即每增加一个元素，那么内存中就要分配一块区域来存储它。
- 通常我们并不会一次处理所有元素，而只是集中在其中的某些相邻的元素上。所以如果列表元素可以用某种算法用已知量推导出来，就不必一次创建所有的元素。这种边循环边计算的机制，称为生成器（generator），生成器是用时间换空间的典型实例。

定义 generator 方法
- 只要把一个列表生成式的[]改成()，就创建了一个 generator。
- 如果一个函数定义中包含 yield 关键字，那么这个函数就不再是一个普通函数，而是一个 generator 函数，调用一个 generator 函数将返回一个 generator。

注意事项
- 在Python中，一边循环一边计算的机制，称为生成器：generator。
- generator 中保存的是算法，每次通过算法生成需要的数据。生成器实际上就是利用时间换空间。



参考资料：
- [1] [生成器](https://www.liaoxuefeng.com/wiki/1016959663602400/1017318207388128)
- [2] [14. 生成器和迭代器](https://pythonhowto.readthedocs.io/zh_CN/latest/iterator.html#)
- [3] []()

<br>
<div STYLE="page-break-after: always;"></div>

