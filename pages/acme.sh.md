public:: true
date:: "2023-07-16"
tags:: DevOps

- 项目地址： https://github.com/acmesh-official/acme.sh
- acme.sh支持智能识别nginx和apache的配置生成证书，并且完成后不留痕，不过推荐的用法是域名套[dns管理api生成证书](https://github.com/acmesh-official/acme.sh/wiki/dnsapi)。也支持docker粉丝使用，不过acme.sh用了新的[签发ZeroSSL生成](https://github.com/acmesh-official/acme.sh/wiki/ZeroSSL.com-CA)，只需要一个邮箱信息进行登记就可直接使用，docker由于跳过了安装所以这个过程要手动注册。生成证书后就是安装了，所谓安装就是生成我们真正要使用的证书，就像密钥生成密钥对，[安装证书的时候](https://github.com/acmesh-official/acme.sh/wiki/%E8%AF%B4%E6%98%8E#3-copy%E5%AE%89%E8%A3%85-%E8%AF%81%E4%B9%A6)可以对不同服务端配置区别，但本质一样要重启服务端。