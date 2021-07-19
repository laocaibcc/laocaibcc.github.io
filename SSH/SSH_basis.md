

## SSH基础

UPDATE: Nov.09, 2018<br>
Author: laocai

Content
- 1.简介
- 2.SSH客户端基本用法

<br>


### 1. 简介

#### 什么是SSH？

> "Secure Shell（安全外壳协议，简称SSH）是一种加密的网络传输协议，可在不安全的网络中为网络服务提供安全的传输环境." - [Secure Shell](https://zh.wikipedia.org/wiki/Secure_Shell)

SSH，字面意思是安全的shell，但SSH并不是一种shell，只是创建了一个通道在远程服务器上运行 shell。SSH是客户端/服务器的体系结构。一般来说，它具有下面几种特点：
- 身份验证
- 加密性
- 完整性

SSH实际上并不是一种完全安全的解决方案，但是目前为止似乎也还没有完整安全的解决方案。


#### SSH的用途

SSH可以有很多用途，一般来说，我们经常用来：
- 远程登录
- 文件传输
- X11连接
- 端口转发

> "SSH的经典用途是登录到远程电脑中执行命令。除此之外，SSH也支持隧道协议、端口映射和X11连接。借助SFTP或SCP协议还可以传输文件。" - [Secure Shell](https://zh.wikipedia.org/wiki/Secure_Shell)


#### 常见的术语

使用SSH时可能遇到一些名词，为避免混淆，简单介绍一下：
- [SSH](https://zh.wikipedia.org/wiki/Secure_Shell): 通用的术语，泛指SSH协议或者相关软件。
- SSH-1: SSH协议版本1。
- SSH-2: SSH协议版本2。
- SSH1: SSH设计者Tatu Ylönen最初实现的软件版本，基于SHH-1协议。（Tatu Ylönen后面成立了SSH Communications Security Corp.）
- SSH2: SSH Communications Security Corp.的SSH产品，基于SSH-2协议。
- [Open SSH](https://www.openssh.com/): SSH协议的开源实现版本，是OpenBSD项目的产品。 1、2 协议均有实现。OpenSSH是最流行的SSH实现，是大量操作系统的默认组件。
- [SFTP](https://zh.wikipedia.org/wiki/SSH%E6%96%87%E4%BB%B6%E4%BC%A0%E8%BE%93%E5%8D%8F%E8%AE%AE): SSH文件传输协议。
- [SCP](https://zh.wikipedia.org/wiki/%E5%AE%89%E5%85%A8%E5%A4%8D%E5%88%B6): 安全复制，基于SSH协议进行的文件传输。
- ssh（全部小写）: 远程登录的命令, 类似的还有sftp, scp, sshfs等

<br>


### 2. SSH客户端基本用法

#### SSH远程登录

SSH远程登录，通常使用客户端程序进行登录，一般只需要填写账户，密码和端口等。SSH客户端程序有很多，比如MobaXterm, PuTTY, Xshell等。常用SSH客户端的比较可以参考:
- [SSH客户端比较](https://zh.wikipedia.org/wiki/SSH%E5%AE%A2%E6%88%B7%E7%AB%AF%E6%AF%94%E8%BE%83)

 除了客户端程序，Linux和Unix系统等操作系统是默认安装OpenSSH程序的，可以使用命令行直接登录（实际上，通过配置文件，使用命令行会更便捷）。

```sh
# 命令行登录
$ ssh user@host  # 登录主机

# 例子: 用户tux通过ssh登录111.111.111.1服务器，端口为1111
$ ssh tux@111.111.111.1 -p 1111

# 常见的参数(参数顺序不影响)
-p  # 端口号，如果端口号为默认端口（22），则不用添加，(p为小写)
-i  # 密钥文件（如果登录方式为密钥登录）
-X  # 使用X11 
-l  # 用户名，可以用@方式省略，现在很少用
-v  # debug 信息
```

#### 基于SSH的文件传输
基于SSH协议的文件传输主要有两种: **SFTP**和**SCP**。
##### SFTP
> "SSH文件传输协议（英语：SSH File Transfer Protocol，也称Secret File Transfer Protocol，中文：安全文件传送协议，英文：Secure FTP或字母缩写：SFTP）是一数据流连线，提供文件访问、传输和管理功能的网上传输协议。" - [SSH文件传输协议](https://zh.wikipedia.org/wiki/SSH%E6%96%87%E4%BB%B6%E4%BC%A0%E8%BE%93%E5%8D%8F%E8%AE%AE)

很多SSH客户端程序远程登录时默认建立了SFTP连接，不需要另外连接。

SFTP命令行用法
```sh
# 最常见的用法
$ sftp -P xxxx user@host  # 建立SFTP连接

# 常见参数（有文件路径时，这些参数需要放在文件路径之前）
-P  # 端口号, 如果端口号为默认端口（22），则不用添加，(P为大写)
-i  # 密钥文件（如果登录方式为密钥登录）

# 直接利用sftp下载文件（这种用法目前用的比较少了）
$ sftp user@host:/remote/path/file  # 从远程服务器复制文件到本地

# 建立sftp连接后，最常用的两个命令
get  # 从远程服务器文件下载至本地
put  # 把本地文件上传至远程服务器
# 具体用法，文件夹路径前加上: -r
get /remote/path/sourcefile /local/targetpath/
put /local/path/sourcefile /remote/targetpath/

# 建立sftp连接后，还有很多其他命令可以使用，类似shell
bye  # 结束连接, exit也可以
ls, cd, pwd, mkdir, rmdir, delete等 # 针对远程服务器的操作
lls，lcd等  # 针对本地的操作，功能与ls, cd同
```

##### SCP

> "安全复制（英语：Secure copy，缩写SCP）是指在本地主机与远程主机或者两台远程主机之间基于Secure Shell（SSH）协议安全地传输电脑文件。[1]“SCP”通常指安全复制协议或者程序本身。" - [安全复制](https://zh.wikipedia.org/wiki/%E5%AE%89%E5%85%A8%E5%A4%8D%E5%88%B6)  

SCP文件传输通常需要其他的客户端，连接方式与SSH基本一致: 账户，密码和端口等。  

SCP命令行用法
```sh
$ scp /local/path/sourcefile user@host:/remote/targetpath/  # 复制文件到主机
$ scp user@host:/remote/path/sourcefile /local/targetpath/  # 从主机复制文件

# 常见参数(注意，这些参数需要放在文件路径之前)
-P  # 端口号, 如果端口号为默认端口（22），则不用添加，(P为大写)
-i  # 密钥文件（如果登录方式为密钥登录）
-r  # 文件夹
```

##### SFTP与SCP比较

SFTP与SCP的命令行文件传输方法有些差别，SCP功能比较单一，基本只能用来文件传输，而SFTP的功能较多。

协议 | 速度 | 安全 | 功能 | 大文件传输 | 断点续传 | 其他
--- | --- | --- | --- | --- | --- | ---
SFTP | 慢 | 较安全 | 较多 | 支持 | 支持
SCP | 快 | 较安全 | 单一 | 支持 | 不支持


<br>
<br>

##### 参考资料
- 《SSH 权威指南》
- [Secure Shell](https://zh.wikipedia.org/wiki/Secure_Shell)
- [Open SSH](https://www.openssh.com/)
- [SSH客户端比较](https://zh.wikipedia.org/wiki/SSH%E5%AE%A2%E6%88%B7%E7%AB%AF%E6%AF%94%E8%BE%83)
- [SSH文件传输协议](https://zh.wikipedia.org/wiki/SSH%E6%96%87%E4%BB%B6%E4%BC%A0%E8%BE%93%E5%8D%8F%E8%AE%AE)
- [安全复制](https://zh.wikipedia.org/wiki/%E5%AE%89%E5%85%A8%E5%A4%8D%E5%88%B6) 
- [Logging In to a Remote System to Copy a File (sftp)](https://docs.oracle.com/cd/E26502_01/html/E29001/remotehowtoaccess-14.html)
- [SCP vs SFTP - 5 Key Comparisons](https://www.jscape.com/blog/scp-vs-sftp)
