---
title: Ubuntu 安装 mongoDB 报错
categories: Linux
---



## 一、安装步骤一切ok
```
启动时 
$ sudo service mongodb start
```
```
#报错 
couldn't connect to server 127.0.0.1:27017 (127.0.0.1), connection attempt failed at src/mongo/shell/mongo.js:146
```
 ```
#停止时
$ sudo service mongodb stop
```
```
#报错 
unknown instance
```

搜了下有人这样解决了：

>* Step 1: Remove lock file.sudo rm /var/lib/mongodb/mongod.lock
* Step 2: Repair mongodb. sudo mongod --repair 
* Step 3: start mongodb.sudo start mongodb orsudo service mongodb start
* Step 4: Check status of mongodb.sudo status mongodb or sudo service mongodb status
* Step 5: Start mongo console.mongo

但我也试了，却没有解决...

**卸载之前装的mongodb**
```
$ sudo apt-get purge mongodb-org
$ sudo apt-get autoremoveRemove the old mongodb.list you created
$ sudo rm /etc/apt/sources.list.d/mongodb.list
```
准备重新安装，由失败到成功，整理了一下：

* 执行命令
 ```
sudo apt-get install mongodb-server
```
* 进入目录  
```
vim ~/.bashrc
```
* 添加此句
```
$ export PATH=/home/yhl/mongodb-linux/bin:$PATH
```
* 查看版本号
```
$ mongod -version 
```
* 
```
$ mkdir data
```
* 
```
$ mkdir log
```
```
$ mongod --dbpath data/ --logpath log/mongodb.log -logappend --fork
```

* 最后将启动命令保存在start中，方便下次启动使用（亲测成功）
```
$ echo "mongod --dbpath data/ --logpath log/mongodb.log -logappend --fork">> [start.sh](http://start.sh/) 
```

### 二、补充一下之前遇到的问题：
```
sudo service mongod start
Failed to start mongod.service: Unit mongod.service failed to load:
No such file or directory.
```

添加以下内容：
```
[Unit]
Description=High-performance, schema-free document-oriented database
Documentation=man:mongod(1)
After=network.target

[Service]
Type=forking
User=mongodb
Group=mongodbRuntime
Directory=mongodPIDFile=/var/run/mongod/mongod.pid
ExecStart=/usr/bin/mongod -f /etc/mongod.conf --pidfilepath /var/run/mongod/mongod.pid --fork
TimeoutStopSec=5
KillMode=mixed

[Install]
WantedBy=multi-user.target
```

就可以解决了。

**我是半生不熟 喜欢照自己的怪念头行事
喜欢一切意外 想把生活过成诗的样子
若哪天有幸相遇 请别诧异 其实我并不是个乖孩子**