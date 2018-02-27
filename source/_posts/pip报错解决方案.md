---
title: pip报错解决方案
date: 2018-02-14 11:07:37
tags:
---
python3.6 pip无法安装插件

pip is configured with locations that require TLS/SSL, however the ssl module in Python is not available.

pip is configured with locations that require TLS/SSL, however the ssl module in Python is not available.
Collecting flask
Could not fetch URL https://pypi.python.org/simple/flask/: There was a problem confirming the ssl certificate: Can't connect to HTTPS URL because the SSL module is not available. - skipping
Could not find a version that satisfies the requirement flask (from versions: )
No matching distribution found for flask

新版的pip 默认要求使用https了，

pip 的源可以使用国内的源，下载速度会很快。

参考这个 http://mirrors.aliyun.com/help/pypi

pip.conf中要有trusted-host，就可以不用https了。同时也可以解决你的问题。

CentOS 7安装Python3.5
http://www.linuxidc.com/Linux/2016-04/129784.htm


在~/.pip/pip.conf文件中添加或修改
[global]
index-url = http://mirrors.aliyun.com/pypi/simple/

[install]
trusted-host=mirrors.aliyun.com