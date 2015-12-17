---
title: "ReactiveCocoa[翻译]"
layout: post
categories: [develop,translation]
tags: [iOS]
excerpt: "对ReactiveCocoa官方文档的翻译"
---

ReactiveCocoa (RAC)是一个Cocoa框架库，灵感来自于[函数式响应编程](https://en.wikipedia.org/wiki/Functional_reactive_programming)。它为合成、转换按时间变化的数据流提供了API。  

1. [介绍](#简介)
2. 例子：在线搜索
3. Objective-C 和 Swift
4. ReactveCocoa与Rx（Microsoft’s Reactive Extensions）的关系？
5. 开始实践

如果你已经对`函数响应式编程`有所了解，或者已经了解`ReactveCocoa`是什么，你可以直接把仓库中[Documentation](https://github.com/ReactiveCocoa/ReactiveCocoa/tree/master/Documentation)目录下的内容拿出来深入了解RAC的运行机制。然后直接从文档中学到更多api的用法。  

如果你遇到了问题，请从相关讨论区中（[GitHub issues](https://github.com/ReactiveCocoa/ReactiveCocoa/issues?q=is%3Aissue+label%3Aquestion+)或者[Stack Overflow](http://stackoverflow.com/questions/tagged/reactive-cocoa)）查找是否有类似的问题。如果没有，请随便给我们提新的issue。

## 简介
ReactiveCocoa灵感来自于[函数式响应编程](https://en.wikipedia.org/wiki/Functional_reactive_programming)。RAC提供了`Signal`和`SignalProducer`类型的事件流来不断的传值，而不是用变量来记录和改变值。


