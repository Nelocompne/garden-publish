public:: true
tags:: DevOps

- # C#
- [[.NET]] 作为一个跨平台环境，以 C# 作为编程语言。而 C# 基本上也只服务于基于 .NET 的内容。
- # 开发部署
- 如果要用 .NET 开发，那部署环境来说，说简单也不简单，说难也不难。微软为它的 [[Windows]] 付出了一些，比如 [[IDE]] 的 [[Visual Studio]] 。它几乎可以完成所有的 .NET 开发了，不过它是纯窗体的。
- 如果要满足一个真正在（ in ）跨平台的开发，那 [[.NET SDK]] 就是这样的存在，在程序包中它名叫[[Dotnet]]，它囊括了在开发中需要的工具链，在早期叫做 [[.net framework]]。[官方文档](https://docs.microsoft.com/zh-cn/dotnet/)。
- > 吐槽：`dotnet`包含了三个主要内容，在官方文档介绍它们的时候，我认为有些滑稽。比如安装`.NET CLI`需要先安装`.NET SDK`，而安装它要参考安装`.NET Core`，然后再去看就告诉你安装`.NET Core`中包含安装`.NET SDK`，于是你去看安装`.NET SDK`后又告诉你——安装`.NET SDK`中包括了以上的所有东西。XD
- ## 快速阅读：
  [[.NET Framework]] Windows 下 .NET 的开发平台
- [[.NET Standard]] 为所有 [[.NET 5]] 之前的统一标准API