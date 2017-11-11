---
title: 关于HEXO安装失败的解决方法
date: 2017-11-02 14:44:06
tags: hexo
---
目前国内npm源有问题；所以键入如下代码即可安装成功:

```
npm install -g cnpm --registry=https://registry.npm.taobao.org
cnpm install hexo-cli -g
```