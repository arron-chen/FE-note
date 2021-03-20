### FE学习笔记

> 个人学习笔记，记录总结所有经历的前端实践。

#### 前端是什么？

Front-End 前端：在用户界面设计图确定之后，根据不同的目标环境（Android/IOS/浏览器/windows/Mac OS）进行对应的软件实现。而通常我们所说的前端开发是指开发工作在浏览器上的网页，而对应的移动开发工程师则是开发工作在手机上的软件。这两者都是编写面向用户的软件的，所学习的只是以及工作流程也是非常相似的，因此我们可以统称为客户端开发工程师。

#### 大前端的概念？

2017年，以饿了么为代表的一些企业开始提出大前端的概念。2018年，InfoQ 举办了首届全球大前端技术大会，在大会中将前后端分离、跨平台和 PWA 等技术设立了专场，这次大会具有重要的意义，它预示了大前端时代的到来。
那么大前端是什么呢，直接来说，大前端是所有前端的总称，最接近用户的那一层都叫前端，比如 Android、iOS、Web、Watch、小程序等。
简而言之：一套代码，多端复用


#### 基础
1. vue与react的异同
2. PWA是什么？应用场景
3. polyfill兼容如何使用？
4. web安全 如何防止xss
5. 

## html

1. html5新特性： 语义化标签、audio、canvas、本地存储（localstorage、sessionstorage）、
2. [浏览器从输入URL到页面显示过程](https://juejin.cn/post/6928677404332425223) 
    [url解析到页面显示](https://juejin.cn/post/6939170194367447053)

3. 

## CSS

1. 布局
2. 盒模型
3. 回流重绘
4. css动画 animation transform
5. BFC
6. [1px解决方案](https://juejin.cn/post/6874940963635232775)
7. viewport与移动端布局
8. 像素单位与设计稿实现 px em rem vw vh
9. 预处理语言（sass、less） 区别
10. [H5自适应方案](https://juejin.cn/post/6844903795613237261)

## JS

1. 事件委托
2. 事件轮询
3. 事件流
4. 路由 history
5. this
6. 闭包 闭包的作用与应用场景 闭包的缺陷
7. 作用域
8. 原型链
9.  基础类型 判断数据类型有几种(typeof instanceof constructor)
10. 对象
11. 字符串
12. 数组 数组方法（splice、slice、sort、map）
13. intersectionObserve [如何判断元素是否进入可视区域](https://juejin.cn/post/6844903725249609741)
14. 正则
15. 深拷贝 浅拷贝
16. 防抖节流
17. call、apply、bind
18. 函数柯里化
19. 数组扁平化
20. 数组去重
21. 算法基础 二叉树、链表、排序查找、深度广度优先算法
22. https通信 http0.9、http1.x、http2 的区别 [http请求get与post区别](https://m.php.cn/article/413628.html)  http2的优点（多路复用）
23. 浏览器工作原理  回流与重绘
24. 垃圾回收
25. 缓存 强缓存、协商缓存
26. [ajax无感知刷新](https://www.jianshu.com/p/54a2e4c4b567)
27. promise与 async await 异步解决方案变迁与优缺点
28. ES6新特性： let、const变量 解构赋值 字符串模版  promise proxy 
29. [TypeScript](https://juejin.cn/post/6844904182843965453) 
30. iframe优缺点
31. 模块化
32. 
## 前端优化
1. [性能优化常见方法](https://juejin.cn/post/6931157334508961799)
   [性能优化](https://juejin.cn/post/6904517485349830670)
   
`压缩资源大小`
1. html css js 图片大小


`加快首屏加载`

`懒加载`

1. DNS预解析
2. CDN缓存
3. 资源缓存、数据缓存
4. 骨架屏
5. 服务器开启gzip
6. 组件按需加载
7. 减少dom操作
8. 

## 框架
### vue

`vue基础`
1. 生命周期
2. 指令介绍
3. 自定义指令
4. 双向绑定原理
5. nextTick原理
6. 动态变化
7. 模版编译原理
8. diff算法
9. 虚拟dom树
10. keep-alive
11. vue性能优化 函数式组件按需加载 路由懒加载 局部变量 computed使用解构 非响应式数据 异步组件 [性能优化](https://juejin.cn/post/6922641008106668045)
12. slot的使用
13. 组件通信
14. 自定义组件方法有哪些directives 钩子函数（bind、inserted、update）钩子参数（el, binding）
15. v-loader作用
16. vue模版编译理解
17. [vue优化](https://juejin.cn/post/6940190960609394695)
18. [初级面试题](https://juejin.cn/post/6844903874709766152) [vue中级面试题](https://juejin.cn/post/6844903934314676231)
    [高级面试题](https://juejin.cn/post/6844903913498345479) [v-router面试题](https://juejin.cn/post/6844903961745440775)
    [js面试题](https://juejin.cn/post/6844903636271644680)
    
    
`vue-router`
1. [路由详解](https://blog.csdn.net/sinat_17775997/article/details/8068839  ) [路由详解2](https://www.jianshu.com/p/7d71d3f23988) [路由使用分析](https://juejin.cn/post/6844904084567228430)
2. active-class router-link的属性，什么作用
3. vue-router实现的原理
4. 如何定义动态路由
5. 有哪几种导航钩子及作用
6. 
7. 
`vuex`
1. [vuex原理](https://juejin.cn/post/6844904081119510536) [vuex使用及原理](https://juejin.cn/post/6844904068553392141)
   [vuex快速使用](https://juejin.cn/post/6844903764671856653)
2. 属性介绍
`SSR`
1. nuxt.js 服务端渲染解决方案
`vue3`
1. compositionAPI
2. teleport
3. suspense
4. fragment 多个根节点
5. 更好的tree-shaking
6. [异步组件](https://juejin.cn/post/6940454764421316644)
7. [vue3更新简介](https://juejin.cn/post/6940454764421316644)

`axios`
1. 组件通信

### React

`react基础`
`redux`

### electron
## 跨平台解决方案

`flutter`
`mpvue`
`uni-app`
## 打包

### webpack 
`webpack基础`
1. [webpack详解](https://juejin.cn/post/6926760819375996941)
2. [入门webpack](https://juejin.cn/post/6940447269703385095)
3. [webpack代码分离](https://juejin.cn/post/6939708814555873311)
4. [webpack从0到1打包一个按需引入组件](https://juejin.cn/post/6932736907830886413)
`webpack优化`
1. mode改为production 
2. tree-shaking 
3. scope hoisting 模块关系推测打包更小
4. 代码压缩 uglifyPlugin
5. css优化 将css提取到单独文件中 异步加载只针对css mini-css-assets-webapack-plugin
6. codeSplit代码分块 按需加载 splitChunksPlugin 
7. 动态导入
8. noParse 第三方模块不解析内部依赖
9. ignorePlugin 使用动态链接库 框架代码只构建一次
10. 分析优化 webpack-bundle-analyzer speed-measure-webpack-plugin

## 服务端
### node
`node基础`

`express`

`koa2`