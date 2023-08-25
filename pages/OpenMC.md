public:: true
date::  [[Jun 21st, 2022]]

- 官网：[OpenMC](https://openmc.org/)，源码：[openmc-dev/openmc: OpenMC Monte Carlo Code (github.com)](https://github.com/openmc-dev/openmc)
- 它是用[[Python]]写的，可以运行在windows/mac/linux平台上。有两种自选的安装方式：通过[[Conda]]安装，通过 [[Docker]] 安装。
- ## Docker的安装方式
- 官方的[[Docker]]镜像中包含了[[python]]的源码和[[OpenMC]]需要的数据库，所以镜像比较大，大概有4G左右，好处是我们可以直接使用了。
- 镜像`exec`运行，进入openmc的源码目录进行安装，openmc安装完后就是命令行工具使用。