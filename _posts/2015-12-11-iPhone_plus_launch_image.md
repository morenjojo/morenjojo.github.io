---
title: "iPhone 6 Plus启动图适配问题"
layout: post
category: develop
tags: [iOS]
excerpt: "最近遇到的一个奇葩问题，6p启动图总是用6的素材，状态栏尺寸也是拉伸的，着实费了一番脑力才fix了"
---

###问题的现象

同事的6p，启动app时展示的启动页面总是模糊的，而且顶部的状态栏是大版本的，跑来说是适配没做好，让赶紧查查原因改一下；

###问题的解决
一般遇到这种，我第一反应是没有适配好启动图尺寸就会这样；可怎么查代码，查图片素材都没有问题，用模拟器跑了也都正常。百度谷歌搜了很久，也都没有类似的情况；无果；

###事实的真相
呵呵哒，请相信自己的代码没有问题，工程设置都没问题；是6p开启了`“放大模式”`，在设置中关掉一切恢复正常!
