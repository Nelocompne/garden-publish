public:: true
date:: "2020-12-30"
tags:: Game

- 早期很多模拟器都需要手动加载相应游戏机的固件才能完整工作（如PSV，PS3，NS），而Cemu作为WiiU的模拟器没有这种固件，所以关于这类只需要模拟器本体即可。
- ## 手柄体感配置
- 1. Cemu模拟器自己本身是没有手柄体感输入接口的，所以你需要去下载cemuhook并安装在模拟器中，cemuhook由另外一个作者负责，并且模拟器作者也非常支持。安装后就可以进行体感输入。
- 2. 当确保你的手柄能够在电脑上正常提供体感功能后（这通常需要查看你手柄的厂家是否适配相关功能），使用BetterJoy（Github开源）可以将手柄配置出多种输入模式，并可以[[UDP]]的连接形式进行转发，在cemuhook的配置中需要以udp连接接收来自手柄的信号。更直观的是【手柄】——【BetterJoy】——【cemuhook】。关于这部分更详细的配置在[BetterJoy使用说明](https://github.com/Davidobot/BetterJoy#how-to-use)，和[cemuhook使用说明](https://cemuhook.sshnuke.net/padudpserver.html)中都有详细的教程，这里不再复述。
- 参考：[[cemu模拟器扫盲超级小白目录]Wiiu游戏之路的问题整理 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/104337967)