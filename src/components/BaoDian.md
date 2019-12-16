# Html 相关


# CSS 相关


# JS 相关

## 1.原始类型有哪几种？

    存在着 6 种原始值
    1.boolean
    2.null
    3.undefined
    4.number
    5.string
    6.symbol


## 2.0.1+0.2为什么不等于0.3？

    0.1和0.2在转换成二进制后会无限循环，由于标准位数的限制后面多余的位数会被截掉，相加后因浮点数小数位的限制而截断的二进制数字在转换为十进制就会变成0.30000000000000004。



# 手写题目相关
## 1.手写一下数组去重
        var array=[2,1,3,4,5,3,2,4,5,6,1,2,4,5,6,1,2,3,6,6,1,2,5,2,6,1,45,6];
        function quchong(array){
        	var res=[];
        	for(var i=0;i<array.length;i++){
        		var current =array[i];
        		if(res.indexOf(current)===-1){
        			res.push(current);
        		}
        	}
        	return res;
        }
        console.log(quchong(array));

## 2.手写防抖

    <!DOCTYPE html>
    <html lang="en">

    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <title>防抖debounce</title>
    </head>

    <body>
        <div>
            <button id="debounce">防抖</button>
        </div>
    </body>
    <script>
        var debounce = document.getElementById('debounce');
        debounce.addEventListener('click', newdebounce(SayHi));

        function newdebounce(fn) {
            let Timer = null;
            return function () {
                clearTimeout(Timer)
                Timer = setTimeout(() => {
                    fn.call(this, arguments)
                }, 1000)
            }

        }

        function SayHi() {
            console.log('sayHi 防抖');
        }
    </script>

    </html>

## 3.手写节流

    <!DOCTYPE html>
    <html lang="en">

    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <title>throttle节流</title>
    </head>

    <body>
        <div>
            <button id="throttle">
                节流throttle
            </button>
        </div>
    </body>
    <script>
    var throttle = document.getElementById('throttle');
    throttle.addEventListener('click', newthrottle(SayHI))

    function newthrottle(fn) {
        let State = true;
        return function () {
            if (!State) {
                return;
            }
            State = false;
            let timer = null;
            timer = setTimeout(() => {
                State = true;
                fn.call(this, arguments);
            }, 1000)
        }
    }

    function SayHI() {
        console.log('节流success');
    }
    </script>

    </html>
# HTTP 网络相关
## 1.从url地址到最终页面渲染完成 发生了什么呢？

	1.dns解析 将域名解析为IP地址
		-浏览器DNS缓存
		-系统DNS缓存
		-路由器缓存
		-网络运营商得DNS缓存
		-递归搜索
	2.TCP三次握手
		第一次握手 
			是由浏览器发起的，用来告诉服务器我要发送请求
		第二次握手
			是由服务器发起，告诉浏览器我准备接受了，你发吧
		第三次握手
			是由浏览器发起得，告诉浏览器我马上发了，准备接受吧
	3.发送请求
		-请求报文，HTTP协议得通信内容
	4.接受响应
		-响应报文
	5.渲染页面
		-遇见HTML标记 调用HTML解析器 解析对应得token标记，构成DOM树
		-遇见style/link标记 浏览器会调用css解析器，处理并声称cssdom树
		-遇见script标记 调用javascript解析器 处理script代码（绑定事件，修改dom/css树）
		-将DOM和CSSOM树合并成一个渲染树
		-根据渲染树计算布局（布局）
		-将各个节点颜色绘制到屏幕上（渲染）
		注意：这几个步骤 不一定按照顺序执行 可能会反复多次执行如果dom和css树被修改了 可能会执行多次
	6.断开连接（TCP四次挥手）
		第一次挥手
			由浏览器发起，发送给服务器，我发送完了（请求报文），你准备关闭吧
		第二次挥手
			由服务器发起，我东西接受完了（请求报文） 我准备关闭了你也准备把
		第三次挥手
			由服务器发起，告诉浏览器我发送完毕，你准备关闭吧，这里指的响应报文
		第四次挥手
			由浏览器发起，告诉服务器 我东西发完了 我准备关闭了你也准备吧
		--先关服务器 在关浏览器	

# ES6相关



## 1.什么是ES6

	ES6是新一代js语言标准 新增了一些js原生方法 使js使用更加规范 更加优雅
## 2.ES5,ES6有什么区别

	  ES2015特指在2015年发布的新一代JS语言标准
	  ES6泛指下一代JS语言标准，包含ES2015、ES2016、ES2017、ES2018等
	  现阶段在绝大部分场景下，ES2015默认等同ES6。ES5泛指上一代语言标准。ES2015可以理解为ES5和ES6的时间分界线。
## 3.了解babel吗 有什么作用

	babel是一个ES6转码器 可以将代码转为ES5代码 以便兼容那些还没支持ES6得平台
## 4.let有什么用 有了var 为什么还要使用let
	
	let 声明的变量拥有自己的块级作用域，且修复了var声明变量带来的变量提升问题。

## 5.箭头函数 

	箭头函数没有自己得this this总是指向他的上一层this
	箭头函数不能用作构造函数 因为它没有自己的this 无法实例化
## 6.双冒号运算符 用来取代 bind call和apply

foo：：bar
## 7.symbol是什么

	symbol是ES6引入得第七种原始数据类型 symbol属性不能被for。。。in遍历
	也不是私有属性
## 8.set是什么

	set是ES6引入得一种类似Array得新的数据结构 Set实例得成员类似于数组得item成员 区别就是 数组去重   数组中元素不重复
## 9.Map是什么

	是一种类似obj得新的数据结构
## 10.promise是什么

	promise是ES6引入得一个新的对象 他的主要作用是用来解决Js异步机制例得
	回调地狱 只是封装了异步回调 使得异步回调写的更加优雅 可读性更高
	let promise=new promise((resolve,reject)=>{
		let promise
		if(xx){}else{}
		promise.then(respone=>{
			xxx
		}).catch(error=>{
			xxx
		})
	})



# Vue 相关

## 1.简单得介绍一下Vue？

    vue.js是一个用户创建WEB交互界面得库.
    
    他让你通过简单的操作api创建数据驱动的ui组件.
    
    同时他也是一个声明式，组件式框架.

## 2.说一说Vue的生命周期 

	beforeCreate、created、
	beforeMount、mounted、
	beforeUpdate、updated、
	beforeDestroy、destroyed
	创建=>挂载=>更新=>销毁
	所以vue的组件也是有生命周期的，四个阶段，八个钩子
	beforeCreate
		千万不要去修改data数据 最早也要放在created里面去做
		在实例化初始之后 实例初始化 new vue（）
		在实例初始化之后，数据观测和暴露了一些有用的实例属性与方法。
	created
		是一个template编译的过程 结果是解析成了render函数
		
## 3.Vue组件间通信
	组件通信得几种方式
		子传父 父传子  兄弟组件传递  爷孙组件传递（隔代组件）
	1.props
		通过一般属性传递 父传子
		通过函数属性实现子传父
		缺点：隔代属性比较麻烦
	2.自定义事件函数
		子组件向父组件通信
		绑定监听@xxx='xxx'
		this.@emit('xx',data)	
	3.slot
		专门实现父子传递得数据标签
	4.vuex
		专门做状态管理得库（一个大的面试点！！！）
	5.pubsub(消息订阅和发布)
		我通常使用pubsub.js
			订阅：pubsub.subscribe('xxx',fun(名字,data){})
			发布：pubsub.publish('名字',data)	
		优点随意传递 随意关系得传递
## 4.Vuex是什么？

    Vuex是一个专门为Vue.js应用程序开发的状态管理模式

    它采用集中式存储管理应用得所有组件得状态

    并以相应的规则保证状态以一种可预测的方式发生变化

## 5.Vuex应用场景

    Vuex只能用于单个页面中不同组件得数据流通（组件件数据传递）

## 6.Vuex基础概念

	State是什么
		vuex得单一状态树
		state是vuex自己维护的一份状态数据，数据得格式需要根据业务去设计
	Getters
		getters属性主要是对state中数据得一种过滤，属于一种加强属性
	Actions
		对于store中数据得操作动作在action中提交
		action和mutation类似 但是action提交时mutation并不直接修改数据	
	Mutations
		更改VueX得store中得状态得唯一方式是提交mutation 
		mutation只能执行同步操作
	Module模块化
		业务逻辑得增多可以使用模块话得方式使代码清晰整洁
## 7.vue-router是什么？

    路由就是SPA（单页应用）得路径管理器
    
    路由模块得本质就是建立起url和页面之间得映射关系

    传统页面是靠a标签进行跳转 但是vue中不可以这样 因为vue只有一个主

    的index.html 所以必须使用vue-router进行管理

## 8.Vue-router实现原理

    SPA单一页面应用程序 只有一个完整的页面 他在加载时不会加载整个页面
    知识更新某个指定容器中的内容

## 9.Hash模式

    Vue-router默认hash模式 使用url的hash来模拟一个完整的URL 于是当URL改变时 页面不会重新加载 hash（#）是url锚点 代表的是网页中的一个位置  改变#后的部分 只会滚动到相应位置 不会重新加载网页 也就是用来指导浏览器动作的 所以说hash模式通过锚点值得改变 渲染制定dom位置不同得数据

## 10.History模式

    由于hash模式会在url中自带# 如果不想要很丑得hash 可以用路由得history模式  只需要在配置路由规则时 加入mode:history 就可以用Api来完成URL跳转而无需重新加载页面

## 11.跳转方式

    方式一 直接修改地址

    方式二 this.$router.push('路由地址')

    方式三 <router-link to='路由地址'></router-link>

## 12.vue-router 使用方式

    1. 下载
    2. 在main中引入
    3. 安装插件 vue。use
    4. 创建路由对象 并且配置路由规则
    5. 在app.vue中留坑  <router-view>
    
## 13.vue-router如何传递参数

    1.用name传递参数
    2.通过router-link标签中的to传参
    3.利用url传递参数 在配置文件以冒号形式设置参数
## 14.vue-router跳转方法

    1. .go跳转到上一次浏览的页面
    2. .replace指定跳转地址
    3. .replace{name}跳转到指定名字下  #不可以退回
    4. .push通过push进行跳转   #可以后退
    5. push（name）同3
    6. 404 是*地址

## 15.vue-router导航卫士

    全局守卫 
    1 router.beforeEach全局前置守卫 进入路由之前
    
    2 router.beforResolve全局就解析首位 在beforerouteenter调用之后
    
    3 router.afterEach全局后置钩子 进入路由之后
## 16.to from next这三个参数

     to和from 是将要进入和将要离开的路由对象 路由对象指的是平时通过this.route获取到的路由对象
     
     next是一个函数 且必须调用 否则不能进入路由（页面空白）
     
    next 进入该路由
    
    next（false） 取消进入 url地址重置为From路由地址
    
    beforeEnter: (to, from, next) => { 
    
    // 参数用法什么的都一样,调用顺序在全局前置守卫后面，所以不会被全局
    
    守卫覆盖
    
    // ...
    
    }	
## 17.路由组件内的守卫：

    beforeRouteEnter 进入路由前
    
    beforeRouteUpdate (2.2) 路由复用同一个组件时
    
    beforeRouteLeave 离开当前路由时

## 18.说一说keep-alive

	是用来缓存组件内部状态 避免重新渲染 是一个抽象组件 他自身不会
	渲染一个Dom元素 也不会出现在父组件链中 
	主要用于保留组件状态或避免重新渲染
生命周期钩子

	activated和deactivated
	activated在组件第一次渲染时会被调用
	，之后在每次缓存组件被激活时调用。
	deactivated：组件被停用(离开路由)时调用
	使用了keep-alive就不会调用beforeDestroy(组件销毁前钩子)
	和destroyed(组件销毁)，因为组件没被销毁，被缓存起来了。
新增属性

	include：匹配的 路由 组件 会被缓存
	exclude 匹配的 路由 组件 不会被缓存
	include和exclude支持三种方式来有条件的缓存路由：
	采用逗号分隔的字符串形式，正则形式，数组形式。
    当你缓存了组件之后 再次进入beforeCreate created beforemounted

    mounted  如果想使用 使用activated钩子和destoyed钩子使用


# React 相关


# 性能优化相关


# node 数据库相关


























<!-- ---
title: 个人面试笔记
author: 王雪龙
avatar: https://wangdeimg.oss-cn-beijing.aliyuncs.com/20171110225150_ym2jw.jpeg
authorLink: https://www.wangxuelong.com
authorAbout: thisone
authorDesc: 一个好奇的人
categories: 技术
date: 2019-06-12 12:16:01
comments: true
tags: 
 - web
 - 面试
keywords: Sakura
description: 面试笔记
photos: https://static.2heng.xin/wp-content/uploads//2019/02/wallhaven-672007-1-1024x576.png
--- -->