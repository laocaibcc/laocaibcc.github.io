## Gitlab 代码管理


### 目的

- 版本控制
- 协作开发
- 记录备份

> cheap local branching, convenient staging areas, and multiple workflows


<br>
<br>

### Git 工作流程

三种广泛应用的工作流程：
- Git flow（采用这种流程）
- Github flow
- Gitlab flow

参考资料：
- [Git 工作流程](http://www.ruanyifeng.com/blog/2015/12/git-workflow.html)
- [Git分支管理最佳实践](https://www.ibm.com/developerworks/cn/java/j-lo-git-mange/index.html)


#### Git-flow
git-flow 应该是目前流传最广的 Git 分支管理实践。git-flow 围绕的核心概念是版本发布（release）。

git-flow 流程中包含 5 类分支，分别是 master、develop、功能分支（feature）、发布分支（release）和 补丁分支（hotfix）。这些分支的作用和生命周期各不相同：master与develop是两个长期分支；功能分支（feature）、发布分支（release）和 补丁分支（hotfix）为短期分支，目的完成后即被删除。

<img src='https://nvie.com/img/git-model@2x.png' width=300>


参考资料：
- [A successful Git branching model](https://nvie.com/posts/a-successful-git-branching-model/)
- [git-flow 的工作流程](https://www.git-tower.com/learn/git/ebook/cn/command-line/advanced-topics/git-flow)
- [您必须知道的Git分支开发规范](https://juejin.im/post/5b4328bbf265da0fa21a6820)


#### Github flow

Github flow 是Git flow的简化版，专门配合"持续发布"。它是 Github.com 使用的工作流程。
它只有一个长期分支，就是master，因此用起来非常简单。

<img src='http://www.ruanyifeng.com/blogimg/asset/2015/bg2015122305.png'>


#### Gitlab flow

Gitlab flow 是 Git flow 与 Github flow 的综合。它吸取了两者的优点，既有适应不同开发环境的弹性，又有单一主分支的简单和便利。它是 Gitlab.com 推荐的做法。

- 上游优先
- 持续发布
- 版本发布

<img src='http://www.ruanyifeng.com/blogimg/asset/2015/bg2015122306.png' width=300>

#### 分支管理（Git-flow 流程）

项目中长期存在的两个分支:
- master
- develop

短期分支（其完成功能开发之后需要删除）:
- feature
- release
- hotfix

##### master 分支
- master 为主分支，也是用于部署生产环境的分支，确保master分支稳定性
- master 分支一般由develop以及hotfix分支合并，**任何时间都不能直接修改代码**

##### develop 分支
- develop 为开发分支，始终保持最新完成以及bug修复后的代码
- 一般开发的新功能时，feature分支都是基于develop分支下创建的

##### release 分支
- release 为预上线分支，发布提测阶段，会release分支代码为基准提测
- 测试完成后，需要合并到master与develop分支

##### feature/* 分支

- 开发新功能时，以develop为基础创建feature分支
- 分支命名: feature/ 开头的为特性分支， 命名规则: feature/user_module、 feature/cart_module

##### hotfix/* 分支

- 分支命名: hotfix/ 开头的为修复分支，它的命名规则与 feature 分支类似
- 线上出现紧急问题时，需要及时修复，以master分支为基线，创建hotfix分支，修复完成后，需要合并到master分支和develop分支


注意事项：
- master分支作为测试完成后发布的最终版本代码，不同版本用tag进行标记
- 各个分支的代码及时更新与同步
- 临时分支的代码，任务完成后要及时合并至长期存在分支（master与develop），然后删除


<br>
<br>

### 大文件管理

代码库的文件随着时间的增加本身就会不断增多，如果不时有大文件添加，代码库大小不可想象。深度学习中，模型文件跟踪记录很重要，需要利用一些工具对大文件进行管理。

- [Git Large File Storage (LFS)](https://git-lfs.github.com/)

注：
- 详细使用方法后面添加，需要测试一下


<br>
<br>

### Git 基础

#### 日志规范

编写良好的Commit messages可以达到3个重要的目的：
- 加快review的流程
- 帮助我们编写良好的版本发布日志
- 让之后的维护者了解代码里出现特定变化和feature被添加的原因

当前业界应用的比较广泛的是 [Angular Git Commit Guidelines](https://github.com/angular/angular.js/blob/master/DEVELOPERS.md#-git-commit-guidelines)，参照该格式规范，适当调整。

每次提交，Commit message 都包括三个部分：header，body 和 footer。

```
<type>(<scope>): <subject>
<body>
<footer>
```
##### Header
Header部分只有一行，包括三个字段：type（必需）、scope（可选）和subject（必需）。

###### type
用于说明 commit 的类别，只允许使用下面7个标识。
- feat：新功能（feature）
- fix：修补bug
- docs：文档（documentation）
- style： 格式（不影响代码运行的变动）
- refactor：重构（即不是新增功能，也不是修改bug的代码变动）
- test：增加测试
- chore：构建过程或辅助工具的变动

###### scope
scope，属于可选项，用于说明 commit 影响的范围，比如数据层、控制层、视图层等等，视项目不同而不同。如果你的修改影响了不止一个scope，你可以使用*代替。

###### subject
subject是 commit 目的的简短描述，不超过50个字符。

##### Body
Body 部分是对本次 commit 的详细描述，可以分成多行。

##### Footer（可选）
Footer 部分一般只用于以下情况：不兼容变动。


参考资料:
- [git commit 规范指南](https://segmentfault.com/a/1190000009048911)
- [GIT代码管理规范](https://www.jianshu.com/p/74268bf8c270)
- [Git 使用指南 培养使用Git的好习惯](https://www.jianshu.com/p/a980fc1eb626)


#### 一些有用的技巧
##### Git 的分区
区域名称 | 位置 | 用途
--- | --- | ---
工作区(workspace) | 当前PC目录 | 日常文本操作或者查看
版本库(repository) | 工作区里的隐藏目录 .git | 本地仓库，维持本地git各种管理，分支管理，暂存管理，备份管理等等
暂存区(stage) | 版本库里的东西 | git add命令添加到的就是stage分区，commit就是将暂存区的目标内容提交到当前本地仓库
远程仓库(remote) | 服务端的代码 | 有时候也叫服务库，作为开发组的同步基准

<img src='https://image-static.segmentfault.com/171/646/1716463609-5bf0fbfc7c3aa' width=400>

##### gitignore

控制不必要的文件上传，主要包括：
- 操作系统自动生成的文件
- 编译生成的中间文件、可执行文件等，也就是如果一个文件是通过另一个文件自动生成的，那自动生成的文件就没必要放进版本库，比如python编译产生的.pyc文件
- 带有敏感信息的配置文件，比如存放口令的配置文件
- 占用空间很大的文件

注：实际文件名为: ```.gitignore```

gitignore的语法可以参考：
- [Git中.gitignore的配置语法](https://www.jianshu.com/p/ea6341224e89)

##### git tag 

tag 用于版本标记，一般用于master与release分支。在利用 tag 对不同版本进行标记时，一般需要遵循语义化版本控制规范（Semantic Versioning）。
规范的概要如下：
> 版本格式：主版本号.次版本号.修订号，版本号递增规则如下：
> 1. 主版本号：当你做了不兼容的 API 修改，
> 2. 次版本号：当你做了向下兼容的功能性新增，
> 3. 修订号：当你做了向下兼容的问题修正。
>
> 先行版本号及版本编译信息可以加到“主版本号.次版本号.修订号”的后面，作为延伸。

为什么要有这套规范，就是为了避免软件管理的领域里存在的，称为“依赖地狱”的死亡之谷。
规范详情，可以参考:
- [语义化版本](https://semver.org/lang/zh-CN/)


git tag 的使用教程可以参考：
- [Git打标签与版本控制规范](https://juejin.im/post/5b0531c6f265da0b7f44eb8c)