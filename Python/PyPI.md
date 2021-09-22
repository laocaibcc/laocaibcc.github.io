## Python PIP

- [pip (package manager)](https://en.wikipedia.org/wiki/Pip_(package_manager))
#### Python Package Manager (pip)

##### pip (Ubuntu) 安装
```
$ sudo apt-get install python-pip  # 安装pip
$ sudo apt-get install python3-pip  # 安装pip3
```

##### 使用 pip 安装 python package
```sh
$ pip install numpy # 安装numpy
$ pip install numpy==1.14  # 安装指定版本numpy
$ pip uninstall numpy  # 卸载numpy
$ pip install --upgrade numpy  # 升级numpy
```

##### pip2 or pip3  
pip2 或者 pip3 下载对应版本 python 的库。  
注：查看 pip 下载模块的路径可以通过 ```pip install``` 已安装的库，会提示已安装库的路径。
```sh
# pip3升级的正确操作
$ pip3 install --upgrade pip
```

##### pip 更改默认源
Python pip默认源是国外的，在国内会下载比较慢，可以换成国内源，能提速较多，国内源比较多。 
```sh
# 清华：https://pypi.tuna.tsinghua.edu.cn/simple  
# 豆瓣：http://pypi.douban.com/simple/  


# 临时使用
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple numpy  # 每次使用时指定下载源


# 永久使用
# 修改 ~/.pip/pip.conf(没有则创建)， 修改内容如下 (Linux)：
[global]
index-url = https://pypi.tuna.tsinghua.edu.cn/simple

# 在 user 目录中创建 pip 目录(C:\Users\xx\pip)，新建文件 pip.ini，内容如下 (Windows):
[global]
index-url = https://pypi.tuna.tsinghua.edu.cn/simple
```
参考资料：  
> [pip安装源更改与用户权限问题](https://blog.csdn.net/index20001/article/details/80627951)  

##### pip 指定安装路径
```sh
--target=/path/distpackage/  # 指定pip的安装路径
```

###### 获取某个项目中的 python 的依赖库

```python
# 1.install pipreqs 库
pip install pipreqs

# 2. 利用 pipreqs 库统计某个项目中使用到的库文件 
pipreqs /path/project/directory
```