# 深入理解JavaScript闭包

闭包是指能够访问自由变量的函数。换句话说，定义在闭包中的函数可以“记忆”它被创建时候的环境。

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
