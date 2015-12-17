---
title: "iOS 面试题"
layout: post
categories: [develop]
tags: [iOS]
excerpt: "iOS面试题，为了面试别人和被别人面试，会不断更新"
---


#BLOCK
###在编写网络层代码时，用block是不是合适，应该怎么用，需要注意些什么?

- block很难追踪，难以维护

>我们在调试的时候经常会单步追踪到某一个地方之后，发现尼玛这里有个block，如果想知道这个block里面都做了些什么事情，这时候就比较蛋疼了。

- block会延长相关对象的生命周期

>block会给内部所有的对象引用计数加一，这一方面会带来潜在的retain cycle，不过我们可以通过Weak Self的手段解决。另一方面比较重要就是，它会延长对象的生命周期。

>在网络回调中使用block，是block导致对象生命周期被延长的其中一个场合，当ViewController从window中卸下时，如果尚有请求带着block在外面飞，然后block里面引用了ViewController（这种场合非常常见），那么ViewController是不能被及时回收的，即便你已经取消了请求，那也还是必须得等到请求着陆之后才能被回收。

>然而使用delegate就不会有这样的问题，delegate是弱引用，哪怕请求仍然在外面飞，，ViewController还是能够及时被回收的，回收之后指针自动被置为了nil，无伤大雅。


**`所以平时尽量不要滥用block，尤其是在网络层这里。`**

###Objective-C Blocks Quiz
[这里](http://blog.parse.com/learn/engineering/objective-c-blocks-quiz/)有关于Block的小测验  

###参考
- [iOS 面试基础题目](http://www.jianshu.com/p/4d7292741f53)
- [这些 iOS 面试基础题，你会么？](http://ios.jobbole.com/82858/)
- [iOS 面试大全从简单到复杂(简单篇)](http://www.jianshu.com/p/a2435b29875b)
- [百度 iOS 面试总结](http://ios.jobbole.com/82855/)
- [推荐：iOS开发面试题整理](https://mp.weixin.qq.com/s?__biz=MzA3NzM0NzkxMQ==&mid=402545546&idx=1&sn=11c05fbaa018f25f889486b7e33a64ce&scene=0&key=ac89cba618d2d976665200f1949ada2961faa673cca3a5d6997019e948c01f84e2f88a371d094ceb4559315c95376a58&ascene=0&uin=NjQ1NjQ1&devicetype=iMac+MacBookAir6%2C2+OSX+OSX+10.11.1+build(15B42)&version=11020201&pass_ticket=IEssflilCZxqf%2BSXHAfgY%2BYS%2BWX1OOw5Tv1iUa5pgYY%3D)