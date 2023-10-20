public:: true
date:: [[Oct 5th, 2023]]

- https://github.com/BililiveRecorder/BililiveRecorder
- https://rec.danmuji.org/
- ## [[Docker]]
- ```shell
  docker run -d \
    --name=brec \
    --restart=unless-stopped \
    -v 宿主机路径:/rec \
    -p 2356:2356 \
  bililive/recorder run \
    --bind "http://*:2356" --http-basic-user "用户名" --http-basic-pass "密码" /rec
  ```
- 配置最后一行同样配置来自命令行程序