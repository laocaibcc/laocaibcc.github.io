
## Git 代码迁移

主要分两种情况：
- 1.不迁移代码提交日志和分支：直接下载代码即可，比较简单。
- 2.迁移代码提交日志和分支

### 迁移代码提交日志和分支

通常，代码迁移是希望将所有的记录和分支都保留，这样才能达到代码管理的目的，能够快速的回退到指定版本。
一般可以有两种方法：
- 1.下载代码，然后 push 到新的代码库上：**已经验证有效**。
- 2.直接更改 remote_url 地址：**暂未验证**。

**方法 1**
- 下载代码，然后 push 到新的代码库上。
```sh
# 1. 从原地址 clone 一份裸版本代码
git clone --bare git://github.com/username/project.git

# 2. 在 Git 服务器上新建一个新项目，比如: new_project

# 3. 以镜像推送的方式上传到新项目上
cd project.git  
git push --mirror git@gitcafe.com/username/new_project.git

# 4. 删除原项目本地代码即可
```

**方法 2**
- 直接更改 remote url 的地址



参考资料：
- [1] [Git仓库迁移](http://blog.adoregeek.com/2018/04/17/Git%E4%BB%93%E5%BA%93%E8%BF%81%E7%A7%BB/)
- [2] [git仓库迁移的两种解决方案](http://www.cnblogs.com/ZhangRuoXu/p/6706530.html)
- [3] [git clone --mirror和git clone --bare之间的区别是什么](http://landcareweb.com/questions/420/git-clone-mirrorhe-git-clone-barezhi-jian-de-qu-bie-shi-shi-yao)

