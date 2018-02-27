---
title: carthage
date: 2018-02-12 09:15:34
tags: iOS-Carthage 安装以及使用
---
iOS-Carthage 安装以及使用
#### 1、Carthage 简介

* Carthage 类似于 CocoaPods，为用户管理第三方框架和依赖，但不会自动修改项目文件和生成配置
* Carthage 是去中心化的依赖管理工具，安装依赖时不需要去中心仓库获取 CocoaPods 所有依赖的索引，节省时间
* 对项目无侵入性，Carthage 设计上也比较简单，利用的都是 Xcode 自身的功能，开发者在创建依赖时，相比CocoaPods 也简单许多
* Carthage 管理的依赖只需编译一次，项目干净编译时，不会再去重新编译依赖，节省时间
* 自动将第三方框架编程为 Dynamic framework( 动态库 )
* 与 CocoaPods 无缝集成，一个项目能同时拥有 CocoaPods 和 Carthage

#### 缺点： 
* 仅支持 iOS8 +
* 它只支持框架，所以不能用来针对 iOS 8 以前的系统版本进行开发
* 支持的 Carthage 安装的第三方框架和依赖不如 CocoaPods 丰富
* 无法在 Xcode 里定位到源码
* 安装包的大小比用CocoaPods安装的包大

安装 Homebrew

可以使用 [Homebrew](https://brew.sh/) 来安装 Carthage

> 将以上命令粘贴至终端 
脚本会在执行前暂停，并说明将它将做什么。高级安装选项在 这里（需要OSX 10.5+）

```
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

> 安装完 homebrew 后执行下面命令，获取最新版本【可选】

```
$ brew update
```

>注意：如果遇到 Error: The /usr/local directory is not writable.错误，就执行以下命令 sudo chown -R $(whoami):admin /usr/local，再更新。

#### 其他 brew 命令:

```
brew install git    // 使用brew安装软件
brew uninstall wget // 使用brew卸载软件
brew search /wge*/  // 使用brew查询软件，其中/wge*/是个正则表达式，需要包含在/中
brew list           // 列出已安装的软件
brew home           // 用浏览器打开brew的官方网站
brew info           // 显示软件信息
brew deps           // 显示包依赖
```

#### 2、安装 Carthage

```
$ brew install carthage
```

安装 Carthage 之后，可查看版本

```
carthage version // 目前的版本号为:0.20.1

```

#### 3、使用 Carthage 安装依赖

进入项目所在文件夹

```
cd ~/路径/项目文件夹
```

创建一个空的 Carthage 文件 Cartfile

```
touch Cartfile
```

使用 Xcode 打开 Cartfile 文件


```
open -a Xcode Cartfile
```

编辑 Cartfile【可手动打开进行编辑】

```
github "Alamofire/Alamofire" == 4.4.0
```

执行更新命令

```
$ carthage update --platform iOS
```

更新成功后，项目文件夹中会多出三个文件

* cartfile
* Cartfile.resolved
* Carthage/ 
* Build/
* Checkouts/

Carthage 会 clone 文件中对应的 git 第三方库，把每一个第三方库编译成二进制文件的 framework 文件。 
其中 “–platform iOS” 命令是可选的，作用是保证只为 iOS 编译framework，如果不指定平台，会为全平台编译 framework 文件。如果想要了解更多的命令，可以运行 carthage help update查看。

#### 4、添加 Frameworks 到项目中
- 点击”项目名称”–> “TARGETS” –> “General”，在最底部找到 “Linked Frameworks and Libraries”
- 点击 + 号，选择左下角 Add Other… 按钮，选择项目下 Carthage/Build/iOS/Alamofire.framework 文件，点击 Open 加入到项目中

```
目的是告诉Xcode链接你的app到这个 framework，允许你在代码中使用
```
- 下一步选择菜单上的 Build Phases，点击左上角 + 号添加一个新的 Run Script，并添加以下命令：

```
/usr/local/bin/carthage copy-frameworks
```

- 点击 Input Files 下面的 + 号为每一个 framework 添加访问路径

```
carthage copy-frameworks 命令剔除了额外的框架
```

```
$(SRCROOT)/Carthage/Build/iOS/Alamofire.framework

```
- Import 框架名到控制器，Command + B 编译项目，如果成功，就可以使用了
```
import Alamofire
```


