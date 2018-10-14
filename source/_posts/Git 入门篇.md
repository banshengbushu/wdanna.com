---
title: Git 入门篇
categories: Git
---



### 1、读音
本人一直对技术词汇的发音有不可描述的强迫症现象，所以还是先来聊一聊它的发音。


![先记住Git标志](http://upload-images.jianshu.io/upload_images/2190281-ca50fe1d44eb78e4.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

曾经偶尔不止一次地听到身边有人看着Git叫“鸡特”（谐音），从一开始的满脸懵逼到最后竟笑出了声...
![正确发音是酱紫的](http://upload-images.jianshu.io/upload_images/2190281-92a7c0df8094b53b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
我觉得作为一个程序不管是猿还是媛，为了避免引起其他猿或者是媛莫名发笑，为了避=避免被一群诧异的眼光注视，为了避免在跟别人讨论技术问题的时候被人揪着发音不放，还是确保你的发音准确吧。

 **忘掉“鸡特”，记住“给特”！**
### 2、起源
>同生活中的许多伟大事物一样，Git 诞生于一个极富纷争大举创新的年代

Git的作者是大名鼎鼎的Linus Torvalds，没错，就是Linux之父，Linus花了两周时间自己用C写了一个分布式版本控制系统，于2005发布第一个Git版本。

Git迅速成为最流行的分布式版本控制系统，尤其是2008年，GitHub网站上线了，它为开源项目免费提供Git存储，无数开源项目开始迁移至GitHub，包括jQuery，PHP，Ruby等等。

![对，就是他](http://upload-images.jianshu.io/upload_images/2190281-0923196f9000bee3.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 3、是什么

>Git是目前世界上最先进的分布式版本控制系统（没有之一）

Git是一款免费、开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目。

Git 是 Linus Torvalds 为了帮助管理 Linux 内核开发而开发的一个开放源码的版本控制软件。

### 4、解决了什么问题
* 假如你想修改一个文件，但又担心修改的不对，改的乱七八糟找不回以前的代码，这是你会怎么办呢...
你可能会说把这个文件或者文件夹copy一份在U盘或者电脑上（以前我就是酱紫干的），然后就放心的去修改了，这样当然可以解决很多问题，但有没有想过若是有天你需要修改的文件并不是一个文件，而是很多不同的文件，大小可能达到几个G，你还要用U盘拷来拷去吗，人生苦短，不如节省下来这些时间去吃个饭，跑会儿步，多看看这个大千世界呢...

* 如果有天你找到一个很久前写的代码（并不是你一个人做的修改），你很着急想知道是哪个人什么时候修改了哪一块的代码，你会怎么办？
打电话联系队友吗？确定还存着她的电话吗？她换号了怎么办？手机静音怎么办？她也不记得怎么办...

* 如果有天你被困在一个不能连接网络的地方时就像在飞机上，地下室，电梯等等，这时候你是不是也想记录自己的代码版本呢
**还有诸如此类等等很多问题，这时Git就像一个小精灵一样帮你解决这些问题**

###5、分布式控制系统
与它对应的叫集中式控制系统，两者的区别是什么呢（详情请看[廖雪峰的官方网站](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001374027586935cf69c53637d8458c9aec27dd546a6cd6000)
）
>一句话，就是：“分头做事”与“一堆人”的区别

**个人理解（这里感谢[ [icorvoh](http://www.jianshu.com/users/ecbf49bf207b) 给我的指导意见](http://www.jianshu.com/users/ecbf49bf207b/latest_articles)）**—假如现在需要五个人一起修改一份文档，然后发布到网上，这时...
* **分布式**—这五个人手里分别有这份文档的拷贝版（每份文档含有所有修改记录），然后协商后各自修改文档的不同部分，任何一个人修改完成后都可以自行发布到网上，然后本地存着最新版本，这时要合并文档的话，选择一个人作为原版解决大家的冲突，其他人当然也可以看到别人修改的部分，这时一个人的电脑出问题了没关系，别人电脑上也有拷贝版（包含最早的原版和修改后的新版本）。但由于每两个电脑很可能不在同一个局域网内，无法互相直接访问，通常引入一台充当“中央服务器”的电脑（如Github服务器），但这个服务器的作用仅仅是用来方便“交换”大家的修改而已。
* **集中式**—这五个人中需要一个领导者，他手里有这份文档的最终保存版（所有修改记录），他负责分配任务，安排谁修改哪一部分，然后其他四个人从他那里领取任务（拷贝文档的副本，不含修改记录），修改完成后各自的部分后交给这个领导者，由他发布到网上，也就是说即使大家都修改的准确无误，一旦这个领导者这里出了问题，那将功亏一篑。

###6、安装
* Linux安装Git
```
$ sudo apt-get install git
```
* Windows安装Git[请看这里](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137396287703354d8c6c01c904c7d9ff056ae23da865a000)

* 成功后查看版本号
 ```
$ git --version
git version 2.7.4
```

###7、基本配置
* 在[Github官网](https://github.com/)注册并登录自己的账号

![点击Sign in输入账号即可](http://upload-images.jianshu.io/upload_images/2190281-fdd2266ed0173ac4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![这是我的主页](http://upload-images.jianshu.io/upload_images/2190281-2392ba00a94057b7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 为了其他人方便的查看与联系提交人，所以我们第一步就是要设置自己的用户名与邮箱。执行以下代码
```
$ git config --global user.name "your name"
$ git config --global user.email "your email"
```
**git config命令的--global参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址**

* **生成SSH**（默认的https 方式在push的时候是需要验证用户名和密码的；而 SSH 在push的时候，是不需要输入用户名的，这时你的效率很提高很多），首先打开终端执行以下命令
```
$ cd ~/.ssh
$ ls
#检查是否已经存在 id_rsa.pub 或 id_dsa.pub 文件，如果文件已经存在，那么你可以跳过下一步，直接进入下下一步
$  ssh-keygen -t rsa -C "youremail"
Generating public/private rsa key pair.
Enter file in which to save the key (/home/xx/.ssh/id_rsa): 
#一直输入回车即可（不设置密码）
SHA256:83MxSnlgDza94rXX9hUJhBGnXRje+q0ABAyIl9OqHcU wangdanna1995@outlook.com
The key's randomart image is:
+---[RSA 2048]----+
|   . =.o.  o++o. |
|  . = E .. o*.o  |
|   . +    B..+ . |
|    o    + * .o .|
|   o .  S = B. o |
|  . .    = * +..o|
|          = + ..=|
|           o o oo|
|              . .|
+----[SHA256]-----+
```

* **添加你的 SSH key 到 github**
首先你需要拷贝 id_rsa.pub 文件的内容，你可以用编辑器打开文件复制，然后进入Github首页

![进入主页后，点击settings](http://upload-images.jianshu.io/upload_images/2190281-7fcc42fc3783ce48.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![点击左侧的SSH and GPG keys，然后点击右上角的New SSH key](http://upload-images.jianshu.io/upload_images/2190281-d4199c4953079c2c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

把你复制的 SSH key 代码粘贴到 key 所对应的输入框中，记得 SSH key 代码的前后不要留有空格或者回车。当然，上面的 Title 所对应的输入框你也可以输入一个该 SSH key 显示在 github 上的一个别名。默认的会使用你的邮件名称。

* **测试该SSH key**
继续在终端执行
```
ssh -T git@github.com
```
中间看到提示就输入回车，看到一下提示即成功
```
Hi username! You've successfully authenticated, but GitHub does not
# provide shell access.
```

###8、将你的代码提交到Github
* 远程创建一个仓库
进入主页点击右上角的小加号

![选择第一个New repository](http://upload-images.jianshu.io/upload_images/2190281-486b58f592c1e131.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![Repository name那里输入你的仓库名字，选中Public和Initinlize那个选项](http://upload-images.jianshu.io/upload_images/2190281-631e54867b9b8ac0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![点击clone那个绿色按钮然后复制那个地址](http://upload-images.jianshu.io/upload_images/2190281-ef64ae25e9a61dcd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 打开终端，在本地选择一个要放这个仓库的目录，输入这条命令，即可将远程仓库克隆到本地
```
$ git clone git@github.com:banshengbushu/test.git
Cloning into 'test'...
remote: Counting objects: 3, done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
Checking connectivity... done.
$ cd test
$ ls
README.md
```
* 这时你可以通过这条命令查看仓库文件的状态
```
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working directory clean
```
这说明现在的工作目录相当干净。换句话说，所有已跟踪文件在上次提交后都未被更改过，当前目录下没有出现任何处于未跟踪的新文件
* 修改README.md文件内容并保存

![](http://upload-images.jianshu.io/upload_images/2190281-dc677cda68bc7a67.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 这时使用`git status`查看哪些文件当前处于什么状态（列出已缓存、未缓存、未追踪的文件），这时这个文件变成了红色，也就是**未跟踪**的文件，意味着Git在之前的快照（提交）中没有这些文件；Git 不会自动将之纳入跟踪范围。现在，我们确实想要跟踪管理 README 这个文件

![未跟踪状态](http://upload-images.jianshu.io/upload_images/2190281-03c6091bd0e8bdaa.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 跟踪新文件
```
$ git add README.md
```
此时再运行 `git status` 命令，会看到 README 文件已被跟踪，变成绿色了，并处于暂存状态

![暂存状态](http://upload-images.jianshu.io/upload_images/2190281-66a529fdf9e1dc8a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
只要在 “Changes to be committed” 这行下面的，就说明是已暂存状态。如果此时提交，那么该文件此时此刻的版本将被留存在历史记录中

* 提交更新
现在的暂存区域已经准备妥当可以提交了。在此之前，请一定要确认还有什么修改过的或新建的文件还没有` git add`
 过，否则提交的时候不会记录这些还没暂存起来的变化。所以，每次准备提交前，先用` git status`
 看下，是不是都已暂存起来了，然后再运行提交命令
```
$ git commit -m "备注信息"
[master 279ce27] modify content
 1 file changed, 2 insertions(+), 1 deletion(-)
```
再次查看状态
```
$ git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)
nothing to commit, working directory clean
```
* 推送数据到远程仓库
```
$ git push origin master
Counting objects: 3, done.
Writing objects: 100% (3/3), 289 bytes | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/banshengbushu/test.git
   8e0624f..279ce27  master -> master
```
只有在所克隆的服务器上有写权限，或者同一时刻没有其他人在推数据，这条命令才会如期完成任务，这样就成功push了，再看看你的状态

![就跟开始一样干净啦](http://upload-images.jianshu.io/upload_images/2190281-99ec6c4bc74a9f3d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
快去刷新下你远程仓库的代码吧，是不是也一起跟新了呢
![那是必须更新的呦](http://upload-images.jianshu.io/upload_images/2190281-8acd0c4d0a068cd1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

###9、学习资料整理

* 韩亦乐同学写的git入门文档：[http://www.jianshu.com/p/b238de250c06](http://www.jianshu.com/p/b238de250c06)， 有问题可以与 [@icorvoh](https://bbs.excellence-girls.org/uid/58) 交流
* 视频教程《版本控制入门 – 搬进 Github》：[http://www.imooc.com/learn/390](http://www.imooc.com/learn/390)
* 胡皓提供的Git学习资源指南: [https://github.com/iamcoach/git](https://github.com/iamcoach/git)
* Git简明指南：[http://rogerdudler.github.io/git-guide/index.zh.html](http://rogerdudler.github.io/git-guide/index.zh.html)
* 免费的git书箱 progit2: [https://www.gitbook.com/book/bingohuang/progit2/details](https://www.gitbook.com/book/bingohuang/progit2/details)，点击 Download PDF按钮下载
* git常用命令手册：[https://bbs.excellence-girls.org/topic/166](https://bbs.excellence-girls.org/topic/166)
* 廖雪峰的git在线教程：[http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
* 在线尝试git: [https://try.github.io/](https://try.github.io/)， 中文翻译在这里：[http://blog.csdn.net/u011109881/article/details/51447500](http://blog.csdn.net/u011109881/article/details/51447500)
* Git学习资源汇总：[http://www.jianshu.com/p/55496ff224e9](http://www.jianshu.com/p/55496ff224e9)

**我是半生不熟 喜欢照自己的怪念头行事
喜欢一切意外 想把生活过成诗的样子
若哪天有幸相遇 请别诧异 其实我并不是个乖孩子**