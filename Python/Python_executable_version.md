## python project 编译Linux的可执行版本

2017.11.18

### 1. 使用工具
pyinstaller

### 2. 安装方法
* 官网下载：http://www.pyinstaller.org/downloads.html
* pip方式下载：pip install pyinstaller

### 3. 编译方法
#### 3.1 编译main.py
```shell
$ pyinstaller main.py  # main.py是需要编译的主程序文件，后文中main同此
```
注：编译成功后会产生两个文件夹:``build``和``dist``，可执行的版本就在``dist``中。

##### 3.2 运行程序
在``/dist/main/``下运行输入 ``./main`` 就可以运行


### 4.遇到的问题及解决方案
#### 4.1 与 ``ImportError: No module named _cwt`` 相关的问题
``No module named xxx`` 问题一般是某个包没有被打包编译，解决办法是修改 ``main.spec`` 文件中的 ``hiddenimports``（``main.spec`` 文件是 ``pyinstaller main.py`` 编译后生成的），添加上该文件的具体路径。``_cwt`` 这个问题出现的比较多，应该是与python有关，不是与项目中使用的包相关。google一下就能够找到解决办法，具体解决方案如下：

```python
hiddenimports=[]  # 修改前
hiddenimports=['pywt._extensions._cwt']  # 修改后
```
完成之后，再重新编译，运行下面的命令
```sh
pyinstaller main.spec
```

后面遇到了类似的问题： ``ImportError: No module named _THCUNN``， 这个问题是与该项目具体使用的包有关，因此网上没有找到相关的答案。主要解决办法是找到名为 ``_THCUNN`` 的文件，通过搜索发现确实存在 ``_THCUNN.so`` 的文件，确定该文件路径为 ``torch/_thnn/_THCUNN.so`` 。因此在 ``hiddenimports`` 中添加的东西为：``torch._thnn._THCUNN``。之后别忘了重新编译：``pyinstaller main.spec``。  
因此，遇到 ``No module named xxx`` 问题时，修改 ``hiddenimports`` 是一个可以参考的解决思路。当然，并不确定是否所有类似的问题都能这样解决，这里只是提供一个解决思路。

#### 4.2 与 ``RuntimeError: Unable to find torch_shm_manager at /home/imaging/release_main/dist/main/torch/lib/torch_shm_manager`` 相关问题
这个问题比较清楚，就是没有找到某个文件。解决这个问题的方法也很直接，就是将需要的文件配置到指定的路径。将``torch``包复制到``/dist/main/``路径下，再次运行就可以了。  
注：或许可以通过设置相关参数的方式将需要的``torch``包导入，但是这方面的信息比较少，没有查找到。
附：如果需要``debug``，方便解决问题，可以将``main.spec``中的debug属性。
``debug=False`` 改为 ``debug=True``  
后续遇到了类似的问题：  
``tensorflow/contrib/util/tensorflow/contrib/framework/python/ops/_checkpoint_ops.so: cannot open shared object file: No such file or directory``  
用同样的方法即可解决。

#### 4.3 特殊问题

``Exception: Versioning for this project requires either an sdist tarball, or access to an upstream git repository. It's also possible that there is a mismatch between the package name in setup.cfg and the argument given to pbr.version.VersionInfo. Project name mock was given, but was not able to be found. [2103] Failed to execute script segm_main``

该问题好像不具有一般性，没有发现一些规律，只是找到了解决方案，如下：
```python
# 文件的首行插入
import os
# export pbr version for tensorflow user
os.environ["PBR_VERSION"]='3.0.1'  # 要去查询自己的版本
```

参考资料：  
https://github.com/pyinstaller/pyinstaller/issues/2883

### 5. 补充说明
- 上述所有的解决过程都是针对linux下的python projects，对于windows 下的python projects是否相同，并不确定，但可以参考解决思路。
- pyinstaller编译后，有些库可能由于不同机器下版本不同，需要重新导入。
- 实际上，pyinstaller的使用并不多，因此网上的资源比较少，遇到问题google上不容易找到解决方案，可以去pyinstaller的github，会有一些问题的解决方案，也可以发帖询问，在这里寻找答案更加具有针对性，具体网址：https://github.com/pyinstaller/pyinstaller/issues

