---
title: 浏览器 HTTP Caching 策略 (已验证)
categories: Web 前端
---


很多人会觉得 HTTP 的 Caching 策略很难，我之前也不例外，究其原因，它是乌龟的屁股，规定（龟腚），在官方介绍中也没有给出简单有效的事实验证，自己也没有相对多的机会去实践验证。

这样一来，很容易让人对它的认识比较模糊，也就很容易被忽略，有机会前两天和  [项目组大牛](https://liyaodong.com/) Pair 研究了之后，想出了一个较为简单方法可以快速地验证了一些 Case，通过一些测试用例可以清楚地得出一些结论，文末会给出 repo 的地址。

![](https://upload-images.jianshu.io/upload_images/2190281-9ffea266c68d97d1.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### Cache
说到缓存，知乎上看到过这样一个解释，觉得还挺有意思。

![Cache](https://upload-images.jianshu.io/upload_images/2190281-df5cca82a32a6b2a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

>如上图一样，Cache 可以认为是一种保管箱。
>右边那个被锈掉的 Food Cache，就是部署在森林里的存应急物资的保管箱。功能是把你需要用的东西放在更容易拿到的地方。
>
>虽然常用准确翻译叫缓存，但台湾的翻译更好，叫快取。

这样一来，看WiKi 的解释也就很清楚了。
>A **cache** [/kæʃ/](https://en.wikipedia.org/wiki/Help:IPA/English "Help:IPA/English") [*KASH*](https://en.wikipedia.org/wiki/Help:Pronunciation_respelling_key "Help:Pronunciation respelling key"),<sup>[[1]](https://en.wikipedia.org/wiki/Cache_(computing)#cite_note-1)</sup> is a hardware or software component that stores data so future requests for that data can be served faster

相信很多人应该经常也会看到 `304` 的请求吧

![](https://upload-images.jianshu.io/upload_images/2190281-c456429b8d7a8e9d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这也就为什么进入一个网页后之后的刷新会比首次快很多，归根结底都是 Cache 的功劳。

至于缓存的作用，我想应该就不用多说了，减少服务器压力，减少网络延迟和带宽，加快网页加载速度等等，所以可想而知，一个优秀的缓存策略其实对网站的优化帮助还是蛮大的。

那浏览器对资源的缓存究竟是怎么做到的？遵循什么策略，什么时候会返回 `304` 的 `code` ，具体有什么约束呢，我们来接着看。


###HTTP 缓存策略

>**HTTP 1.0**

在 HTTP 1.0 的时代，可以通过在 HTTP `Header` 中设置以下两个值来控制缓存

* **Pragma: no-cache**
Pragma 只有这一个用法，强制要求服务器在返回缓存的资源之前将请求提交到源服务器进行验证。

* **Expires**
定义了是资源“失效时刻”，对应的值是一个具体的 GMT（格林尼治时间），比如`Mon, 22 Jul 2002 11:12:01 GMT`，如果浏览器的时间还没过该时间点，那么发起的请求都不会到达服务器，它会直接从本地的缓存中读取资源内容 。
但要注意的是，Expires 所定义的缓存时间是相对服务器上的时间而言的，因为其定义的是资源“失效时刻”，所以如果浏览器上的时间跟服务器上的时间不一致（特别是用户修改了自己电脑的系统时间），那缓存时间可能就没啥意义了。

>**HTTP 1.1**

为了解决前面说到的 `Expires 定义的时间是相对服务器而言，无法保证和浏览器时间统一`的问题， HTTP 1.1 新增了 `Cache-Control` 通用首部字段来控制已缓存的内容，在 `request` 和 `response` 的 Header 均可设置，设置方法很简单，举一个例子
```
import HTTP from 'http';

let server = HTTP.createServer(( req, res )) => {
  res.setHeader( 'Cache-Control', 'public, max-age=86400' )
  res.end( 'harttle.land' )
})

server.listen(8080)
```

具体可以设置的值有以下几种：
* **no-store**
缓存中不允许存储任何关于浏览器请求和服务器响应的内容。每次由浏览器发起的请求都会从服务器下载完整的响应内容

* **public**
该响应可以被任何中间人（比如中间代理、CDN等）缓存。若指定了"public"，则一些通常不被中间人缓存的页面（默认是private）（比如 带有 HTTP 验证信息（帐号密码）的页面或某些特定影响状态码的页面），将会被其缓存

* **private**
表示该响应是专用于某单个用户的，中间人不能缓存此响应，该响应只能应用于用户自己的浏览器私有缓存中

* **max-age**
`max-age =<seconds>`表示资源能够被缓存的最大时间，在该时间段内，不会向 服务器发起请求。
相对 Expires 而言，max-age 是距离请求发起的时间的秒数，通常针对一些不会改变的文件，可以手动设置一定的时长以保证缓存有效，比如图片、css、js等静态资源。

>如果没有设置 `max-age` 则会检查是否有 `Expires` 字段，如果这两个都没有设置，浏览器则会有条默认的计算规则，就是读取 `Date` 和 `Last-Modified` 的差值除以 10，也就是说浏览器总有一个时间来保证缓存的有效期

* **no-cache**
每次有请求发出时，缓存会将此请求发到服务器（该请求应该会带有与本地缓存相关的验证字段），服务器端会验证请求中所描述的缓存是否过期，若未过期（实际就是返回304），则缓存才使用本地缓存副本，如过期，就是正常的返回响应内容。

>所以 `Pragma: no-cache` 可以应用到 HTTP 1.0 和 HTTP 1.1 ,而 `Cache-Control: no-cache` 只能应用于 http 1.1，所以很多网站为了做 HTTP 协议的向下兼容，还是可以看到依旧会带上这两个字段，比如 [腾讯课堂](https://ke.qq.com/)。

**同时要注意，如果三个字段同时出现的话，优先级从高到低分别是**
 **Pragma > Cache-Control > Expires**

### **其他首部字段**
*  **Last-Modified & If-Modified-Since**

![](https://upload-images.jianshu.io/upload_images/2190281-d3c2dc76da10e9b1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

在第一次请求资源，服务器将资源传递给浏览器时，会将资源最后更改的时间以 `Last-Modified: GMT` 的形式加在 `response` 首部上一起返回给浏览器。

第二次请求这个资源时，浏览器会给 `request` 加上 `If-Modified-Since: GMT` 这个头，发送给服务器，询问该时间之后文件是否被修改过，如果浏览器传来的最后修改时间与服务器上的一致，则直接返回 `304` 状态码，内容为空，如果两个时间不一致，则服务器会返回该资源并返回 `200` 状态码，和第一次请求类似。

* **ETag & If-None-Match**

不知道你有没有发现，其实仅仅使用 `Last-Modified: GTM` 是存在一些问题的，

比如说有些资源的内容并没有修改，只是修改了时间，其实我们是不希望重新请求服务器的，但 `Last-Modified`是无法识别的。

还有一个问题就是 `Last-Modified` 和 `If-Modified-Since` 的单位是以秒计算的，如果说资源的修改非常频繁的时候，比如在毫秒之内的话，依然是会有问题的。

为了解决上面这些问题，Http 1.1 还推出了 ETag (Entity Tag) 实体首部字段，具体的原理是这样的。

![](https://upload-images.jianshu.io/upload_images/2190281-acb37806b2bbca68.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

服务器会通过某种算法，为每个资源都计算得出一个唯一标识符，比如 `md5` 标识符，一旦这个资源发生了变化，这个标识符就会发生变化。

如上图，在浏览器第一次请求这个资源的时候， 服务器会加上`ETag: 唯一标识符` 的头，随资源一起返回给浏览器。

浏览器在收到后会保留该 `ETag` 字段，并在下一次请求时在头部增加 `If-None-Match: 唯一标识符` 将其发到服务器端，这时，服务器端只需要比较浏览器传来的`If-None-Match: 唯一标识符`跟自己服务器上该资源的 `ETag` 是否一致，就能很好地判断该资源相对浏览器而言是否被修改过了，如果被修改了，就返回 200 以及新的资源，如果 ETag 是一致的，则直接返回 `304` 告诉浏览器读取本地缓存即可。

**所以可以明显的看到，ETag 是有很多好处的，它可以更加精确的判断资源是否被修改，可以识别一秒内多次修改的情况。**

### 组合需合理
从官网上找了一张图，可以通过组合的方式来确定你使用的特定资源或一组资源的最优缓存策略。

>**理想情况下，目标应该是在浏览器上缓存尽可能多的响应、缓存尽可能长的时间，并且为每个响应提供 ETag，以便进行高效的重新验证。**

![组合需合理](https://upload-images.jianshu.io/upload_images/2190281-a679fdec71fe8bc9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


但说到这里，相信大家对具体情况到底该怎么组合应该还是有疑虑的，我们在研究后写了一些测试用例，建立在每个 Case 都可以被验证的事实上加深了对它的理解，得出的其中一个很重要的结论就是：**组合需合理**

* **如果只设置了 max-age ，则在其设置的有效期内永远不会向服务器发起请求**
* **public 和 max-age 一起使用，相当于 只设置 max-age，因为 max-age 会隐式地表明该资源是public的）**
* **no cache 单独和 max-age 一起使用其实是没有意义的，因为这每次都会向 服务器发起请求，返回资源内容，即使请求的资源内容没有发生变化**
* **ETag 和 max-age 一起使用是一个较好的缓存策略，在资源内容没有改变的情况下，服务器会返回 `304` ，让浏览器从缓存中读取资源，并且这时的缓存有效期会根据 max-age 的值自动向后 extend。**

以上这些结论都可以从 repo 的测试用例中得到，我们使用了 **puppeteer**（谷歌官方出品的一个通过DevTools协议控制headless Chrome的Node库。可以通过Puppeteer的提供的api直接控制Chrome模拟大部分用户操作来进行UI Test或者作为爬虫访问页面来收集数据）来模拟对浏览器的操作， 还有前端测试框架 **Jest** 写了一些很容易看懂的测试用例, 大家也可以添加自己不明白想验证的 Case，也欢迎大家提 Feedback。

###最后

最后想说的是，很多人应该也见到过同样是  `200`的 `code`， 有些资源是 from memory cache，而有些却是 from disk cache 的，如下图
![from disk cahce](https://upload-images.jianshu.io/upload_images/2190281-ec05410362c558aa.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![from memory cache](https://upload-images.jianshu.io/upload_images/2190281-f25375a25a1e7105.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


这个我们其实没有做过多的研究，因为这并不影响缓存策略的设置，但确定的是，这完全是由浏览器自己决定的，`memory cache` 会将资源存到内存中，从内存中获取，`disk cache` 则会将资源缓存到磁盘中，从磁盘中获取，**二者最大的区别在于：当退出进程时，内存中的数据会被清空，而磁盘的数据则不会。大家如果感兴趣可以自己再做些研究的啦。**

最后附上 [PPT 的链接](https://drive.google.com/file/d/1Scr71fTScyWEPCWqUUms5Uypsk2rWSdK/view?usp=sharing) 以及 [ repo](https://github.com/banshengbushu/HTTP-Caching-demo) 地址