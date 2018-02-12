---
title: No application encryption key has been specified.
date: 2018-01-29 10:56:12
tags: PHP
---
环境：php7.1.10
laravel5.5
出现：
![](https://images2017.cnblogs.com/blog/1102222/201711/1102222-20171104161629841-1764260339.png)

解决：
在根目录下执行：

```
php artisan key:generate
```
终端打印：
``` 
Application key [base64:LvcrejzLdgyaqyCDVQI/fUyUd6Ktf/JAL1szXdGiu30=] set successfully.
```

OK问题解决
