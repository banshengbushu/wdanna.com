---
title: Accessibility 我们能做些什么(下)
categories: Web 前端
---


在上篇的 [不能永远忽略的 Accessibility (上)](https://www.jianshu.com/p/6d01f1611372) 中了解到了真正的 Accessibility 的是什么以及为什么要关注它，同样，想必你也看到了它那些看了也不知道具体该怎么做的规范吧，那对于一个前端工程师来说，究竟我们需要怎么做呢，今天就来说说围绕 WCAG 2.0 的规范我们可以怎么做。

![](https://upload-images.jianshu.io/upload_images/2190281-270e391d59651c29.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


## HTML 语义化
* **标题，段落，列表等内容的保持良好的结构**
正确地使用各个语义化的标签，不仅是自身代码质量的提高，对阅读你代码的人，也会有极大的帮助，同样对于开发成本，网站的SEO来说都是有好处的。
对于 Accessibility 来说，良好的标题，段落，列表结构也会提高辅助设备对用户的良好体验，比如屏幕阅读器在阅读到相对于的语义化标签的时候，是会自动地将对于标签读给用户听的。

* **尽量使用语义化的标签**
可能平时大家很少关注一个叫 Accessibility tree 的东西，翻译过来叫无障碍树，当你选中一段 DOM 的时候，在 Devtools 里面都可以看到，浏览器实际呈现给屏幕阅读器的就是这个结构 (浏览器获取 DOM 树，并将其修改成适用于辅助技术的形式) 将DOM 树变成无障碍树，所以良好的使用语义化标签，能让辅助设备更合理地将你网站的内容转化成 Accessibility tree，从而解读给用户。
![](https://upload-images.jianshu.io/upload_images/2190281-d1a4217624271484.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

所以确保页面中的重要元素具有正确的无障碍角色、状态和属性并确保指定无障碍名称和说明，浏览器便可让辅助技术获取该信息以打造自定义体验，这一点很重要。

* **为任何非文本内容提供文本替代项**
图像是大多数网页的重要组成部分，当然也是对弱视用户造成阻碍的一个特定因素，特别是那些浏览图片的网站，这时候添加文本替代性是非常重要的，举个简单的 🌰
```
<img src="/160204193356-01-cat-500.jpg" alt="一只目光汹汹凝视远方的猫”>
```
alt 允许指定在图像不可用时（例如图像加载失败、被网络爬虫访问或被屏幕阅读器读取时）使用的简单字符串，alt 不同于 title 或任何类型的字幕，因为它只在图像不可用时使用。

另一方面，描述图像并不总是有用。
例如，假定在一个包含文本“搜索”的搜索按钮内有一幅放大镜图像。如果其中不包含文本，您肯定会指定“搜索”作为这幅图像的 alt 值。 但由于文本处于可见状态，屏幕阅读器将拾取并朗读“搜索”一词；因此，图像上完全相同的 alt 值就成了多余的内容, 如果将 alt 省略，我们听到的很可能不是替代文本，而是图像文件名, ，只需使用空的 alt 属性就可让屏幕阅读器将图像整个跳过。
```
<img src="magnifying-glass.jpg" alt=“”>
```

**所有图像都应有 alt 属性，但它们无需都包含文本。 重要的图像应使用描述性替代文本简洁地说明图像内容，而装饰性图像应使用空的 alt 属性，即 alt=“”**

* 表单输入有关联的文本标签
  * 将 input 元素置于 label 元素内
  * 使用 label 的 for 属性并引用元素的 id
推荐使用后者，举个简单的 🌰

```
<input id="promo" type="checkbox"></input>

<label for="promo">This is a checkbox</label>
```
屏幕阅读器便可报告元素角色为 checkbox，处于 checked 状态，名称为“This is a checkbox”。

* **DOM 顺序和视觉顺序保持一致**
一般我们设计的时候，往往考虑的都是视觉可见得用户，那其实对于只能使用屏幕阅读器浏览网站的用户，这时候如果 DOM 结果不一致的话，就会造成用户的疑惑。

## 关于 Focus
大家应该都发现过我们在使用 Tab/ Shift Tab 键或者上下左右键的时候，也可以和网页进行交互，这种设计不仅方便与一般人的操作，其实对不能使用鼠标的用户来说是不必可少的设计。

同样，我们应该也见到过不同的浏览器会有不同的样式，Chrome 通常使用蓝色边框突出显示聚焦的元素，而 Firefox 则是使用虚线边框，每个浏览器都有自己默认的 Outline 样式。

但是，又会发现很多网站是没有这些交互的，这就是在网页设计以及实现的时候禁用了这写功能或者说没有使用合理的标签。

>Web AIM 检查清单才会在其第 2.1.1 节中指出，[所有页面功能应该都能使用键盘来执行](http://webaim.org/standards/wcag/checklist#sc2.1.1)

关于 Outline，官网上是这样说的
![](https://upload-images.jianshu.io/upload_images/2190281-586d9e54bc4d3040.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

>**禁止设置 outline 为 none， 在不提供替代项的情况下**

**HTML 默认的 focusable 元素**，它们是自动插入到 Tab 键顺序中，并且内置了键盘事件处理，默认支持 keyboard 功能，基本的都可以在 [这里](https://www.w3.org/TR/2011/WD-html5-20110525/editing.html) 找到。

所以，关于 Focus 我们可以做的有

* 不要 Remove 原生支持的 outline 样式，除非你有更好看的样式替代它
* 尽量使用原生支持的 focusable 的元素
* 如果有复杂的 UI, 需要使用非语义化的标签但确实是和用户有交互的时候，请为它加上 tabindex
* 可以自己写一些 js 或者一些库来区分键盘和鼠标或者触摸事件，来实现不同的 outline 样式，比如只想在使用键盘的时候有 outline，使用鼠标或者触摸的时候去掉 outline，我觉得这是相对合理的设计，比如 [Google 的 Accessibility 页面](https://www.google.com/accessibility/)。
* ......

## 设计样式的时候
* 正确的 Tab 键顺序，也就是设计出来的 Tab 键的顺序需要遵循正常的视觉顺序，从上至下，从左至右，比如这张图。
![](https://upload-images.jianshu.io/upload_images/2190281-0424de68e2a1df6c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
## Use WAI-ARIA

[ARIA](https://www.w3.org/TR/html-aria/#sec-strong-native-semantics) 全称 Accessible Rich Internet Applications，可以修改现有元素的语义，也 可以向不存在原生语义的元素添加语义，在复杂的 UI 控件会涉及到非语义的 HTML，这时候通过增加浏览器和辅助技术可以识别和使用的进一步语义来让用户知道正在发生的事情。

它提供了一系列可以使用的 attribute 来达到该目的，常用的有
* **role**
如果使用的是原生支持的语义化标签，那本身就是有默认的 role的，比如 button 的 role 就是 button。如果我们使用 Div + style 来实现一个button，那就需要考虑加 role 了。
* **aria-label**
举个 🌰，如果我们有一个按钮，其上的 text 是个 x，代表关闭的意思，如果只是使用普通的标签，这时候，辅助设备是无法识别这个 x 的含义表达给用户的，这时候就需要添加 aria-label = 'close'，这时候屏幕阅读器就会将这个 close 阅读给用户，但不会在视觉上有任何的影响。
* **aria-labellby**
和 aria-label 的作用类似，只是当你想要的标签文本已在其他元素中存在时，可以使用aria-labelledby，所有读取的元素的 id 即可。
* **aria-owns**
aria-owns 会将 DOM 中独立的一个元素视为当前元素的子项 任何向 DOM 显式隐藏的内容同样不会包含在无障碍树中。
* **aria-hidden**
我们大概都知道，当网站弹出一个模态框的时候，我们几乎是看不清除模态框以外的元素的，也是不能和其交互的，但对于使用屏幕阅读器的用户怎么办呢，因为如果你不加任何 ARIA 标签，他们默认还是会听到每个元素的解读，这时候你就需要使用 aria-hidden 来屏蔽掉除模态框以外的 DOM
* ......


## 对比度的设计
![](https://upload-images.jianshu.io/upload_images/2190281-c746ed4425b89636.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
这张图从左到右，我们能看到对比度越来越低，识别度也越来越低，如果我们使用了类似的对比度，有人统计过，大约 5% 用户在访问您的网站时无法获得我们预想的体验。
WCAG 2.0 对页面上文字的对比度有一个最低的要求 4.5 : 1
所以保持一个合理的对比度，也是我们可以很容易就做到事情。

## 总结一些好的实践
再简单总结一些开发时可以用到的实践，都可以在 WCAG 2.0 里面找到。
* 非交互式内容（例如，标题）应该避免可聚焦
* 防止存在于DOM但不可见的屏幕外内容时刻聚焦
* 检查所有自定义控件以获取 role 赋予其状态的适当和任何所需的ARIA属性
* 视觉隐藏内容，确保设置 aria-hidden=”true”
* 链接和按钮等交互式元素需要hover 状态
* 避免键盘陷阱
* 设计尽量简洁简约

## 手动测试是不是太累了
那开发做了这些之后，QA怎么去测试呢，或者说我们开发了一个网站之后怎么知道我们有哪些做的不合理的地方不利于 Accessibility呢，总结了一些工具。

Chrome 插件
* [ax](https://chrome.google.com/webstore/detail/axe/lhdoppojpmngadmnindnejefpokejbdd?hl=zh-cn) 可以测试网站的 Accessibility 现状，并指出哪里需要改进以及建议的方法
* [WAVE](https://chrome.google.com/webstore/detail/wave-evaluation-tool/jbbplnpkjmmeebjpijfedlgcdilocofh?hl=zh-cn) 作用同上，只是提示方式有些区别
* [Nocoffee](https://chrome.google.com/webstore/detail/nocoffee/jjeeggmbnhckmgdhmgdckeigabjfbddl?hl=zh-cn) 可以模拟一些有视力问题的用户，从他们的视角来看看你的网站

手动测试站点的可访问性可能是乏味且容易出错的，自动化流程当然是最好的。

自动化测试工具
* [pa11y](http://pa11y.org)
ThoughtWorks 在2017年3月的技术雷达，具体使用可参考[《无障碍性测试工具 Pa11y》](http://insights.thoughtworkers.org/accessibility-testing-tools-pa11y/)


## 明明可以做的更好
整理了一些相关的视频，感触颇多，他们都可以这么努力，更何况我们呢。
* [他们可以用眼上网](https://www.bilibili.com/video/av4682091/)
* [苹果公司无障碍主题视频](https://v.qq.com/x/page/t0561x2zxd1.html)
* [帮助盲人探索世界](https://www.ted.com/talks/chieko_asakawa_how_new_technology_helps_blind_people_explore_the_world/transcript?/&language=zh-cn#t-33387)

最后我想认真地打出这几个我们常说的几个字 — **人人平等**。
我想，我们真的可以做的更好。
