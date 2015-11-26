在Linux操作系统中，经常需要查看日志文件的实时输出内容，通常会使用`tail -f`或者`tailf`命令。查看实时日志可能会需要首先SSH连上Linux主机，步骤很麻烦不说，如果是生产环境的服务器，可能还会控制各种权限。此时可以考虑基于Web显示实时日志。

由于传统的HTTP协议是请求/响应模式，而实时日志需要不定时的持续的输出，有新的日志内容时需要由服务器主动推送给客户端浏览器。所以这里使用的是HTML5的WebSocket协议。

按照惯例，先上图：
![Web实时日志](http://7xidft.com1.z0.glb.clouddn.com/blog/20151125195638286.jpg)

## Getting Started
在Linux下用Maven Jetty插件运行Demo：
```
git clone https://github.com/wucao/websocket-tail-demo.git
cd websocket-tail-demo
mvn jetty:run
```
成功后可以在http://localhost:8080/查看实时日志。

## 部署
可以将项目部署在支持JSR 356的服务器，例如Tomcat、Jetty的最新版本。由于用到tail命令，该项目需要部署在Linux系统上。
