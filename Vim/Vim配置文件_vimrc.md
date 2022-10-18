## Vim

<font color=#FF0000>问题与改进</font>  


youcompleteme 是否能够设置哪些自动补全，哪些不需要。



一个比较不错的vim教程，早日完成
> [简明 VIM 练级攻略](https://coolshell.cn/articles/5426.html) - 陈皓  

vim 插件配置
- [Vim与Python真乃天作之合](http://codingpy.com/article/vim-and-python-match-in-heaven/)
- [Vim中编辑Python的利器](http://blog.guoyb.com/2016/07/17/python-vim/)

### 1. vim的配置  
步骤：配置.vimrc  → 配置插件  
(1).vimrc是vim的profile，可以根据自己的需求调整与设置。  
Linux建议在个人home目录下配置
```sh
# vim个人配置文件及插件配置
$ cp .vimrc ~/  # 将配置文件复制到个人home目录下
$ source ~/.vimrc  # 使配置文件生效(Linux)
$ git clone https://github.com/gmarik/vundle.git ~/.vim/bundle/vundle  # 安装vundle，插件管理器
$ cp .vimrc.bundles ~/  # 将插件的配置文件也放在home目录下

# 插件安装(两种方式)
:BundleInstall  # 打开vim之后，在vim中运行该命令
$ vim +BundleInstall +qall  # shell中运行

# 可能注意的地方
YouCompleteMe可能需要重新安装
```
详细配置可以参考：
> [Vim配置、插件和使用技巧](https://www.jianshu.com/p/a0b452f8f720) - Sam_Lau  
> [vim配置文件和插件管理](http://www.cnblogs.com/wxw16/p/6259292.html) - wuxiwei  
> [vim插件管理器：Vundle的介绍及安装（很全）](https://blog.csdn.net/zhangpower1993/article/details/52184581) - zhangpower1993   


**常见插件**  
>插件管理器: [vundle](https://github.com/VundleVim/Vundle.vim) - github  
>树形目录插件: NerdTree   
>快速补全: YouCompleteMe  
>跳转插件: ctrlp


### 2. vim快捷键记录（实践）
#### 2.1 光标移动
```sh
# 基本操作
h,j,k,l  # 左，上，下，右
H  # 跳到屏幕顶部
M  # 跳到屏幕中间
L  # 跳到屏幕底部
f  # 向后查找，例:fa 查找字符a，光标跳转到字符a处
F  # 向前查找
0  # 调到行首
$  # 调到行末
ctrl+o  # 光标调到上一位置
ctrl+i  # 光标跳到下一次位置（与上面配合使用）

# 调整页面
ctrc-f  # 向下翻页
ctrl-b  # 向上翻页
z. or zz  # 将当前行置为屏幕的中央
zt  # 将当前行置为屏幕的顶部
zb  #  将当前行置为屏幕的底部

# 程序员常用移动命令
%  # 匹配括号移动，包括 (, {, [.
*, #  # 匹配光标当前所在的单词，移动光标到下一个（或上一个）匹配单词（*是下一个，#是上一个）
```


更多可以参考：  
> [Vim中如何快速进行光标移动？](http://harttle.land/2015/11/07/vim-cursor.html) - Harttle   


垂直选择，可以参考：
- [技巧：Vim 的纵向编辑模式](https://www.ibm.com/developerworks/cn/linux/l-cn-vimcolumn/index.html)


```
# 标记跳转(为什么注释的格式与之前不一样)
ma  # set mark a at current cursor location
'a  # jump to line of mark a (first non-blank character in line)
`a  # jump to position (line and column) of mark a
d'a  # delete from current line to line of mark a
d`a  # delete from current cursor position to position of mark a
c'a  # change text from current line to line of mark a
y`a  # yank text to unnamed buffer from cursor to position of mark a
:marks # list all the current marks
:marks aB # list marks a, B
```

>[Using marks](http://vim.wikia.com/wiki/Using_marks)


#### 2.2 字符编辑  

删除，复制，粘贴，替换：

```
y  # 复制
d  # 删除
r  # 替换，只替换当前字符
s  # 替换当前字符并进入insert mode
yy  # 复制一行
d$  # 删除光标至末尾
d0  # 删除光标至首字符

u  # 撤销
ctrl+r  # 前进（与上面配合使用）

# in visual mode
U  # for uppercase
u  # for lowercase. 
~  # To swap all casing

gU<motion>  # motion uppercase
gu<motion>  # for lowercase
```

命令使用：
```sh
:%s/old/new/gc  # 全局查找并替换，需要确认
:%s/word//gn  # 统计字符数量
```

#### 2.3 窗口调整
同时显示多个文件：
```sh
:split  # 水平划分
:vsplit  # 垂直划分

ctrl+w+方向键  # 切换到前／下／上／后一个窗格
ctrl+w+h/j/k/l  # 同上
ctrl+ww  # 依次向后切换到下一个窗格中
```


#### 2.4 整体调整
vim多行整体偏移

<font color=#FF0000>多行移动需要了解哈</font>  
```
7gg4<<  # 这个需要研究
```
v进入可视化，然后<或者>实现做左移或右移

对折叠基本操作（当前光标所在之折叠）:
```
za  # 切换折叠状态
zc  # 关闭折叠，就是折叠起来
zd  # 删除折叠
```



#### 2.9 其他操作
以普通用户进入，但是想保存read only file的解决办法。
```
:w !sudo tee %
```

更多请阅读：
> [以普通用户启动的Vim如何保存需要root权限的文件](http://feihu.me/blog/2014/vim-write-read-only-file/) - feihu  



### 3. 问题记录

##### 1.安装插件时错误：  
youcompleteme unavailable, no module named future
git submodule update --init --recursive

参考资料：  
https://github.com/Valloric/YouCompleteMe/issues/

##### 2.The ycmd server SHUT DOWN (restart with ':YcmRestartServer'). YCM core library not detected; you need to compile YCM before using it. Follow the instructions in the documentation.  

参考资料：  
https://github.com/Valloric/YouCompleteMe#full-installation-guide

##### 3.windows 与 linux 不同系统之间的文件乱码  
解决方案：  
- 1.找到vim的配置文件。linux与windows下vim的配置文件位置不同，一般windows下vim（准确的说是gvim）的配置文件"C:\ProgramFiles\Vim\_vmrc"。linux的一般在/usr/share/vim/vimrc（系统的），或者/home/username/.vimrc（用户的）。这里不详细介绍配置文件相关的知识。下面这篇文章给出了比较详细的说明：  
http://easwy.com/blog/archives/where-is-vimrc/
- 2.修改文件编码格式。linux下的文件编码格式为utf-8，而windows下的格式为cp936，因此我们需要添加一些语句设定。
```sh
# windows下：
set encoding=cp936 fileencodings=ucs-bom,utf-8,cp936

# linux下：
set encoding=utf-8 fileencodings=ucs-bom,utf-8,cp936
```
encoding是设置该操作系统下的编码格式，而fileencodings是在前者符合的前提下，从前往后探测比较，如果合适，就用该种编码格式打开。该排列方式是参照了网友滇狐的推荐的顺序，主要依据是编码的严格程度。
set fileencodings=ucs-bom,utf-8,cp936,gb18030,big5,euc-jp,euc-kr,latin1

关于vim中文件的编码格式可以参考下面文章具体了解：  
http://edyfox.codecarver.org/html/vim_fileencodings_detection.html

在解决该方案时参考了以下文章：  
http://blog.csdn.net/xmyzlz/article/details/8595276

- 2015.12.17

