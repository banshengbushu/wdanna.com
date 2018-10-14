---
title: 你不知道 Ubuntu 我来告诉你
categories: Linux

---



### 1、起源

![Ubuntu是平民出身的绅士](http://upload-images.jianshu.io/upload_images/2190281-cf11259e492a5448.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 发音—国际音标：英语发音：`/ʊˈbʊntuː/`
* 由马克·舍特尔沃斯创立，其首个版本—4.10发布于2004年10月20日。
* 其名称来自非洲南部祖鲁语或科萨语的“ubuntu”一词（译为乌班图），意思是“人性”、“我的存在是因为大家的存在”，是非洲传统的一种价值观
* 独立之精神，自由之思想—与大家共勉，向开源致敬。

###2、与Linux的关系
首先还是发音，有人这样调侃—Linux是自由的，包括它的发音


![哈哈，咱们不闹](http://upload-images.jianshu.io/upload_images/2190281-a34f7636eccb197a.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
**很庆幸一开始，我就接触到了正确的读音，其实身边80%的发音都不对，它的音标是这样的—` [‘li:nэks]`，谐音—“哩呐克斯”，附上linus torvalds（Linux内核的发明人及该计划的合作者）的一段录音[听听看](http://richardlee.blog.51cto.com/gallery/9729/9729_1346.mp3)**

>一句话—Ubuntu是世界上最流行的Linux发行版，也是各种推荐入门Linux爱好者安装的一个Linux发行版)

一提到 Linux，许多人都会说到“自由”，但我们是否都知道“自由”的真正涵义呢？

“自由”是一种权力， 它决定你的计算机能做什么，同时能够拥有这种“自由”的唯一方式就是知道计算机正在做什么。 “自由”是指一台没有任何秘密的计算机，你可以从它那里了解一切，只要你用心的去寻找。

>Linux不就是敲命令嘛？和DOS有啥区别嘛？
嗯，这其实就是百姓眼里Linux的真实写照。Linux对平常人而言，是命令行，是来自远古的怪兽。

Linux 是从极客的学生宿舍里走出来的操作系统，更是通过互联网完成协同开发的典范，汇集了全球极客的智慧

Linux像是平民女神，不华美，自带一股冷艳的气质。折腾过程会遇到各种乍看起来稀奇古怪的问题。


![free and open](http://upload-images.jianshu.io/upload_images/2190281-e7f879846cd30cb5.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


我用Ubuntu算起来也有一年多了，从开始的双系统，到现在只有Ubuntu，改变的不仅仅是电脑环境，还是我的学习方式、生活习惯和办事效率。

**就有一种当你找到对的人的时候，就会有种相见恨晚的感觉，对其他的人也就兴趣不大了。
你总会发现他这个不好，那个不好，但是你换做其他的时候，你却总想着他的好。**
###3、Ubuntu比起windows好在哪里

>用户知道自己想要生么，也明白自己在做什么，并且会为自己的行为负责

以前总有同学问我，“大家都说Linux好，你告诉我到底好在哪里？”
我—“开源，快，免费啊...”
“那跟你有什么关系”
“...(思考了半天)现在好像是没有什么关系...”
今天，我终于可以说出来它究竟好在哪里了，实际的看得见感受的到的好...
 * 自己用的体验，比windows快，尤其开机关机快好多，可以运行在比较老旧的电脑上。（AMD Athlon 3600+ / 1G RAM 运行毫无压力）

 * 在知道要计算做什么的时候直接给出相应的命令操控电脑，比如我需要安装 Firefox，只需要键入：`sudo apt-get install firefox`，你再想想windows...

 * 版本更新较快，基本半年一个版本

 * 免费，还是免费，终于不用找各种好的版本的盗版windows系统了。每次windows升级都要去网上找好长时间的破解教程

 * 社区比较活跃，几乎遇到的问题都能在上面个找到答案

 * 想装软件立马装起来想卸载立马删掉想换个系统尝鲜根本不用格盘丢数据丢注册表丢驱动甚至直接chroot就能做到发行版切换；

 * 多样的低成本（多数软件是免费的而且不用花力气花时间去寻找）的应用。`sudo apt-get` 解决掉90%以上的软件需求，而且这些软件都很纯净、干净，绝对不会像windows下面一样各种弹窗和广告。我猜windows下面大家找杀软就要找半天。

* 编程环境友好，不需要像windows那样配置复杂的编程环境

###4、安装Ubuntu
你可以戳[这里](http://www.jianshu.com/p/2eebd6ad284d)，很详细的教程，建议新手可以先安装windows+ubuntu双系统。
###5、常用快捷键
安装好了吗，来个彩蛋，在你的终端输入一条有意思的命令，大家可在评论区贴出来呦，看看你平时都喜欢干什么～
```
$ history | awk '{print $2}' | sort | uniq -c | sort -rm | head -10
```
因为重新装过一次系统，我的是酱紫哒，统计了你使用过的命令的频率
```
 2 ^[[200~docker
      1 bahs
      7 bash
      1 cat
    137 cd
      1 CD
      1 chmod
      1 chsh
      1 clear
      1 cnpm
```
这些基本的你要会用哦...
* Ctrl-U: 擦除一行光标前面的部分。
* Ctrl-H: 擦除光标前面的一个字符。
* Ctrl-D: 终止输入。（退出shell，如果您正在使用shell的话）。
* Ctrl-C: 终止当前正在运行的程序。
* Ctrl-Z: 暂停程序
* Ctrl-S: 停止向屏幕输出。
* Ctrl-Q: 重新激活向屏幕输出。
* 默认的shell，bash， 有历史编辑和tab补齐功能。
* up-arrow: 开始历史命令搜索。
* Ctrl-R: 开始增量历史命令搜索。
* TAB: 完整的把文件名输入到命令行。
* Ctrl-Shift-C 终端复制
* Ctrl-Shift-V 终端粘贴

快捷键在这里设置


![可自行更改](http://upload-images.jianshu.io/upload_images/2190281-d245b6113e3b8c01.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

###6、推荐的终端
* [gauke](http://guake-project.org/)—一个下拉式的终端程序，F12一键呼出，可设置透明，绝对好用

![张这样子](http://upload-images.jianshu.io/upload_images/2190281-b7734e4c3b64368e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



![谐音—挂科，哈哈](http://upload-images.jianshu.io/upload_images/2190281-4f90b9e1039f685d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  1、安装

```
$ sudo add-apt-repository ppa:webupd8team/unstable
$ sudo apt-get update
$ sudo apt-get install guake
```
2、设置guake为默认的terminal：
`$ sudo update-alternatives --config x-terminal-emulator`
3、然后输入guake所在的序号

* [zsh](http://ohmyz.sh/)—有强大的自动补全功能，能自动补全命令、参数、文件名、进程、用户名、变量、权限符等，使用Git开发，可以清楚地看到分支，方便的不是一点点

1、安装
```
$ sudo apt-get install zsh git wget
$ wget --no-check-certificate https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | sh
```
2、替换bash为zsh：
```
$ chsh -s /bin/zsh
```
### 7、常用工具推荐
*  [QQ](https://github.com/ZQiang94/ubuntu-QQ) —功能还是比较齐全的，基本相当于Windows下QQ2013的功能了。QQ对话气泡、传文件、远程协助、群聊、讨论组、视频和语音通话都是有的，体验还是比较好的
* [微信网页版](https://wx.qq.com/)—基本功能全，跟windows差不多

![我的QQ](http://upload-images.jianshu.io/upload_images/2190281-85e0a2516be7af93.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


*  [网易云音乐](http://music.163.com/#/download)—良心网易，网易开发了Linux版的网易云音乐，跟windows版一模一样，很好用，强烈推据说网易云支持Linux版是deepin争取的结果

![是不是很赞](http://upload-images.jianshu.io/upload_images/2190281-11e24001a8a151a1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* [搜狗输入法linux版](http://pinyin.sogou.com/linux/?r=pinyin)，跟windows上一样好用
* [Office | WPS Office](http://linux.wps.cn/) 文档什么的不用发愁啦
* [xournal](http://xournal.sourceforge.net/)：只有Linux上有，非常强大，可以自由记笔记，插文字图片，涂鸦，划线，pdf做笔记，标注，设计很棒。安装—`sudoapt-getinstallxournal`

### 8、程序员必备
* `cURL` 是一个强大的命令行 HTTP 工具，未来很多软件的快速在线安装都会用到。
安装
```
sudo apt update
sudo apt install curl
```
* ` zeal` 是一款 Linux 下强大的离线开发文档查看工具，它参照了 OS X 操作系统上收费、强大且几乎程序员必备的 Dash，并且与其共用离线文档。
安装
```
sudo apt update
sudo apt install zeal
```
*  `XMind `是当前最为流行且强大的跨平台思维导图工具，学习和工作中不可或缺。

 下载 64 位 deb 安装包 http://www.xmind.net/download/linux/
* [Jetbrains全家桶](https://www.jetbrains.com/)—简直是业界良心秒杀全场，好看，精细。平时开发：Java—IntellJi IDEA(感觉比eclipse好用)，前端—webstorm

### 9、遇到妹纸装个逼



![啦啦啦](http://upload-images.jianshu.io/upload_images/2190281-13cc0e79b23eca90.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 打开终端，全屏
```
sudo apt-get install cmatrix
```
输入密码，安装后，输入`cmatrix -b`，逼格瞬间暴增,`Ctrl+c`退出

![帅不帅](http://upload-images.jianshu.io/upload_images/2190281-c4931790acc97cd1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 打开终端，全屏
```
sudo apt-get install sl
```
安装后执行`sl`，怒看屏幕上一辆火车开过。。。

![哈哈](http://upload-images.jianshu.io/upload_images/2190281-796c5fbb64b16db6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 打开终端，全屏
```
telnet towel.blinkenlights.nl
```

![看完喽](http://upload-images.jianshu.io/upload_images/2190281-8fb75ff8f4e3544f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

静静等待终端下即将开始播放的《星球大战》吧，按下`Ctrl+]`后输入`quit`退出

### 10、无聊来发小游戏
代码敲累了，换个思维吧，在终端玩游戏也是挺程序员的。
* BASTET（俄罗斯方块的玩法）
安装
```
sudo apt install bastet
bastet
```

![bastet](http://upload-images.jianshu.io/upload_images/2190281-275993793af172a9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* NINVADERS（飞机大战坦克的玩法，空格键发射）
安装
```
sudo apt-get install ninvaders
ninvaders
```


![哈哈](http://upload-images.jianshu.io/upload_images/2190281-72fd5a46f2b12d52.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 2048（你懂的）
安装
```
wget https://raw.githubusercontent.com/mevdschee/2048.c/master/2048.c gcc -o 2048 2048.c
./2048
```
* BACKGAMMON（五子棋）
```
sudo apt-get install bsdgames
backgammon
```
![一开始有点蒙](http://upload-images.jianshu.io/upload_images/2190281-78fff060cd583d1f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 11、工具与资源
![好了，你该学习了](http://upload-images.jianshu.io/upload_images/2190281-36d289988aa2d762.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
你是不是已经喜欢上它了呢，还等什么，快去学习吧
* Ubuntu官网：[http://cn.ubuntu.com/](http://cn.ubuntu.com/)
* Ubuntu官方中文网站：[http://cn.ubuntu.com/](http://cn.ubuntu.com/)
* 在线简单体验Ubuntu的桌面环境：[http://tour.ubuntu.com/zh-CN/](http://tour.ubuntu.com/zh-CN/)
* Ubuntu新手指南：[http://thoughtworks-academy.github.io/linux-guide/zh-hans/](http://thoughtworks-academy.github.io/linux-guide/zh-hans/)
* Ubuntu桌面完全教程：[http://forum.ubuntu.org.cn/viewtopic.php?f=94&t=140531](http://forum.ubuntu.org.cn/viewtopic.php?f=94&t=140531)
* Ubuntu问答网站：[http://askubuntu.com/](http://askubuntu.com/)
* Ubuntu中文社区：[http://forum.ubuntu.org.cn/](http://forum.ubuntu.org.cn/)
* Linux中文社区：[https://linux.cn/](https://linux.cn/)

**我是半生不熟 喜欢照自己的怪念头行事
喜欢一切意外 想把生活过成诗的样子
若哪天有幸相遇 请别诧异 其实我并不是个乖孩子**