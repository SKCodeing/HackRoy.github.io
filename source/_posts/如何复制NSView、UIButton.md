---
title: 如何复制NSView、UIButton
date: 2017-11-02 15:32:08
tags: ios
---
场景:

1. 一般我们使用ib设计器设计好一个NSView之后(通常用NSView组合多个控件), 需要复制一个NSView来重新布局显示.

如果调用[view copy] 消息的话会抛异常.

```
[XXView copyWithZone:]: unrecognized selector sent to instance 0x600000124240
```


解决办法就是使用 NSKeyedArchiver 档案来序列化之后再用 NSKeyedUnarchiver 还原.

```objc
NSData * archivedView       = [NSKeyedArchiver archivedDataWithRootObject:productView];
DhProductView * myViewCopy  = [[NSKeyedUnarchiver unarchiveObjectWithData:archivedView] retain];
```

