---
title: 使用apt-get和nvm安装node的区别
categories: 工具
---



初识 apt-get 和 nvm 
--------------------------------------------
--------------------------------------------- 

###apt-get
* **是什么**
在各个平台都有相关的包管理工具，比如 ubuntu 下面有 `apt-get`，centos 下面有 `yum`，mac 下面有 `brew` 等，它们都是安装软件的非常方便的利器，主要用于自动从互联网的软件仓库中搜索、安装、升级、卸载软件或操作系统
* **如何使用 apt-get 安装 node**
```
$ sudo apt-get install nodejs
$ sudo apt-get install npm
```
这里，因为使用 `apt-get`  安装的 node 的包管理工具 `npm` 并没有初始安装，所以需要安装 ` npm`

* **查看安装版本**
 * 查看 node 版本
```
$ node --version
v6.3.0
```
 * 查看 npm 版本
```
$ npm  --version
3.10.3
```
在查看版本号时，也可以通过 `-v` 命令查看，比如： `node -v`，`npm -v` 
* **怎么使用 node**
 * 进入 node  环境
```
 $  node
 > 
```
或
```
$ nodejs
>
```
通过 `>` 可以看出现在已经进入 node 环境

 * 运行  js 文件，例如运行 hello.js
```
$ nodejs hello.js
```
或
```
$ node hello.js
```

###nvm

* **是什么**
[nvm](https://github.com/creationix/nvm)是一个开源的 Node 版本管理器，通过简单的 bash 脚本来管理、切换多个 Node.js  版本,使用 `nvm` 可以安装官网最新版本之前的任意版本,可以任意切换不同版本
*  **如何使用 nvm 安装 node**
 * 首先我们需要安装 nvm
```
$ curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.29.0/install.sh | bash
```
 * 接下来查看一下 node 有哪些版本可以安装
```
$ nvm ls-remote

         v6.1.0  
         v6.2.0  
         v6.2.1  
         v6.2.2  
         v6.3.0  
         ....
```
 * 下载所需要的 node 版本,比如说我们需要 `v6.3.0` 版本
```
$ nvm install v6.3.0
```
*  **查看安装版本和使用 node 的方法 和 `apt-get` 相同，这里不再复述 **
* **使用 nvm 切换 node 版本**
 * 查看当前已安装版本
```
$ nvm ls
 ->       v6.3.0  
default -> v6.3.0
node -> stable (-> v6.3.0) (default)
stable -> 6.3 (-> v6.3.0) (default)
iojs -> N/A (default)
lts/* -> lts/argon (-> N/A)
lts/argon -> v4.6.0 (-> N/A)
```
从运行结果可以看出，当前电脑上的 node 版本只有一个 `v6.3.0`,并且当前正在使用的版本也是 `v6.3.0`,默认的版本同样也是 `v6.3.0`
 * 例如要使用 `v4.4.5` 版本，首先安装该版本(可以先使用 `nvm ls-remote` 查看所有版本)
```
$ nvm install v4.4.5
```
 * 使用 `use` 命令切换至该版本
```
$ nvm use v4.4.5
Now using node v4.4.5 (npm v2.15.5)
```
 * 设置默认版本
```
$ nvm alias default v6.3.0
```
 如果没有设置  `default` 默认开机 node 是没有启动的，所以可能会报找不到 node 命令的错误，因此我们需要设置默认版本

 * 卸载某个 node 版本,例如卸载 `v4.4.5` 版本
```
$ nvm uninstall v4.4.5
```
 
#### 个人建议
* 个人平时使用 node 时，习惯使用  node 命令，毕竟少输个 “js”，节省时间
* 安装 node 时，node 各个版本特性不同，对于 Node.js 这个版本帝而言，很多项目需要使用不同版本的  node 开发机器上可能要同时存在几个 Node.js 的大版本，所以建议大家使用 nvm 方式安装 node

两种方式安装的具体差异
------------------------------------
------------------------------------
* **安装版本**
  * apt-get
  不是最新版本（在linux下默认源中没有 node 的程序），安装的版本有且只有一个，而且执行`sudo`命令的时候，是以超级管理员身份运行，以后你用`npm`如果是以超级管理员权限执行的，所以别人就可以更改系统文件，会造成安全性问题，假如别人上传了一个不太好的npm包，里面的脚本实际上是删除系统文件，让你装一下，说帮他测试一下，你install完，sudo一执行。他就可以改系统文件了，那就完蛋了...但前提是你使用了`sudo`

 * nvm
可以供我们选择要安装的版本，并且则解决了多版本共存、切换问题，但在安装之前，请确认本机以前的安装包已经被卸载
* **安装目录**（终端通过 `whereis node` 查看）
 * apt-get
```
 /usr/local/bin/node
```
 * nvm
```
/home/xxx/.nvm/versions/node/v6.3.0/bin/node
```

nvm 使用 node 切换版本内部实现原理
-----------------------------------------
-----------------------------------------
**实现原理：**在一个目录下存放多个版本的目录，在切换时候将相应的版本路径加入 PATH 中，从而实现版本的切换，例如从 `v6.3.0`  切换到  `v4.4.5` 具体流程如下： 
* 查看一下当前使用的 node 版本
```
$ node --version
  v6.3.0
```
* 现在来看一下  node 环境变量
```
$ echo $PATH    
/home/guoru/.nvm/versions/node/v6.3.0/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
```
通过环境变量我们可以看出，现在使用的 node 版本是  `v6.3.0`
* 使用 `nvm use v4.4.5` 切换版本，并且查看环境变量 
```
$ nvm use v4.4.5
Now using node v4.4.5 (npm v2.15.5)
$ echo $PATH    
/home/guoru/.nvm/versions/node/v4.4.5/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
```
可以看出环境变量已经将 PATH 路径中的版本改为 `v4.4.5`版本了

总结
-----
-----
如果您是一个前端开发人员，建议您使用 `nvm` 来安装  node，如果您是一个普通的用户，建议您使用 `apt-get` 安装 node 。

 ** 如果您还有兴趣，请继续阅读 **
启动 node 时内部实现过程
-----------------------------------------
-----------------------------------------
在命令行启动 node 程序时，传入参数，node 程序根据输入的命令参数，执行相应的处理流程。即：在 node 程序中会使用`process.argv`获取命令行输入参数。`Process.argv`是一个数组，用于存放从命令行传入的参数。其类似C语言 main  函数中的`char* argv[]`，假定我们在控制台输入 `node argument.js –r arguments.js`. 那么程序argument.js 启动后， `process.argv` 数组中就就存储了以下几个字符串信息:`process.argv[0] = “node”, process.argv [1]= “argument.js”, process.argv [2] = “-r”，process.argv[3] = “argument.js`”. 由于参数数组的前两个存储的是字符串 ”node” 和源代码文件名，要想获得有效的输入参数，我们一般会从`process.argv[2]` 开始处理。
```
var args = {  
 '-h': displayHelp,  
 '-r': readFile  
};  
function displayHelp() {  
    console.log('Argument processor:', args);  
}  
function readFile(file) {  
    if (file && file.length) {  
       console.log('Reading:' ,file);  
       console.time('read');  
       var stream = require('fs').createReadStream(file);  
  
       stream.on('end', function() {  
          console.timeEnd('read');  
       });  
       stream.pipe(process.stdout);  
    }  
    else {  
        console.error('A file must be provided with the -r option');  
        process.exit(1);  
    }  
  }  
  
    if (process.argv.length > 0) {  
  
        process.argv.forEach(function(arg, index) {  
            if (arg === '-r' || arg === '-h') {                    
              console.log(process.argv.slice(index + 1));           
              args[arg].apply(this, process.argv.slice(index+1));  
            }  
        });  
    } 
```
args 对象存储了对应参数要执行的对应函数，例如输入参数是 `-r` 那么执行 `readFile`函数， 如果输入参数`-h`则执行`displayHelp`函数。readFile 函数被调用时，传入的参数是要读取的文件名。通过 Node  的文件系统模块`fs`所提供的接口调用`createReadStream`, 将指定文件名的文件内容读入形成输入流对象，然后再通过输入流对象的`pipe`函数，将输入流中的所有数据内容，重定向到标准输出，其实也就是输出到控制台

**我是半生不熟 喜欢照自己的怪念头行事
喜欢一切意外 想把生活过成诗的样子
若哪天有幸相遇 请别诧异 其实我并不是个乖孩子**