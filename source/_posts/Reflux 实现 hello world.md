---
title: Reflux 实现 hello world
categories: Web 前端

---



初识Reflux
--------------- 
* Reflux  是一个简单的单向数据流应用库，灵感来自于ReactJs Flux
* 解决了数据在React 应用中的流动方式及过程

需求分析
------------
* 用 **Reflux** 实现界面渲染 hello world

分解任务
------------
1. 使用 React 创建一个组件，在页面渲染出 *hello word*
2. 安装 Reflux
3. 创建一个 **Action**
4. 创建一个 **Store**，用来监听** Action **，并且获取 **Action** 传递的 *hello world*
5. **Store** 将值传递给 **Component**，并且渲染到页面
6. 将代码上传至 Github

分步实现任务
------------------
*  使用 React 创建一个组件，在页面渲染出 *hello word*

```
'use strict';

import React from 'react';
import {render} from 'react-dom';

const App = React.createClass({    
              render:function(){       
                      return <div>                    
                             hello world                
                       </div>   
     }
});
render(<App/>, document.getElementById("content"));
```
此时，使用 React 在页面渲染出 *hello world*
*  安装 Reflux
    `npm install reflux `
  
* 创建一个 **action**
`const action = Reflux.createActions(['getHello']);`

* 创建一个 **store**，用来监听** action **，并且获取 **action** 传递的 *hello world*
```
const store = Reflux.createStore({    
                   listenables: [action],   
                   onGetHello: function (hello) {      
                               this.trigger(hello);    
                  } 
});
```
使用 `listenables` 来监听 **action **，使用`this.trigger()` 来更新数据状态

*  **store** 将值传递给 **component**，并且渲染到页面
```
const App = React.createClass({   
      mixins: [Reflux.connect(store, "hello")],  
      componentDidMount: function () {       
            action.getHello("hello world!");   
     },    
     render: function () {       
            return     <div>           
                 {this.state.hello}      
         </div>   
      }
  });
```
使用 `mixins` 将 **store** 和 component 连接 ，使用`action .getHello()`调用action

* 将代码上传至 github
[源代码地址](https://github.com/RangelZZZ/reflux-demo)

深入理解Reflux
--------------------
1. 三大主要内容
 * **Action** 是把数据从应用传到 Store 的有效载荷，是Store 数据的唯一来源，只用来描述“发生了什么”
 * **Store** 负责封装应用的业务逻辑和数据交互
 * **Views（controller-views）**是整个App 的 入口，监听Store 的变化以获取新的数据，重新 render 自己及子组件
2. 单向数据流
    Action ———————> Store ——————> View Component
      ^ 
     └───────────────────────────────────┘ 

            数据和操作在三者之间单向流动

3. 数据流动问题
 Reflux 中主要由 Action 和 Store 组成，例：当组件 list 增加 Item 时，会调用Action 某个方法（如addItem（data）并将新的数据当参数传递进去，通过事件机制，数据会传送到 Store 中，Store 可以向服务器发送请求并提交给数据库，数据更新后，再通过事件机制传递到 list 当中，并更新 UI
4. 与 Redux 的区别
 * Reflux 中去除了 Redux 中的 **Dispatch** 和 **Reducer**，保留了 Action 和 Store
 * 概念关系图对比如下：
![Redux概念关系图](http://upload-images.jianshu.io/upload_images/3106897-1e94804c19b52810.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![Reflux概念关系图](http://upload-images.jianshu.io/upload_images/3106897-7ceae309157e18bb.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
5. 优缺点
 * 优点：单向数据流，数据流动方向可以跟踪，追查问题的时候可以跟快捷
 * 缺点：写起来不太方便。要使UI发生变更就必须创建各种 Action 来维护对应的 State

总结
--------------------
1. 学习过程中遇到的问题
 * 在开始画思维导图的时候过于注重概念，没有注重实践，浪费了大量时间
 * 在使用 ReactMixins 时因为找不到 react-mixins 的cdn，花了好长时间
 *  由于不想使用 ` ReactMixins.onclass() `方法，将 ReactMixins 改成 mixins 花了好长时间
2. 经验
 * 以后学习新知识的时候要分清问题的侧重点，确定目标后再分步学习去完成目标
 * 学习知识要在最开始确定任务范围，尽量不引入别的新知识，增加学习负担