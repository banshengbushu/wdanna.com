---
title: 今天聊聊 CSS
categories: Web 前端

---



###1、CSS是什么
>CSS全称为Cascading Style Sheets，中文翻译为“层叠样式表”，简称CSS样式表，所以称之为层叠样式表（Cascading Stylesheet）简称CSS。

在网页制作时采用`CSS`技术，可以有效地对页面的布局、字体、颜色、背景和其它效果实现更加精确的控制。只要对相应的代码做一些简单的修改，就可以改变同一页面的不同部分，或者页数不同的网页的外观和格式。
###2、CSS作用

CSS具有对网页的布局、颜色、背景、宽度、高度、字体进行控制，让网页按您的美工设计布局的更加美观漂亮。

###3、基本样式

* `font-size` 字体大小
 * `font-size:12px `对象文字大小为12px
* `float` 浮动
 *` Float:left`靠左浮动
 * `Float:right`靠右浮动
* `width` 宽度
 * `Width:20px` 对象宽度20px
* `height` 高度
  * `Height:20px` 对象高度20px
* `margin `外边距
 * `Margin:1px 2px 3px 4px` 对象上距离1px；右为2px；下为3px；左为4px
* `padding `内补距
 * `Padding:1px 2px 3px 4px` 对象内距离边上为1px；右为2px；下为3px；左为4px
* `border `边框
 * ` Border:1px solid #111` 对象边框为1px宽黑实线
* `font-family` 字体
 * `font-family`"黑体"; 对象文字字体为黑体
* `font-weight` 文字加粗
 * `font-weight:bold `对象文字被加粗
* `line-height` 行高
 * ` line-height:20px` 对象内上下2排文字行高为20px（包括文字自身占用高度）
* ` text-decoration` 文字装饰（下划线、删除线）
 * `text-decoration:underline` 对象文字加下划线
* `background` 背景属性
 * `background:#FFF url(bg.png) repeat-x 0 0 `对象背景色为白色、背景图片为`bg.png `按X轴分析重复显示并距离顶部和左为0像素
* `text-align `内容左中右对齐

更多样式请 [查看CSS手册](http://www.thinkcss.com/shouce/)
###4、基本选择器
`CSS`是一种用于屏幕上渲染`html`，`xml`等一种语言，`CSS`主要是在相应的元素中应用样式，来渲染相对应用的元素，那么这样我们选择相应的元素就很重要了，如何选择对应的元素，此时就需要我们所说的选择器。选择器主要是用来确定`html`的树形结构中的`DOM`元素节点。
 * **元素选择器**—如果设置 HTML 的样式，选择器通常将是某个` html` 元素，比如 `<p>`、`<h1>`、`<em>`、`<a>`，甚至可以是 `html` 本身：
```
h1 {color:blue;}
p {color:silver;}
```
 * **类选择器**—为了将类选择器的样式与元素关联，必须将 `class `指定为一个适当的值
```
<h1 class="important">This heading is very important.</h1>
```
```
.important {color:red;}
```
 * ** id选择器**—选择器可以为标有特定 id 的 HTML 元素指定特定的样式，选择器以 "#" 来定义
```
<p id="red">这个段落是红色。</p>
```
```
#red {color:red;}
```


###5、伪元素
伪元素用于创建一些不在文档树中的元素，并为其添加样式。比如说，我们可以通过`:before`来在一个元素前增加一些文本，并为这些文本添加样式。虽然用户可以看到这些文本，但是这些文本实际上不在文档树中。

* 伪元素包括这些
 * `::after`—可以在元素的内容之后插入新内容
 * `::before`—可以在元素的内容前面插入新内容
 * `::first-letter`—用于向文本的首字母设置特殊样式
 * `::first-line`—用于向文本的首行设置特殊样式
 * `::selection`—定义用户鼠标已选择内容的样式  
 * `::backdrop`—用于改变全屏模式下的背景颜色，全屏模式的默认颜色为黑色

* 举个栗子
```
HTML:
<p>Hello World, and wish you have a good day!</p>
```
```
CSS:
p:first-letter {
    font-size: 5em;
}
```
如果不创建一个`<span>`元素，我们可以通过设置`<p>`的`:first-letter`伪元素来为其添加样式。这个时候，看起来好像是创建了一个虚拟的`<span>`元素并添加了样式，但实际上文档树中并不存在这个`<span>`元素
###6、完成一个需求

![用CSS实现这个效果](http://upload-images.jianshu.io/upload_images/2190281-62cafcb9ac5fd8fe.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

用到了一些基本样式，实现代码可访问我的[Github](https://github.com/banshengbushu/HTML_BASIC/blob/master/UML-paper-style.html)

###7、更多资源与工具
* CSS在线验证： [http://codebeautify.org/cssvalidate](http://codebeautify.org/cssvalidate) (该网站上还有很多别的工具）
* 学习CSS布局：[http://learnlayout.com/](http://learnlayout.com/)
* CSS基础教程：[http://www.w3school.com.cn/css/index.asp](http://www.w3school.com.cn/css/index.asp)
* CSS3新特性（了解即可）：[http://www.w3school.com.cn/css3/](http://www.w3school.com.cn/css3/)
* CodeForDream上提供的CSS课程：[http://www.codefordream.com/courses/css_basic/sections](http://www.codefordream.com/courses/css_basic/sections)

**我是半生不熟 喜欢照自己的怪念头行事
喜欢一切意外 想把生活过成诗的样子
若哪天有幸相遇 请别诧异 其实我并不是个乖孩子**