---
title: Trello 无法打开
categories: 工具
---



一直用的好好的`Trello`，某天打开它却突然成了这个样子，什么鬼......


![chrome打开的样子.png](http://upload-images.jianshu.io/upload_images/2190281-557afbbd2033bd93.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


很明显不是翻墙的问题，于是按照提示刷新了几遍，但还是不行，看到它说浏览器的问题，于是跑去`FireFox`试了试，果然是好的

![fireFox好好的](http://upload-images.jianshu.io/upload_images/2190281-9eb6b9fa55d593ab.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

那么问题来了...... That's Why?? 

google了下原因和解决办法

* 原因
**事实上，它是关于SSL证书问题 - Chrome无法访问Trello CDN**
* 解决办法
**访问这个链接 [https://d78fikflryjgj.cloudfront.net/test.html](https://d78fikflryjgj.cloudfront.net/test.html)，这时chrome会弹出警告，选择信任该链接，然后再返回`Trello`主页即可**，参考下图

![点击ADVANCED.png](http://upload-images.jianshu.io/upload_images/2190281-e3c98ee8cc98c619.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![点击最后一行.png](http://upload-images.jianshu.io/upload_images/2190281-62cec2b5442c97d1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![点击Trello.png](http://upload-images.jianshu.io/upload_images/2190281-8fec78e0d4a3816c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![成功进去了.png](http://upload-images.jianshu.io/upload_images/2190281-764800919961dcf6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

感觉好神奇的样子，我还是去看看这些都是什么吧

* SSL证书
>SSL证书通过在客户端浏览器和[Web服务器](http://baike.baidu.com/view/460250.htm)之间建立一条SSL安全通道（Secure socket layer(SSL)安全协议是由Netscape Communication公司设计开发。
简单来讲：服务器部署了[SSL 证书](http://cn.globalsign.com/) 后可以确保用户在浏览器上输入的机密信息和从服务器上查询的机密信息从用户电脑到服务器之间的传输链路上是高强度加密传输的，是不可能被非法篡改和窃取的。同时向网站访问者证明了服务器的真实身份，此真实身份是通过第三方权威机构 （GlobalSign） 验证的。也就是说有两大作用：数据加密和身份认证。
* CDN
>Content Delivery Network的简称，即“内容分发网络”，一般我们所说的CDN加速，一般是指[网站](http://www.xujiahua.com/tag/website-skill)加速或者用户下载资源加速
CDN基本思路就是尽可能避开互联网上有可能影响数据传输速度和稳定性的瓶颈和环节，使内容传输的更快、更稳定。通过在网络各处放置节点服务器所构成的在现有的互联网基础之上的一层智能虚拟网络，CDN系统能够实时地根据网络流量和各节点的连接、负载状况以及到用户的距离和响应时间等综合信息将用户的请求重新导向离用户最近的服务节点上
简单来说，就是加速，当一个网站开启了CDN加速，其给用户的感觉是访问网站速度或者下载东西的速度会明显比没有开启加速更快，变快或者下载东西变快了。

**我是半生不熟 喜欢照自己的怪念头行事
喜欢一切意外 想把生活过成诗的样子
若哪天有幸相遇 请别诧异 其实我并不是个乖孩子**