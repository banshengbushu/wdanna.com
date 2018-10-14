---
title: React那些事

categories: Web 前端
---


## 背景
React是=起源于 Facebook 的内部项目，因为该公司对市场上所有 JavaScript MVC 都不满意，就决定自己写一套，用来架设 [Instagram](https://instagram.com/) 的网站，2013年5月开源

## WHAT
官网是这样解释的 —— **A JavaScript library for building user interfaces**，三大特性如下：
  * **Declarative**
声明式编程，告诉机器你想要什么（What），让机器想出如何做（How），
对应的是命令式编程，命令机器如何去做某件事（How），而不管你要的是什么，它都会按照你的命令实现。
  * **Component-Based**
任何一个功能独立的模块都定义成组件，一个个组件通过不断复用，组合与嵌套，构成一套完整的UI界面。
  * **Learn Once, Write Anywhere**

## 核心思想
#### **组件化思想**
React 让我们重新规划界面，把任何一个功能独立的模块都定义成组件，即被独立封装的可复用 UI 部件。一个个的组件通过不断复用，组合与嵌套等，构成一套完整的 UI 界面。

一个组件的写法

```
import React, { Component } from 'react';
import { render } from 'react-dom';

class HelloMessage extends Component {
  render() {
    return <div>Hello {this.props.name}</div>;
  }
}
render(<HelloMessage name="world" />, mountNode);

```
`render`会把这个组件显示到页面上的某个元素`mountNode`里面，显示的内容就是<div>Hello world</div>

组件的划分
* 把 UI 划分出组件层级，可以想想**什么情况下我们需要新建一个函数或对象**）

  * 单一功能原则， DRY
  * 一个组件应该只做一件事情。如果这个组件功能不断丰富，它应该被分成更小的组件


#### **JSX语法**——有些人喜欢它，而其他人认为这是一个很大的退步，

>不得不说是一种非常聪明的做法，JSX代替传统的HTML Templates，让前端实现真正意义上的组件化成为了可能

HTML直接嵌入了JS代码里面，前端被“表现和逻辑层分离”这种思想“洗脑”太久了，可能不好接受的设定之一。

实际上组件的HTML是组成一个组件不可分割的一部分，能够将HTML封装起来才是组件的完全体，React发明了JSX让JS支持嵌入HTML，但它具有无可争议的优点：静态分析，JSX标记中发生错误，编译器会立即报错而不是留待运行时出现莫名其妙的问题。这有助于开发人员快速排查错误以及避免其它愚蠢的错误，比如拼写错误。

好处是你可以不一定使用这种语法，但是要使用包含JSX 的组件，是需要“编译”输出JS 代码才能使用的

#### Virtual DOM
DOM是什么？

>DOM是Document Object Model，就是将XML（或者HTML）内的节点定义成基本统一的对象数据可以供程序语言（如javaScript）控制的技术规范
通过 DOM 你可以改变网页。

你可以使用 Javascript 语言来操作 DOM 以改变网页。

为了改变网页，你必须告诉 Javascript 改变哪一个节点。这就是操作 DOM。

真正的 DOM 元素非常庞大，这是因为标准就是这么设计的。而且操作它们的时候你要小心翼翼，轻微的触碰可能就会导致页面重排，这可是杀死性能的罪魁祸首。

React 最大的特色是当View层在渲染的时候,它不会直接从模板里面去构建一个DOM节点. 首先, 它创建一些暂时的, 虚拟的 DOM, 然后和真实的DOM还有创建的Diffs一起做对比, 然后才决定需不需要渲染。

当组件状态state有更改的时候，React会自动调用组件的render方法重新渲染整个组件的UI，所以React实现了一个Virtual DOM，组件DOM结构就是映射到这个Virtual DOM上，React在这个Virtual DOM上实现了一个diff算法，当要重新渲染组件的时候，会通过diff寻找到要变更的DOM节点，再把这个修改更新到浏览器实际的DOM节点上，所以实际上不是真的渲染整个DOM树。这个Virtual DOM是一个纯粹的JS数据结构，所以性能会比原生DOM快很多。

Virtual DOM 本质上就是在 JS 和 DOM 之间做了一个缓存。可以类比 CPU 和硬盘，既然硬盘这么慢，我们就在它们之间加个缓存：既然 DOM 这么慢，我们就在它们 JS 和 DOM 之间加个缓存。CPU（JS）只操作内存（Virtual DOM），最后的时候再把变更写入硬盘（DOM）

Virtual DOM 算法：
 * 触发相应组件render方法

 * 重新构建新的虚拟DOM树

 * 将当前新的虚拟DOM树和上一次的旧树进行对比

 * 得到DOM结构的区别，计算出最小变化集，进行实际的浏览器DOM更新（批量更新）。


#### Data Flow
数据如何存放，如何更改数据，如何通知数据更改等等，单向响应的数据流，从而减少了重复代码，这也是它为什么比传统数据绑定更简单。

接受输入数据（通过 this.props ），组件还可以保持内部状态数据（通过 this.state ）当一个组件的状态数据的变化。

**React 组件之间交流的方式**

组件免不了要与用户互动，React 的一大创新，就是将组件看成是一个状态机，一开始有一个初始状态，然后用户互动，导致状态变化，从而触发重新渲染 UI。

* 【父组件】向【子组件】传值；
父组件的数据可以通过设置子组件的props传递数据给子组件
* 【子组件】向【父组件】传值；
可以在父组件中传一个callback(回调函数)给子组件，子组件内调用这个callback即可改变父组件的数据
* 兄弟组件之间传值
没有任何嵌套关系的组件之间传值（PS：比如：兄弟组件之间传值）
当两个组件不是父子关系，但有相同的父组件时，将这两个组件称为兄弟组件。兄弟组件不能直接相互传送数据，此时可以将数据挂载在父组件中，由两个组件共享：如果组件需要数据渲染，则由父组件通过props传递给该组件；如果组件需要改变数据，则父组件传递一个改变数据的回调函数给该组件，并在对应事件中调用。

写了个简单的例子如下：
```
//孙子，将下拉选项的值传给爷爷
var Grandson = React.createClass({
    render: function(){
        return (
            <div>性别：
                <select onChange={this.props.handleSelect}>
                    <option value="男">男</option>
                    <option value="女">女</option>
                </select>
            </div>
        )
    }
});
//子，将用户输入的姓名传给爹  
//对于孙子的处理函数，父只需用props传下去即可
var Child = React.createClass({
    render: function(){
        return (
            <div>
                姓名：<input onChange={this.props.handleVal}/>
                <Grandson handleSelect={this.props.handleSelect}/>
            </div>
        )
    }
});
//父组件，准备了两个state，username和sex用来接收子孙传过来的值，对应两个函数handleVal和handleSelect
var Parent = React.createClass({
    getInitialState: function(){
        return {
            username: '',
            sex: ''
        }
    },
    handleVal: function(event){
        this.setState({username: event.target.value});
    },
    handleSelect: function(event) {
        this.setState({sex: event.target.value});
    },
    render: function(){
        return (
            <div>
                <div>用户姓名：{this.state.username}</div>
                <div>用户性别：{this.state.sex}</div>
                <Child handleVal={this.handleVal.bind(this)} handleSelect={this.handleSelect.bind(this)}/>
            </div>
        )
    }
});
React.render(
  <Parent />,
  document.getElementById('test')
);
```

* Props 传递数据
>如果组件嵌套层次太深，那么从外到内组件的交流成本就变得很高，通过 props 传递值的优势就不那么明显了。所以个人建议尽可能的减少组件的层次，就像写 HTML 一样，简单清晰的结构更惹人爱）

* 难的地方
在创建应用的每一个 state之前要做的：
* 确定每一个需要这个 state 来渲染的组件。
* 找到一个公共所有者组件(一个在层级上高于所有其他需要这个 state 的组件的组件)
* 这个公共所有者组件或另一个层级更高的组件应该拥有这个 state。
* 如果你没有找到可以拥有这个 state 的组件，创建一个仅用来保存状态的组件并把它加入比这个公共所有者组件层级更高的地方
* 当应用足够复杂时才能体会到它的好处，虽然在一般应用场景下你可能不会意识到它的存在

兄弟组件的沟通的解决方案就是找到两个组件共同的父组件，一层一层的调用上一层的回调，再一层一层地传递props。如果组件树嵌套太深，就会出现如下惨不忍睹的组件亲戚调用图

![](http://upload-images.jianshu.io/upload_images/2190281-98d607e2b049be45.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 全局事件
Context 使用上下文可以让子组件直接访问祖先的数据或函数，无需从祖先组件一层层地传递数据到子组件中

## 第三方的类库
React让我们有很大的自由度去挑选第三方的类库，比如


* [路由](https://link.juejin.im/?target=https%3A%2F%2Freacttraining.com%2Freact-router%2Fweb%2Fguides%2Fquick-start)机制

* AJAX（[Fetch](https://link.juejin.im/?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fen%2Fdocs%2FWeb%2FAPI%2FFetch_API) or [axios](https://link.juejin.im/?target=https%3A%2F%2Fgithub.com%2Fmzabriskie%2Faxios)）
* 各种CSS封装（详见：[github.com/MicheleBert…](https://link.juejin.im/?target=https%3A%2F%2Fgithub.com%2FMicheleBertoli%2Fcss-in-js)）
* 更强大的单元测试（[Enzyme](https://link.juejin.im/?target=https%3A%2F%2Fgithub.com%2Fairbnb%2Fenzyme)）
* Remarkable 渲染markdown语法

## Redux
Redux是一种组织代码的推荐思想，就像 “引导数据流流向的导流管”，解决上面那幅关系复杂的亲戚图问题
* 整个应用只有唯一一个可信数据源，也就是只有一个Store，如 Redux 限定一个应用中只能有单一的 store，这样的限定能够让应用中数据结果集中化，提高可控性

*  Action、Reducer、及 Store

* State 只能通过触发Action 来更改
* State 的更改必须写成纯函数，也就是每次更改总是返回一个新的State，在*Redux 里这种函数称为Reducer

>Redux 对于组件间的解耦提供了很大的便利，如果你在考虑该不该使用 Redux 的时候，社区里有一句话说，“当你不知道该不该使用 Redux 的时候，那就是不需要的”

Redux 用起来一时爽，重构或者将项目留给后人的时候，就是个大坑，Redux 中的 dispatch 和 subscribe 方法遍布代码的每一个角落。

**我是半生不熟 喜欢照自己的怪念头行事
喜欢一切意外 想把生活过成诗的样子
若哪天有幸相遇 请别诧异 其实我并不是个乖孩子**