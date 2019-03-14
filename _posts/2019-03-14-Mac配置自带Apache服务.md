---
layout:     post
title:      Mac配置自带服务器
subtitle:   Mac自带Apache的配置
date:       2019-03-14
author:     MY
header-img: img/post-bg-kuaidi.jpg
catalog: true
tags:
    - Mac
    - Apache
    - 服务器
    - 配置
---

# 前言

还久没有用Mac自带的**Apache**服务了，最近想用就配置了一下，看了网上的很多教程发现，配置过都报 **403 Forbidden**错误，踩了坑，分享记录一下，如有错误，谢谢指正

#### 常用命令

- 开启服务

```
sudo apachectl start
```

- 关闭服务

```
sudo apachectl stop
```

- 重启服务

```
sudo apachectl restart
```

----

#### 配置

1、首先创建一个用于服务的文件夹。

2、用**vim编辑器**编辑httpd.conf文件

```
cd /etc/apache2
sudo vim httpd.conf
```

3、找到***DocumentRoot*** 修改成自己刚才创建的文件

```
DocumentRoot "/Users/自己的用户名/Sites"
<Directory "/Users/自己的用户名/Sites">

    Options Indexes FollowSymLinks Multiviews
    MultiviewsMatch Any
    AllowOverride All
    Require all granted
</Directory>

```
- 注意：Options Indexes FollowSymLinks Multiviews 中的***Indexes*** 一定要添加上，不能少，如果少了报403

4、找到LoadModule php7_module libexec/apache2/libphp7.so 将前面的**#**去掉

5、wq退出

----

#### 测试

- 开启服务 

显示 Index of /  配置完成

如有问题，<myevery15@gmail.com>
