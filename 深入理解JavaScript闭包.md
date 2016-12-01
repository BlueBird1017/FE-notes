# 深入理解JavaScript闭包(Closure)

[MDN的javaScript闭包教程](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Closures)中对闭包定义如下：闭包是指能够访问自由变量的函数。换句话说，定义在闭包中的函数可以“记忆”它被创建时候的环境。

### 词法作用域

首先考虑如下的函数：

	function init(){
		var name = "Mozilla"; // name is a local variable created by init
		function displayName(){ // displayName() is the inner function, a closure
			alert(name); //displayName() uses variable declared in the parent function
		}
		displayName();
	}
	init();
	
函数init()创建了一个局部变量name，然后定义了名为displayName()的函数。displayName()是一个内部函数——定义于init()之内且仅在该函数体内可用。displayName()没有任何自己的局部变量，然而它可以访问到外部函数的变量，即可以使用父函数中声明的name变量。

注：在JavaScript中，变量的作用域是由它在源代码中所处位置决定的，并且嵌套的函数可以访问到其外层作用域中声明的变量。

### 闭包

再来看如下例子：

	function makeFunc(){
		var name = "Mozilla";
		function displayName(){
			alert(name);
		}
		return displayName;
	}
	
	var myFcunc = makeFunc();
	myFunc();
	
可以看到字符串"Mozilla"将被显示在一个JavaScript警告框中。displayName()内部函数在执行前被从外围函数中返回了。

### 闭包的实用性

对于闭包的简单理解就是以上这些——那么闭包的应用在哪呢？让我们看看闭包的实践意义。**闭包允许将函数与其所操作的某些数据（环境）关联起来**。这显然类似于面向对象编程。在面向对象编程中，对象允许我们将某些数据（对象的属性）与一个或多个方法相关联。

所以，一般来说，可以使用只有一个方法的对象的地方，都可以使用闭包。

在Web中，可以这样做的情形非常普遍。大部分我们所写的Web JavaScript代码都是**事件驱动**（对应如Vue.JS是数据驱动）——**定义某种行为，然后将其添加到用户触发的事件之上（比如点击或者按键）**。我们的代码通常添加为回调：**响应事件而执行的函数**。

### 用闭包模拟私有方法

诸如Java在内的一些语言支持将方法声明为私有的，即它们只能被同一个类中的其它方法所调用。

对此，JavaScript并不提供原生的支持，但是可以使用闭包模拟私有方法。私有方法不仅仅有利于限制对代码的访问：还提供了管理全局命名空间的强大能力，避免非核心的方法弄乱了代码的公共接口部分。

--
以下笔记参考阮一峰老师的[《学习JavaScript闭包（Closure）》](http://www.ruanyifeng.com/blog/2009/08/learning_javascript_closures.html)。

### 一、变量的作用域

要理解闭包，首先必须理解JavaScript特殊的变量作用域。

变量的作用域无非就是两种：全局变量和局部变量。

JavaScript语言的特殊之处，就在于函数内部直接读取全局变量。

	var n =999;
	
	function f1(){
		alert(n);
	}
	
	f1();// 999
	
另一方面，在函数外部自然无法读取函数内的局部变量。

	function f1(){
		var n=999;
	}
	
	alert(n);// error

这里需要注意的是，函数内部声明变量的时候，一定要使用var命令。如果不用var，你实际上声明了一个全局变量。

	function f1(){
		n=999;
	}
	
	f1();
	
	alert(n); // 999

### 二、如何从外部读取局部变量？

出于种种原因，我们有时候需要得到函数内部的局部变量。但是，前面已经说过了，正常情况下，这是办不到的，只有通过变通方法才能实现。

那就是在函数的内部，再定义一个函数。

	function f1(){
		var n=999;
		
		function f2(){
			alert(n); // 999
		}
	}

在上面的代码中，函数f2被包含在函数f1内部，这时f1内部的所有局部变量，对f2都是可见的。但是反过来，f2内部的局部变量，对f1就是不可见的。这就是JavaScript语言特有的“链式作用域”结构（chain scope），子对象会一级一级地向上寻找所有父对象的变量。所以，父对象的所有变量，对子对象都是可见的，反之则不成立。

既然f2可以读取f1中的局部变量，那么只要把f2作为返回值，我们就可以在f1外部读取它的内部变量了。

	function f1(){
		var n =999;
		
		function f2(){
			alert(n);
		}
		
		return f2;
	}

	var result=f1();
	
	result(); // 999
	
### 三、闭包的概念

上一节代码中的f2函数，就是闭包。理解起来，闭包就是能够读取其它函数内部变量的函数。

由于在JavaScript语言中，只有函数内部的子函数才能读取局部变量，因此可以把闭包简单理解成“定义在一个函数内部的函数”。

所以，在本质上闭包就是将函数内部和函数外部连接起来的一座桥梁。

### 四、闭包的用途

闭包可以用在许多地方。它的最大用处有两个，一个是前面提到的可以读取函数内部的变量，另一个就是让这些变量的值始终保持在内存中。

怎么来理解这句话呢？请看以下代码。

	function f1(){
		var n=999;
		
		nAdd=function(){n+=1}
		
		function f2(){
			alert(n);
		}
		
		return f2;
	}
	
	var result=f1();
	
	result(); // 999
	
	nAdd();
	
	result(); // 1000
	
在这段代码中，result实际上就是闭包f2函数。它一共运行了两次，第一次的值是999，第二次的值是1000。这证明了，函数f1中的局部变量n一直保存在内存中，并没有在f1调用后被自动清除。

为什么会这样呢？原因就在于f1是f2的父函数，而f2被赋给了一个全局变量，这导致f2始终在内存中，而f2的存在依赖于f1，因此f1也始终在内存中，不会在调用结束后，被垃圾回收机制（garbage collection）回收。

这段代码中另一个值得注意的地方，就是"nAdd=function(){n+=1}"这一行，首先在nAdd前面没有使用var关键字，因此nAdd是一个全局变量，而不是局部变量。其次，nAdd的值是一个匿名函数（anonymous function），而这个匿名函数本身也是一个闭包，所以nAdd相当于世一个setter，可以在函数外部对函数内部的局部变量进行操作。

### 五、使用闭包的注意点

1）由于闭包会使得函数中的变量都被保存在内存中，内存消耗很大，所以不能了滥用闭包，否则会造成页面的性能问题，在IE中可能导致内存泄露。**解决方法是，在推出函数之前，将不使用的局部变量全部删除**。

2）闭包会在父函数外部，改变父函数内部变量的值。所以，如果你把父函数当作对象（object）使用，把闭包当做它的公用方法（Public Method），把内部变量当做它的私有属性（private value），这时一定要小心，不要随便改变父函数内部变量的值。

### 六、思考题

如果你能理解下面两段代码的运行结果，应该就算理解闭包的运行机制了。

code1

	var name = "The Window";
	
	var object = {
		name : "My Object",
		
		getNameFunc : function(){
			return function(){
				return this.name;
			};
		}
	};
	
	alert(object.getNameFunc()());
	
code2

	var name = "The Window";
	
	var object = {
		name : "My Object",
		
		getNameFunc : function(){
			var that = this;
			return function(){
				return that.name;
			};
		}
	};
	
	alert(object.getNameFunc()());