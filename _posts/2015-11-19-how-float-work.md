---
title: "0.1 + 0.2 = ?"
layout: post
categories: [develop,translation]
tags: [iOS,php,math]
excerpt: "如果0.1 + 0.2 = 0.3, 那么0.1 + 0.2 - 0.3 = ?"
---

[神奇的网站](http://0.30000000000000004.com/)  

![](http://7xo1be.com1.z0.glb.clouddn.com/img35.pic.jpg)  
#Floating Point Math
Your language isn't broken, it's doing floating point math. Computers can only natively store integers, so they need some way of representing decimal numbers. This representation comes with some degree of inaccuracy. That's why, more often than not, .1 + .2 != .3.  
> 你所用的编程语言并没有出错，它只是在进行浮点数运算。计算机天生只能存储整数，所以他们有自己的方式代表小数。这种方式的副作用是有一定的误差。这就是多半情况下，`.1 + .2 != .3`的原因所在。  
 
###Why does this happen?

It's actually pretty simple. When you have a base 10 system (like ours), it can only express fractions that use a prime factor of the base. The prime factors of 10 are 2 and 5. So 1/2, 1/4, 1/5, 1/8, and 1/10 can all be expressed cleanly because the denominators all use prime factors of 10. In contrast, 1/3, 1/6, and 1/7 are all repeating decimals because their denominators use a prime factor of 3 or 7. In binary (or base 2), the only prime factor is 2. So you can only express fractions cleanly which only contain 2 as a prime factor. In binary, 1/2, 1/4, 1/8 would all be expressed cleanly as decimals. While, 1/5 or 1/10 would be repeating decimals. So 0.1 and 0.2 (1/10 and 1/5) while clean decimals in a base 10 system, are repeating decimals in the base 2 system the computer is operating in. When you do math on these repeating decimals, you end up with leftovers which carry over when you convert the computer's base 2 (binary) number into a more human readable base 10 number.

> 道理非常简单。当你使用10进制的系统（就像我们正在用的），系统只能用这个系统主要的分解值（2和5）来表示分数。所以1/2, 1/4, 1/5, 1/8, 还有 1/10都可以准确的表示出来，因为他们的分母是10的分解值整数倍数。相反，1/3, 1/6, 和 1/7都是无限循环小数，因为他们的分母都是3或7的倍数。在二进制系统里，（或者基于2的倍数），只有一个分解因子2。所以你只能准确的表示分母是2的幂值的分数。二进制里面，1/2, 1/4, 1/8都是准确的小数值。然而，1/5 或者 1/10都是无限循环小数。所以，0.1 和 0.2 （1/10 和 1/5）在十进制的计算机系统里面是准确的小数，但在二进制里面是无限循环小数。当你在对这些无限循环小数进行数学运算时，把2进制数据转换为更可读的10进制数据时，你就会碰到多出来的小数位数参与运算的情况。

###注
本文翻译得到了 **老驴** 的校正，特别感谢！
