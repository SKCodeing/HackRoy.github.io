---
title: 解决ld:library not found for -lPods的问题
date: 2017-10-17 10:45:10
tags: Pods的问题
---
最近计划把公司的项目重构一下，第一步就是引入CocoaPods(以下简称pods)来管理第三方库。但是这第一步就不是太顺利。
首先建好Podfile，并在命令行中输入pod install，结果报以下错误

```
[!] The XXX target overrides the 'OTHER_LDFLAGS' build setting defined in  
'Pods/Target Support Files/Pods/Pods.debug.xcconfig'.  
 This can lead to problems with the CocoaPods installation  
    - Use the '$(inherited)' flag, or
    - Remove the build settings from the target.

```

```
[!] The 'SubWayWifi [Release]' target overrides the 'OTHER_LDFLAGS' build setting defined in 
'Pods/Target Support Files/Pods/Pods.release.xcconfig'. 
This can lead to problems with the CocoaPods installation
    - Use the '$(inherited)' flag, or
    - Remove the build settings from the target.

```

现在打开有pods建好的workspace文件，尝试编译，会报ld: library not found for -lPods错误，原因就是工程里面的设置项覆盖了pods中xcconfig中的设置。解决办法就是在build setting->other linker flag中，加上$(inherited)即可。

OK，重新安装pod试试，由于我们已经进行过一次安装，所以本次只用更新一次即可，在命令行中输入pod update，现在没有报任何错误。但是当我尝试编译工程的时候，又报了一个错误:ld: library not found for -lReactiveCocoa。咋又找不到相应的第三方库了呢？好吧，继续查资料。

最后还是在cocoapods的官网Troubleshooting找到的解决办法。在Edit Scheme中，找到Build项，点击+号，找到Pods静态库，点击Add。再尝试编译，编译通过。

作者：ray_xia
链接：http://www.jianshu.com/p/cb1973a78650
來源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。