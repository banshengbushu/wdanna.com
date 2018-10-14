---
title: 神奇的 Linux 命令行
categories: Linux

---



#### 1、命令行真的好吗
![程序员的使命](http://upload-images.jianshu.io/upload_images/2190281-654d37c0cc309fba.jpg)
* **维基百科的解释**
>命令行界面（英语：command-line interface，缩写：CLI）是在图形用户界面得到普及之前使用最为广泛的用户界面，它通常不支持鼠标，用户通过键盘输入指令，计算机接收到指令后，予以执行。也有人称之为字符用户界面（CUI）。
* **也有人这样说**
>熟练使用命令行是一种常常被忽视，或被认为难以掌握的技能，但实际上，它会提高你作为工程师的灵活性以及生产力


* **个人观点**
有看到不同行业的人在评论区各种互撕，那到底用命令行是好还是不好呢..其实我觉得有时候花时间纠结这些问题是没有意义的，你觉得有用就学，不看好它就不看了呗，等哪天你发现它的好了，打心里想学了就去学呗，学习这东西，只要你愿意开始，什么时候都不晚。
任何东西都没有绝对的说法，要看使用的场合，常说水能载舟，它亦能覆舟。
我自己会的命令行也不是很多，但真的打心里羡慕那些把命令行用的很溜的大牛们，也在学习着熟悉大部分命令行，因为我觉得至少现在对我来说，它是极好的。
你是否注意到，在电影中一个“超级黑客”坐在电脑前，从不摸一下鼠标， 就能够在30秒内侵入到超安全的军事计算机中。这是因为电影制片人意识到， 作为人类，本能地知道让计算机圆满完成工作的唯一途径，是用键盘来操纵计算机。
**但不得不说不好的地方是**
 * 命令行对新手不太友好，所以能否熟练应用命令行算是一个高手和新手能显著拉开效率差距的点。

 * 娱乐的时候不友好，你要打游戏或者要聊天，这个时候就还是图形化界面占上风了，当然对用户来说也美观
 * 看到有人这样说—我就想让照片上妹子脸上的小痘痘消失，怎么用命令行实现呢

 **好在哪**
 * 人生苦短，效率，效率，效率，还是效率
 * 鼠标不适合快速操作，命令行通常比在菜单中点来点去更简单，更容易，更直接。
 * 稳定,可移植性强
 * 开发省心省钱

### 2、感受下效率
试着玩玩，就能体会到它的效率了

|使用命令|用途|
|------------|-------|
|poweroff|立刻关机|
|shutdown -h 10|10分钟后自动关机|
|reboot|重启|
|shutdown -r 10（20:35）|过10分钟（在时间为20:35）自动重启(root用户使用)|
|ls|列举出当前工作目录的文件和文件夹|
|mkdir <new-directory-name>|新建一个文件夹|
|touch <new-directory-name>|新建一个文件|
|rm <file-name>|删除给定的文件或文件夹|
|cp <source-file> <destination-file>|对文件或文件夹进行复制|
|cat <file>|用于在标准输出（监控器或屏幕）上查看文件内容|
|pwd|显示当前工作目录|
### 3、基本命令行

|使用命令|用途|
|------------|-------|
|  sudo passwd root |   设置root密码（输入当前系统账户的密码并设置新的UNIX密码 |
|users| 显示当前登录系统地用户|
|who| 登录在本机的用户与来源|
|hostname| 查看主机名
|man <command-name>|会为给定的命令显示一个使用手册页面|
|tail -n N <file-name>|指定在标准输出上显示文件的最后N行内容（默认显示10行）|
|grep "<string>" <file-name>|在给定的文件中搜寻指定的字符串|
|tar xvf FileName.tar|解包|
|tar cvf FileName.tar DirName|打包文件|
|gzip -d FileName.gz|解压|
|gzip FileName|压缩|
|which <file_name> | 查看可执行文件的位置，在PATH变量指定的路径中查看系统命令是否存在及其位置|
#### 4、这些你也要会（举例说明）

|使用命令|用途|
|------------|-------|
|```$ cat >> /Documents/test.txt <<  "EOF"export PATH=$HOME/jdk1.8.0_31/bin:$PATHexport JAVA_HOME=$HOME/jdk1.8.0_31/EOF ```|使用`>>`命令往配置文件里插入多行文本（两个”EOF“之间的所有内容都会被添加到文件中）|
|tree #使用`sudo apt-get install tree`安装|将文件目录以树状形式查看，有时候很方便|
|echo  "line 1\nline 1" |   显示`line 1\nline 1`|
|echo -e "line 1\nline 2" |   显示`line 1(换行了)line 2`（-e：遇到转义字符特殊处理）|
|ps -aux | 显示所有进程状态|
|kill <进程号(就是ps -A中的第一列的数字)>|终止一个进程|
|kill -9 <进程号>|强制中止一个进程(在上面进程中止不成功的时候使用)|
|netstat -tp  |查看网络连接命令|
|service --status-all  |查看系统服务状态|
|whereis <安装的应用名称>  |查找应用位置|
#### 5神奇的`top`
**这里选择把top单独介绍（信息量略大）**
* `top`的用途—作为日常管理工作中最常用也是最重要的Linux 系统监控工具之一，可以动态观察系统进程状况，显示当前系统正在执行的进程的相关信息，包括进程ID、内存占用率、CPU占用率等默认值是每5秒更新一次，按q键可以退出。
* 在你的终端输入这条命令即可查看
```
$ top
```
* 它会出现这些信息（本人电脑举例）
```
top - 21:11:46 up 29 min,  2 users,  load average: 0.29, 0.28, 0.18
Tasks: 240 total,   1 running, 239 sleeping,   0 stopped,   0 zombie
%Cpu(s):  2.6 us,  0.8 sy,  0.0 ni, 96.6 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  8081084 total,  4966452 free,  1533752 used,  1580880 buff/cache
KiB Swap:        0 total,        0 free,        0 used.  5930172 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                            
  979 root      20   0  370140  45300  33148 S   4.6  0.6   0:56.69 Xorg                                                                               
 3473 wangdan+  20   0  643452  53564  31976 S   3.3  0.7   0:01.12 python2                                                                            
 2067 wangdan+  20   0 1233768 113492  65108 S   2.3  1.4   1:06.83 compiz                                                                             
  769 mongodb   20   0  552156  67876  33636 S   0.7  0.8   0:12.55 mongod                                                                             
 2466 wangdan+  20   0 1122656 213372 122840 S   0.7  2.6   1:42.89 chrome                                                                             
 3509 wangdan+  20   0   49044   4240   3516 R   0.7  0.1   0:00.52 top                                                                                
 3552 wangdan+  20   0  924300 189484  82964 S   0.7  2.3   0:04.20 chrome                                                                             
 1680 wangdan+  20   0  578900 101304  46068 S   0.3  1.3   0:03.93 fcitx                                                                              
 1905 wangdan+  20   0  206868   6532   5900 S   0.3  0.1   0:00.23 at-spi2-registr                                                                    
 2097 wangdan+  20   0  469672  14668  11180 S   0.3  0.2   0:00.33 indicator-appli                                                                    
 2398 wangdan+  20   0 3091788  80880  49128 S   0.3  1.0   0:03.90 sogou-qimpanel                                                                     
 3141 root      20   0       0      0      0 S   0.3  0.0   0:00.24 kworker/u8:2                                                                       
 3581 wangdan+  20   0  531268  52284  28648 S   0.3  0.6   0:00.12 chrome                                                                             
    1 root      20   0  185468   6144   4020 S   0.0  0.1   0:02.98 systemd                                                                            
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd                                                                           
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.02 ksoftirqd/0                                                                        
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0H                                                                       
    6 root      20   0       0      0      0 S   0.0  0.0   0:01.88 kworker/u8:0                                                                       
    7 root      20   0       0      0      0 S   0.0  0.0   0:01.92 rcu_sched                                                                          
    8 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh                                                                             
    9 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 migration/0                                                                        
   10 root      rt   0       0      0      0 S   0.0  0.0   0:00.01 watchdog/0                                                                         
   11 root      rt   0       0      0      0 S   0.0  0.0   0:00.01 watchdog/1                                                                         
   12 root      rt   0       0      0      0 S   0.0  0.0   0:00.01 migration/1                                                                        
   13 root      20   0       0      0      0 S   0.0  0.0   0:00.02 ksoftirqd/1                                                                        
   14 root      20   0       0      0      0 S   0.0  0.0   0:00.01 kworker/1:0                                                                        
   15 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/1:0H                                                                       
   16 root      rt   0       0      0      0 S   0.0  0.0   0:00.01 watchdog/2                                                                         
   17 root      rt   0       0      0      0 S   0.0  0.0   0:00.01 migration/2                                                                        
   18 root      20   0       0      0      0 S   0.0  0.0   0:00.06 ksoftirqd/2                                                                        
   20 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/2:0H                                                                       
   21 root      rt   0       0      0      0 S   0.0  0.0   0:00.01 watchdog/3                                                                         
   22 root      rt   0       0      0      0 S   0.0  0.0   0:00.01 migration/3                                                                        
   23 root      20   0       0      0      0 S   0.0  0.0   0:00.01 ksoftirqd/3                                                                        
   25 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/3:0H                                                                       
   26 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kdevtmpfs  
```
* 第一行含义解释
  *  `21:11:46`—当前系统时间
  * ` up 29 min`—系统已经运行了29分钟（在这期间系统没有重启过）
  *  `2users`—当前有2个用户登录系统
  * ` load average: 0.29, 0.28, 0.18—loadaverage`—后面的三个数分别是1分钟、5分钟、15分钟的负载情况
  * `loadaverage`—数据是每隔5秒钟检查一次活跃的进程数，然后按特定算法计算出的数值。如果这个数除以逻辑CPU的数量，结果高于5的时候就表明系统在超负荷运转了
* 第二行含义解释
  * `Tasks: 240 total,   1 running, 239 sleeping,   0 stopped,   0 zombie`—系统现在共有240个进程，其中处于运行中的有1个，239个在休眠（sleep），stoped状态的有0个，zombie状态（僵尸）的有0个。
* 第三行含义解释
 * `2.6 us`—用户空间占用CPU的百分比。 
 * `0.8 sy`—内核空间占用CPU的百分比。
 * ` 0.0%ni`—改变过优先级的进程占用CPU的百分比
 * `96.6 id`—空闲CPU百分比
 * `0.0 wa`—IO等待占用CPU的百分比
 * `0.0hi`—硬中断（HardwareIRQ）占用CPU的百分比
 * `0.0si`—软中断（SoftwareInterrupts）占用CPU的百分比`
* 第四行含义解释
 * `8081084 total`—物理内存总量（80GB）
 * `1533752 used`—使用中的内存总量（14GB）
 * `4966452 free`—空闲内存总量（49GB）
 * `1580880 buff/cache`—缓存的内存量（15G）
* 第五行含义解释(swap交换分区信息)
 * `0 total`—交换区总量（0K）
 * `0used`—使用的交换区总量（0K）
 * `0free`—空闲交换区总量（0K）
 * `5930172 avail Mem`—可用内存（59G）
* 第七行含义解释（各进程（任务）的状态监控）
 * `PID`—进程id
 * `USER`—进程所有者
 * `PR`—进程优先级
 * `NI`—nice值。负值表示高优先级，正值表示低优先级
  * `VIRT`—进程使用的虚拟内存总量，单位kb。VIRT=SWAP+RES
  * `RES`—进程使用的、未被换出的物理内存大小，单位kb。RES=CODE+DATA
  * `SHR`—共享内存大小，单位kb
  * `S`—进程状态。D=不可中断的睡眠状态R=运行S=睡眠T=跟踪/停止Z=僵尸进程
  * `%CPU`—上次更新到现在的CPU时间占用百分比
  * `%MEM`—进程使用的物理内存百分比
  * `TIME+`—进程使用的CPU时间总计，单位1/100秒
  * `COMMAND`—进程名称（命令名/命令行）



#### 6、参考（来自[卓越女生BBS总理的分享](https://bbs.excellence-girls.org/topic/213/markdown)）
* [常用命令行介绍](https://github.com/iamcoach/console/blob/master/COMMANDS.md)
* [常用命令行cheet sheet](https://bbs.excellence-girls.org/topic/167)
* [每个程序员都应该知道的8个Linux命令](http://www.imooc.com/article/1276)
* [29个你必须知道的Linux命令](http://www.imooc.com/article/1285)
* [Linux mkdir、tar 和 kill 命令的 4 个有用小技巧](http://www.imooc.com/article/1316)
* [慕课网 《Linux达人养成计划 I》](http://www.imooc.com/learn/175)
* [慕课网 《Linux达人养成计划 II》](http://www.imooc.com/learn/111)
* [Ubuntu各种技巧](http://wiki.ubuntu.org.cn/UbuntuSkills)
* [Ubuntu常用命令行教程](http://teliute.org/linux/Tecli/)
* [书籍《鸟哥的Linux私房菜》](https://book.douban.com/subject/4889838/)


**我是半生不熟 喜欢照自己的怪念头行事
喜欢一切意外 想把生活过成诗的样子
若哪天有幸相遇 请别诧异 其实我并不是个乖孩子**