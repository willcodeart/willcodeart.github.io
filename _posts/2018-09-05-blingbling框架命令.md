---
title: 框架命令
description: 框架相关命令内容整理
categories:
tags:


---

##### SPRING-BOOT后端

安装lombok

mac下操作步骤：

1.官网下载lombok.jar （ https://projectlombok.org/download.html）

2.找到Eclipse应用（在Mac上就是Eclipse.app文件），选择打开包内容，找到eclipse.ini

3.将lombok.jar拷贝至eclipse.ini所在目录下，并在eclipse.ini文件最后加上如下两行

```
-Xbootclasspath/a:lombok.jar
-javaagent:/Users/abc/Eclipse/eclipse-jee-mars-1-macosx-cocoa- x86_64/Eclipse.app/Contents/Eclipse/lombok.jar
```

4.重启eclipse

##### VUE 前端

当我们使用默认配置从npm官网下载模块时，由于网络的因素，会导致我们的下载速度特别慢。所以，我们可以配置一些国内的镜像来加快我们的下载速度。在这里，我推荐使用[淘宝的npm镜像](淘宝 NPM 镜像), 具体使用方式如下:

临时使用, 安装包的时候通过`--registry`参数即可

```
npm install express --registry https://registry.npm.taobao.org
```

全局使用

```
 $ npm config set registry https://registry.npm.taobao.org
  // 配置后可通过下面方式来验证是否成功
  npm config get registry
  // 或
  npm info express
```

使用cnpm使用

```
  // 安装cnpm
  npm install -g cnpm --registry=https://registry.npm.taobao.org

  // 使用cnpm安装包
  cnpm install express
```

##### REDIS

```
src/redis-server

redis_cli

keys *

flushall

```

