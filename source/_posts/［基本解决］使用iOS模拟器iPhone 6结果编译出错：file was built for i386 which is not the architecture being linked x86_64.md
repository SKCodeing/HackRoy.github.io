---
title: 使用iOS模拟器iPhone 6结果编译出错：file was built for i386 which is not the architecture being linked x86_64
date: 2017-10-17 11:06:37
tags: Xcode编译警告
---


Build Settings-》Build Active Architecture Only－》Debug的Yes改为No
结果编译出现警告了：
```
Target ‘Pods-QorosSales’ of project ‘Pods’ was rejected as an implicit dependency for ‘Pods_QorosSales.framework’ because its architectures ‘x86_64’ didn’t contain all required architectures ‘i386 x86_64’
```
如图：
![](https://www.crifan.com/files/pic/uploads/2016/05/Target-of-project-Pods-was-rejected-as-an-implicit-dependency-for-because-its-architectures-x86_.png)
【解决过程】
1.Architectures中添加i386和x86_64
![](https://www.crifan.com/files/pic/uploads/2016/05/add-x86_64-and-i386-for-architectures-of-xcode_thumb.png)
![](https://www.crifan.com/files/pic/uploads/2016/05/add-x86_64-and-i386-for-valid-architectures_thumb.png)
