---
title: iPhone开发之：iPhoneX、iOS11适配
date: 2017-10-11 11:29:00
tags: iOS
---
### iPhoneX屏幕尺寸相关变化 ###
```
1.1 高度增加了145pt，变成812pt.
1.2 屏幕圆角显示，注意至少留10pt边距。
1.3 状态栏高度由20pt变成44pt，留意这个距离就能避开“刘海”的尴尬，相应的导航栏以上变化64-88。
1.4 底部工具栏需要为home indicator留出34pt边距。
1.5 物理分辨率为1125px * 2436px.
```
#### ios11适配安全边距（宏定义）####
`` adjustsScrollViewInsets_NO(self.tableView, self);``
#### iPhone X 宏定义 ####
``#define iPhoneX (SCREEN_WIDTH == 375.f && SCREEN_HEIGHT == 812.f ? YES : NO)``
#### 适配iPhone X 状态栏高度 ####
`` #define MC_StatusBarHeight (iPhoneX ? 44.f : 20.f) ``
#### 适配iPhone X Tabbar高度 ####
``#define MC_TabbarHeight (iPhoneX ? (49.f+34.f) : 49.f)``
#### 适配iPhone X Tabbar距离底部的距离 ####
``#define MC_TabbarSafeBottomMargin (iPhoneX ? 34.f : 0.f)``
#### 适配iPhone X 导航栏高度 ####
``#define MC_NavHeight (iPhoneX ? 88.f : 64.f)``

