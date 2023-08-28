public:: true
date::  [[Jun 17th, 2023]]

- [[openwrt]] 的 [[Docker]] 版本太老所以`dockerd` 守护进程还不支持 _--http_proxy_ 参数，但是官方说[支持环境变量](https://docs.docker.com/engine/reference/commandline/dockerd/#environment-variables)加入代理。然后细看 `/etc/init.d/dockerd` 因为是用的 #procd 进程管理，根据[文档](https://openwrt.org/docs/guide-developer/procd-init-scripts) 应该这样添加代理环境变量
	- ```shell
	  procd_set_param env http_proxy=example.com:3189
	  procd_set_param env https_proxy=example.com:3189
	  ```
- 也就是通过这种原理，我们可以无痛给守护进程加入代理稳定pull镜像！😊