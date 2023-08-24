public:: true
date:: "2023-03-28"

- ## 固件选择（[[openwrt]]）
	- https://github.com/soffchen/NanoPi-R2S 大杂烩，省事
	- https://github.com/stupidloud/nanopi-openwrt  （原klever1988） _[[immortalwrt]]_ ~~挑卡~~屁用没有
	- https://github.com/msylgj/R2S-R4S-OpenWrt _immortalwrt_ 小 ~~挑卡~~屁用没有 _sfs_
	- https://fw.koolcenter.com/iStoreOS/r2s/ 发行版 稳定 算小 省事 _ext4_ _squashfs_
	- https://github.com/kiddin9/OpenWrt_x86-r2s-r4s-r5s-N1 在线定制编译 能用 小 启动多试 _sfs_
	- https://github.com/thomaswcy/R2S _[[RubikWrt]]_ 能用 小 启动多试 _sfs_ 风扇启停频繁
	- https://github.com/QiuSimons/YAOF 这个也可以试试，但我没用过
- ## 固件烧录安装
- sys灯开始会一闪一闪，当它稳定或者有呼吸闪动后说明准备就绪。**插上网线一直没有识别到网络就是没用**。
- ## 安装openclash
- 如果你选择[[istoreos]]，该发行版已经自己配备好了包源，默认是清华源，根据[[openclash]]的发行说明安装好需要的依赖即可安装。