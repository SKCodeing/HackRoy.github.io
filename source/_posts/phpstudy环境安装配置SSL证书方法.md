---
title: phpstudy环境安装配置SSL证书方法
date: 2017-12-14 17:28:35
tags: 服务器
---
phpstudy环境下如何安装配置SSL证书?有很多集成式的web服务器无法按照一般站点的配置来部署ssl证书，本文以集成式phpstudye为例(apache+mysql)，为大家介绍phpstudy环境安装配置SSL证书方法。

![](https://www.wosign.com/faq/images/phpstudy2016.jpg)

首先，确保你的apache编译了ssl模块，这是支持ssl证书必要的条件(如果没有，请编译,打开phpstudy——设置——PHP模块扩展——php-openssl前面勾选上)。

第一：进入到apache目录下，httpd.conf找到#LoadModule ssl_module modules/mod_ssl.so，去掉前面的注释符，使得ssl模块生效(如果该模块已去掉注释，请不用操作)。

第二，找到网站配置文件vhosts.conf，一般在如下路径：D:\phpStudy\Apache\conf，按照80的配置，另起一个VirtualHost443，如下所示:

Listen 443

ServerName www.yourdomain.com #(和80一样)

ServerAlias yourdomain.com #(和80一样)

DocumentRoot “D:\phpStudy\WWW” #(和80一样)

SSLEngine on

SSLProtocol all -SSLv2 -SSLv3

SSLCipherSuite AESGCM:ALL:!DH:!EXPORT:!RC4:+HIGH:!MEDIUM:!LOW:!aNULL:!eNULL

SSLCertificateFile "C:\phpStudy\Apache\conf\ssl\2_yourdomainame.crt" #(服务器上公钥证书路径)

SSLCertificateKeyFile "C:\phpStudy\Apache\conf\ssl\3_yourdomainame.key" #(服务器上私钥证书路径)

SSLCertificateChainFile "C:\phpStudy\Apache\conf\ssl\1_root_bundle.crt" #(服务器上证书链路径)

第三，重启apache(有可能报错，看一下443端口是否被防火墙拦截或被占用)

第四，apache正常重启后，在浏览器里面输入https://yourdomain.com就能看到安全锁出来啦。

第五，备份好您的SSL证书!

以上就是phpstudy环境安装配置SSL证书方法，大家在部署的时候尽量找准自己的apache下的路径，上面的仅供参考!另，Linux下的环境同windows配置一样。