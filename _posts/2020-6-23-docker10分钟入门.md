---
layout:     post
title:      docker10分钟入门
subtitle:   docker
date:       2020-06-23
author:     RRY
header-img: img/post-bg-cook.jpg
catalog: true
tags:
    - docker
---

## 0x01docker环境
如果安装遇到问题可以先去下面这个网址注册学习.可以开启一个4小时倒计时的docker环境.
`https://labs.play-with-docker.com/`

## 0x02docker常用命令
对容器的操作
`images` `run` `commit` `rm` `ps`
对仓库的操作
`pull` `push`
打包操作
`load` `save`
Dockerfile
`build`

## 0x03使用docker运行一个容器
`docker pull nginx`拉取tomcat的镜像
`docker run -d -p 80:80 --name mynginx nginx`-d参数后台运行,-p指定端口映射,--name指定容器名称,访问docker的ip会发现服务
`docker ps`可以看到容器运行的状况
`docker save nginx > nginx.tar`打包镜像
`docker rm -f id`删除容器
`docker rmi nginx`删除镜像
`docker load < nginx.tar`解压镜像 

## 0x04Dockerfile
`FROM nginx`指定基于nginx镜像
`ADD src /usr/share/nginx/html`将当前目录下的src文件夹拷贝到容器中指定目录
`COPY src /var/www/html`同ADD,但是ADD地址可以是url
`ENV flag="this_is_not_flag"`指定环境变量
`VOLUME src /src`目录映射
`RUN mkdir /var/www/html/upload/`容器构建时执行shell命令
`WORKDIR /usr/local/apache/logs`在容器中创建一个文件夹
`EXPOSE 80`声明端口
`docker build -t test ./`
`docker run -d -t test`
