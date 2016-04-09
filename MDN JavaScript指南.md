#MDN JavaScript指南
##语法和数据类型
####基础知识(Basics)
JS中语句称为statements，并用分号分隔(;)。空格、制表符和换行符被称为空白。JavaScript的脚本的源文本从左到右扫描，并转换成由令牌，控制字符，行结束符，注释或空白组成的输入元素序列。 
####声明(Declarations)
* var:声明变量，可选择将其初始化为一个值
* let:声明块范围局部变量(block scope local variable)，可选择将其初始化为一个值
* const:声明一个只读(read-only)命名常量。

变量的名称称为identifiers，需要遵守一定的规则。

在JS中，一个标识符(identifier)必须以字母、下划线(_)或者美元($)符号开头；后续的字符可以包含数字(0-9)。JS区分大小写。
####声明变量(Declaring variables)
* 使用关键词var，可以同时声明***局部和全局***变量。
* 直接赋值。例如，x = 42。这样就声明了一个全局变量并会导致JavaScript编译时产生一个严格警告。因而你应避免使用这种非常规格式。
* 使用关键词let，声明语句块代码段的局部变量(block scope local variable)。
####对变量求值(Evaluating variables)
用var或let声明的未赋初值的变量，值会被设定为undefined(译注：即为定义值，本身也是一个值)。

* 可以使用undefined来确定变量是否已赋值。
* undefined值在布尔类型环境中会被当作false
* 数值类型环境中undefined值会被转换为NaN(Not a Number)
* 当对一个空变量求值时，空值null在数值类型环境中会被当作0来对待，而布尔类型环境中会被当作false。
####变量的域(Variable scope)
在所有函数之外声明的变量，叫做全局变量，因为它可被当前文档中的其他代码所访问。在函数内部声明的变量，叫做局部变量，因为它只能在该函数内部访问。
####变量声明提升(Variable hoisting)
JS中可以引用稍后声明的变量，即变量声明提升(hoisting)；JS变量感觉上是被“举起”或提升到所有函数和语句之前。然而提升后的变量将返回undefined值，所以即使在使用或引用某个变量之后存在声明和初始操作，仍将得到undefined值。
####全局变量(Global variables)
全局变量实际上是全局对象的属性。在网页中，全局对象是window，所以可以用形如window.variable的语法来设置和访问全局变量。

可以通过指定window或frame的名字，从一个 window或frame访问另一个window或frame中声明的变量。
####常量(Constants)
