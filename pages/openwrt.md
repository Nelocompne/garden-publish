public:: true
date:: [[Aug 28th, 2023]] 
tags:: DevOps

- # LEDE
	- [[Jun 16th, 2023]] 过去 #openwrt 还不叫 openwrt ，叫 #LEDE ， _Lean's LEDE_ 是恩山论坛的用户@Lean 做的分支版本。后面出了个针对中国本地化体验的分支版本 #ImmortalWrt 。#Luci 是支持 [[openwrt]] 的web面板，软件包里带 `luci` 字样的说明该包的使用带有面板。
- # 固件扩容
	- 参考： https://www.izilzty.com/?post=5
	- 此适用于`squashfs`分区类型的固件，并且是在机器首次启动前就应该做好固件扩容的处理
	- ```shell
	  dd if=/dev/zero bs=1M count=1024 >> openwrt.img
	  # 其中count=1024为要增加的大小，单位为MB
	  
	  fdisk openwrt.img
	  
	  ...
	  # 查看分区，一般第二个就是主要分区，记住第二个分区的起始块
	  # 删除原来的分区，删除的目的是为了从原来分区位置建立新大小空间的分区
	  # 建立新分区从之前记住的起始块开始，然后输入要增加的大小，大小不能超过之前dd增加的空间
	  
	  Partition #2 contains a squashfs signature.
	  
	  Do you want to remove the signature? [Y]es/[N]o: n
	  # 确定新分区大小后会检测到原分区位置存在的 squashfs 签名，我们保留它
	  
	  ...
	  # 最后输入 w 指令写入分区操作
	  ```
- # 主题 argon
	- https://github.com/jerrykuku/luci-theme-argon
	- https://github.com/jerrykuku/luci-app-argon-config/
		- 有个小毛病，直接上传文件会只有个2kb的无效文件，通过sftp传的文件会当场消失，解决方法就是直接上传后，再sftp同文件传一遍直接覆盖即可。
- # ipv6接口的配置
	- 默认编译中包含ipv6的接口，但某些固件默认不会配置的话就需要手动配置了。
	- 手动配置一个`wanv6`接口
	  collapsed:: true
		- ![dhcp.png](../assets/dhcp_1693161448248_0.png){:height 1057, :width 748} _配置参考_
	- ipv6 ULA 生成用于内网前缀 https://www.unique-local-ipv6.com/
	  collapsed:: true
		- ![image.png](../assets/image_1693161526238_0.png){:height 268, :width 748}
	- 如果`lan`口下还有个路由器要注意`ipv6`配置
	  collapsed:: true
		- [[Oct 11th, 2023]] 对于路由器，其实如果它有自动配置的选项，只要在设置里重新加载一遍配置就会自动完成了，基本上不需要手动留意。
		- ![image.png](../assets/image_1693171707819_0.png) 这里 DNS 配置和前面配置的 ULA 前缀对应
	- ![image.png](../assets/image_1693201063448_0.png) 配置成功大概是这个样子
- # 套件
	- [[May 31st, 2023]] 从昨天折腾 #openwrt 后，发现它自己的 #busybox 和自带的工具套件功能太有限了，有更多的功能都做不到，突然想到有个 #nix 或者 #nushell ，然后尝试了一下nix，跑的[Docker版](https://nixos.org/download.html#nix-install-docker)，成功获得了相当好的体验。
	- [[Oct 11th, 2023]] 实际上很好解决，直接在软件包里手动安装需要的指定套件就行了， [[busybox]] 自带的虽然包括大部分套件，但是功能并不完全。