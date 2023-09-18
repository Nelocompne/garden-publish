public:: true
date:: [[Sep 16th, 2023]] 
tags:: DevOps

- 详细参考 [Systemd 入门教程：命令篇 - 阮一峰的网络日志 (ruanyifeng.com)](https://ruanyifeng.com/blog/2016/03/systemd-tutorial-commands.html)
- ## 参考
- 配置目录`/etc/systemd/system/`
- 配置文件`service-name.service`
- 一个依赖互联网运行的简单程序配置参考[^1]
- ```ini
  [Unit]
  Description = service-name
  After = network.target syslog.target
  Wants = network.target
  
  [Service]
  Type = simple
  ExecStart = /usr/local/example-bin
  
  [Install]
  WantedBy = multi-user.target
  ```
- 开机启动切换`systemctl enable service` & `systemctl disable service`
- 服务启动停止 `systemctl start service` & `systemctl stop service`
- ---
- [^1]:来自 [[frp]]的 [配置示例](https://gofrp.org/docs/setup/systemd/)