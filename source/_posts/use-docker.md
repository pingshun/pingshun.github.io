---
title: docker 常用命令备忘
date: 2017-09-06 13:30:48
tags: docker
---

[不太]常用的一些docker命令

<!--more-->

###container相关操作

1. 启动停止container [docker start/stop/restart]
   docker start [OPTIONS] CONTAINER [CONTAINER...]:启动一个或多个已经被停止的容器
   docker stop [OPTIONS] CONTAINER [CONTAINER...]:停止一个运行中的容器
   docker restart [OPTIONS] CONTAINER [CONTAINER...]:重启容器

2. 创建container [docker run／create]

   docker run [OPTIONS] IMAGE [COMMAND] [ARG...] 创建一个新的容器并运行一个命令
   OPTIONS说明：
     -a stdin: 指定标准输入输出内容类型，可选 STDIN/STDOUT/STDERR 三项；
     -d: 后台运行容器，并返回容器ID；
     -i: 以交互模式运行容器，通常与 -t 同时使用；
     -t: 为容器重新分配一个伪输入终端，通常与 -i 同时使用；
     --name="nginx-lb": 为容器指定一个名称；
     --dns 8.8.8.8: 指定容器使用的DNS服务器，默认和宿主一致；
     --dns-search example.com: 指定容器DNS搜索域名，默认和宿主一致；
     -h "mars": 指定容器的hostname；
     -e username="ritchie": 设置环境变量；
     --env-file=[]: 从指定文件读入环境变量；
     --cpuset="0-2" or --cpuset="0,1,2": 绑定容器到指定CPU运行；
     -m :设置容器使用内存最大值；
     --net="bridge": 指定容器的网络连接类型，支持 bridge/host/none/container: 四种类型；
     --link=[]: 添加链接到另一个容器；
     --expose=[]: 开放一个端口或一组端口；
   实例:
     使用镜像nginx:latest以后台模式启动一个容器,将容器的80端口映射到主机的80端口,主机的目录/data映射到容器的/data
     docker run -p 80:80 -v /data:/data -d nginx:latest

   docker create [OPTIONS] IMAGE [COMMAND] [ARG...] 创建一个新的容器但不启动它
     用法同 docker run

3. Docker exec 命令
   docker exec [OPTIONS] CONTAINER COMMAND [ARG...] 在运行的容器中执行命令
   OPTIONS说明：
     -d :分离模式: 在后台运行
     -i :即使没有附加也保持STDIN 打开
     -t :分配一个伪终端
   实例：
     docker exec -it mynginx /bin/sh 在容器mynginx中开启一个交互模式的终端
     docker exec mynginx ls /tmp/ 在mynginx里ls ／tmp