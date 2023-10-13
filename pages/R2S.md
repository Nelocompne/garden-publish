public:: true
date::  [[Mar 28th, 2023]], [[Aug 28th, 2023]]

- ## [[openwrt]] 固件
	- https://firmware-selector.openwrt.org 官方编译版
	- https://github.com/soffchen/NanoPi-R2S 大杂烩，省事
	- https://fw.koolcenter.com/iStoreOS/r2s/ 发行版 稳定 算小 省事 _ext4_ _squashfs_
	- https://github.com/QiuSimons/YAOF 这个也可以试试，~~但我没用过~~， 默认给CPU提频了，我机子体质太差启动不了，要降频才行。
		- https://github.com/nicholas-opensource/OpenWrt-Autobuild fork版，精简的同时编译了 [[dae]] ，非常好
	- https://github.com/stupidloud/nanopi-openwrt  （原klever1988） _[[immortalwrt]]_ ~~挑卡~~屁用没有
	- https://github.com/msylgj/R2S-R4S-OpenWrt _immortalwrt_ 小 ~~挑卡~~屁用没有 _sfs_
	- https://github.com/kiddin9/OpenWrt_x86-r2s-r4s-r5s-N1 在线定制编译 能用 小 启动多试 _sfs_
	- https://github.com/thomaswcy/R2S _[[RubikWrt]]_ 能用 小 启动多试 _sfs_ 风扇启停频繁
- ## 固件烧录安装
- sys灯开始会一闪一闪，当它稳定或者有呼吸闪动后说明准备就绪。**插上网线一直没有识别到网络就是没用**。
- ## 安装openclash
- 如果你选择[[istoreos]]，该发行版已经自己配备好了包源，默认是清华源，根据[[openclash]]的发行说明安装好需要的依赖即可安装。
- ## 死机问题
- [[Aug 23rd, 2023]] 在R2S上跑的服务在工作的时候，总是会出现死机，后面查资料才发现这个细节
	- [1#L28](https://github.com/QiuSimons/YAOF/blob/fa90e032b4cd7b1cca9978e388179b130444c23a/README.md?plain=1#L28) R2C/R2S 核心频率 1.6（交换了 LAN WAN），R4S 核心频率 2.2/1.8（建议使用带有线损补偿的电源，死机大多数情况下，都是因为**你用的电源过于垃圾**，另外，你也可以选择使用**自带的 app 限制最大频率**，茄子 🍆）
- [[Aug 25th, 2023]] 因为用的 [[istoreos]] 它的更新还算活跃，用上最新的固件后死机问题就没有出现过了。