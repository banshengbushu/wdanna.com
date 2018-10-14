---
title: WebStorm卡的问题
categories: Web 前端

---



**很多项目导致WebStorm文件过于庞大，但是WebStorm里面有Excluded功能，用来将某个目录文件，设置为忽略状态，但一般不也轻易设置，比较常见的，一般是`node_modules`文件夹，解决方法如下**

* **推荐解决方法**
把`node_modules`加入到`.gitignore`文件中（如果你的项目是git的托管项目，则webstorm会自动把`.gitignore`里的文件设置为Excluded）
* **如果没有使用以上方法，则这样解决**
1、删除项目下的`node_modules`

![删除项目下面的node_modules](http://upload-images.jianshu.io/upload_images/2190281-0da54de7830676b8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2、新建一个`node_modules`空文件夹

![新建一个node_modules空文件](http://upload-images.jianshu.io/upload_images/2190281-433dab957b51bff5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3、在刚新建的`node_modules`右键点击`mark directory as`——> 点击`Excluded`
4、去`settings`下的`Language&Frameworks`——>`Javascript`——>`libraries`——>勾选`node_modules`——>点击`Remove`

![勾选node_moddules，点击Remove](http://upload-images.jianshu.io/upload_images/2190281-fbf9396e6469b3b6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

5、执行npm install，即可成功解决


**我是半生不熟 喜欢照自己的怪念头行事
喜欢一切意外 想把生活过成诗的样子
若哪天有幸相遇 请别诧异 其实我并不是个乖孩子**