---
title: CSS 实现动态百分比圆环
categories: Web 前端
---



#效果展示
没掌握上传动图的操作，这里就先截静态图吧


![25%](http://upload-images.jianshu.io/upload_images/2190281-be2ac373c69142a4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![50%](http://upload-images.jianshu.io/upload_images/2190281-471f4406c7898dad.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
#实现思路

>自己的思路

一开始看到这个图的时候，想着应该不难
* 外面一个`div`，里面一个`div`，一个背景深蓝色，一个背景白色
* 蓝色的`div`加一个伪元素，背景浅蓝色，再裁剪一半

还是先试试，写着写着发现中间各种设置四周边距，才让中间`div`居中，我都看不下去了

>参考了别人的思路

看了有很多例子，一开始没看懂的时候，觉得都写的什么呀，有这么复杂吗，但不知道怎么就突然开了窍，哇，这么简单，原来都是套路呀。
#CSS属性
* `clip` 设置裁剪，[详细介绍看这里](https://www.w3schools.com/cssref/pr_pos_clip.asp)
* `transform` 设置旋转，[详细介绍看这里](https://www.w3schools.com/cssref/css3_pr_transform.asp)
* `animation` 一个简写属性，用于设置六个动画属性，[详细介绍看这里](https://www.w3schools.com/cssref/css3_pr_animation.asp)

#更合理的思路
>利用遮罩和裁剪的思想。
>* 想象你有一个浅蓝色的圆圈，一个浅蓝色的半圆圈，一个深蓝色的半圆圈，三个半径一样大；
>* 浅蓝色半圆圈，深蓝色半圆圈，浅蓝色圆圈，从上往下依次堆叠放置；
>* 这时候，你会发现将中间那层深蓝色半圆圈稍作转动，从上忘下俯视，就会发现有你要的效果；

* `HTML`设计如下
![HTML结构](http://upload-images.jianshu.io/upload_images/2190281-43cc5c9cccd949ea.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 最外层`div`设置宽度为`10px`的`border`，让里面内容居中
![设置大小和内容居中](http://upload-images.jianshu.io/upload_images/2190281-89c10928d3574f54.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 给内层第一个`div`（深蓝色半圆圈）设置`border`，裁剪右半部分，并让其顺时针旋转90°
![](http://upload-images.jianshu.io/upload_images/2190281-217849ef81029ded.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 给外层`div`设置两个伪元素，分别是`after`（浅蓝色半圆圈）和`before`（浅蓝色圆圈）
![before](http://upload-images.jianshu.io/upload_images/2190281-8d6d2d46ef5da1ba.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![after裁剪右半部分](http://upload-images.jianshu.io/upload_images/2190281-7c9d6c5a2c54c181.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#让它动起来
设置从0°开始顺时针旋转90°
![利用animation一些属性](http://upload-images.jianshu.io/upload_images/2190281-ebb23f5b374895cf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这样，一个动态的圆环就成功啦。

**我是半生不熟 喜欢照自己的怪念头行事
喜欢一切意外 想把生活过成诗的样子
若哪天有幸相遇 请别诧异 其实我并不是个乖孩子**