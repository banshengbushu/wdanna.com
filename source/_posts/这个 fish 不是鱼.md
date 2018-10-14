---
title: 这个 fish 不是鱼
categories: 工具

---



### 1、介绍

![](http://upload-images.jianshu.io/upload_images/2190281-4a697bfc715e520a.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
fish是一个用户友好的命令行[外壳程序](http://baike.baidu.com/view/542.htm)全称Friendly Interactive Shell可用于如 [Linux](http://baike.baidu.com/view/1634.htm) 这样的 Unix 类[操作系统](http://baike.baidu.com/view/880.htm)中

>二逼青年用 bash，普通青年用 zsh，文艺青年用 [fish](http://fishshell.com/)

`fish`的主页这样说—**好了，这是一个为 90 后而生的命令行 shell**

**对于一个没有学过并且不需要学习 bash（或者 Posix shell），我感觉 fish 是一个更好的选择**
#### 2、好处
那些高端的好处并没有使用过多少，就自身使用过的经验来说感觉最人性化的好处有
* **语法高亮**—可以在写命令的时候就知道对错，节省时间

![正确命令](http://upload-images.jianshu.io/upload_images/2190281-879bfe66bfe16a17.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![不存在命令](http://upload-images.jianshu.io/upload_images/2190281-3a818e21ba0eb688.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* **智能建议，根据历史输入自动补全**—非常好用，很长的命令直接Tab补全即可

![可以记录以前使用过的命令](http://upload-images.jianshu.io/upload_images/2190281-e010f1e2ff26a110.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* **快速跳转历史输入目录**
dirh (dir history)就可以显示当前会话中进入的文件夹纪录
```
$ dirh
/home/Documents/study/xiShuaShua
/home/Documents/study/xiShuaShua/public
/home/Documents/study/xiShuaShua/public/src
/home/Documents/study/xiShuaShua/public/src/components
```
 ` prevd `和 `nextd`跳转
假如曾进入过 1 2 3 4 5 这几个文件夹, `prevd 4` 可以让你在 5 中直接跳到 1
```
$~/D/s/xiShuaShua> prevd 1
~/D/s/x/public> 
```

#### 3、安装
* 执行以下命令
```
$ sudo apt-add-repository ppa:fish-shell/release-2
$ sudo apt-get update
$ sudo apt-get install fish
```
* 打开终端启动`fish`
```
$ fish
```

#### 4、改为默认shell
* 执行这条命令查看路径
```
$ which fish
#我的路径如下
/usr/bin/fish
```
* 设置默认shell
```
$ chsh -s /usr/bin/fish
```
* 重启终端打开即可

#### 5、安装nvm
----------------------------
其实用**fish**已经很久了，但一直由于自己的误解，今天才解决这个问题——不能使用**nvm**,其实很简单，依次执行以下命令
* 首先依次执行
```
$ git clone https://github.com/creationix/nvm.git ~/.nvm
$ cd ~/.nvm
$ ~/.nvm> git checkout (git describe --abbrev=0 --tags)
$ cd ~/.config/fish
$ ~/.c/fish> git clone git://github.com/passcod/nvm-fish-wrapper.git nvm-wrapper
```
* 在`config.fish`中加入底下这句命令
```
source ~/.config/fish/nvm-wrapper/nvm.fish
```
* 检查是否成功
```
$ nvm --version
0.29.0
```

#### 6、快去试试吧
----------------------------
**“fish 这条鱼非常有营养。”**
**医生的意见是对的：吃 “鱼” 对您有益**

**我是半生不熟 喜欢照自己的怪念头行事
喜欢一切意外 想把生活过成诗的样子
若哪天有幸相遇 请别诧异 其实我并不是个乖孩子**