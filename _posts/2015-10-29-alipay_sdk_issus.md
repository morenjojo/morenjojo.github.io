---
title: "支付宝sdk 回调问题"
layout: post
category: 开发
tags: [iOS,SDK,Alipay]
excerpt: "在调试支付宝支付时遇到的，由于用的模拟器一直没有发现在真机上有问题..."
---

在调试支付宝支付时遇到的，由于用的模拟器一直没有发现在真机上有问题...

###问题
用模拟器调试支付宝支付，只能用内置webview完成支付操作，能够正常回调，一切都正常；

在真机上测试时，支付能够正常跳转到支付宝app，支付、扣款都正常，也能回到我自己的app，但是支付宝的sdk没有任何回调，app端没有任何响应了；

###解决办法
检查过代码后，发现支付宝sdk有个方法没用上
```
- (void)processOrderWithPaymentResult:(NSURL *)resultUrl
                      standbyCallback:(CompletionBlock)completionBlock;
```

文档注释  
`处理钱包或者独立快捷app支付跳回商户app携带的支付结果Url`

恍然大悟，原来是在处理传回的open url系统回调函数里没调用支付宝的这个方法；
修改自己app的代码，加上这个之后一切正常了；


