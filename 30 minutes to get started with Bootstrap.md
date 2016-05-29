# 30 minutes to get started with Bootstrap

### 写在前面

笔记整理自[“阿里百川”《30分钟快速掌握Bootstrap》](http://mp.weixin.qq.com/s?__biz=MzA4MjA0MTc4NQ==&mid=504089744&idx=1&sn=17a6b48b09d8d5794b40c1375ee2391f#rd)一文

### Bootstrap整体架构

初学者可以理解Bootstrap为一个前端样式框架，虽然这样的称谓并不是很准确，但这样的称呼可以让你更快明白Bootstrap到底是一个什么东西。（因为我在刚刚接触Bootstrap的时候就有这样的困惑，没有明白Bootstrap到底是什么。）

对于Bootstrap，首先介绍的是它的整体架构——也就是它到底由什么组成。

![Bootstrap](http://images2015.cnblogs.com/blog/916034/201603/916034-20160320205949584-457012901.png)

* [12栅格系统](#12栅格系统)

就是将屏幕平分成12份（列）。使用行（row）来组织元素（每一行都包括12个列），然后将内容放在列内。通过```col-md-offset-*```来控制列偏移。

* [基础布局组件](#基础布局组件)

Bootstrap提供了多种基础布局组件。如排版、代码、表格、按钮、表单等。

* [CSS组件](#CSS组件)

Bootstrap为我们预实现了很多CSS组件，如下拉框、按钮组、导航等。也就是Bootstrap为我们定义好了很多CSS样式，你可以将这些样式直接应用到对应元素中。

* [JavaScript插件](#JavaScript插件)

Bootstrap也为我们实现了一些JS插件，可以利用其插件直接完成一些功能。

* Jquery

Bootstrap所有的JavaScript插件都依赖于Jquery。如果要使用这些JS插件，就必须引用Jquery库。

* 响应式设计

响应式设计是一种设计理念。所谓响应式就是它会根据屏幕尺寸来自动调整页面，使得前端页面在不同尺寸的屏幕上都可以表现的很好。

### <a name="12栅格系统"></a>12栅格系统

Bootstrap定义12栅格系统，其目的就是为了更好的布局。每个前端框架都首先定义好的就是布局系统。在Bootstrap中，利用行和列来创建页面布局。其布局有几个原则：

* 行（row）必须包含在.container（固定宽度）或.container-fluid（100%宽度）中
* 每行都包含12列
* 将内容放置在每列中

在Bootstrap的栅格系统中，根据宽度将浏览器分为4种。其值分别是：自动（100%）、750px、970px、1170px。

对应的样式为超小（XS）、小型（sm）、中型屏幕（md）、大型（lg）。

（其本质是通过媒体查询定义最小宽度实现。所以，Bootstrap做出来的网页向大兼容，向小不兼容。）

在Bootstrap框架内，已预先定义好了屏幕大小的分界值，其分界值就是通过媒体查询来定义的。其定义方式如下：

	/* 超小屏幕（手机，小于 768px） */
	/* 没有任何媒体查询相关的代码，因为这在Bootstrap中是默认的（在Bootstrap是移动设备优先）*/
	
	/* 小屏幕（平板，大于等于 768px） */
	@media(min-width:@screen-sm-min){...}
	
	/* 中等屏幕（桌面显示器，大于等于992px） */
	@media(min-width:@screen-md-min){...}
	
	/* 大屏幕（大桌面显示器，大于等于1200px）*/
	@media(min-width:@screen-lg-min){...}
	
### <a name="基础布局组件"></a>基础布局组件

基础布局组件就是Bootstrap框架内为一些基础布局的标签定义了一统一的样式。如Table、按钮、表单等。

### <a name="CSS组件"></a>CSS组件

CSS组件和基础布局组件差不多，也就是Bootstrap为一些标签定义了一些已有的样式，同样只要引用即可。

### <a name="JavaScript插件"></a>JavaScript插件

默认情况下，所有的JS插件都可以通过设置特定的HTML代码和相应的属性来实现，而无需写一行JavaScript代码。其实现本质就是Bootstrap为这些属性实现了对应的JavaScript代码。

### 总结

快速的了解之后，你会发现Bootstrap只不过是一个样式框架罢了。利用它我们可以快速方便地构建Web页面。