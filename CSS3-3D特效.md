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

添加属性transition:<过渡属性名称> <过渡时间>

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
	