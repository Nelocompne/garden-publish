public:: true
date::  [[Dec 27th, 2022]]

- # ikemen
- MUGEN 已经万年没更新了，而且有一些需求已经无法满足，比如64位程序的更多内存支持、键盘手柄支持、联机服务…这些都没有，玩家需要打上制作的补丁才能支持。况且因为 MUGEN 获得来源不同，上面甚至可能携带来自 “上古” 时期的电脑病毒，所以还是推荐使用 Ikemen 作为你的引擎。
- _[Ikemen-go](https://github.com/ikemen-engine/Ikemen-GO)_ 是用 #golang 重写的引擎，开发者将它开源，你可以在Github上找到该项目代码。
- Ikemen 支持 MUGEN 的所有功能，并且还支持新的特性，优化更好，支持 Lua 脚本，以及支持上面提到的玩家需要但是 MUGEN 没有的功能。更重要的是，因为开源，会有开发者为其不断的持续更新，同时 Golang 支持编译不同的平台，也就是说不止在 Windows 上运行 MUGEN，还可以在 Linux 或苹果设备运行。
- 但是 Ikemen 也有一点缺点，就是编写的配置文件中不能包含多种编码，这就要求制作者尽可能的使用UTF-8码编写配置，相比起来 MUGEN 在这方面没有限制。
- | 功能/引擎    | Ikemen-go | M.U.G.E.N |
  |----------|-----------|-----------|
  | 4G以上内存支持 | ✔         | ❌         |
  | 游戏手柄支持   | ✔         | ❌         |
  | 联机服务     | ✔         | ❌         |
  | Lua扩展    | ✔         | ❌         |
  |  跨平台支持 | Windows/Linux/Mac       |  仅Windows     |
  |  配置多编码支持 | 仅UTF-8       |  不限     |
- # 制作工具
- 和其他任何游戏一样，你需要有个文本编辑器、内容制作工具、图像处理工具。在 2023 年，这方面你有太多的选择，这方面我十分推荐文本编辑器 [Visual Studio Code](https://code.visualstudio.com/)，MUGEN 内容制作工具 [Fighter Factory Studio](http://fighterfactory.virtualltek.com/)（[汉化补丁](https://qxmugen.com/tools/10049)），图像处理工具 [Krita](https://apps.kde.org/zh-cn/krita/)，[GIMP](https://www.gimp.org/)。选择它们的原因是因为都很强大，并且免费。处理编码，制作脚本的语法高亮，制作色表（Sprite Sheet）……
- 还有一些额外的推荐，录制你的电脑视频：[OBS Studio](https://obsproject.com/)，录制一个动画GIF [ScreenToGif](https://www.screentogif.com/)。
- # 如何做一款自己的mugen
- 和任何一款游戏一样，即使是mugen这样的格斗游戏，它包含已有的框架可以免去很多开发成本。但是你依然要面对大多数游戏制作中的挑战：美术、画面、动画、声音、音乐、脚本、函数逻辑甚至剧本等等……
- 所以这注定了制作一款自己的mugen不会是简单的事情，所以第一件事就是认清，有了mugen并不会让你做一款格斗游戏轻松多少，你需要会很多东西，除非你有朋友可以为你分担一些工作。
- 但如果你真的下定决心想为自己的角色、或是喜欢的角色能够在擂台上叱诧风云，也不用因此气馁，幸运的是我们有互联网，互联网有大量的经验和示例可以给我们参考，再者就像我说的，你可以找到一些朋友，他们总有擅长的一方面，他们可以帮助你完成一些工作。
- # 辅助工具
- **VSelect**🔎 用于调整人物选择面板的工具。
	- 千寻地址 [VSelect](https://qxmugen.com/tools/10116)
	- wiki介绍 [VSelect](https://mugen.fandom.com/wiki/VSelect)
	- 官方页面 [VSelect](http://tunglashor.webnode.com/products/vselect/)
	- gamebanana论坛 [VSelect](https://gamebanana.com/tools/6090)
- **瑞士军刀**🏑又译十德，是来自日本 MnsUouxgOs 和 Ziddia 开发的 mugen 瑞士军刀，可以用于 mugen 运行中的调试。
	- 千寻地址 [十德（兼容mugen全版本） ](https://qxmugen.com/tools/10115)
	- 官方博客地址 [MUGEN Room](https://ziddia.blog.fc2.com/)
	- 更新地址 [Update: Swiss Army Knife for 1.1 (2021/07/05 version) ](https://ziddia.blog.fc2.com/blog-entry-62.html)
	- 开源地址 [SwissArmyKnife](https://github.com/ZiddiaMUGEN/SwissArmyKnife)
- # 游戏交流社区
- [Everything M.U.G.E.N. (reddit.com)](https://www.reddit.com/r/mugen/)
- [mugen吧-百度贴吧](https://tieba.baidu.com/f?kw=mugen&ie=utf-8)
- [千寻分享 (qxmugen.com)](https://qxmugen.com/)
- # 额外阅读
- [[MUGEN全面教程（摘抄）]]
- [[对于MUGEN圈现状的看法]]