---
title: 初识docker
categories: docker
---

### 概述

Docker 是一个开源的应用容器引擎，Docker 可以让开发者打包他们的应用以及依赖包到一个容器中，然后发布到linux机器上。


### 镜像（Image）

相当于一个root文件系统。

常见操作：

```bash
# 列出本机上的镜像
docker images

# -i 交互式操作 -t 终端 /bin/bash 镜像名称后面的命令
docker run -t -i ubuntu /bin/bash

# 获取镜像
docker pull ubuntu

# 查找镜像
docer search ubuntu

# 删除镜像
docker rmi ubuntu

# 创建镜像 -t 指定创建的镜像名 . Dockerfile 文件所在目录
docker build -t test .
```

### 容器（Container）

相当于镜像的一个实例，容器是镜像运行的实体，可以被创建，启动，停止，删除，暂停等。

常见操作

```bash
# 以命令行模式进入容器
docker run -t -i -p 5000:5000 ubuntu /bin/bash

# 退出终端，直接在终端中输入exit
exit

# 查看所有的容器
docker ps -a

# 启动一个已停止的容器
docker start [id]

# 停止一个容器
docker stop [id]

# 重启容器
docker restart [id]

# 进入容器
docker attach [id]
docker exec [id] # 退出时不会导致容器停止
docker exec -it 243c32535da7 /bin/bash

# 导出容器
docker export  [id] > [name] # eg: docker export 1e560fca3906 > ubuntu.tar

# 导入容器
cat [fileName] | docker import - [imageName] # eg: cat docker/ubuntu.tar | docker import - test/ubuntu:v1
docker import http://example.com/exampleimage.tgz example/imagerepo # 从url地址导入

# 删除容器
docker rm -f [id]
```