

## SSH基础

UPDATE: Nov.09, 2018<br>

Content
- 1.简介
- 2.SSH客户端基本用法

<br>


### 1. 简介


- ssh 生成密钥


- ssh 密钥的用法
  - ssh 访问服务器：需要将公钥（*.pub）上传到服务器，并进行将内容写入到 ```~/.ssh/authorized_keys```，本地在 ssh 中配置好私钥路径即可。（如果不显示指定，是否会读默认密钥？）
  - git 配置，实现免密登录：将公钥（*.pub）内容复制粘贴到 git 网站，本地需要配置密钥的路径。（如果不显示指定，是否会读默认密钥？）

- gitlab 与 SSH 访问是否有差别

- SSH 密钥与 GPG 密钥的差别

各种不同的密钥分析


参考资料：
- [1] [SSH 密钥登录](https://wangdoc.com/ssh/key.html)


