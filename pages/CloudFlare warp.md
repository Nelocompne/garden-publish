public:: true
date:: [[Jul 16th, 2023]] 
tags:: DevOps

- warp作为CloudFlare免费的VPN服务深受大家喜爱，但如果要想在自己的vps服务上部署你要需要了解些东西，这里我就不介绍了，别人[写的项目](https://github.com/fscarmen/warp)里足够了，比如我非常喜欢这个项目里关于[用socks使用的服务](https://github.com/fscarmen/warp#%E6%8C%87%E5%AE%9A%E7%BD%91%E7%AB%99%E5%88%86%E6%B5%81%E5%88%B0-socks5-%E7%9A%84-xray-%E9%85%8D%E7%BD%AE%E6%A8%A1%E6%9D%BF-%E9%80%82%E7%94%A8%E4%BA%8E-warp-client-proxy-%E5%92%8C-wireproxy)，里面的v2ray配置模板我非常喜欢，以及[原理介绍](https://github.com/fscarmen/warp#warp%E5%8E%9F%E7%90%86)，里面也谈到了[CloudFlare账号和非账号的区别](https://github.com/fscarmen/warp#warp-license-%E5%8F%8A-id-%E8%8E%B7%E5%8F%96)，避坑必读。作为 [[Docker]] 粉丝肯定喜欢的一个项目，因为warp实际上是wireguard的客户端，如果想让事情更可控一些，可以通过方式[作为socks服务提供](https://github.com/Mon-ius/Docker-Warp-Socks)。
- ## 指导
- warp https://github.com/Mon-ius/Docker-Warp-Socks
- ```shell
  docker run --privileged --restart=always -itd \
    --name warp_socks \
    --cap-add NET_ADMIN \
    --cap-add SYS_MODULE \
    --sysctl net.ipv6.conf.all.disable_ipv6=0 \
    --sysctl net.ipv4.conf.all.src_valid_mark=1 \
    -v /lib/modules:/lib/modules \
    -e TZ=Asia/Tokyo \ #对申请warp没啥影响，可忽略配置
    -p 9091:9091 \
  monius/docker-warp-socks
  ```
- 检验 `curl --proxy socks5h://127.0.0.1:9091 https://www.cloudflare.com/cdn-cgi/trace`
- [[Oct 8th, 2023]]
	- 今天突然发现 https://github.com/fscarmen/warp 项目被ban了
	- https://github.com/fscarmen/warp-sh
		- 不过别的平台找到了这个 https://gitlab.com/fscarmen/warp
- [[Oct 14th, 2023]] warp更新
	- mon-ius 版本的 warp socks 运行并不稳定，有个新项目，并且还是用 [[sing-box]] 作为客户端
	- https://github.com/baby9/wgcf-socks-docker
	- ```shell
	  docker run -d \
	  --name wgcf_socks \
	  -p 40000:40000 \
	  --restart=unless-stopped \
	  zenexas/wgcf-socks:latest
	  ```
	- 验证 `curl -s4m8 -x socks5://127.0.0.1:40000 https://www.cloudflare.com/cdn-cgi/trace | grep warp`