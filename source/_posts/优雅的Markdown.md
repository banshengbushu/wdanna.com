---
title: 优雅的Markdown
categories: 工具
---

### -1- 先感受下
你可以试着搜下，网上关于`Markdown`的介绍和称赞数不胜数，而且都写的很优美，在这里我就不用自己的话夸赞它了，引用几句话大家随意感受下
> * Markdown本身就是为写博客而生的
* 15分钟就能够基本了解，连续使用一星期就能够熟练掌握
* 专注文字内容本身，而更少的关注排版样式
* 低碳环保，可移植性高

![](http://upload-images.jianshu.io/upload_images/2190281-e9f45de62f12d849.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**哦...对了，知道一下创始人也是必要的—约翰·格鲁伯（John Gruber），于2004年发布**

### -2- 快速上手
在这里介绍一些基本常用的语法，保证你快速上手
##### 1、标题
|Markdown|HTML| 预览|
|-------------|-------|---- --|
|#Level 1 title|<h1>Level 1 title</h1>|<h1>Level 1 title</h1>|
|## Level 2 title|<h2>Level 2 title</h2>|<h2>Level 2 title</h2>|
|### Level 3 title|<h3>Level 3 title</h3>|<h3>Level 3 title</h3>|
|#### Level 4 title|<h4>Level 4 title</h4>|<h4>Level 4 title</h4>|
|#####  Level 5 title|<h5>Level 5 title</h5>|<h5>Level 5 title</h5>|
|###### Level 6 title|<h6>Level 6 title</h6>|<h6>Level 6 title</h6>|
##### 2、文本
|Markdown|HTML| 预览|
|-------------|-------|---- --|
|  \**\**Bold\**\**|<strong>Bold</strong>|<strong>Bold</strong>|
|  \**Italic\**|<em>Bold</em>|<em>Italic</em>|
##### 3、链接和图片
|Markdown|HTML| 预览|
|-------------|-------|-------|
|  \[Google](http://www.google.com)|<a href="http://www.google.com">Google</a>|<a href="http://www.google.com">Google</a>|
| \!\[Alt text](/path/to/img.jpg)   | ![](/path/to/img.jpg)|![](/path/to/img.jpg)|
##### 4、列表
|Markdown|HTML| 预览|
|-------------|-------|------|
|\* Item | <li>Item </li> | <li>Item </li>| 
|\* Item   <br />       \* Item 1<br />       \* Item 2 |<li>Item <br />    <ul><br />        <li>Item 1 </li><br />        <li>Item 2 </li><br />       </ul><br /></li>| <li>Item<ul><li>Item 1 </li><li>Item 2</li> </ul></li>|
|1. Item   <br />       1. Item 1<br />       2. Item 2 |     <li><br />       <ol>Item<br />           <li>Item  1</li><br />        <li>Item 2 </li><br />    </ol><br /></li>    |  <ol><li>Item<ol><li>Item 1 </li><li>Item 2</li></ol></li></ol>|
##### 5、分隔线
|Markdown|HTML| 预览|
|-------------|-------|------|
|  一行用三个以上的星号、减号、底线来建立，行内不能有其他东西|<hr   />|--------------------|
##### 6、引用
|Markdown|HTML| 预览|
|-------------|-------|---- --|
|  \>quote|<blockquote>quote</blockquote>|<blockquote>quote</blockquote>|

##### 7、代码
|Markdown|HTML| 预览|
|-------------|-------|---- --|
| \```<br />.header<br /> { <br />   display: block; <br />   width: 100%;<br /> }<br />\```|.header<br /> { <br />   display: block; <br />   width: 100%;<br /> }|```.header```<br />```{```<br />   ```display: block;  ```<br />    ``` width: 100%; ```<br />```}```|
| \`<p>line</p>\`|<p>line</p>|`<p>line</p>`|

##### 8、表格
* Markdown:
```
| Header 1  | Header   2 |
|-----------|------------|
|row 1 col 1| row 1 col 2|
|row 2 col 1| row 2 col 2|
```
* HTML
```
<table border='1'>
    <tr>
       <th>Header 1</th>
       <th>Header 2</th>
    </tr>
    <tr>
       <td>row 1 col 1</td>
       <td>row 1 col 2</td>
    </tr>
    <tr>
       <td>row 2 col 1</td>
       <td>row 2 col 2</td>
    </tr>
</table>
```

* 预览

|Header 1|Header  2|
|-----------|----------|
|row 1 col 1| row 1 col 2|
|row 2 col 1| row 2 col 2|

**是不是看起来并不难呢，快动手实践吧**

![啊哦...](http://upload-images.jianshu.io/upload_images/2190281-90d72bb3fe9bcae2.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### -3- 关于`inline code`
>关于这个问题—什么时候应该使用`inline code`

**个人观点如下**
* 专业词汇或代码片段与文字在一起出现时
* 说明代码关键字时使用
* 行内某些字符是代码块的时候

### -4- 感兴趣的戳这里(引用自[卓越女生BBS总理整理的链接](https://bbs.excellence-girls.org/topic/213/markdown))
[创始人 John Gruber 的 Markdown 语法说明](http://daringfireball.net/projects/markdown/syntax)
[一篇比较好的介绍Markdown及相关工具的文章](https://zhuanlan.zhihu.com/p/22755240)
[Github提供的markdown教程，必看](https://guides.github.com/features/mastering-markdown/)
[Markdown的正确使用方式](https://unnamed42.github.io/2015-12-02-Markdown%E7%9A%84%E6%AD%A3%E7%A1%AE%E4%BD%BF%E7%94%A8%E6%96%B9%E5%BC%8F.html)
[免费的markdown在线预览及示例](http://dillinger.io/)
[推荐的跨平台且所见即所得的markdown编辑器](https://bbs.excellence-girls.org/topic/133)
[在线生成markdown table](http://www.tablesgenerator.com/markdown_tables)

**我是半生不熟 喜欢照自己的怪念头行事
喜欢一切意外 想把生活过成诗的样子
若哪天有幸相遇 请别诧异 其实我并不是个乖孩子**