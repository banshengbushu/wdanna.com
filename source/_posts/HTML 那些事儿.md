---
title: HTML 那些事儿
categories: Web 前端

---



###1、第一个需求

![HTML—列表](http://upload-images.jianshu.io/upload_images/2190281-3b033c3e71a07603.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
###我的思考
* 最外层的是两个**无序列表**（`<ul>标签`）
* 靠近最外层的分别是两个**有序列表（`<ol>标签`）**
* 最里层的也是**无序列表**（`<ul>标签`），这里应有一个`type=“square”`的属性
* 所有列表项目都需要使用`<li> 标签`

###实现效果

![我的效果](http://upload-images.jianshu.io/upload_images/2190281-1f274004267dfa07.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

###错误纠正
对于开始理解的无序列表添加`type=“square”`的属性那块，在这里是不需要加的，因为默认的无序列表的嵌套结构是这样的，
![从第三层开始默认的样式就是`square`，所以不用加样式](http://upload-images.jianshu.io/upload_images/2190281-0f48022a360ed071.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
实现代码请访问我的 [Github](https://github.com/banshengbushu/HTML_BASIC/blob/master/html-list.html)
###3、第二个需求

![HTML-表格](http://upload-images.jianshu.io/upload_images/2190281-a065ded03c3dd373.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

###我的思考
* 表格分为标题（`<caption>标签`）和表格主体内容部分（5行4列）
* 表格主体内容部分首先要有边框（设置`border`属性）
* 表格相关的标签有
 * 表格— `<table> `标签
 * 表格的行—`<tr>`标签
 * 每行被分为若干单元格—`<td>`标签
 * 表格需要进行跨行（`rowspan`）、跨列（`colspan`）合并
 * 表格有些内容需要居中显示

###实现效果

![我的表格](http://upload-images.jianshu.io/upload_images/2190281-4bf3ab76312c50fa.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



实现代码请访问我的[Github](https://github.com/banshengbushu/HTML_BASIC/blob/master/html-table.html)

###2、第三个需求
![HTML-UML试卷](http://upload-images.jianshu.io/upload_images/2190281-0ecab4110fd8daf9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

###我的思考
* 大致浏览下，应分为7部分—标题、卷头、一～五个大题
* 看着卷子，要想到会使用到的标签
 * `<h1>`—标题
 * `<span>`—用来组合文档中的行内元素
 * `<input>`—输入框，可通过改变`type`变成`checkbox`复选框
 * `<ol>`—有序列表，在小标题时使用
 * `<textarea>`—标签定义多行的文本输入控件

###实现效果


![我的效果](http://upload-images.jianshu.io/upload_images/2190281-a80e155abd020d33.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

实现代码请访问我的[Github](https://github.com/banshengbushu/HTML_BASIC/blob/master/UML-paper.html)

###更多HTML学习资源与工具
* html在线验证：[http://www.freeformatter.com/html-validator.html](http://www.freeformatter.com/html-validator.html)(该网站上还有很多别的工具）
* html在线格式化代码：[http://www.cleancss.com/html-beautify/](http://www.cleancss.com/html-beautify/)
* W3School上的HTML基础教程：[http://www.w3school.com.cn/html/index.asp](http://www.w3school.com.cn/html/index.asp)
* Html5新特性：[http://www.w3school.com.cn/html5/index.asp](http://www.w3school.com.cn/html5/index.asp)
* CodeForDream上提供的HTML课程：[http://www.codefordream.com/courses/html_basic/sections](http://www.codefordream.com/courses/html_basic/sections)


**我是半生不熟 喜欢照自己的怪念头行事
喜欢一切意外 想把生活过成诗的样子
若哪天有幸相遇 请别诧异 其实我并不是个乖孩子**