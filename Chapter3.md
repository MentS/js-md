## 词法结构

### 区分大小写

ECMAScript 中的一切(变量，函数和操作符)都区分大写。注意在 HTML 中是不区分大小写的

### 标识符

标识符指变量，函数，属性的名字或者 函数的参数。标识符必须满足下列要求

1.  第一个字符 必须是字母，下划线(\_)，或者美元符号($)
2.  其他字符可以是字母，数字，下划线，美元符号
3.  不能是保留字，关键字

### 严格模式

ECAMScript 引入了严格模式(strict mode)的概念。一种不同的解析与执行模型。严格模式下 ECAMScript 中的一些不确定行为将得到处理。对某些不安全的操作抛出错误。在脚本中启用严格模式可以在顶部 添加代码 "strict mode"

### 语句

ECMAScript 中语句以一个分号结尾 ; 如果省略分号，则由解析器确定语句的结尾。 ; 是上一句的结尾标识符，下一句代码开始的标识符(自执行函数的一种实现)。

### 变量

1.  变量是松散类型，即可以保存任何值
2.  每个变量仅仅是一个用于保存值的占位符
3.  变量使用 var 来定义
4.  定义一个变量 但未赋值的变量会保存一个特殊的值 undefined // var message;
5.  全局变量可以通过 window 访问到
6.  省略 var 操作符的变量也会变为 全局变量 // message = 'aa' 全局变量(不推荐) 严格模式会报错

### 数据类型

Javascript 是一种动态类型语言，数据类型在脚本执行时会根据需要自动转换

1.  基本数据类型: undefined, null, boolean, number, string, symbol(ES6)

2.  对象数据类型: Object, Array,Function

### typeof 操作符

typeof 操作符的操作数可以是变量 也可以时值字面量

```javascript
typeof undefined; // undefined
typeof {}; // object
typeof []; // object
typeof ""; // string
typeof 0; // number
typeof function fun() {}; // function
typeof true; // boolean
typeof false; // boolean
10 * "a"; // NaN
```

### Undefined 类型

Undefined 类型只有一个值，即特殊的 undefined。使用 var 声明变量但未给其复制，就是 undefine;

```javascript
var lee;
typeof lee; // undefined
```

### Null 类型

null 类型是第二个只有一个值的数据类型，这个特殊的值是 null.从逻辑角度 null 值表示一个空对象指针,这也是 typeof 操作符 返回 null 的原因。

### Boolean 类型

Boolean 类型只有两个字面值 true 和 false

| 数据类型  | 转换为 true 的值         | 转换为 false 的值 |
| --------- | ------------------------ | ----------------- |
| Undefined |                          | undefined         |
| Null      |                          | null              |
| String    | 任何非空字符串           | ''(空字符串)      |
| Number    | 任何非零数字(包括无穷大) | 0 和 NaN          |
| Object    | 任何对象                 | null              |

### Number 类型

Number 类型使用 IEEE754 格式来表示整数和浮点数。可以表示十进制，八进制，十六进制的字面值来表示，浮点数的计算会存在 精度缺失。

#### 浮点数

浮点数的精度最高是 17 位小数，在进行算数运算是会存在精度缺失。例如 0.1+0.2 不等于 0.3 而是 0.30000000000000004

#### 数值范围

由于内存限制，并不能保存所有的数值。最小值为 5e-324,最大值为 1.7976931348623157e+308。超过范围则表示为正无穷 Infinity
或负无穷-308。超过范围则表示为正无穷 Infinity 或负无穷

#### NaN

NaN, 即非数值(Not a Number) 是一个特殊的数值用于表示一个本来要返回数值的操作树未返回数值的情况。NaN 有两个不同的特点

1.  任何涉及 NaN 的操作都返回 NaN 例如 NaN / 10
2.  NaN 与任何值都不相等，包括自身。

通过这两个特点 ECMAScript 定义了 isNaN()函数。函数接收一个任意类型的参数返回 Boolean 值。

```javascript
// 松散类型 在运行根据需要自动转换
// 显示转换和隐性转换

isNaN(NaN); // true
isNaN(10); // false
isNaN("10"); // false(可以转换为 10)
isNaN("blue"); // false
isNaN(true); // false(转换为数值 1)
```

#### 数值转换

有三个函数可以把非数值转为数值: Number(), parseInt(), parseFloat().Nunmber()用于任何数据类型, 而另外两个专门用于把字符转为数值.三个函数对不同的输入返回不同的结果.
Number() 函数转换规则如下:

1.  如果是 Boolean 值, true 和 false 分别转换为 1 和 0.
2.  如果是数字,只是简单的传入和返回.
3.  如果是 null, 返回 0.
4.  如果是 undefined, 返回 0.
5.  如果是字符串: 遵循以下
    1.  字符串中只包含数字(包扩前面的正负号),将其转换为十进制数值,即 "1" 会变成 1, 而"011" 是 11(前导的 零 被忽略)
    2.  如果字符串中包含有效的浮点格式 如 "1.1", 则将其转为对应的浮点数值(忽略前导的零)
    3.  如果字符串中包含有效的十六进制格式,例如"0xf",将其转换为相同大小的 十进制数值
    4.  如果字符串是空, 转换为 0.
    5.  如果字符串包含出上述格式之外的字符,转为 NaN
6.  如果是对象,则调用 valueOf() 方法,然后按上转换.如果结果是 NaN,则调用对象的 toString()方法.

```JavaScript
Number("Hello 007") // NaN
Number("")          // 0
Number("008")       // 8
Number(true)        // 1
Number(null)        // 0
Number(undefined)   // 0
```

### String 类型

String 类型用于表示零或多个 16 位 Unicode 字符组成的字符序列,即字符串.字符串可以由双引号或单引号表示.

#### 字符串特点

ECMAScript 中的字符串是不可变的,字符串一旦创建,他们的值就不能改变,要改变某个变量保存的字符串,首先要销毁原来的字符串,用心的字符串填充该变量.

#### 转换为字符串

##### toString()

默认情况下以十进制格式返回数值的字符串表示.也可以接受一个参数,表示输出二进制,八进制,等表示.

##### String()

String()函数可以将任何类型的值转换为字符串,遵循以下规则

1.  如果值有 toString()方法,则调用该方法(没有参数),并返回结果
2.  如果值是 null 返回 null ,是 undefined 返回 undecfined

```JavaScript
var num = 10;
num.toString()    // "10"
num.toString(2)   // "1010"
num.toString(8)   // "12"
num.toString(16)  // "a"

String(10)        // "10"
String(true)      // "true"
String(null)      // "null"
String(undefined) // "undefined"
```

### Object 类型

Object 类型所具有的任何属性和方法也同样存在于更具体的对象中.
Object 的每个实例都具有以下属性和方法

1.  Constructor: 保存用于创建当前对象的函数,即构造函数
2.  hasOwnProperty(propertyName): 用于检查给定的属性在当前的实例中是否存在.参数必须以字符串形式
3.  isPrototypeOf(Object): 用于检查传入的对象是否是另一个对象的原型.
4.  propertyIsEnumerble(propertyName): 用于检测给定的属性能否枚举
5.  toLocaleString)(): 返回对象的字符串表示,字符串与执行环境的地区对应
6.  toString(): 返回对象的字符串表示.
7.  valueOf(): 返回对象的字符串,数值或布尔值表示.通常与 toString() 返回值相同.

### 操作符

#### 一元操作符

只能操作一个值的操作符叫做 _一元操作符_ .

##### 递增和递减操作符

1.  前置型: 当有其他操作符时 按照代码顺序 从左到右依次执行
2.  后置型: 当有其他操作符时 先执行 其他操作符
3.  只有递增和递减操作符时 结果一样

```JavaScript
// 后置型
var a = 1;
var b = a++ + 1;
// b = 2, a = 2

// 前置型
var a = 1;
var b = ++a + 1;
// b = 3, a = 2
```

递增和递减操作符遵循以下规则

1.  在应用与一个包含有效数字字符时.先将其转换为数字值,在执行加减 1 的操作,字符串变量变成数值变量
2.  在应用与一个不包含有效数字字符时,将变量设置为 NaN.字符串变为数值变量.
3.  用于布尔值 先转换为 数值 在执行加减 1 操作,布尔值变量变为数字值变量.
4.  用于浮点数时,执行加减 1 的操作
5.  在用于对象时,根据情况调用 valueOf() 或 toString()

### 位操作符

ECMAScript 中的所有数都以 IEEE-754 64 位来表示,在执行位操作符时 64 位的数值先转换为 32 位的数值,在执行位操作符,最后再将 32 位转换为 64 位数值.

#### 按位非(NOT)

按位非操作符由一个波浪线(~) 表示, 操作符的本质是:操作数的负数值 减 1.

#### 按位与(AND)

按位与操作符由一个字符(&) 表示.只有在两个数值的对应位都是 1 时才返回 1,任何一位 是 0,结果都是 0.两边的数值会*自动转换数据类型*

#### 按位或(OR)

按位或操作符由一个字符(|) 表示.只要有一个数值对应位是 1 就返回 1 ,只有都是 0 的时候才返回 0.

#### 按位异或(XOR)

按位异或有符号(^)表示,这个操作在对应位上只有一个 1 时才返回 1,如果对应的两位之都是 1 或 0,则返回 0.

```JavaScript
 ~2018   // -2019

 1 & '1' // 1

 1 & false // 0

 0 | false // 0

 "0" | false // 0

 1 | false  // 1

 1 ^ 1      // 0

 1 ^ 0      // 1

 0 ^ 0      // 0
```
