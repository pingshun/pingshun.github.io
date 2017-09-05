---
title: 使用ssh用户配置文件config来简化你的ssh
date: 2017-08-23 10:48:59
tags: [技术,ssh]
---
有时候我们用ssh去连接server的时候经常会带上很多参数(port, username…),有的时候需要连接一个超级长的HostName，有的时候需要连接不同的server使用不同的密钥文件...这些需求，都可以用ssh的用户配置文件来简化，这个文件位置：~/.ssh/config（没有的话自己建一个就行了）
<!--more-->
这个配置文件的用法：
Host    别名
    HostName        主机名
    Port            端口
    User            用户名
    IdentityFile    密钥文件