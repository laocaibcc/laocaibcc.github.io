## Python 开发环境配置


目标：
- **项目隔离**：每个项目都单独创建一个可以独立运行的环境
- **用户可用性**：所有用户都是可用的，不需要用户自行配置环境
- **最少依赖库**：每个环境中，都是安装最少需要的库。最好库是可以链接到公用环境的库，避免重复安装


常见的开发环境配置工具
- virtualenv
- pipenv

<br>
<div STYLE="page-break-after: always;"></div>


### virtualenv

使用反馈：
- 每个项目需要单独安装，重复安装较多，浪费资源
- 仅个人用户可用，共享性不够
- 如何设定库的共享：包括项目之间，用户之间的共享

#### **安装 & 使用**

```sh
# pip 安装
pip install virtualenv

# 创建虚拟环境（名字自己定，此处为 venv）
virtualenv venv

# 指定 python 版本创建虚拟环境
virtualenv -p /usr/local/bin/python3.6 venv

# 激活虚拟环境（venv 为创建的虚拟环境名字）
source venv/bin/activate

# 关闭虚拟环境（进入虚拟环境后才有效）
deactivate

# 删除虚拟环境
rm -r /path/to/venv

# 安装项目依赖库
pip install python_lib
pip install -r requirements.txt
```


#### **问题与解决**

参考资料：
- [Python--Virtualenv简明教程](https://www.jianshu.com/p/08c657bd34f1)
- [virtualenv 虚拟环境安装](https://www.jianshu.com/p/2857638f039d)

<br>
<div STYLE="page-break-after: always;"></div>


### pipenv

使用反馈： 
- 安装 python 库的过程比较不顺畅
- 很久未更新了


#### **安装 & 使用**

```sh
# pip 安装
pip install pipenv

# 指定 python 版本安装
pipenv install --python 3.6  # 卡在此处，有 bug

# 安装库（由于 pipenv lock 很慢，建议安装库时，添加 --skip-lock，注明使用库的版本，不使用 lock）
pipenv install --skip-lock numpy==1.15.4
pipenv install -r requirements.txt
```

#### **问题与解决**

1.使用 ```pip3``` 安装，可能会遇到 ```pipenv: command not found```

解决办法： 
- （1）在 ```.bashrc``` 中添加 ```export PATH="$PATH:/usr/local/python3.6/bin"```; 
- （2）在 ```.bashrc``` 中添加 ```alias pipenv="python3 -m pipenv```

<br>

2.命令不会自动补全：

解决办法：
- 配置命令补全：在 ```.bashrc``` 中补充 ```eval "$(pipenv --completion)"```


参考资料：
- [pipenv 更优雅的管理你的python开发环境](https://segmentfault.com/a/1190000012837890)
- [pipenv使用指南](https://crazygit.wiseturtles.com/2018/01/08/pipenv-tour/)
- [Pipenv: Python Dev Workflow for Humans](https://pipenv-fork.readthedocs.io/en/latest/index.html)



<br>
<div STYLE="page-break-after: always;"></div>


### 其他