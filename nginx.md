# nginx学习笔记

## 前言

Nginx是一个高性能的`HTTP`和`反向代理`服务器，也是一个`IMAP/POP3/SMTP`服务器。Nginx是由伊戈尔·赛索耶夫为俄罗斯访问量第二的`Rambler.ru`站点（俄文：Рамблер）开发的。它也是一种轻量级的web服务器，可以作为独立的服务器部署网站（类似TOMCAT）。它高性能和低消耗内存的结构受到很多大公司青睐，如淘宝网站架设。

## 安装

##### windows

* [下载链接](http://nginx.org/en/download.html)

* 启动： nginx

* 关闭： nginx -s stop

* 重启： nginx -s reload

* 检查配置: nginx -t

    ```
    nginx: the configuration file /usr/local/etc/nginx/nginx.conf syntax is ok
    nginx: configuration file /usr/local/etc/nginx/nginx.conf test is successful
    ```
<hr/>

## 一、什么是反向代理与负载均衡

### 1、反向代理

##### 1）、代理服务器

* 定义： 代理服务器，客户机在发送请求时，不会直接发送给目的主机，而是先发送给代理服务器，代理服务接收客户机请求之后，再向主机发出，并接收目的主机返回的数据，存放在代理服务器的硬盘中，再反送给客户机。

* 为什么使用代理服务器
    * 提高访问速度： 目标主机返回的数据会存放在代理的服务器硬盘中，因此下一次客户机在访问同一个站点数据时，会直接从代理服务器的硬盘中读取，起到了缓存的作用。
    * 防火墙作用： 所有客户机请求都必须通过代理服务器访问远程站点，因此可在代理服务器上设限，过滤不安全的信息
    * 通过代理服务器访问不能访问的目标站点： 翻墙
    
##### 2)、反向代理 vs 正向代理


##### 3）、反向代理配置

**proxy_pass**

```json
server {
	listen 4567;  // 监听端口
	server_name www.example.com; // 映射域名
	location / {
		proxy_pass http://192.168.220.189:93;  // 代理的地址
	}
}
```

### 2、 负载均衡

建立了一个服务器集群，当用户访问网站的时候，先访问一个中间服务器，再让这个中间服务器在服务器集群中选择一个压力较小的服务器，然后将该访问引入选择的服务器。分担服务器的压力，避免服务器崩溃的情况。

**nginx会给你分配服务器压力小的区访问**

* http重定向
* DNS负载均衡
* 反向代理负载均衡
* IP负载均衡(LVS-NAT)
* 直接路由(LVS-DR)
* IP隧道(LVS-TUN)

## 二、服务器集群

服务器集群就是指将很多服务器集中起来一起进行同一种服务,在客户端看来就像是只有一个服务器.集群可以利用多个计算机进行并行计算从而获得很高的计算速度,也可以用多个计算机做备份,从而使得任何一个机器坏了整个系统还是能正常运行.

## 三、分布式

是将不同地点的，或具有不同功能的，或拥有不同数据的多台计算机通过通信网络连接起来，在控制系统的统一管理控制下，协调地完成大规模信息处理任务的计算机系统。

> 分布式和集群区别

分布式:一个复杂业务分拆多个子业务,部署在不同的服务器上.
集群:同一个业务,部署在多个服务器上.
集群是个物理形态,分布式是个工作方式
集群一般是物理集中、统一管理的,而分布式系统则不强调这一点.