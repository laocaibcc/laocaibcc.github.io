
## Linux 用户权限管理


TODO
- [ ] 权限说明
- [ ] 分组管理
- [ ] 添加保护的文件如何删除

### 1. 用户和分组

chown


参考资料：
- [Linux 高级编程 - 有名管道 FIFO](https://dlonng.com/posts/fifo)


<br>

### 1. 文件基本属性

在 Linux 中，一切都是文件（文件夹也是一种特殊的文件）。了解文件的基本属性。在 Linux 中我们可以使用 ```ls -l``` 或者 ```ll``` 命令来显示一个文件的属性以及文件所属的用户和组。

```sh
# ll 或 ls -l 通常可以看到下面的信息
drwxr-xr-x  8 root root 4096 Jun  3 15:16 lib/
lrwxrwxrwx  1 root root    9 Mar 13  2018 man -> share/man/
...
```

第一列，10个字符，类似 ```drwxr-xr-x```。
字符位置 | 说明
--- | ---
第1位 | 文件类型 
第2-4位 | 所属用户权限
第5-7位 | 所属组别用户权限
第8-10位 | 其他用户权限
 |  |  | 

#### 1.1 文件类型说明

Linux 中的文件具体来说有以下几种类型：

符号 | 文件类型 | 说明
--- | --- | ---
\- | 普通文件 | 最多的一种文件类型, 包括 纯文本文件(ASCII)；二进制文件(binary)；数据格式的文件(data);各种压缩文件。
d | 文件夹（或目录） | 在 Linux 系统中，文件夹也是一种文件。
l | 链接文件 | 对于链接文件，剩余的文件属性总是 "rwxrwxrwx"，这些都是虚拟值。真正的文件属性是指链接所指向文件的属性
b | 块设备文件 | 即存储数据以供系统存取的接口设备，简单而言就是硬盘
c | 字符设备文件 | 即串行端口的接口设备，例如键盘、鼠标等等
s | 套接字文件 | 这类文件通常用在网络数据连接。可以启动一个程序来监听客户端的要求，客户端就可以通过套接字来进行数据通信
p | 管道文件 | 一种特殊的文件类型

注：
- b, c, s, p 四种文件都是伪文件，实际上是不占用磁盘空间的。


#### 1.2 文件权限说明

从之前的说明可以看出，文件属性的第2-10位都是对文件权限的描述。只不过，2-4位，5-7位，8-10位分别独立成为一组，每组都是用 ```rwx``` 表示文件的权限，其具体含义如下：

字符 | 权限说明 
--- | ---
r | 允许打开并读取文件内容
w | 允许写入文件内容或截断文件。但是不允许对文件进行重命名或删除，重命名或删除是由目录的属性决定的
x | 允许将文件作为程序来执行，使用脚本语言编写的程序必须设置为可读才能被执行

文件权限的表示

字符表示 | 二进制 | 10进制
--- | --- | ---
--- | 000 | 0 
--x | 001 | 1
-w- | 010 | 2
-wx | 011 | 3
r-- | 100 | 4
r-x | 101 | 5
rw- | 110 | 6
rwx | 111 | 7

修改权限：
- chmod 修改用户权限


参考资料：
- [Linux 文件基本属性](https://www.runoob.com/linux/linux-file-attr-permission.html)
- [Linux: Linux的文件类型及查看文件类型的方法](https://www.cnblogs.com/yongdaimi/p/12573298.html)

---

### 其他

```sh
$ cat  /etc/passwd # 查看所有用户的home目录和shell类型, 可以用grep查找特定用户信息

$ sudo useradd -d /home/testuser -m testuser  # 创建testuser账户及相应的home目录  
$ sudo passwd testuser # 给已创建的用户testuser设置密码

# 修改用户的shell类型，两种方式
# (1)修改 /etc/passwd 文件中用户的shell类型
# (2)使用usermod命令进行更改, usermod -s shell类型 用户名
$ sudo usermod -s /bin/bash username

# 群组管理
/etc/group  # 群组配置文件

$ usermod -G group user  # 将用户user添加到group群组（第二群组，不是默认群组）
$ usermod -g group user  # 将用户user添加到group群组（基础群组，默认群组）
$ usermod -a -G group user  # 用户添加群组
$ groupmod -n new-name current-name  # 修改用户名称
```

##### 2. 用户添加sudo权限，以及添加账号
修改/etc/sudoers文件即可获得sudo权限  

```sh
$ chmod u+w /etc/sudoers  # 增加写权限
$ sudo vim /etc/sudoers  # 打开并修改文件/etc/sudoers

# 在文件的root ALL=(ALL) ALL 行下添加   
username ALL=(ALL) ALL  # 添加sudo权限

$ chmod u-w /etc/sudoers  # 去掉文件写权限，保证安全性
```


#### 默认权限修改

- umask 设置权限
- ACL 设置权限

```sh
# ubuntu 修改默认 umask 文件
sudo gedit /etc/login.defs
```

<font color=#FF0000>是否还有其他更加安全的方式？</font>  