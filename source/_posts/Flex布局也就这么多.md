---
title: Flex布局也就这么多
categories: Web 前端

---

还清楚记得第一次用Flex实现了垂直居中的时候，我那各种unbelievable的心情，然后就深深喜欢上了这个好玩的东西

![flex layout](http://upload-images.jianshu.io/upload_images/2190281-c77651f6b6f323c7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 为什么出现
关于Flex布局的出现解决了的问题，个人总结了以下几点原因。

先看看到现在WEB布局的一个发展吧
![布局](http://upload-images.jianshu.io/upload_images/2190281-04d2aa9e82e4d45f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 传统的布局都是基于盒模型，然后设置各种display和position，必要时再加上相应地float，想必写过CSS的同学都感受到过，实现一些复杂的布局会非常不方便，有时候自己写的样式，过段时间看都不敢相信。
* 对于一些常用的居中问题，比如垂直居中的实现，使用flex会非常简单
* 还有一些内容的伸缩，等分等问题

**我觉得最主要的一点就是简化了样式的编写，同样实现一个复杂的需求，之前用CSS可能得编写一大堆代码，但是用flex可能几行就实现了**

## 是什么
flex的全称是`Flexible Box`，是2009年`W3C`提出的一个布局概念，目的是简便、完整、响应式地实现各种页面的布局。

画了张flex从工作草案到候选的的大事年表
![](http://upload-images.jianshu.io/upload_images/2190281-78be66b0a95bf60c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


要注意的一点：
* 设为 flex 布局以后，子元素的`floa`t、`clear`和`vertical-align`属性将失效
* flex布局默认是首行左对齐
## 概念
理解flex中有几个概念很重要，像下图，如果是用翻译，注意是侧轴，不要老说纵轴，是主轴，不要老说横轴，因为代表的意义不一样。
![](http://upload-images.jianshu.io/upload_images/2190281-ee0593505e66fbd2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



## 如何使用
使用flex很简单，只用设置display属性为flex就可以，像下面这样：
![image.png](http://upload-images.jianshu.io/upload_images/2190281-a1fc0af170342e3c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**自己写了一个Demo，建议，打开demo，可边看边试，会理解的特别快，点击[在线演示](https://banshengbushu.github.io/flex-demo/)可修改样式**

## Container的属性（6个）
从概念图可以看出，flex布局有两个最大的概念也就是container和item，所以相应地所有属性也只对这两个元素起作用的，下来介绍container的属性，当然前提是container设置了`display: flex`

* **1. flex-direction**
```
.container {
  flex-direction: row | row-reverse | column | column-reverse;
}
```
> 设置item排列的方向
默认是row，从主轴的起点向终点依次排列。
row-reverse: 从主轴的终点位置开始向起点依次排列。
column: 从侧轴的起点向终点依次排列。
column-reverse: 从侧轴的起点位置开始向终点依次排列。
**注意设置了这个属性的item会影响tab键的顺序哦。**

* **2. flex-wrap**
```
.container{
  flex-wrap: nowrap | wrap | wrap-reverse;
}
```
> 设置item是否换行
默认是nowrap，不换行显示。
wrap:   一行排列显示不下的时候会自动换行显示，默认主轴从起点到终点。
wrap-reverse：一行排列显示不下的时候会自动换行显示，默认主轴从终点到起点。

* **3.  flex-flow（，row nowrap）**
>这个是flex-direction 和 flex-wrap 属性的缩写，默认是row nowrap
就像margin和margin-left、margin-right、margin-top、margin-buttom的关系一样

* **4.  justify-content**
```
.container {
  justify-content: flex-start | flex-end | center | space-between | space-around;
}
```
>主轴上的所有子元素都不能伸缩或已经达到其最大值时，这一属性可对多余的空间进行分配
>* flex-start: 默认值，子元素从主轴的起点开始排列
>* flex-end: 子元素从主轴的终点开始排列
>* center: 子元素关于主轴的中点对齐排列
>* space-between 弹性盒子元素两端对齐，其余平均地分布在行里
>* space-around 弹性盒子元素会平均地分布在行里，两端保留子元素与子元素之间间距大小的一半

* **5. align-items**
```
.container {
  align-items: flex-start | flex-end | center | baseline | stretch;
}
```
>设置元素在侧轴上的对齐方式，对单行起作用
>* flex-start: 默认值，子元素从侧轴的起点开始排列
>* flex-end: 子元素从侧轴的终点开始排列
>* center: 子元素关于侧轴居中排列
>* baseline:  子元素关于侧轴的基线对齐
> * stretch: 如果不设置width和height，元素高度默认撑满父容器

* **6. align-content**
>堆叠伸缩行的对齐方式， 定义了多根轴线的对齐方式，项目只有一根轴线，该属性不起作用

#item的属性
* **1. order**
```
.item {
  order: 0;
}
```
>按照order的属性排列元素, 数值小的在前面，还可以是负数，默认是0

* **2. flex-grow**
```
.item {
  flex-grow: 0;
}
```
>定义项目的放大比例, 默认是0，即父容器如果存在剩余空间，也不放大
>* 所有项目的flex-grow属性都为1，则它们将等分剩余空间

* **3.  flex-shrink**
```
.item {
  flex-shrink: 1;
}
```
>* 设置弹性盒的缩小比例，默认是1
>* 父容器如果空间不足以分配子元素，元素会默认缩小等分不足空间
>* 可以设置item的flex-shrink的属性为0来保证该元素不会被缩小

* **4.  flex-basis**
>定义了在分配多余空间之前，项目占据的主轴空间
如果不设置改属性，默认的main-size就是item的width或height，取决于主轴是什么

* **5. flex**

>* flex是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto，后两个系数可选
>* 两个快捷值：auto (1 1 auto) 和 none (0 0 auto)

* **6. align-self**
```
.item {
  align-self: auto;
}
```
>align-self 属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性, 默认值为auto, 取值和container的align-items属性一致

## 浏览器的兼容性
在[这里](https://caniuse.com/)查询，可以看到已被大多数浏览器支持

参考：
[Flex 布局教程—实例篇](http://www.ruanyifeng.com/blog/2015/07/flex-examples.html)
[一个完成的flexbox指南](https://www.w3cplus.com/css3/a-guide-to-flexbox-new.html)

