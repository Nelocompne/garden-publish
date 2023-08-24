public:: true
tags:: DevOps

- ## 安装和管理
- 还有什么能比直接用nvm更方便呢？
- [nvm-sh/nvm: Node Version Manager - POSIX-compliant bash script to manage multiple active node.js versions (github.com)](https://github.com/nvm-sh/nvm)
- [coreybutler/nvm-windows: A node.js version management utility for Windows. Ironically written in Go. (github.com)](https://github.com/coreybutler/nvm-windows)
- ## 相关的程序包
- ### npm
- npm 的包管理实际上应该是理解为当前项目使用的模组，而不是通常编程语言中的“库”，并依赖与此它的工作方式以目录为主，在各自的目录，也就是各自的项目，都可以管理即安装不同的模组。安装位置默认为安装在当前目录的项目中。还有“全局安装”，就类似编程语言中的“库”，因为它可以应用在所有的项目中。
- ```shell
  `npm install --save` #安装当前项目部署
  `npm install -g` #全局安装
  ```
- [[npm]]担任的工作不止是安装包而已，在一个项目中`package.json`，里面`"scripts"` 参数中记录了`npm run`可以进行的操作，这个东西就可以很方便的运行一些来自包的快捷指令（大概可以这么理解）。
- > 小技巧：package.json 在vscode中可以可视化的`调试`执行 npm run。
- ### npx
- [[Node.js]] 开发者过去通常将大多数可执行命令发布为全局的软件包，以使它们处于整个环境中且可被立即地执行。这很痛苦，因为无法真正地安装同一命令的不同版本。运行 `npx commandname` 会自动地在项目的 `node_modules` 文件夹中找到命令的正确引用，而无需知道确切的路径，也不需要在全局和用户路径中安装软件包。
- 如果想让 npx 强制使用本地模块，不下载远程模块，可以使用`--no-install`参数。如果本地不存在该模块，就会报错。`npx --no-install http-server`
- 反过来，如果忽略本地的同名模块，强制安装使用远程模块，可以使用`--ignore-existing`参数。比如，本地已经全局安装了`create-react-app`，但还是想使用远程模块，就用这个参数。`npx --ignore-existing create-react-app my-react-app`
- ## 镜像源
- 就如软件包有镜像源那样，你可以为npm配置镜像源，比如[淘宝镜像源](https://npmmirror.com/)。