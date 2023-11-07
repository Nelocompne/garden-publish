public:: true
tags:: Linux

- ## 如何开始arch [[linux]]
- 如果对于那些业余人士来直接使用 [[archlinux]] 还是太勉强了，推荐还是从一些容易入门的基于Arch的其他开发版，比如 [[manjaro]]。
- 但如果真的想要比 manjaro 更自由的体验，可以从arch别的发行版开始：
	- [ArcoLinux](https://arcolinux.com)（有四个不同的版本）
	- [Arka Linux GUI](https://sourceforge.net/projects/arch-linux-gui/) archlinux-gui（带有gui的archlinux安装版本）
	- [EndeavourOS](https://endeavouros.com/)
	- [ArchLabs Linux](https://archlabslinux.com/)
	- [Archcraft](https://archcraft.io/)（有更好看的桌面）
- ### ArcoLinux
- [[Arcolinux]]有四种L/S/B/D不同的版本。
- 当然还可以借助安装安装脚本，虽然也比直接安装archlinux好不了多少，但好歹有安装引导：
	- [archfi](https://github.com/MatMoul/archfi)
		- [archdi](https://github.com/MatMoul/archdi) 预装桌面环境
	- [simplyarch](https://github.com/geminis3/simplyarch)（不能正常安装）
	- [ArchTitus](https://github.com/ChrisTitusTech/ArchTitus)
	- [alis](https://github.com/picodotdev/alis)
- ### [[Archinstall]]
- Arch linux 官方的安装引导程序，[archinstall](https://wiki.archlinux.org/title/Archinstall_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))
- > ~~已知问题：pacman镜像源无法更新~~ 一定要记得装网络管理器
- ### 配置桌面
- [owl4ce/dotfiles](https://github.com/owl4ce/dotfiles)
- ### 输入法
- [Rime (简体中文) - ArchWiki (archlinux.org)](https://wiki.archlinux.org/title/Rime_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))
- ### [[pacman]]
- 包管理工具，通常只要记住一些基本操作。
- ```shell
  pacman -Syu # 同步数据并更新
  pacman -Ss <name> # 搜索某个包
  pacman -S <name> # 安装包
  ```
- ### pacman[[镜像源]]
- ```/etc/pacman.d/mirrorlist
  Server = https://mirrors.tuna.tsinghua.edu.cn/archlinux/$repo/os/$arch
  Server = https://repo.huaweicloud.com/archlinux/$repo/os/$arch
  Server = https://mirrors.cloud.tencent.com/archlinux/$repo/os/$arch
  Server = http://mirrors.aliyun.com/archlinux/$repo/os/$arch
  Server = http://mirrors.163.com/archlinux/$repo/os/$arch
  ```
- ## VirtualBox虚拟机的Archlinux食用方法
- 通过archinstall安装，可以最小配置安装，再安装好网卡。通过[[virtualbox]]安装增强功能，当vbox弹出无法挂载的时候，就说明光盘已经加载但是并没有自动挂载成功，因为最小配置安装没有图形界面，所以我们要手动挂载光盘，一般第一个光盘的默认挂载点是`/dev/sr0`。
- 或者通过 `dmesg | grep CD-ROM` 查询已加载的光驱。
- 安装增强功能是因为我们网络默认使用NAT，不用桥接之类的，NAT下高级功能有一个端口转发，直接映射主机端口和子系统端口即可，两边IP不用输入会默认为本机。
- 有了这个端口转发，我们再安装好[[openssh]]，[[systemd]]启动`sshd`服务后重启虚拟机。就可以ssh使用虚拟机了。