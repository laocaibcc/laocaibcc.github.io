## TensorFlow


目标：
- **项目隔离**：每个项目都单独创建一个可以独立运行的环境
- **用户可用性**：所有用户都是可用的，不需要用户自行配置环境
- **最少依赖库**：每个环境中，都是安装最少需要的库。最好库是可以链接到公用环境的库，避免重复安装





<br>
<div STYLE="page-break-after: always;"></div>


### TensorBoard


#### 1.TensorBoard 介绍

- 生成 Events 文件
- 2.查看 Events 文件

#### 2.远程服务器访问查看TensorBoard

```sh
本地终端登陆远程服务器
ssh -L 10086:127.0.0.1:8080 work@221.122.128.92 -p 31196

远程服务器中找到 tensorboard所在目录并运行
tensorboard --logdir ./tensorboard --port 8080

在本地浏览器中输入如下地址即可查看tensorboard结果
http://127.0.0.1:10086
```


参考资料：
- [1] [tensorboard 可视化详细](https://www.cnblogs.com/sienbo/p/11478628.html)
- [2] [在远程服务器下运行tensorboard，并在本地浏览器下查看](https://zhuanlan.zhihu.com/p/403439895)



