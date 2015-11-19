---
title: "Git 多人协同的正确方式"
layout: post
category: 开发
tags: [Git]
excerpt: "Git比起svn，冲突的概率小了，多人协作更有效率，解决起冲突也更灵活。这篇日志不是讲Git的基本用法，主要想说一下在多人协作的iOS团队中如何正确的使用git，把冲突的概率降到最低"
---

###写在前面的废话
long long ago，在接触Git之前，代码版本管理一直用的svn，很少去开分支和merge代码。如果出现了冲突（冲突不可能避免），多半也是靠比较工具（Byond Compare）去手动合并代码解决冲突...(原谅我svn不会用😢)

后来，接触到了Git，与svn不同的是，git可以本地提交，本地做多个版本，在本地就可以做很多事情，最后把纯净的代码push到远程服务器上。代码冲突的概率小了很多，也不是完全不会冲突。

###git 冲突的根源
大家都会修改的文件而且频繁修改的文件，就会冲突!  
main storyboard  
工程配置文件  
公共xib文件  
……  

##解决办法

###从本地代码层面  
- controller尽量不要都定义在同一个storyboard，按业务分割成多个storyboard
- 如果不喜欢用storyboard，多用xib也是好的

###从Git使用方式
- 远程上多开几个分支: master(默认) develop 对应每个开发成员的分支
- 本地只在自己的分支开发
- 自己的分支只允许自己push到远程
- 合并代码在develop分支合并，再push到远程

###合并代码
1. 首先，切换到`develop`分支
2. `git pull`拉取最新代码
3. 假如你是小明，你的个人分支是`dev_xiaoming`,合并命令`git merge dev_xiaoming`
4. 本地解决冲突，再把`develop` 提交到远程
5. 每完成一个功能就提交一次。特别提醒：**不要在本地积累过多的修改**!!

###参考
1. [iOS开发中的Git流程](http://www.jianshu.com/p/87e34894a9f9)
