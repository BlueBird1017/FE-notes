# CSS3 3D特效

### 要点概览
* transition
* 使用 CSS 3.0 创建简单的3D场景
	- perspective；perspective-origin
	- transform：translate，rotate
* 创建3D动画效果

### transition

CSS3中的动画功能主要分别两部分：

* ***transition***（主要用于使元素从一个属性值平滑过渡到另一个属性值）
* animation（支持通过关键帧技术实现复杂效果）

##### 语法

在CSS中添加如下属性：

```
transition:<过渡属性名称> <过渡时间>
```

注意不用浏览器添加不同的前缀：

	-webkit-transition //Chrome,Safari
	-moz-transition    //Firefox
	-o-transition      //Opera

 例如：
 
 * -webkit-transition:color 1s;
 * -webkit-transtion:height 3s;

```
	<head>
		<style>
			#block{
				width:400px;
				height:400px;
				background-color:#69c;
				margin:0 auto;
				-webkit-transition:background-color:3s;
			}
			#block:hover{
				background-color:red;
			}
		</style>
	</head>
	<body>
		<div id="block">
		</div>
	</body>
```

上例在页面中渲染出一个长宽均为400px的蓝色盒子，当鼠标悬停时，会在三秒内变成红色。
	
##### transition效果分析

```
-webkit-transition:color 1s;
```

实际上是两个属性的缩写：

```
-webkit-transition-property:color;
-webkit-transition-duration:1s;
```
* 实现多个属性的过渡效果：
	- 方法1
		* －webkit-transition:<属性1> <时间1>，<属性2> <时间2>， ......
	- 方法2
		* -webkit-transition:<属性1> <时间1>;
		* -webkit-transition:<属性2> <时间2>;

###### 第三个属性值

```
transition:<过渡属性名称> <过渡时间> <过渡模式>
```

也就是

```
transition-timing-function
```

该属性值主要有以下5个：

属性值	   		|对应效果
-------------|-------------
ease 		   |缓慢开始，缓慢结束
linear	  	   |匀速
ease-in	   |缓慢开始
ease-out	   |缓慢结束
ease-in-out  |缓慢开始，缓慢结束（和ease稍有区别）

当不设置该属性值时，其默认值为```ease```，即缓慢开始，缓慢结束。

### 使用CSS3.0创建简单的3D场景

浏览器本身就是一个2D平面，我们需要增加一个维度（深度）使其成为一个3D空间。







