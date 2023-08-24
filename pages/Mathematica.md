public:: true

- 相比起 [[Matlab]] 更“人性化”的工程软件。全套及相关代替品指南、安装与下载参考：[Mathematica 激活指南](https://tiebamma.github.io/InstallTutorial/)
- ## vscode中使用（废弃）
- ### 建立可靠的wolfram jupyter notebook（并不一定）
- 直接`ctrl+shift+p`呼出`Jupyter: Enter the url of local/remote Jupyter Notebook`
  [查阅](https://marketplace.visualstudio.com/items?itemName=donjayamanne.jupyter)
- ### 关于[[vscode]]使用[[jupyter]]启动[[wolfram]] engine
- 而在vscode中比较难处理虚拟环境中python版本与wolfram的链接关系。而jupyter notebook是前端，最好的解决方法就是独立启动venv.python.jupyter这个环节，然后在vscode中制定一个现有的服务器。而它有一个token，如果不自行指定会不知道vscode自行开启的jupyter和独立开启的弄混，所以我们可以使用jupyter的服务器配置文件指定token。
- 执行`jupyter notebook --generate-config`参数，随后会输出生成的配置文件地址，一般在`~/.jupyter/jupyter_notebook_config.py`，编辑其中的token指定即可，为使用方便还可以将`c.NotebookApp.open_browser`关闭。
- 结论：**别用**