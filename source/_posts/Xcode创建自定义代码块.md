---
title: Xcode创建自定义代码块
date: 2017-10-19 10:31:00
tags: Xcode
---
由于项目、所用语言或者编码习惯的差别，不同的程序员习惯用的代码片段也不尽相同，这就有了自定义代码片段的需求，好在Xcode是支持该功能的。他的好处是使程序员以最快的速度输入很常用的代码片段，提高编程效率。

该功能是从Xcode4开始引入的。在Xcode中的位置如下图所示：

如上图，右边系统就定义很对的代码块，包括一些我们很常用的@interface 和@implementation的声明和实现。

二、自定义我们常用的代码块步骤

Ｅｇ：@property属性的定义是Cocoa程序开发中很常用的一个功能，下面就以此为例说明如何自定义代码片段。

1、书写代码片段

在声明@property属性的地方写下如下语句：

@property (nonatomic, retain) <#type#> <#name#>;

这里<#type#>和<#name#>起什么作用可以在后面的使用效果中看出来。
![](http://upload-images.jianshu.io/upload_images/5977975-3f977414479d57c8.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
2、新建代码片段


１）点击Code Snippet Library

2)选择User 用户自定义

3）出现如下空白界面

4）把刚编辑好的代码选中，拖到上面的空白处，出现如下的编辑窗口

![](http://img.blog.csdn.net/20130929182943812?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvd3p6dmljdG9yeQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

图中从上到下的含义依次是：

①Title

代码片段的标题

②Summary

代码片段的描述文字

③Platform

可以使用代码片段的平台，有IOS/OS X/All三个选项

④Language

可以在哪些语言中使用该代码片段

⑤Completion Shortcut

代码片段的快捷方式，比如本文开头用到的dowhile，在这里，把属性设置的快捷方式设为property

⑥Completion Scopes

可以在哪些文件中使用当前代码片段，比如全部位置，头文件中等，当然可以添加多个支持的位置。

最后的一个大得空白区域是对代码片段的效果预览。

一切设置完成以后，点击该菜单右下角的Done按钮，新建工作就结束了。

5）验证效果：我在代码里面输入”pro“ 即出现如下提示：（直接点击Enter键，一整条语句就自动补齐了）

![](http://img.blog.csdn.net/20130929183935093?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvd3p6dmljdG9yeQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

三、代码片段的备份

Xcode中的代码片段默认放在下面的目录中：

~/Library/Developer/Xcode/UserData/CodeSnippets

我们可以将目录中的代码片段备份，也可以将其直接拷出来放在不同的电脑上使用，因此多台电脑之间的协作也毫无压力。

