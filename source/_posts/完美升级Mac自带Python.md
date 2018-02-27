---
title: 完美升级Mac自带Python2.7~3.6
date: 2018-02-13 16:48:42
tags: Python
---
### 前言
> Mac系统自带python2.7，本文目的是将自带的python升级到3.6版本。 
网上有本多的做法是让python2.7和python3.X两个版本共存，博主并不知道，是两版本共存好，还是直接升级好，所以读者要慎重选择方法。

> 关闭Rootless机制
由于Mac下的python2.7 默认是安装在／System目录下的。但是～～～Mac有个Rootless机制，默认不允许直接在／System下作修改。所以要先关闭Rootless机制。

### 关闭Rootless机制的方法: 

#### 关闭: 
* 1）.重启电脑, 重启过程中按住command+R, 进入恢复模式 
* 2）.打开terminal，键入: csrutil disable 
* 3）.重启电脑

如果之后要再开启Rootless机制，方法如下： 

#### 开启: 
* 1）.重启电脑, 重启过程中按住command+R, 进入恢复模式 
* 2）.打开terminal，键入: csrutil enable 
* 3）.重启电脑


### 下载安装python3.6

从[官网](https://www.python.org/downloads/ )
下载pkg版本，并安装。安装选默认路径，会安装到

```
/Library/Frameworks/Python.framework/Versions/
```

目录下

### 删除python2.7

```
sudo rm -R /System/Library/Frameworks/Python.framework/Versions/2.7
```

### 移动python3.6

将python3.6安装到/System/Library/Frameworks/Python.framework/Versions/

```sudo mv /Library/Frameworks/Python.framework/Versions/3.6 /System/Library/Frameworks/Python.framework/Versions
```

### 修改文件所属的Group

设置Group为wheel，原来系统自带的就是这样的。

```
sudo chown -R root:wheel /System/Library/Frameworks/Python.framework/Versions/3.6
```

### 更新一下Current的Link

在Versions的目录里有一个Current的link，是指向当前的Python版本，原始是指向系统自带的Python2.7，我们把它删除后，link就失效了，所以需要重新链一下

```
sudo rm /System/Library/Frameworks/Python.framework/Versions/Current
sudo ln -s /System/Library/Frameworks/Python.framework/Versions/3.6 /System/Library/Frameworks/Python.framework/Versions/Current
```

### 重新链接可执行文件

#### 先把系统原来的执行文件删掉


```
sudo rm /usr/bin/pydoc
sudo rm /usr/bin/python
sudo rm /usr/bin/pythonw
sudo rm /usr/bin/python-config
```
#### 建立新的链接

```
sudo ln -s /System/Library/Frameworks/Python.framework/Versions/3.6/bin/pydoc3.6 /usr/bin/pydoc
sudo ln -s /System/Library/Frameworks/Python.framework/Versions/3.6/bin/python3.6 /usr/bin/python
sudo ln -s /System/Library/Frameworks/Python.framework/Versions/3.6/bin/pythonw3.6 /usr/bin/pythonw
sudo ln -s /System/Library/Frameworks/Python.framework/Versions/3.6/bin/python3.6m-config /usr/bin/python-config
```


#### 更新.bash_profile文件

默认的bash_profile里python的bin是指向/Library/Frameworks/Python.framework/Versions/3.6/
bin

的。要改到/System/目录下


### 测试
在命令行中，用pip -V和pip3 -V查看版本和位置。用python进入。 
Mac下升级python2.7到python3.6，升级成功。