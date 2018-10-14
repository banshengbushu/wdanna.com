---
title: 与Ruby的第一天
categories: Web 前端

---



### 1、学习使我快乐
早就听说`Ruby`这个语言的表达能力是一般的语言不能比的，现在终于有机会见识见识啦，虽然一开始是拒绝的，但古人不常说嘛，学如逆水行舟，不进则退～何况语言都是相通的，那就开始吧

![对，人丑就改多读书](http://upload-images.jianshu.io/upload_images/2190281-f732a3030b550dbd.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 2、基本用法（与之前学过的比较）
* 定义类
在 Ruby 中，类总是以关键字 class 开始，后跟类的名称。类名的首字母应该大写，例如
```
class Customer
```
* 创建对象
下面的实例创建了类 Customer 的两个对象 cust1 和 cust2：
cust1 = Customer. new
cust2 = Customer. new
* 创建数组
```
names = Array.new
```
* 设置全局变量
全局变量以 $ 开头。未初始化的全局变量的值为 `nil`（相当于`Js`中的`null`），例如
```
$global_variable = 10
```
* 判断
`Ruby` 使用 `elsif`，不是使用 `else if`
* 循环
 `for…in`语句：
```
for val  in  Array  [do]

              #code

       End
```
* 定义方法
方法名应以小写字母开头。如果您以大写字母作为方法名的开头，Ruby 可能会把它当作常量，从而导致不正确地解析调用。
```
def method_name 
   expr..
end
```
* 可以使用`#{ expr }`替换任意 Ruby 表达式的值为一个字符串

### 3、安装RubyMine

* 点击[这里](https://www.jetbrains.com/ruby/)下载并安装`RubyMine`，一个高效方便的`ruby`IDEA哦！
* 下载好安装包后，进入到解压目录下的`bin`目录执行
```
$ ./rubymine.sh
```
* 在桌面点击`Lock form Launcher`即可

### 4、Hello World

* 新建一个文件`hello_world`，写如以下内容
```
puts("Hello World")
```
* 进入该文件目录，执行
```
$ ruby hello_world
```
* 输出`Hello World`即成功
![hello_world](http://upload-images.jianshu.io/upload_images/2190281-b3a990038b98e399.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 5、完成一个需求

![需求](http://upload-images.jianshu.io/upload_images/2190281-e204d50dcf17b137.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 描述
编写一个输出数字从1到n的字符串表示形式的程序。对于三的倍数，应该输出“Fizz”五的倍数输出“Buzz”，既是5的倍数又是三的倍数的输出“FIzzBuzz”
* 思路
 * 思路—新建数组—>判断语句—>输出字符串
 * 写单元测试
* 实现
![实现的代码](http://upload-images.jianshu.io/upload_images/2190281-92c85ff5528a3e15.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 单元测试
Ruby中也提供了单元测试的框架，Ruby内置的库里面没有包含[TestSuite](http://test-unit.rubyforge.org/test-unit/index.html)，需要额外安装一个第三方的`gem（test-unit）`
```
$ sudo gem install test-unit
```
在项目中可以新建一个`test-unit`就会生成测试代码模板，


![测试](http://upload-images.jianshu.io/upload_images/2190281-41957821626a3e77.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

比如
```
assert true
```
这行代码叫做“断言”（assertion）。断言只有一行代码，把指定对象或表达式和期望的结果进行对比。例如，断言可以检查：
两个值是够相等；
对象是否为nil；
这行代码是否抛出异常；

每个测试中都有一个到多个断言。只有所有断言都返回真值，测试才能通过。

* 测试代码
![测试代码](http://upload-images.jianshu.io/upload_images/2190281-1085ff4fa25231fd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 运行测试代码，执行以下命令
```
$ ruby FizzBuzz.rb
```
![成功喽](http://upload-images.jianshu.io/upload_images/2190281-03c52a550e874512.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
具体实现代码见[我的Github](https://github.com/banshengbushu/ruby-demo)

### 6、学习资料
* 书籍《Ruby基础教程》:[https://book.douban.com/subject/25958845/](https://book.douban.com/subject/25958845/)
* 在线学习ruby：[http://tryruby.org/](http://tryruby.org/)
* Ruby学习资源汇总：[http://iwanttolearnruby.com/](http://iwanttolearnruby.com/)
* ruby中文学习社区：[https://ruby-china.org/](https://ruby-china.org/)
* ruby练习题：[http://rubyquiz.com/](http://rubyquiz.com/)
* Ruby在线学习教程：[https://www.codecademy.com/zh/learn/ruby](https://www.codecademy.com/zh/learn/ruby)

**我是半生不熟 喜欢照自己的怪念头行事
喜欢一切意外 想把生活过成诗的样子
若哪天有幸相遇 请别诧异 其实我并不是个乖孩子**