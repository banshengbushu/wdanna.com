---
title: Concordion 实现 Hello World
categories: Web 前端
---


### 读音
踩过一些坑后,每接触一个以新单词命名的知识一定会先搞清楚读音
concordion
### 是什么
Concordion 是写和管理基于 Java 项目的自动化验收测试的有力工具。 它直接与 JUnit 框架集成，使之可以与所有流行的基于 Java 的 IDE 像 Netbeans 的是，Eclipse，IntelliJ IDEA 的使用 

### 查看结果
好了，知道了它是一个测试工具，那么怎么查看呢...
当 Concordion 运行测试时，输出XHTML文件显示原规范和测试结果。 成功的测试是使用“绿”色高亮显示，失败的测试使用的是“红”突出显示。 系统中的任何变化都会导致失败的测试，从而确保规格始终保持最新。 
如下图

![成功的测试](http://upload-images.jianshu.io/upload_images/2190281-8d35414fa58f2354.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



![失败的测试](http://upload-images.jianshu.io/upload_images/2190281-12b5d7f80bae3572.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 测试一个Hello World
* 下载Concordion和其所依赖的包
[点击这里下载](http://concordion.org/download/java/markdown/)
* IntelliJi新建一个项目

![新建项目,选择java 1.8](http://upload-images.jianshu.io/upload_images/2190281-d66ff95bb4545f83.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![点击Next](http://upload-images.jianshu.io/upload_images/2190281-ee3429dcef1c1226.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![填写项目名及路径](http://upload-images.jianshu.io/upload_images/2190281-e370150bc803ddc5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 将下载后的包解压,直接放到项目根目录下

![点击ok](http://upload-images.jianshu.io/upload_images/2190281-c0d400b987b768be.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 选中所有的`jar`包
![Ctrl可多选](http://upload-images.jianshu.io/upload_images/2190281-53081412c9a3dc30.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 右键选择`Add to Libary`
![点击ok](http://upload-images.jianshu.io/upload_images/2190281-dc10e3c201e33cfa.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* src下新建main和test包

![右键新建](http://upload-images.jianshu.io/upload_images/2190281-d0be328c9b03b65c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* main中新建`HelloWorld.java,test`中新建`HelloWorld.html`和`HelloWorldTest.java`

![test中是测试文件](http://upload-images.jianshu.io/upload_images/2190281-9d13d3b9b388b632.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* HelloWorld.html中添加如下代码
```
<html xmlns:concordion="http://www.concordion.org/2007/concordion">
<body>
<p>Should print:</p>
<p concordion:assertEquals="sayHello()">HelloWorld</p>
</body>
</html>
```

* HelloWorld.java中添加如下代码
```
package main;
public class HelloWorld
{
public String sayHelloWorld()
    {
return "HelloWorld";
    }
}
```
* HelloWorldTest.java中添加如下代码
```
package test;
import main.HelloWorld;
import org.concordion.integration.junit4.ConcordionRunner;
import org.junit.runner.RunWith;
@RunWith(ConcordionRunner.class)
public class HelloWorldTest 
{   
   public String sayHello()    
    {        
        return new HelloWorld().sayHelloWorld();    
    }
}
```

* 在 HelloWorldTest.java中

![有个绿色的三角](http://upload-images.jianshu.io/upload_images/2190281-bd29a7ec591b3e92.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 单击 `run HelloWorldTest`

![即可运行](http://upload-images.jianshu.io/upload_images/2190281-b5ed34aea35769d7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 复制下方的`file:`后面的内容
![复制蓝色选中部分](http://upload-images.jianshu.io/upload_images/2190281-a23c0de6099b8bd3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 在浏览器粘贴复制的网址,绿色表面测试Hello World成功

![运行成功](http://upload-images.jianshu.io/upload_images/2190281-e098902bb2bd5884.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 在一期源码里的作用
注册和登录部分的测试