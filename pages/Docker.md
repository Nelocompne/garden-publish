public:: true
tags:: DevOps

- ## 入门
- Docker 是在 [[Linux]] 内核下的容器服务，它的所有工作自然依赖 Liunx 系统，也就是说一个正在运行的容器里包含 Linux 系统中最基础的部分，这就是为什么 Windows 用户在使用 Docker 之前需要安装 [[WSL]] 。我个人的使用方式是直接在 [[VirtualBox]] 中创建的 Linux 系统使用 Docker。
- ## 结构
- Docker下的产品（程序）很多，可以像不同的模块那样组合在一起工作。主要分为以下部分：
	- Docker Engine 本体
	- [[Docker Compose]] 快速创建Docker脚手架工具
	- Docker Desktop 桌面系统下的图形管理工具
	- Docker Hub 官方镜像仓库，地址： https://hub.docker.com/
- ## 安装
- 在不同的 Linux 发行版的包管理会有各自维护的 Docker 版本，你可以通过包管理器安装，但我个人推荐直接使用[官方的安装脚本docker-install](https://github.com/docker/docker-install)（注意，该脚本 [[ArchLinux]] 无法使用），这个安装脚本会自动安装最新的适应当前系统和CPU架构版本的Docker以及Docker Compose，如果你手动安装的话，这两个要分别安装的。
- ## 工作方式
- 一个运行的Docker容器（container）基于一个镜像（images）启动。镜像的获取有两种方式：一是通过Docker构建（build），二是通过Docker仓库（repository）拉取（pull）。当然构建一个镜像也可以在另外一个镜像的基础上进行构建。
- ## 基本使用
- > 注意：Docker需要root权限。
- 基本的使用方式：
- ```shell
  docker pull image_name # 拉取镜像
  
  docker image ls/rm [container name/id] # 查看/删除已有镜像的容器
  docker images [container name/id] # 同等 docker image ls
  docker rmi [container name/id] # 同等 docker image rm
  
  # 一个基础的例子
  docker run --rm -d \ # --rm 运行的容器在停止后会自动删除; -d 使容器在后台启动
      -p 8080:80 \ # -p [主机端口]:[容器内端口] 映射容器内端口到主机端口
      -v $PWD/workdir:/dir \ # -v [主机目录]:[容器内目录] 映射容器和主机目录空间
  image_name
  
  docker ps # 查看正在运行的容器信息
  docker ps -a # 查看所有的容器信息
  
  docker attach [container name/id] # 进入正在运行的容器 “主进程” ，Ctrl+P Ctrl+Q 离开
  docker exec -it [container name/id] /bin/sh ls /dir # 向容器内shell执行指令
  ```
- ## 资源限制
- 例子
- `-m 500M --memory-swap 500M --cpuset-cpus="0,1-3"`