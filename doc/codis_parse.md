###Codis 目源码录结构?

目录								  功能
models								Models包，封装了slot, server-group, server,proxy, action对象操作接口以及常量定义。所有关于对象的操作（读取、修改、关系等）通过该包进行调用
proxy								  proxy-server实现相关
	cachepool						缓存池相关
  group						  	proxy-server 封装对group的操作
  parser							proxy-server中对解析相关的操作
  redispool						Proxy与redis操作的池实现
  route							  服务启动，接收请求，反向代理等
	topology					  封装对zookeeper的统一操作接口，包括slot、server-group、proxyInfo等，供proxyserver调用。内部会使用models接口
utils								  提供一些工具操作接口，包括与redis和通用的
cmd									  包括codis-config 服务和 proxy主入口
cconfig								codis-config 服务相关
  main.go							codis-config入口 main
proxy.go							condis-config 与 proxy之间通信的接口
  slot.go             封装codis-config与slot
  server-group.go		  server-group操作相关的接口
  migrate负载均衡相关			
  action						 codis-config产生action的接口，并同步到zk上
  dashbord					 管理界面，面板
proxy								  Proxy的主入口main
extern								针对redis-2.8.13封装的几个命令实现，以及redis-port
