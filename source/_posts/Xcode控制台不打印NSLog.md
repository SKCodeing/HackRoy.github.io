---
title: Xcode控制台不打印NSLog
date: 2017-10-11 13:39:25
tags: iOS
---
最近Xcode8发布了，发现Xcode8运行起来App后控制台打印出来一堆乱七八糟的Log，解决方法是

Product -> Scheme -> Edit Scheme -> Run -> Arguments -> Environment Variables

增加 "OS_ACTIVITY_MODE" 值为 "disable"，并勾选（注意如果真机运行的时候不打印NSLog，要取消勾选），重新run即可消失。所以我想是不是和某个环境变量的设置有关。
![](http://www.skyfox.org/wp-content/uploads/2016/09/49FBC898-072F-49DC-9311-2A36615A1446.jpg)