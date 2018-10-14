
---
title: Jenkins安装和配置
categories: DevOps
---


## 一、作用
项目中一直在用`Jenkins`，但自己对这部分的开发参与的不是很多，最近准备毕设的时候才开始慌了，倒腾了大半天，之前也有人问我，就准备整理了下相关知识，也便以后回顾。

我们在做项目的时候简单来说一般会有这五个步骤，**开发—>提交—>编译—>测试—>部署**。人工的流程走就是把项目同步到` Git`，再用 `SSH` 登录服务器把项目`pull`下来，再`migrate`数据库，运行单元测试和迁移静态资源，项目每天都会有若干个`commit`，在多人开发中带来许多的不便。



![Jenkins管家](http://upload-images.jianshu.io/upload_images/2190281-7b40d6e8d66d6c15.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



为了减轻人为的操作，就可以使用`Jenkins`来对项目进行持续集成。它可以帮你在写完代码后，一键完成开发过程中的一系列工作，就比如上面五个步骤中，除了第一步，后续的四步都可以自动化完成。具体的，当你完成了提交，Jenkins会自动运行你的编译脚本，编译成功后，再运行你的测试脚本，这一步成功后，接着它会帮你把新程序发布出去，完成部署。

>Jenkins是一个持续集成工具，如大家所说相当于一个调度平台，如果你的目的只是自动化部署的话，直接自己写脚本或者用`Ansible`、`Salt`、`Puppet`、`Chef`、`Fabric`等自动化部署工具就行如果你是想在`job`中加入自动话部署流程的话，可以先写好自动化部署脚本然后在`Jenkins`构建任务的`Execute Shell`中调用相应的`Script`。

重复单一易出错的操作将慢慢被机器所取代，具体到软件开发中就是，每次打包送测等操作是可以交给机器去自动执行的。以前打包给测试的流程是，测试拿了好几个手机过来，开发一一安装，然后送给测试慢慢测试。使用了持续集成之后将变成，开发本地提交代码，Jenkins等持续集成工具监测到代码变化，自动编译打包，生成开发包，测试直接拿着开发包安装测试即可。Jenkins做的操作其实很简单，它只是将我们平时做的每一步重复的操作自动化了而已。

## 二、安装（ubuntu16.04）
*`Jenkins`是开源的,使用`Java`编写的持续集成的工具*
首先需要先安装`Java`，再执行以下步骤
* 添加LTS版本PPA
``` 
$ wget -q -O - http://pkg.jenkins-ci.org/debian-stable/jenkins-ci.org.key | sudo apt-key add -
$ sudo sh -c 'echo deb http://pkg.jenkins-ci.org/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
```
* 更新源并安装Jenkins
```
$ sudo apt-get update
$ sudo apt-get install jenkins
```

* 安装后，Jenkins默认在8080端口上启动，如果8080被用，可以配置其他，比如配置为8088
```
编辑 /etc/default/jenkins  并更新HTTP_PORT到8088。

 HTTP_PORT=8088
```
* 启动`Jenkins`服务
```
$ sudo service jenkins start
```
* 关闭`Jenkins`服务
```
$ sudo service jenkins stop
```

这时已经安装成功，可以在浏览器访问`localhost:8088`
* 首次进入，首先要输入一个密钥来进入`Jenkins`,密钥可以在 /var/lib/jenkins/secrets/initialAdminPassword 获取
![复制命令行的密码粘过来](http://upload-images.jianshu.io/upload_images/2190281-d816e580280de86b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 选择相应的选项来安装插件，选择系统推荐即可
![installplugins.png](http://upload-images.jianshu.io/upload_images/2190281-7a11c5f5cd155f2d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 会有失败的情况，我搜了下，说不影响，很多由于从国外的网站下，失败很正常，直接进行下一步，后面也可以再安装
![](http://upload-images.jianshu.io/upload_images/2190281-84c6ee6fd61c1f05.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 接下来可以为Jenkins设置一个管理员帐户，以后就可以用它登录到Jenkins了
![填写即可](http://upload-images.jianshu.io/upload_images/2190281-619a6e9a88edba98.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* Jenkins安装向导成功完成后，就可以看到这个页面啦
![weblcome.png](http://upload-images.jianshu.io/upload_images/2190281-c6dff5b5813401af.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 三、安装插件

`Jenkins`提供了非常多的插件，几乎你想要的插件全有，前提是你能找的到~官网提供了插件搜索功能，选择`Plugins`页就可以各种搜索了。
![manage jenkins](http://upload-images.jianshu.io/upload_images/2190281-9f9847b0a103b368.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![plugins](http://upload-images.jianshu.io/upload_images/2190281-5c4dc2562e6789b0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



![search plugins](http://upload-images.jianshu.io/upload_images/2190281-a98ce285d172371f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

安装完成之后重启`Jenkins`

这里推荐我们使用的几个插件

* 要用Jenkins对项目进行持续集成，首先要在插件管理中下载好`Github Plugin`，使得Jenkins能操作`Github`中的仓库

* `Dashboard`插件可以用来定义自己的`Jenkins`主页 [Dashboard View](https://wiki.jenkins-ci.org/display/JENKINS/Dashboard+View)
![homepage.png](http://upload-images.jianshu.io/upload_images/2190281-ffe470335ed10f73.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* `Wall display` 用来将`jobs`的状态更加直观地显示在大屏幕上。
![display](http://upload-images.jianshu.io/upload_images/2190281-f625e6b92ccfb555.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* `Jenkins`内置的邮件功能,它可根据构建的结果，发送构建报告，给当前的committer （用git做代码管理） [Email Extension Plugin](https://link.juejin.im/?target=http%3A%2F%2Fwiki.jenkins-ci.org%2Fdisplay%2FJENKINS%2FEmail-ext%2Bplugin) 的配置
开发人员`build project` 之后，build结果无论是成功还是失败，都要及时的通知组内其他成员了解最新情况，邮件通知这时候就派上用场
**不知什么原因，用QQ邮箱配置失败了，后面若成功了会把步骤贴上来，请参照这个链接 [jenkins邮件扩展插件的使用](http://www.jianshu.com/p/2afb099f2a79)**

**我是半生不熟 喜欢照自己的怪念头行事
喜欢一切意外 想把生活过成诗的样子
若哪天有幸相遇 请别诧异 其实我并不是个乖孩子**