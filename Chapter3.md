## ECMAScript 基本概念

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
