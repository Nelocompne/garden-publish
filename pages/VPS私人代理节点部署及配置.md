public:: true
date:: [[Jul 16th, 2023]] 
tags:: DevOps

- ## 什么情况下你应该继续看这篇文章？
- 掌握 [[Docker]] 。
- 熟练掌握 Linux 、 建站 、服务器运维。
- 尊重您所在的当地法律。
- ## 从头开始配置
- 首先只要有个1核1G内存的VPS就行了，选好系统，一般ubuntu或者debian就好，可别centos啥的，~~redhat系讨厌死了，都2023年了能不能新潮点~~。
- 为了安全和方便，给vps配个ssh密钥，SSH key generator 这个工具是真的很好用。
- 首先软件包更新一波，然后安装docker，别自己装，直接用docker[官方的install脚本](https://github.com/docker/docker-install)。顺便你还可以装些常用的工具 `tmux neofetch htop` ……
- 关闭系统自带的防火墙，或者开放服务端口。这个方法自己上网找。~~[参考](https://isedu.top/index.php/archives/33/)~~：
	- `sudo iptables -P INPUT ACCEPT && sudo iptables -P FORWARD ACCEPT && sudo iptables -P OUTPUT ACCEPT && sudo iptables -F` 注意，这个方法在服务器重启后就会重置
- 开启BBR加速算法，这个也自己去上网搜。参考：
  ```shell
  echo net.core.default_qdisc=fq >> /etc/sysctl.conf
  echo net.ipv4.tcp_congestion_control=bbr >> /etc/sysctl.conf
  sysctl -p
  ```
- 找个html的模板，这里我[随便找了一个](https://github.com/kuzan-ux/Anime-world)。
- 然后使用xray的[模板](https://github.com/XTLS/Xray-examples)
	- 下载 xray 程序，模板要用
	- 准备xray配置文件、nginx配置文件，都放在适合的地方即可。
- 然后按以下步骤开始。
- ## All on docker
- 用docker的话还可以配合上这个[小工具](https://github.com/jesseduffield/lazydocker)
- ### [[acme.sh]]
- {{embed [[acme.sh]]}}
- ### [[CloudFlare warp]]
- {{embed [[CloudFlare warp]]}}
- ### "Just runing a real linux environment."
- alpine https://hub.docker.com/_/alpine
- ```shell
  docker run -d --name unix \
    -v xrayunix:/dev/shm \
  alpine ping 127.0.0.1 # 随便找个能让容器持续运行下去的服务
  ```
- 这里的 `xrayunix` 指向的是后面 xray 和 nginx 共同需要的 _Unix域套接字地址_ 目录，因为这个空间 `/dev/shm` 是在Linux系统的内存中，所以为了保持这个空间在下面两个服务运行前是干净的，需要一个 _真实_ 的 Linux 容器来自动处理它。
- ### xray
- xray https://hub.docker.com/r/teddysun/xray
- ```shell
  docker run -d --name xray \
    --network host \
    --restart=always \
    -v xrayunix:/dev/shm \ # Unix域套接字地址
    -v $PWD/xray:/etc/xray \
    -v $PWD/out:/out \
    -p 443:443 \ # https
    -p 3001:3001 -p 3002:3002 -p 3003:3003 -p 3004:3004 \ # grpc
  teddysun/xray
  ```
- ### [[nginx]]
- nginx
- ```shell
  docker run -d --name nginx \
    --network host \
    --restart=always \
    -v xrayunix:/dev/shm \ # Unix域套接字地址
    -v $PWD/html:/var/www/html \ # 静态页面目录
    -v $PWD/nginx.server.conf/:/etc/nginx/conf.d \
    -v /etc/localtime:/etc/localtime \
  nginx
  ```
- ## Debug
- curl https://hub.docker.com/r/alpine/curl
	- `docker run --rm alpine/curl -fsSL https://www.google.com/`
- [reload docker daemon](https://docs.docker.com/config/daemon/systemd/)
- `curl --proxy socks5h://127.0.0.1:9091 --location --request GET 'https://ip.useragentinfo.com/json' | jq .`
- `curl --request GET 'https://ip.useragentinfo.com/json' | jq .`
- ### 疑难
- 部署好了节点没法用？去检查防火墙
- 速度、延迟问题？自己跑mtr看ip