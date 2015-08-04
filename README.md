移动端前端开发规范
===

## 规范概述

规范的制定是我们长期以来对工作的积累与沉淀的产物，帮助我们更快、更好、更高效的完成繁重、复杂、多样化的任务，我们制作规范的主要目的在于：

- 降低每个组员介入项目的门槛成本；
- 提高工作效率及协同开发的便捷性；
- 高度统一的代码风格；
- 提供一整套HTML、CSS解决方案，来帮助开发人员快速做出高质量的符合要求的页面。


规范名称 | 移动研发中心前端开发规范
----|---
当前版本 | v1.0 beta
参与人群 | 移动研发中心前端开发部
最后更新 | 2014.11.27

## HTML相关

### 通用html模板

	<!DOCTYPE HTML>
	<html>
	<head>
		<meta charset="UTF-8">
		<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0"/>
		<meta name="apple-mobile-web-app-capable" content="yes"/>
		<meta name="apple-mobile-web-app-status-bar-style" content="black"/>
		<meta content="telephone=no" name="format-detection"/>
		<meta name="keywords" content="苏宁易购手机版,家用电器, 手机, 电脑, 笔记本,冰箱, 洗衣机, 相机, 数码, 缤购化妆品, 红孩子母婴用品,日用百货"/> 
		<meta name="description" content="苏宁易购手机版是领先的手机网上购物商城，在线销售家用电器、触屏数码、电脑、缤购化妆品、红孩子母婴用品、日用百货等各种商品和服务。上苏宁易购手机版，随时随地，尽享购物乐趣！"/>
		<title>苏宁易购手机版 – 家用电器、手机、电脑、红孩子母婴、缤购化妆、日用百货</title>

### 注意事项

- 属性标签必须小写


### 注释写法

	<!-- 导航 [[-->
	<nav>
		<ul>
			<li></li>
		</ul>
	</nav>
	<!-- ]] 导航 -->

## CSS相关

### 注释写法

- 文件注释

<div></div>

	/*
	* @description: xxxxx中文说明
	* @author: 12345678(工号)
	* @update: 2014-11-11 18:00
	*/

- 模块注释

<div></div>

	/* Global */
	body {min-width:320px;line-height:1.5;color:#333;background:#F2F2F2;}

- 多行注释

<div></div>

	/*
	* this is comment line 1.
	* this is comment line 2.
	*/

- 特殊注释

<div></div>

	/* TODO: xxxx by 12345678 2014-11-11 18:00 */
	/* BUGFIX: xxxx by 12345678 2014-11-11 18:00 */

### 特别注意

- 样式定义的 class 里不要出现类似 `ad`,`download`,`banner` 之类的词语作为样式名,会被部分浏览器屏蔽!

### 代码提交格式规范

- 有 jira 单的填 jira 单号，没有的可以不用写，名字要加上。
- 示例：[SNBTC-6664] - 合并channel.js 点击加载更多方式替换成滚动加载_小罗

### 书写规范

- 选择器、属性和值都使用小写
- 使用!important请小心，确认是否有必要
- 多个selector共用一个样式集，则多个selector必须写成多行形式
- 避免中文，或使用转义，推荐前者
	- 如：`font-family: "Microsoft YaHei"`; `font-family:\5fae\8f6f\96c5\9ed1`;

<div></div>

	body {min-width:320px;line-height:1.5;color:#333;background:#F2F2F2;}
	.demo1 .list,.demo2 .list {display:inline-block;background:#F1F1F1;}
	

[javascript 书写风格规范](https://github.com/suning-wireless/Front-End-Standards/issues/1)

### 命名规则

- 规则命名中，一律采用小写加中划线的方式，不允许使用大写字母或 _,使用大写字母和 _ 说明此标签有js操作.
- 避免 class 与 id 重名
- 禁止直接给标签设置样式




## 注意事项

### 前后台对接

- css和js文件一定要对比过后才能提交!

### 商品图片拼接方式

目前整站有9种商品图片的调用格式

`30*30`、`60*60`、`100*100`、`120*120`、`160*160`、`200*200`、`220*220`、`400*400`、`600*600`、`800*800`

调用方式为:

http://image5.suning.cn/b2c/catentries/000000000106040162_1_200x200.jpg

200x200对应着9种图片格式,针对不同的格式进行输出



## 常用静态资源，对应本地 common 文件夹路径


	http://m.suning.com/RES/wap/
			│
			├── common/style/
			│  ├── base/base1.0.css [通用样式库,目前版本 1.0 ]
			│  └── module/ [样式组件库,待更新]
			│
			├── common/script/lib/
			│	└──zepto/1.1.4/zepto.min.js [团队基础库,内置 $.cookie, artTemplate]
			│
			├── common/script/module/
			│  │		
			│  └── swipe/
			│		    ├──1.0.0/swipe.js [通用滑动 1.0.0 版本]
			│			└──1.1.0/swipe.js [通用滑动 1.1.0 版本]
			│
			└── project/ [项目相关,待更新]



## 移动性能优化

### 发布前必要检查项

- 所有非维护图片必须有进行过压缩
- 如果项目允许，图片使用CSS Sprites 或 DataURI
- 外链 CSS 中避免 @import 引入
- 确保接入层已开启Gzip压缩（考虑提升Gzip级别，使用CPU开销换取加载时间） 注意！
- 尽量使用 CSS3 代替图片
- 首屏内图片无需延迟加载，直接写赋值 src
- `初始首屏之外的图片资源和静态资源静态资源（JS/CSS）延迟按需加载 注意！`
- `单页面应用(SPA)考虑延迟加载非首屏业务模块
- `源码输出是否符合预期`


[移动H5前端性能优化指南](http://isux.tencent.com/h5-performance.html)


### 开发注意事项

- 缓存 DOM 选择与计算
- 避免触发页面重绘的操作
- `a 链接的区域一定要大,使用户有足够的操控区域`
- 尽可能使用事件代理，避免批量绑定事件
- 使用CSS3动画代替JS动画
- 避免在低端机上使用大量CSS3渐变阴影效果，可考虑降级效果来提升流畅度
- HTML结构层级保持足够简单
- 尽能少的使用CSS高级选择器与通配选择器





## 结语

坚持一致性的原则。

一个团队的代码风格如果统一了，首先可以培养良好的协同和编码习惯，其次可以减少无谓的思考，再次可以提升代码质量和可维护性。

统一的代码风格，团队内部阅读或编辑代码，将会变得非常轻松，因为所有组员都处在一致思维环境中。 

[Code Guide](http://alloyteam.github.io/code-guide/)
