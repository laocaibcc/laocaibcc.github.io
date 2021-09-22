
## Git 代码迁移

主要分两种情况：
- 不迁移log日志和分支
- 迁移log日志和分支（居多）

#### 迁移log日志和分支

分两种方法：
- 下载代码，然后push到新的代码库上
- 直接更改remote_url地址

##### 方法一
```sh
# 1. 从原地址 clone 一份裸版本代码
git clone --bare git://github.com/username/project.git

# 2. 在 Git 服务器上新建一个新项目，比如 new_project

# 3. 以镜像推送的方式上传到新项目上
cd project.git  
git push --mirror git@gitcafe.com/username/newproject.git

# 4. 删除原项目本地代码即可
```


##### 方法二
直接更改 remote url 的地址


具体可以参考：
- [Git仓库迁移](http://blog.adoregeek.com/2018/04/17/Git%E4%BB%93%E5%BA%93%E8%BF%81%E7%A7%BB/)
- [git仓库迁移的两种解决方案](http://www.cnblogs.com/ZhangRuoXu/p/6706530.html)

其中有关 --mirror 与 --bare 的区别可以参考
- [git clone --mirror和git clone --bare之间的区别是什么](http://landcareweb.com/questions/420/git-clone-mirrorhe-git-clone-barezhi-jian-de-qu-bie-shi-shi-yao)


