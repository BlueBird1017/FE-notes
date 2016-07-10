# W3C 中国十周年庆典
## Web的设计原则（胡春明）
### History
* 1994 中国接入互联网，中科院高性能所提供了中国第一套WWW服务器
* 2003 W3C HK Office设立 中国国际万维网发展论坛
* 2006 W3C China Office设计
* 2011 W3C中国总部筹建启动
* W3C/Beihang总部成立
### 什么是Web
* Web：首先是一个“网络” 
* WorldWideWeb：Proposal for a HyperText Project
### 设计原则1:链接
* Web的设计原则之一：链接／Linking
	* Web是一个“资源”网络
	* “资源”是抽象概念
	* 网页是“资源”的表达形式，表达资源的状态
	* URI是资源的标识符，通过URI获取资源
* 资源的自然语言描述与链接
* 资源的（语义）描述
* 当一类新的资源（资源表示）被引入到Web时，应当回答它应当如何被链接、被引用（references）
### 设计原则2:去中心化
* 去中心化／Decentralization
	* 事实上，这不仅是Web的设计原则，也是internet的设计原则
	* example：IRC
	* Web Server上托管了各类“资源”及其“表达”
	* 尽管会有访问量的差别，但在Web的体系结构上，每个Server都是对等的
### 设计原则3:互操作
* 去中心化原则要求同一类资源托管在多个对等的Server上
* 链接原则要求资源相互可以
* W3C在Social Web上的努力

### 用户代理（浏览器）
* 操作系统是构建应用生态的核心
* 操作系统
	* 向上：提供API和编程框架
	* 向下：管理资源
* 构建Web应用生态：浏览器是核心
* OWP：为Web应用提供Application Foundation
## [新眼光看 Web Apps](www.w3.org/2016/Talks/xq-0709-10th)
* Progressive Web Apps
	* Web App Manifest
	* Service Workers
		* Fetch
		* Sync
		* Push
* Houdini
* RAIL 新的思路：Response，Animation，Idle，Load
