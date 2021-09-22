## Python

content
- 问题记录
- 《fluent python》 学习记录
- Python Tool
- 命名很重要，有时候就是找不到原因，结果是名字的原因。
- 研究确定一下Python命名的常见规范。


<font color=#FF0000>**问题记录**</font>  
- 动态导入与静态导入模块之间的差别？
- python 迭代怎么操作, iter(x) ?
- python 变量等作用域，存储变量自身还是 reference。


#### Python 日常使用小结
- 尽量使用自带的 special method， 程序效率会更高
- 根据需求，采用合适的数据类型， 善于运用优秀的 package
- 自行构造的类或者类型也能使用 spcial method 和 package 等
- 编程是要注意 pythonic

### 《Fluent Python》 学习记录
#### CHAPTER 1. The Python Data Model

- **Pythonic**: 尽量使用 python 自带的格式去构造自己的类, 性能和编程效率都会更高.
    - \_\_repr__: string representation, 清楚的展示变量
    - \_\_str__: 以一种可读的方式将展示

更详细的 special methods 可以参考
> Table 1-1. Special method names (operators excluded)  
> Table 1-2. Special method names for operators

##### 小结
- python 会有很多 magic function，善用这类函数。有些数据类型是本身可以直接使用，有些是可以自行实现。
- magic function 的性能和编程效率通常会更高，注意，这些函数的使用很多是通过一些符号来实现的，不是通过显式的调用。
- 写代码时要注意 pythonic。

Python 编程规范
> [The Zen of Python](https://www.python.org/doc/humor/#the-zen-of-python)

#### CHAPTER 2 An Array of Sequences
Sequence 分类
- types
    - container sequences: _list_, _tuple_, and _collections.deque_ can hold items of different types.
    - flat sequences: _str_, _bytes_, _bytearray_, _memoryview_, and _array.array_ hold items of one type
- mutability
    - mutable sequences: _list_, _bytearray_, _array.array_, _collections.deque_, and _memoryview_
    - immutable sequences: _tuple_, _str_, and _bytes_

尽量使用自带的一些方法
- try to use list comprehension (map, filter 后面了解)
- generator expressions: genexp
- 根据实际需要，可以自行定义 special method 的具体内容。

Tuples Are Not Just Immutable Lists
- \* argr 接受不定数量的变量
- Named Tuples: *collections.namedtuple*, 对 tuple 的每一个变量命名
- builtin function: *_fields*, *_make()*, *_asdict()*

Slicing
- Slices and Range Exclude the Last Item
- seq[start:stop:step], *seq.__getitem__(slice(start, stop, step))*
- ellipsis(...): 省略号
- \* operation with list can get unexpected result, [list]*3 get 3 same reference to the same inner list. 改变内部任何一个 list 中的数据，其他内部 list 对应位置数据也跟着改变。用循环就可以避免这种问题。
- +=, \*= in place function, 对 mutable 数据适用， 对 immutable 数据不适用。

A += Assignment Puzzler
```python
# 一个比较特殊的例子
t = (1, 2, [30, 40])
t[2] += [50, 60]
# the result ?
```
- Putting mutable items in tuples is not a good idea.

*list.sort* and the *sorted* Built-In Function
```python
fruits = ['grape', 'raspberry', 'apple', 'banana']
# 两种方法是不同的， 前者不改变 fruits 的顺序， 后者改变
sorted.fruits
fruits.sort()
```

Managing Ordered Sequences with bisect
* 习惯将函数作为参数的用法。
* Sorting is expensive, so once you have a sorted sequence, it’s good to keep it that way.

Memory Views (还有一些疑问)
* memorview class is a shared-memory sequence type


比较好的 Python Package:
* NumPy
* SciPy
* Pandas
* Blaze

Key Is Brilliant
* The key optional argument of list.sort, sorted, max, and min is a great idea.

##### 小结
- python 自带的 sequence 类型，可以分为 container sequence 和 flat sequence。前者只是保存 reference，后者会存储数据。根据数据是否可变可以分为 mutable sequence 和 immutable sequence。
- list 数据可以使用 listcomps，简洁，容易理解。 genexp 是每次迭代读取一个数据，会占用更少的内存，特别是在数据量很大时，genexp 效果很明显。
- tuple


#### CHAPTER 3 Dictionaries and Sets
dictcomps: 与 listcomps 很类似，尽量习惯使用
mapping types
- the keys must be ***hashable***: 
    - immutable types, including *frozen set*
    - A *tuple* is hashable only if all its items are hashable
    - *id()*  function, 查看内存地址

Handling Missing Keys
- try to use *setdefault*
- set *defaultdict*

Set
- set 的初始化: {3, 4}， 注意空值的特殊性 set()
- 善于使用 set 的 & | - 运算
- setcomps 的使用

---
### Python Tools


python单引号与双引号基本没区别，主要是可以方便在字符串里面使用单引号和双引号。  

#### PEP8
结合 PEP8 与当前代码的习惯, 确定适合自己的代码规范.  
##### 1.命名规范  
1.1 尽量保证统一风格，但是如果风格影响到效率，可以决定去改变。  
1.2 模块命名不要含_（下划线）  
1.3 大小写之类的  

##### 2.注释规范


##### 3.缩减规范


##### 4.logging规范  
4.1 尽量减少使用print， 改用logging解决问题。

4.2 logging配置需求

logging的几种类型

```
logging.info()
```

4.3 **try，except**  
 try except的疑问：  
 何时使用？  
 race conditions，loops, file handling, database communication, network access  
 使用try...except捕获错误还有一个巨大的好处，就是可以跨越多层调用，也就是说，不需要在每个可能出错的地方去捕获错误，只要在合适的层次去捕获错误就可以了。  
 
 raise是什么？   
 抛出错误，将错误抛给上一层去处理。  
 raise语句如果不带参数，就会把当前错误原样抛出。此外，在except中raise一个Error，还可以把一种类型的错误转化成另一种类型：
 
 记录错误: logging.exception(e)  
 同样是出错，但程序打印完错误信息后会继续执行，并正常退出。  
 捕获并抛出错误的处理方式相当常见。捕获错误目的只是记录一下，便于后续追踪。但是，由于当前函数不知道应该怎么处理该错误，所以，最恰当的方式是继续往上抛，让顶层调用者去处理。  

ValueError是什么？错误的一种类型，数值的错误。  
 
 exception是什么？异常，程序
 
assert：凡是用print来辅助查看的地方都可以用assert来查看。如果assert失败，会抛出AssertionError。Python编译时可以用-0参数来关闭assert。
 
对于调试来说，logging才是最值得考虑的。



1. **numpy 数据的先后顺序**  
    The default order in NumPy is to take the elements off the last axis first, then the second to last, back to the first axis.   
> [Index ordering and reshape in NumPy and MATLAB](https://bic-berkeley.github.io/psych-214-fall-2016/index_reshape.html)

2. **python 中super的用法**  
多继承的时候，一般会用到super。  
> [Python中多继承与super()用法](http://www.jackyshen.com/2015/08/19/multi-inheritance-with-super-in-Python/) - 申健  

3. **Pandas 的一些常用方法**
```python
pandas.loc[,]  # 通过columns名称来取数据
pandas.iloc[,]  # 通过index来取数据
```


```python
# numpy 保存为raw数据
image_8bit.astype('int8').tofile(filename + 'prep_data')     
```

#### 调试工具

* [pdb](https://docs.python.org/3/library/pdb.html): python 自带
* [pdbpp](https://github.com/jasonprogrammer/pdbpp): 与pdb完全兼容，更好用，支持自动补全和颜色高亮, 
* [ipdb](https://github.com/gotcha/ipdb): 支持自动补全





#### 问题记录

##### 1.压缩dicom解压
Python中使用不同的package可以解压不同的压缩方式，具体请参考：
- [Handling of compressed image data](https://pydicom.github.io/pydicom/stable/image_data_handlers.html)

Linux中可以安装GDCM工具来解压，具体参考:
- [Tool to convert DICOM to DICOM](http://gdcm.sourceforge.net/html/gdcmconv.html)


##### python opencv

1.弄清楚image的xy方向
- x: horizontal axis, width, cols
- y: vertical axis, height, rows


#### Python 数据存储


python 赋值，浅拷贝，深拷贝
直接赋值：其实就是对象的引用（别名）。

浅拷贝(copy)：拷贝父对象，不会拷贝对象的内部的子对象。

深拷贝(deepcopy)： copy 模块的 deepcopy 方法，完全拷贝了父对象及其子对象。

- [Python 直接赋值、浅拷贝和深度拷贝解析](http://www.runoob.com/w3cnote/python-understanding-dict-copy-shallow-or-deep.html)