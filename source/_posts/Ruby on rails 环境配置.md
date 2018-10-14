---
title: Ruby on rails 环境配置
categories: Web 前端

---



###配置之前
从开始到现在不知道怀疑了多少遍网速，从实验室的无线到有线，从学校的CMCC到EDU到xayd，不知道执行了多少遍`Ctrl V` 和 `Ctrl C`，终于，功夫不负有心人，它成功了！！！
![9788E4C3095705CD21EA9BC6C45EBCF7.jpg](http://upload-images.jianshu.io/upload_images/2190281-ce46be153e9ce030.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

周围有同学用`apt-get`安装的，有用`rbenv`安装的，也有用`rvm`安装的，这里简单介绍下它们分别是什么吧
>rvm 的设计理念是自动化，全面。 rbenv 的设计理念是规范化，小核。

* `apt-get`只能安装一个版本，如果使用了`sudo apt-get update`后安装则是最新的版本
* `rvm`和`rbenv`都是`Ruby`的版本管理工具，都可以安装多个`Ruby`版本，`rvm`应该是最早出现、使用最多的，`rbenv` 比较受欢迎，所以选择哪个自己看喽，本人使用的是`rbenv`安装，

###配置步骤

```
$ cd $HOME
$ sudo apt-get update 
$ sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev python-software-properties libffi-dev

$ git clone https://github.com/rbenv/rbenv.git ~/.rbenv
$ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
$ echo 'eval "$(rbenv init -)"' >> ~/.bashrc
$ exec $SHELL

$ git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
$ echo 'export PATH="$HOME/.rbenv/plugins/ruby-build/bin:$PATH"' >> ~/.bashrc
$ exec $SHELL
```
确保每一步执行成功后，更改rvm源服务器资源信息，毕竟国外的经常被墙掉，还有就是国内的速度快。若不设置，下面可能出现各种问题，如出现服务器积极拒绝（被墙），或者下载速度慢，执行以下命令
```
$ sed -i -e 's/ftp\.ruby-lang\.org\/pub\/ruby/ruby\.taobao\.org\/mirrors\/ruby/g' ~/.rvm/config/db
```
查看`rbenv`版本
```
$ rbenv -v
rbenv 1.1.0
```
查看可用的 ruby版本
```
$ rbenv install --list
```
这里我选择安装最新版本
```
$ rbenv install 2.3.3
Downloading ruby-2.3.3.tar.bz2...
-> https://cache.ruby-china.org/pub/ruby/2.3/ruby-2.3.3.tar.bz2
Installing ruby-2.3.3...
Installed ruby-2.3.3 to /home/xx/.rbenv/versions/2.3.3
```
设置全局版本（全局版本是在没有找到“当前终端”或“本地”作用域的设置时执行）
```
$ rbenv global 2.3.3
```
查看安装的`ruby`版本
```
$ ruby -v
ruby 2.3.3p222 (2016-11-21 revision 56859) [x86_64-linux]
```
`gem`就是`ruby`的软件包.，所以可以直接使用`gem`
`bundle`是`rails`框架里面安装`Gemfile`指定的各种库的工具，先安装了

```
$ gem install bundler
Fetching: bundler-1.13.6.gem (100%)
Successfully installed bundler-1.13.6
Parsing documentation for bundler-1.13.6
Installing ri documentation for bundler-1.13.6
Done installing documentation for bundler after 6 seconds
1 gem installed
```
接下来这条命令的作用[看这里](https://rubygems.org/gems/rbenv-rehash/versions/0.3)，我试了不执行就会出错
```
$ rbenv rehash
```

###Ruby和Rails的关系
>**Ruby**是编辑语言，Rails是基于Ruby来实现的一个用于网站开发的MVC框架，学习Rails需要一些Ruby的基础知识，先学Ruby

>**Ruby on Rails**（官方简称为 Rails。也有人简称为 RoR，该缩写目前仍于一些中文讨论中被使用。），是一个使用[Ruby](https://zh.wikipedia.org/wiki/Ruby)语言写的[开源](https://zh.wikipedia.org/wiki/%E5%BC%80%E6%BA%90)[Web應用框架](https://zh.wikipedia.org/wiki/Web%E5%BA%94%E7%94%A8%E6%A1%86%E6%9E%B6)，它是严格按照[MVC](https://zh.wikipedia.org/wiki/MVC)结构开发的。它努力使自身保持简单，来使实际的应用开发时的代码更少，使用最少的配置。
安装`rails`

###安装Rails
```
$ gem install rails
Fetching: nokogiri-1.6.8.1.gem (100%)
Building native extensions.  This could take a while...
Successfully installed nokogiri-1.6.8.1
Fetching: loofah-2.0.3.gem (100%)
Successfully installed loofah-2.0.3
Fetching: rails-html-sanitizer-1.0.3.gem (100%)
Successfully installed rails-html-sanitizer-1.0.3
Fetching: rails-dom-testing-2.0.1.gem (100%)
Successfully installed rails-dom-testing-2.0.1
Fetching: builder-3.2.2.gem (100%)
Successfully installed builder-3.2.2
...
Done installing documentation for nokogiri, loofah, rails-html-sanitizer, rails-dom-testing, builder, erubis, actionview, actionpack, activemodel, arel, activerecord, globalid, activejob, mime-types-data, mime-types, mail, actionmailer, nio4r, websocket-extensions, websocket-driver, actioncable, thor, method_source, railties, sprockets, sprockets-rails, rails after 45 seconds
27 gems installed
```
成功后查看版本
```
$ rails -v
Rails 5.0.0.1
```

**我是半生不熟 喜欢照自己的怪念头行事
喜欢一切意外 想把生活过成诗的样子
若哪天有幸相遇 请别诧异 其实我并不是个乖孩子**