public:: true
date:: [[Jul 16th, 2023]] 
tags:: DevOps

- nginx都是大家熟知的角色了，当然在[[Docker]]上运行也非常简单。
- 默认下nginx的配置文件只需要存在指定目录中就可读取运行，默认为`/etc/nginx/conf.d` ，而`/var/www/html` 作为配置中指明的话作为网站部署的页面地址，通常是静态网页，这点README中可能介绍的不是非常明确。但是在docker使用中要格外注意这些要挂载的目录。
- 以及[[Docker]]的网络模式是选择端口还是直接host，大家都可以灵活选择。
- 以及为了容器的时间能和宿主机一致，可以选择挂载上`/etc/localtime` ，当然也可以通过别的方法代替都是可以的。