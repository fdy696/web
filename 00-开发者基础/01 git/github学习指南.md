# github学习指南

## 前置概念
### 什么是github？
略
### GitHub 与 Git 的关系

Git 是一款免费、开源的分布式版本控制系统，他是著名的 Linux 发明者 Linus Torvalds 开发的。说到版本控制系统，估计很多人都用过 SVN ，只不过 Git 是新时代的产物，如果你还在用 SVN 来管理你的代码，那就真的有些落伍了。


~~Linus 花了两周时间自己用 C 写了一个分布式版本控制系统，这就是 Git！一个月之内，Linux 系统的源码已经由 Git 管理了！牛是怎么定义的呢？大家可以体会一下。~~


github是一个用git做版本控制的项目托管平台。

### 本地仓库和远程仓库
  **本地仓库：**
  借助git工具，我们可以直接在本地创建一个git仓库（文件夹），这个仓库不需要联网，和github没有关系；初始化后git会记录这个文件夹(仓库)下的文件，内容的变动，在需要时可后退到指定版本。

  **远程仓库：**
  git解决了记录文件历史内容，以及文件修改合并等问题，但是在团队协作上，存在问题，需要网络把每个人的本地仓库，提交到线上，这样团队中的每个人就可以从线上平台clone协作文件，提交自己更新的内容。

  >自己在学习git时，刚开始没有区分git和github的区别，导致后面越学越乱，从入门到放弃。


### git基本概念

**1. 什么是Git？**

Git 是 Linux 发明者 Linus 开发的一款新时代的版本控制系统，那什么是版本控制系统呢？怎么理解？网上一大堆详细的介绍，但是大多枯燥乏味，对于新手也很难理解，这里我只举几
个例子来帮助你们理解。
熟悉编程的知道，我们在软件开发中源代码其实是最重要的，那么对源代码的管理变得异常重要：比如为了防止代码的丢失，肯定本地机器与远程服务器都要存放一份，而且还需要有一套机制让本地可以跟远程同步；又比如我们经常是好几个人做同一个项目，都要对一份代码做更改，这个时候需要大家互不影响，又需要各自可以同步别人的代码；又比如我们开发的时候免不了有bug，有时候刚发布的功能就出现了严重的bug，这个时候需要紧急对代码进行还原；又比如随着我们版本迭代的功能越来越多，但是我们需要清楚的知道历史每一个版本的代码更改记录，甚至知道每个人历史提交代码的情况；等等等类似以上的情况，这些都是版本控制系统能解决的问题。所以说，版本控制是一种记录一个或若干文件内容变化，以便将来查阅特定版本修订情况的系统，对于软件开发领域来
说版本控制是最重要的一环，而 Git 毫无疑问是当下最流行、最好用的版本控制系统。

**2. Git 安装**

上面说了，Git 是一个版本控制系统，你也可以理解成是一个工具，跟 Java 类似，使用之前必须得先下载安装，所以第一步必须要安装，我用的是 Mac ， Mac 上其实系统自带 Git 的，不过这里统一提供一下各平台的安装方式，这部分就不过多介绍，相信大家这里搞的定。


[参考链接🔗](http://wiki.jikexueyuan.com/project/git-tutorial/install-git.html)

### git常用命令

```js
git init  //创建一个git仓库

git status //检查仓库变化
git add a.txt//把a.txt添加到暂存区域
git add . //把当前文件夹下所有变化的文件添加到暂存区
git add xx命令可以将xx文件添加到暂存区，如果有很多改动可以通过 git add -A .来一次添加所有改变的文件。
注意 -A 选项后面还有一个句点。 git add -A表示添加所有内容， git add . 表示添加新文件和编辑过的文件不包括删除的文件; git add -u 表示添加编辑或者删除的文件，不包括新添加的文件。
git rm achecd  //把暂存区文件移除
git commit -m 'first commit' //把暂存区域文件添加到仓库

git branch //查看当前仓库下所有分支，前面有*代表当前所在分支
git branch ａ　//新建a分支
git checkout a //切换到a分支
git checkout -b a //创建并切换到a分支
git merge dev //合并dev分支到master
git branch -d a   //删除已合并的dev分支
git branch -D a  //强制删除a分支·
git log //查看所有commit描述，相当于历史纪录
git reset --hard commit_id  // 版本回退
```


## 远程仓库
将本地仓库和远程仓库连接主要由两种方式

- 1.先在github建立项目，然后gitclone到本地，好处是无需git init和关联本地和线上仓库。
例子：
```js
//1.克隆到本地，也就是命令行所在的目录
git clone git@github.com:fdy696/learngit.git
//2.本地修改内容

//3.存放到暂存区
git add ~
//4.添加到仓库
git commit -m 'xxx'
//把master分支添加到远程仓库
git pull origin master
git push origin master
// 强制本地覆盖远程仓库
git push -f
// 版本回退


```
- 2.将本地仓库连接到远程仓库
关联本地已有项目 如果我们本地已经有一个完整的 git 仓库，并且已经进行了很多次 commit，这个时候第一种方法就不适合了。假设我们本地有个 test2 的项目，我们需要的是在 GitHub 上建一个 test 的项目，然后把本地test2 上的所有代码 commit 记录提交到 GitHub 上的 test 项目。
第一步就是在 GitHub 上建一个 test 项目，这个想必大家都会了，就不用多讲了。第二步把本地 test2 项目与 GitHub 上的 test 项目进行关联，切换到 test2 目录，执行如下命令：
```js
git remote add origin git@github.com:stormzhang/test.git
```
## 分支branch
```js
git branch dev  //创建一个指向master的开发分支，名字叫dev.
git checkout dev //切换到dev分支
git checkout -b a //创建并切换到a分支
//在dev分支下做一些操作
//git checkout master
//git marge dev合并dev分支到master.

```
## 远程仓库冲突及版本回退
```js
git log  // 查看提交历史纪录
q // 退出git log


// commit 9843dbb2d0ba74e44060ebc23f7155aa2c83a448
// Author: fengyong <fengyong@xdstar.net>
// Date:   Mon Dec 24 10:39:25 2018 +0800
// git远程强制命令

git reset --hard HEAD^ //返回上一版

git reset --hard commit版本号  //例如9843dbb2d0ba74e44060ebc23f7155aa2c83a448


```
## 提交冲突
```
git stash  // 把当前代码保存起来

git pull  // 同步线上

git stash pop // 把存起来的代码加入本地

```


### 场景：你是第一天来公司上班的，项目代码托管在GitLab，项目地址：git@lab.com:org/project.git,现在有一处代码需要你修改。请下完成此项任务中，与git/gitlab相关的操作步骤。

第一步：生成公钥
$> ssh-keygen -t rss -C zhangsan@abc.com

第二步：拷贝公钥到gitlab
```
cd ~/.ssh
ls
cat xxx

```

第三步：
```
$> git config —global user.name zhangsan

$> git config —global user.email zhangsan@abc.com
```
第四步：$> git clone git@lab.com:org/project.git

第五步：$> git checkout -b project-20170227-zhangsan-bugfix

第六步：修改代码

第七步：git status

第八步：git add .

第九不：git commit -am ‘bugfix’

第八步：git push --set-upstream origin project-20170227-zhangsan-bugfix
