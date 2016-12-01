#CSS布局
整理自：http://zh.learnlayout.com/
##"display"属性
display是css中最重要的用于控制布局的属性。每个元素都有一个默认的display值，这与元素的类型有关。

一个block元素通常被叫做块级元素。一个inline元素通常被叫做行内元素。
###block
div是一个标准的块级元素。一个块级元素会新开始一行并且尽可能撑满容器。其它常用的块级元素包括p、form和HTML5中的新元素：header、footer、section等等。
###inline
span是一个标准的行内元素。一个行内元素可以在段落中包裹一些文字而不会打乱段落的布局。a元素是常见的行内元素，它可以被用作链接。
###none
另一个常用的display是none。一些特殊元素的默认display值是它，例如script。display:none通常被Javascript用来在不删除元素的情况下隐藏或显示元素。
###其它display值
还有很多的更有意思的display值，例如list-item和table。[这里有一份详细的列表](https://developer.mozilla.org/en-US/docs/Web/CSS/display)。之后我们会讨论下inline-block和flex。
###额外加分点
每个元素都有一个默认的display类型。但你可以随时随地重新它。虽然“人工制造”一个行内元素可能看起来很难以理解，不过你可以把特定语义的元素改成行内元素。常见的例子是：把li元素改成inline，制作成水平菜单。
##margin:auto;

	#main {
		width: 600px;
		margin: 0 auto;
	}
设置块级元素的width可以阻止它从左到右撑满容器。然后你就可以设置左右外边距为auto来使其水平居中。元素会占据你所指定的宽度，然后剩余的宽度会一分为二成为左右外边距。（但这其中存在一个问题，当浏览器窗口比元素的宽度还要窄时，浏览器会显示一个水平滚动条来容纳页面。）
##max-width

	#main {
		max-width: 600px;
		margin: 0 auto;
	}	
在这种情况下使用max-width替代width可以使浏览器更好地处理小窗口的情况。这点在移动设备上显得尤为重要。(所有的主流浏览器包括IE7+在内都支持max-width)
##盒子模型
当你设置了元素的宽度，实际展现的元素却能够超出你的设置：因为元素的边框和内边距会撑开元素。

请看下面两个例子，两个相同宽度的元素显示的实际宽度却不一样

	.simple {
		width: 500px;
		margin: 20px auto;
	}
	
	.fancy {
		width: 500px;
		margin: 20px auto;
		padding: 50px;
		border-width: 10px;
	}
之前，CSS开发者需要用比他们实际想要的宽度小一点的宽度时，需要减去内边距和边框的宽度。值得庆幸地是你不需要再这么做了...
##box-sizing
有一个新增的CSS属性叫做box-sizing。当你设置一个元素为box-sizing:border-box;时，此元素的内边距和边框不再会增加它的宽度。

	.simple {
		width: 500px;
		margin: 20px auto;
		-webkit-box-sizing: border-box;
		-moz-box-sizing: border-box;
		box-sizing:border-box;
	}
	
	.fancy {
		width: 500px;
		margin: 20px auto;
		padding: 50px;
		border: solid blue 10px;
		-webkit-box-sizing: border-box;
		-moz-box-sizing: border-box;
		box-sizing: border-box;
	}
这个属性支持IE8+。
##position
为了制作更多复杂的布局，我们需要讨论position属性。它有一大堆的值，名字还都特别抽象
####static

	.static {
		position: static;
	}
static是默认值。任意position: static;的元素不悔被特殊的定位。一个static元素表示它不会被"positioned"，一个position属性被设置为其它值的元素表示它会被"positioned"。
####relative
	
	.relative1 {
		position:relative;
	}
	.relative2 {
		position: relative;
		top: -20px;
		left: 20px;
		background-color: white;
		width:50px;
	}
relative表现的和static一样，除非你添加了一些额外的属性。

在一个相对定位(position:relative;)的元素上设置top、right、bottom和left属性会使其**偏离其正常位置**。其它的元素则**不会调整位置来弥补它偏离后剩下的空隙**。
####fixed
一个固定定位(position:fixed;)元素会相对于视窗来定位，这意味着即便页面滚动，它还是会停留在相通的位置。和relative一样，top、right、bottom和left属性都可用。

	.fixed {
		positon: fixed;
		bottom: 0;
		right: 0;
		width: 200px;
		background-color: white;
	}
一个固定定位元素不会保留它原本在页面应有的空袭。
####absolute
absolute是最棘手的position值。absolute和fixed的表现类似，除了它不是相对于视窗而是相对于最近的"positioned"祖先元素。如果绝对定位(position属性的值为absolute)的元素没有"positioned"祖先元素，那么它是相对于文档的body元素，并且它会随着页面滚动而移动。记住，一个"positioned"元素是值position值不为static的元素。

这里有一个简单的例子：
	.relative {
		position: relative;
		width: 600px;
		height: 400px;
	}
	.absolute {
		position: absolute;
		top: 120px;
		right: 0;
		width: 300px;
		height: 200px;
	}
这部分比较难理解，但它是创造优秀布局所必需的知识。
##position例子
通过具体的例子可以帮助我们更好地理解"position"。下面是一个真正的页面布局。

	.container {
		position: relative;
	}
	nav {
		position: absolute;
		left: 0;
		width: 200px;
	}
	section {
		/* postion is static by default */
		margin-left: 200px;
	}
	footer {
		positon: fixed;
		bottom: 0;
		left: 0;
		height: 70px;
		background-color: white;
		width: 100%;
	}
	body {
		margin-bottom: 120px;
	}
这个例子在容器比nav元素高的时候可以正常工作。如果容器比nav元素低，那么nav会溢出到容器的外面。
##float
另一个布局中常用的CSS属性是float。float可以用于实现文字环绕图片。

	img {
		float: right;
		margin: 0 0 1em 1em;
	}
##claer
clear属性被用于控制浮动。比较下面两个例子：

html:

	<div class="box">...</div>
	<section>...</section>
css:

	.box {
		float: left;
		width: 200px;
		height: 100px;
		margin: 1em;
	}
在这个例子中，section元素实际上是在div之后的(译注:DOM结构上)。然而div元素是浮动到左边的，于是section中的文字就围绕了div，并且section元素包围了整个元素。

	.box {
		float: left;
		width: 200px;
		height: 100px;
		margin: 1em;
	}
	.after-box {
		clear: left;
	}
使用clear可以将after-box移动到浮动元素div下面。你需要用left值才能清除元素的向左浮动。你还可以用right或both来清除向右浮动或同时清除向左向右浮动。
##清除浮动(clearfix hack)
在使用浮动的时候经常会遇到一个古怪的事情：

	img {
		float: right;
	}
当图片比包含它的元素还高时，且它是浮动的，于是它就溢出到了容器外面。

有一种比较丑陋的方法可以解决这个问题，它叫做清除浮动(clearfix hack)

	。clearfix {
		overflow: auto;
	}
这个可以在现在浏览器上工作。如果你想让它支持IE6，你需要再加入如下样式：

	.clearfix {
		overflow: auto;
		zoom: 1;
	}
有些独特的浏览器需要单独设置样式。清除浮动有很大的内涵，但是这个简单的解决方案已经可以在今天所有的主要浏览器上工作。
##百分比宽度
百分比是一种相对于包含块的计量单位。它对图片很有用：如下我们实现了图片宽度适中是容器宽度的50%。

	article img {
		float: right;
		width: 50%;
	}
你甚至还能同时使用min-width和max-width来限制图片的最大或最小宽度。
##媒体查询
"响应式设计(Responsive Design)"是一种让网站针对不同的浏览器和设备"相应"不同显示效果的策略，这样可以让网站在任何情况下显示的很棒。

媒体查询是做此事所需的最强大的工具。让我们使用百分比宽度来布局，然后在浏览器变窄道无法容纳侧边栏中的菜单时，把布局显示成一列：

	@media screen and (min-width:600px) {
		nav {
		float: left;
		width: 25%;
		}
		section {
			margin-left: 25%;
		}
	}
	@media screen and (max-width:599px) {
		nav li {
			display: inline;
		}
	}
现在我们的布局在移动浏览器上也显示的很棒。

####额外加分点
使用meta viewport之后可以让你的布局在移动浏览器上显示的更好。
##inline-block
你可以创建很多网格来铺满浏览器。在过去很长的一段时间内使用float是一种选择，但是使用inline-block会更简单。让我们看下使用这两种方法的例子：
####困难的方式(使用浮动)

	.box {
		float: left;
		width: 200px;
		height: 100px;
		margin: 1em;
	}
	.after-box {
		clear: left;
	}
####容易的方式(使用inline-block)
你可以使用display属性的值inline-block来实现相同效果。

	.box2 {
		display: inline-block;
		width: 200px;
		height: 100px;
		margin: 1em;
	}
你得做些额外工作来让IE6和7支持inline-block。有些时候人们谈到inline-block会触发叫做hasLayout的东西，你只需要知道那时用来支持旧浏览器的。
##inline-block布局
你可以使用inline-block来布局。有一些事情需要你牢记：

* vertical-align属性会影响到inline-block元素，你可能会把它的值设置为top。
* 你需要设置每一列的宽度
* 如果HTML源代码中元素之间有空格，那么列与列之间会产生空隙
##column
这里有一些列新的CSS属性，可以帮助你很轻松的实现文字的多列布局。

	.three-column {
		padding: 1em;
		-moz-column-count: 3;
		-moz-column-gap: 1em;
		-webkit-column-count: 3;
		-webkit-column-gap: 1em;
		column-count: 3;
		column-gap: 1em;
	}
CSS columns是很新的标准，所以你需要使用前缀，并且它不被IE9及以下和Opera Mini支持。
##flexbox
新的flexbox布局模式被用来重新定义CSS中的布局方式。很遗憾的是最近规范变动过多，导致各个浏览器对它的实现也有所不同。使用flexbox你还可以做的更多；这里只是一些让你了解概念的[例子](http://zh.learnlayout.com/flexbox.html)。